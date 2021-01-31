_SpringBoot MariaDB connection_

In `application.properties`:

```
spring.datasource.url=jdbc:mariadb://[SERVER]:[PORT]/[DATABASE_NAME]
spring.datasource.username=[USER_NAME]
spring.datasource.password=[PASSWORD]
spring.jpa.database-platform=org.hibernate.dialect.MariaDBDialect
```

example:

```
spring.datasource.url=jdbc:mariadb://localhost:3306/database_example
spring.datasource.username=my_user
spring.datasource.password=my_password
spring.jpa.database-platform=org.hibernate.dialect.MariaDBDialect
```

_Possible errors:_

`2021-01-31 20:18:04.525 WARN 14261 --- [nio-8080-exec-4] o.h.engine.jdbc.spi.SqlExceptionHelper : SQL Error: 1046, SQLState: 3D000 2021-01-31 20:18:04.526 ERROR 14261 --- [nio-8080-exec-4] o.h.engine.jdbc.spi.SqlExceptionHelper : (conn=26) No database selected`

The `DATABASE_NAME` was not in the url. The database name is called 'schema' in IntelliJ and 'catalog' in `@Table`.