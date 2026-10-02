# GitLab Variables

* GitLab allows you to define environment variables that can beused in your CI/CD pipelines.
* These variables are set globally for a project and can beaccessed by jobs during pipeline execution.
* GitLab CI/CD variables are specific to the CI/CD pipelines andare used to customize the pipeline behavior.
* GitLab follows a specific order of precedence for variables:CI/CD variables override project-level variables, which, in turn,override group-level variables

```yaml
stages:
  - build
variables:
  MY_VARIABLE: "Hello world!"
build-job:
  stage: build
  script:
    - echo $MY_VARIABLE
```

## pre-defined variables

**In GitLab CI/CD, predefined variables are variables that are set byGitLab and are available for use in your CI/CD pipeline scripts withoutexplicit definition.**

```yaml
CI_JOB_NAME:Description: The name of the current job.Example: If you have a job named "build," CI_JOB_NAME will be set to "build."
CI_PIPELINE_ID:Description: The unique identifier of the current pipeline.Example: This variable contains the pipeline ID.
```
