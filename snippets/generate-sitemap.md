This code dynamically generates a sitemap in Spring Boot

```java
@RequestMapping(value = "/sitemap.xml", method = RequestMethod.GET,
produces = MediaType.APPLICATION_XML_VALUE)
    @ResponseBody
    public XmlUrlSet main() {
        XmlUrlSet xmlUrlSet = new XmlUrlSet();
        create(xmlUrlSet, "", XmlUrl.Priority.HIGH);
        
        // List<String> containing with your urls
        urls.forEach(
                url -> create(xmlUrlSet, url, XmlUrl.Priority.MEDIUM));

        return xmlUrlSet;
    }
```

```java
@XmlAccessorType(value = XmlAccessType.NONE)
@XmlRootElement(name = "urlset", namespace = "http://www.sitemaps.org/schemas/sitemap/0.9")
public class XmlUrlSet {

    @XmlElements({@XmlElement(name = "url", type = XmlUrl.class)})
    private Collection<XmlUrl> xmlUrls = new ArrayList<>();

    public void addUrl(XmlUrl xmlUrl) {
        xmlUrls.add(xmlUrl);
    }

    public Collection<XmlUrl> getXmlUrls() {
        return xmlUrls;
    }
}
```

## Possible errors

### Bing

No issues with Bing, it digest everything ;-)

### Google

_The sitemap doesn't appear immediately in the results after the submission_

The answer has to be `MediaType.APPLICATION_XML_VALUE`, if forgotten the xml will not be processed (http will answer with a json header) without any error message.


_Error: Your Sitemap or Sitemap index file doesn't properly declare the namespace._

Google doesn't like if you have multiple namespaces`prefixes declared. ex.:

```xml
<ns2:urlset xmlns:ns2="http://www.sitemaps.org/schemas/sitemap/0.9">
<url>
<loc>https://marco.dev</loc>`
```

To make Google happy add a `package-info.java` to your package and add the followin line:
```java
@javax.xml.bind.annotation.XmlSchema(namespace = "http://www.sitemaps.org/schemas/sitemap/0.9", elementFormDefault = javax.xml.bind.annotation.XmlNsForm.QUALIFIED, xmlns = { @javax.xml.bind.annotation.XmlNs(namespaceURI = "http://www.sitemaps.org/schemas/sitemap/0.9", prefix = "") })
package ... // your package
```

This will remove the namespace from the xml file
