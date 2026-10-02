# GitLab CI - rules

#### GitLab CI rules provide a powerful way to control the inclusion or exclusion ofjobs in a pipeline based on various conditions.

**Rules are always evaluated in the defined order until the first rule matches.**

```yaml
rules:
  - exists('file.txt')
  - changes('src/**/*')
  - $CI_COMMIT_BRANCH == "main"
```

```yaml
Rule 1 ── match? ──YES──> RUN JOB
   │
   NO
   ↓
Rule 2 ── match? ──YES──> RUN JOB
   │
   NO
   ↓
Rule 3 ── match? ──YES──> RUN JOB
   │
   NO
   ↓
JOB NOT ADDED
```

## Example 1

```yaml
stages:
  - build
docker_build_job:
  stage: build
  rules:
    - if: $CI_COMMIT_BRANCH == "main"
  script:
    - echo "Build Job"
```

## Example 2

```yaml
stages:
  - build
docker_build_job:
  stage: build
  rules:
    - if: $CI_PIPELINE_SOURCE == "merge_request_event"
  script:
    - echo "Build Job"
```
