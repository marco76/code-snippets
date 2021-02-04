## How to determine if an array contains a value in Java

Sometimes we have to record a short list of values in Java and check if a parameter or value is contained in this list.

This code avoid the usage of `if` or more complex constructs.

### Using a Set

```java
Set<String> VALUES = Set.of("First", "Second", "Third");
boolean isInside = VALUES.contains("First");
```

### Using a strean

```java
String[] values = {"First", "Second", "Third"};

boolean isInside = Arrays.stream(values).anyMatch("value"::equals);
```