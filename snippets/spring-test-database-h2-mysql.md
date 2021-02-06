If in Spring Boot you are using a database you can use for your tests H2 or another similar embedded database.

In our case we are using MySQL / PostgreSQL for production and we want to test our code using `@DataJpaTest`.

Some relevant information from the documentation:

> Annotation for a JPA test that focuses only on JPA components.
> Using this annotation will disable full auto-configuration and instead apply only configuration relevant to JPA tests.
> By default, tests annotated with @DataJpaTest are transactional and roll back at the end of each test. They also use an embedded in-memory database (replacing any explicit or usually auto-configured DataSource).

### Include the DB in the classpath

In our case we use H2, we import the library in Maven

```xml
<dependency>
    <groupId>com.h2database</groupId>
    <artifactId>h2</artifactId>
    <scope>test</scope>
</dependency>
```

You have to tell to spring to use the H2 database during the tests, for this you have to create `/src/test/resources/application.properties` with the connection information for H2

```bash
spring.datasource.driver-class-name=org.h2.Driver
spring.datasource.url=jdbc:h2:mem:testdb;DB_CLOSE_DELAY=-1
spring.datasource.username=sa
spring.datasource.password=sa
```

We create the test class with the required dependencies

```java
import org.junit.jupiter.api.Test;
import org.junit.runner.RunWith;
import org.springframework.boot.test.autoconfigure.orm.jpa.DataJpaTest;
import org.springframework.test.context.junit4.SpringRunner;
import org.springframework.transaction.annotation.Propagation;
import org.springframework.transaction.annotation.Transactional;

import static org.assertj.core.api.Assertions.*;

@RunWith(SpringRunner.class)
@DataJpaTest
@Transactional(propagation = Propagation.NOT_SUPPORTED)
class FoodControllerTest {

    @Autowired
    FoodRepository carbsRepository;

    @Test
    void createFood() {
       ...
       foodRepository.save(carbs);
       assertThat(foodRepository.count()).isEqualTo(1);
    }
```