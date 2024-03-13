# dummy-api

This project is a dummy-api using Quarkus.

## How to build the docker image

```bash
mvn install -Dquarkus.container-image.build=true
```

Verify the image has been created.
```bash
docker images
```

Run the container.
```bash
docker run --rm -p 8080:8080 acaron/dummy-api:1.0.0-SNAPSHOT
```

Test the API
```bash
curl http://localhost:18080/hello
```