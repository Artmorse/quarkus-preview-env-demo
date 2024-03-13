# dummy-api

This project is a dummy-api using Quarkus.

## How to build the docker image

https://quarkus.io/guides/container-image#docker

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
curl http://localhost:8080/hello
```

## Configure CI

You need to creates 2 secrets in your repository:
- DOCKER_USERNAME: your docker hub registry account name
- DOCKER_PASSWORD: your docker hub password