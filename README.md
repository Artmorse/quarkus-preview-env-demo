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

## How to generate kubernetes manifests

https://quarkus.io/guides/deploying-to-kubernetes

Adding this dependency and running `mvn verify` a `kubernetes.yml` file will be generated in the `target/kubernetes` directory.

Follow the documentation above to configure specific Kubernetes configuration (we'll configure this in the CI).

You can test to apply the manifest locally using [kind](https://kind.sigs.k8s.io/) by running these commands:
```bash
k create ns dummy-api
kubens dummy-api
kubectl apply -f target/kubernetes/kubernetes.yml
```

:warning: the docker image needs to be created before applying the manifest.

Clean the environment by running:
```bash
k delete ns dummy-api
```

## Configure CI

You need to create 2 secrets in your repository:
- DOCKER_USERNAME: your docker hub registry account name
- DOCKER_PASSWORD: your docker hub password