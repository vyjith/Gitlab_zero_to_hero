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
stages:
  - build
variables:
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
