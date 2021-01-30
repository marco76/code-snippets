To execute a scheduled event in Spring you can use the annotation `@Scheduled`.

You have to remember to annotate the service or component with `@EnableScheduling`. This annotation enables the detection of `@Scheduled`.

You can use the following attributes:
- cron: UNIX tyle expression, e.g. `0 * * * * MON-FRI`
- fixedDelay
- fixedRate 

The method should not have arguments and it should not return any value (`void`), the return value is ignored by the scheduler. If the method is called directly the return method is read by the caller.

```java
// the parameter passed is in milliseconds, 5*60*1000 => 5 minutes 
@Scheduled(fixedRate = 5*60*1000)
public void refreshList() {
    // ...
```

## Documentation

[Official JavaDoc](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/scheduling/annotation/EnableScheduling.html)

[Spring.io Example](https://spring.io/guides/gs/scheduling-tasks/)
