# GitLab Nees

* We can use needs to execute job in any order
* We can ignore stages orders and run any random job in another stages without waiting for previous stage jobs get completed.

```yaml
stages:
  - build
  - test
  - deploy

build_job:
  stage: build
  needs: []
  script:
    - echo "echo building the stage enviornement"
test_job:
  stage: test
  needs: [build_job]
  script:
    - echo "building the test job since we got the successfull from the above"
deploy_job:
  stage: deploy
  needs: []
  script:
    - echo "This is parallely executing"
```yaml
