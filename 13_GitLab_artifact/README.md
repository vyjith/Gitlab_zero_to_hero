# GitLab CI - artifacts

- We can attach useful files and directories as artifacts to the job when itsucceeds, fails, or always.
- The artifacts are collected on GitLab after the job finishes.
- We can download the artifacts from the GitLab UI.
- By default, the jobs in later stages automatically fetch all the artifacts uploaded by the jobs in earlier stages

## The artifact Example

```yaml
stages:
  - scan

docker_scan_job:
  stage: scan
  script:
    - ./scan.sh
  artifacts:
    paths:
      - $CI_PROJECT_DIR/
```

## artifacts:exclued

```yaml
stages:
  - build
  - test
docker_job_build:
  stage: build
  script:
    - echo "Docker build "
  artifacts:
     paths:
       - $CI_PROJECT_DIR
     exclude:
       - Dockerfile
```

## artfacts:expire_in

```yaml
stages:
  - build
  - test
docker_job_build:
  stage: build
  script:
    - echo "Docker build "
  artifact:
     paths:
       - $CI_PROJECT_DIR
     expire_in: 1 week
```
