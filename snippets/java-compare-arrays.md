## Compare two arrays in Java

To check if 2 arrays have the same content in Java you can use the function `Arrays.equals(Object[], Object[])`.

The function compares the arrays and return true if the arrays contain the same values in the same order or they are null.

The function accepts primitives (bytes, float etc.) and Objects.

Example

```java
if (Arrays.equals(md5, updatedMd5)) {
    ...
}
```
