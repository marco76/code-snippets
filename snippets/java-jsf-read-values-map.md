## Use a hash map to store your UI values in JSF

Your Backing Bean doesn't have to declare explicitly all the variables that appear in your facelets. You can easily store the values in a Map.

```html
<h:inputText value="#{backingBean.valuesMap['VALUE_NAME']}">
```

```java

private Map<String, Object> valuesMap = new HashMap();

public Map<String, Object> getValuesMap() {
    return valuesMap;
}
```