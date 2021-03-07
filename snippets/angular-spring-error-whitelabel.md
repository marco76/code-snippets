
### Fix the Whitelabel error when you deploy an Angular application in Spring Boot 

Angular is a frontend application and doesn't manage directly url adresses like 'mywebsite.com/myPage'. The request from your browser goes to the server that cannot find the 'myPage' page because is declared in your Angular routing.

```
Whitelabel Error Page

This application has no explicit mapping for /error, so you are seeing this as a fallback.

Sun Mar 07 09:22:25 UTC 2021
There was an unexpected error (type=Not Found, status=404).
```

You can quickly fix the problem rerouting the pages that Spring cannot find to the root of the website.

The router of Angular will display the correct page.

```java
@Configuration
public class WebRoutingConfig implements WebMvcConfigurer {

    @Override
    public void addViewControllers(ViewControllerRegistry registry) {
        registry.addViewController("/urlNotFound")
                // the viewName should be specified, in our case we forward to the index.html
                .setViewName("forward:/index.html");
    }

    @Bean
    public WebServerFactoryCustomizer<ConfigurableServletWebServerFactory> containerCustomizer() {
        return container -> {
            container.addErrorPages(new ErrorPage(HttpStatus.NOT_FOUND,
                    "/urlNotFound"));
        };
    }

}
```

