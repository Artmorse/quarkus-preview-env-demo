# Setup

https://quarkus.io/guides/rest-json

```bash
mvn io.quarkus.platform:quarkus-maven-plugin:3.6.7:create \
    -DprojectGroupId=dummy.app \
    -DprojectArtifactId=quarkus-preview-env-demo \
    -Dextensions=resteasy-reactive-jackson

mvn quarkus:add-extension -Dextensions='container-image-docker'
```

https://quarkus.io/guides/deploying-to-kubernetes

```bash
mvn quarkus:add-extension -Dextensions='quarkus-kubernetes'
```
