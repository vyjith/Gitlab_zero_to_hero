# GitLab Script

* We use script to specify the commands that we want to execute
* We can give single line or multi-line command to execute

```yaml
stages:
  - test
test-job:
  stage: test
  script:
    - echo "This is for just testing..."
    - ./run_test.sh
```

## before_script

* We can use before_script to add commands that must be executedbefore the job’s script section commands
* We can give single-line or multiple-line commands to execute.
* CI/CD variables are supported within the before_script section

```yaml
stages:
  - test
test-job:
  stage: test
  before_script:
    - echo "Setting up the enviornment"
    - ./setup.sh
  script:
    - echo "Running the test"
    - ./run.sh
```

## after_script

* We can use after_script to add the commands that will be executed aftereach job, including the failed jobs.
* **The commands we specify in after_script will be executed in a new shell,which will be separate from any before_script or script commands.**


```yaml
stages:
  - test
test-job:
  stage: test
  script:
    - echo "running the job"
    - ./run.sh
  after_script:
    - echo "Notification has been send"
    - ./notificatio.sh
```

