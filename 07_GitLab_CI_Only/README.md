# GitLab CI - Only, Except

#### GitLab CI (Continuous Integration) uses a configuration file (usuallynamed .gitlab-ci.yml) to define how jobs are executed. Two importantkeywords in GitLab CI configuration are only and except. Thesekeywords help control when a job should or should not run based onspecified conditions

* Only: Helps to define when a job runs
* Except: Helps to define when a job does not run

```yaml
stage:
  - build
  - test

build-job:
  stage: build
  only:
    - main
  script:
    - echo "Building starting"
docker-test-job:
  stage: test
  except:
    - main
  before_script:
    - echo "Image verification Started"
  script:
    - echo "Test completed"
```
