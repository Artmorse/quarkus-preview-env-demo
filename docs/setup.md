# Setup

https://quarkus.io/guides/rest-json

```bash
mvn io.quarkus.platform:quarkus-maven-plugin:3.6.7:create \
    -DprojectGroupId=dummy.app \
    -DprojectArtifactId=dummy-api \
    -Dextensions=resteasy-reactive-jackson

mvn quarkus:add-extension -Dextensions='container-image-docker'
```
