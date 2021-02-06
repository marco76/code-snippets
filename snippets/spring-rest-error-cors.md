Building a Spring application with a web client when you deploy the application on 2 different servers or ports you could get this error when you try a REST call:

`Access to XMLHttpRequest at '[url]' from origin '[url]' has been blocked by CORS policy: Response to preflight request doesn't pass access control check: No 'Access-Control-Allow-Origin' header is present on the requested resource.`

By default, for security reasons, the application server doen't allow that clients running in other machines use your service without authorization.

For an intranet / secured network application you can simply allow all the request to be executed

```java
import org.springframework.web.bind.annotation.CrossOrigin;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
@CrossOrigin("*")
public class FoodController {
```

The `*` accepts requests from every origin, for production environments you have to fine tune this parameter. 

To see in the detail the feature:

(@CorsOrigin source code)[https://github.com/spring-projects/spring-framework/blob/master/spring-web/src/main/java/org/springframework/web/bind/annotation/CrossOrigin.java]

(CorsConfiguration source code)[https://github.com/spring-projects/spring-framework/blob/master/spring-web/src/main/java/org/springframework/web/cors/CorsConfiguration.java]