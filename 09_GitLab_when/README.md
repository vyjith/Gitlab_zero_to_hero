# GitLab - CI - when

* We can use when to configure the conditions like when our job will run


### Available inputs:
* on_success (default)
* manual
* delayed
* never
* always
* on_failure

We can use when with rule os dynamic job control

```yaml
stages:
  - build
  - test
  - deploy
build_job:
  stage: build
  script:
    - echo "Just building the enviornment"

test_job:
  stage: test
  script:
    - echo "running tests"
  when: on_success

deploy_job:
  stage: deploy
  script:
    - echo "deploying the job"
  when: manual
```
