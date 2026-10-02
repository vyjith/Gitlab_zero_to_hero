# GitLab CI - Timeout

* We can use a timeout value to configure a timeout for a specific job.
* If our job is running for longer than the timeout, the job will fail.
* We can configure the job-level timeout longer than the project-leveltimeout, but it cannot be longer than the runner's timeout

### Possibe inputs

* 30 seconds
* 20 minutes
* 2h 10m


```yaml
stages:
  - test
test_job:
  stage: test
  script:
    - echo "Timeout Example"
    - sleep 80
  timeout: 10s
```
