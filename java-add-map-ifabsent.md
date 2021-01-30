---
title: How to add a value to a map only if key not present
description: Add a value to a map in Java only if value absent or null
date: 2021-01-21T01:41:48+00:00
author: marco
main-class: java
permalink: /snippet/marco/map-putIfAbsent
categories:
reference:

---
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
