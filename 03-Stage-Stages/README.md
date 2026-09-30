# GitLab CI - Stages
**Definition:** Stages in GitLab CI determine when to execute jobs and provide a structured approach
to the CI/CD pipeline.


## The following is the one sample yaml file syntax

```yaml
stages:
  - build
  - test
variables:
  MY_VARIABLE: "Hello World"
build_job:
  stage: build
  script:
    - echo "Building the project..."
test_job:
  stage: test
  script:
    - echo "Running tests..."
    - echo "$MY_VARIABLE"
```


In GitLab, the Default pipeline stages are:
[] .pre
[] build
[] test
[] deploy
[] .post
.pre -> will always be the first stage, we cannot change it.
.post -> will always be the last stage, we cannot change it as well.
builds, test & deploy -> these stages sequence we can change