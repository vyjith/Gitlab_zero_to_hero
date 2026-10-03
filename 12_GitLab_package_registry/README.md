# GitLab CI - Package Registry

## GitLab includes a Package Registry feature that allows you to store and managevarious types of packages such as Maven packages, NPM packages, and more.

You can view your packages for your project by following the below steps:Go to the project1.
Go to Deploy > Package Registry.2.
We can use GitLab CI/CD to build or import packages into your package registry.

## GitLab CI - Container Registry

GitLab CI/CD (Continuous Integration/Continuous Deployment) and GitLabContainer Registry are powerful features within the GitLab platform that helpautomate the software development lifecycle and manage Docker containerimages.
We can check the container registry for our project:
* For a project, select Deploy > Container Registry.

**Note: Only members of a private project will be able to access the containerregistry.**

```yaml
image: docker:27

services:
  - docker:27-dind

stages:
  - build

variables:
  DOCKER_HOST: tcp://docker:2375
  DOCKER_TLS_CERTDIR: ""
  CONTAINER_REGISTRY: registry.gitlab.com
  USERNAME: Vyjith
  PROJECT: this-fortestsing
  CONTAINER_IMAGE: $CONTAINER_REGISTRY/$USERNAME/$PROJECT

before_script:
  - docker login -u CI_REGISTRY_USER -p CI_REGISTRY_PASSWORD $CONTAINER_REGISTRY

build:
  stage: build
  script:
    - docker build -t $CONTAINER_IMAGE
    - docker push $CONTAINER_IMAGE
```

## You can use the following Docker file image and index.html file for this project

1. Dockerfile

```yaml
FROM nginx:latest

# Copy your content files (webpages, static assets)
COPY index.html /usr/share/nginx/html

# Start nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]
```
2. index.html

```yaml
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Light Demo Page</title>
  <style>
    body {
      font-family: sans-serif;
      background-color: #f2f2f2;
      margin: 0;
      padding: 20px;
    }

    h1 {
      font-size: 3em;
      color: #333;
      margin-bottom: 12px;
    }

    p {
      line-height: 2;
      color: #666;
    }
  </style>
</head>
<body>
  <h1>Welcome to the Demo Page!</h1>
  <p>This is a simple example of an HTML Page deployed via GitLab CI/CD</p>
</body>
</html>

```
