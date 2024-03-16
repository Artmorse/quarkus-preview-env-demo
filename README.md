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

## How to setup preview environments

I've created the [_preview_ directory](/preview) with Helm templates based on the kubernetes ones (generated previously).
They'll be used by our ArgoCD application to create preview environments.

## Configure CI

You need to create 2 secrets in your repository:
- DOCKER_USERNAME: your docker hub registry account name
- DOCKER_PASSWORD: your docker hub password

## Setup ArgoCD application

Follow [this documentation](argocd/) to set up ArgoCD application.
