# In git lab there is two main thing one build and stage

## The below is the one sample GitLab pipeline

```yaml
stages:
  - build

job-build:
  step: build
  script: 
    - echo "running the job"
    - whoami

```

**build** --> Stage
**job-build** --> Job
