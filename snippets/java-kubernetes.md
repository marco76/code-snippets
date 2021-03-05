not published
## Basic configuration of Java in Kubernetes

This is just a summary of the following articles and twit. I wrote the infomation here to easily find it in the future. The value of the content is to attribute to the authors.

https://twitter.com/brunoborges/status/1365198025824477184?s=21


https://tech.olx.com/improving-jvm-warm-up-on-kubernetes-1b27dd8ecd58

Point to take in consideration when a Java app is deployed in Kubernetes.

- JVM selects G1GC by default only when the JVM sees more than 1792 MB of available memory and 2 processors (2000m+ in k8s). With less resources SerialGC is selected.
_Solution:_ force --XX:+UseG1GC