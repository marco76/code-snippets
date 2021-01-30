Sometimes I see the following code (or similar):

```java
if (map.get("property") == null) {
    map.put(value)
 }
```

The goal is to avoid to overwrite an existing value in the map.

Since Java 8 it's much easier to use:

```java
map.putIfAbsent("property", value);
```

Internally the method simply checks if the property is defined, if it's not defined the value is added.

```java
default V putIfAbsent(K key, V value) {
        V v = get(key);
        if (v == null) {
            v = put(key, value);
        }

        return v;
    }
```
