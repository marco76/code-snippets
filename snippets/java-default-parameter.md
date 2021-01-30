Java doesn't support a default parameter for the methods.

One common solution is the _method overloading_, e.g.:

```java
String getValue(String firstParameter, String secondParameter) {
//...
}

String getValue(String firstParameter) {
    return getValue(firstParameter, "defaultParameter");
}
```

a less clean approach is to use _null_ values, e.g.:

```java
String getValue(String firstParameter, String secondParameter) {
    if (secondParameter == null) {
        secondParameter = "defaultParameter";
        }
//...
}

```
