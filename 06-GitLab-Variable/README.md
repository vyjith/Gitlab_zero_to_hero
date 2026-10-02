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
CI_JOB_NAME: The name of the current job.Example: If you have a job named "build," CI_JOB_NAME will be set to "build."
CI_PIPELINE_ID: The unique identifier of the current pipeline.Example: This variable contains the pipeline ID.
# General/context
CI: true when running in CI
CI_SERVER_URL: the GitLab instance URL
CI_API_V4_URL: API v4 root URL
CI_API_GRAPHQL_URL: GraphQL API URL
CI_DEFAULT_BRANCH: project’s default branch
CI_PROJECT_ID, CI_PROJECT_NAME, CI_PROJECT_NAMESPACE, CI_PROJECT_PATH, CI_PROJECT_URL: project identity details
Commit, repo, and refs
CI_COMMIT_SHA, CI_COMMIT_SHORT_SHA: commit hash
CI_COMMIT_REF_NAME: branch or tag name being built
CI_COMMIT_REF_SLUG: slugified ref name
CI_COMMIT_MESSAGE: full commit message
CI_COMMIT_TAG: tag name (if building a tag)
CI_COMMIT_BEFORE_SHA: previous commit SHA
# Pipeline and job details
CI_PIPELINE_ID, CI_PIPELINE_IID, CI_PIPELINE_SOURCE: pipeline metadata
CI_JOB_ID, CI_JOB_NAME, CI_JOB_STAGE, CI_JOB_STATUS: current job details
CI_JOB_URL, CI_JOB_STARTED_AT: job specifics
CI_NODE_INDEX, CI_NODE_TOTAL: parallel job info (if using parallel)
#Runner and environment
CI_RUNNER_ID, CI_RUNNER_DESCRIPTION, CI_RUNNER_TAGS: runner details
CI_ENVIRONMENT_NAME, CI_ENVIRONMENT_URL, CI_ENVIRONMENT_SLUG, CI_ENVIRONMENT_ACTION, CI_ENVIRONMENT_TIER: environment context
CI_DISPOSABLE_ENVIRONMENT: disposable environment flag
Registry and deployment
CI_REGISTRY, CI_REGISTRY_IMAGE: container registry info
CI_DEPENDENCY_PROXY_* :  Dependency Proxy variables
User and permissions
GITLAB_USER_ID, GITLAB_USER_NAME, GITLAB_USER_EMAIL, GITLAB_USER_LOGIN: user context (depending on visibility)
# Debugging and config
CI_DEBUG_TRACE: enable trace logging
CI_CONFIG_PATH: path to CI config file (usually .gitlab-ci.yml)
```

## pre-defined variables Example 

```yaml
stage:
  - test
test-job
  stage: test
  script:
    - echo "Running test on the branch: $CI_COMMIT_REF_NAME"
    - echo "Building the pipeline ID: $CI_PIPELINE_ID"
```

## Secret variable
We can add CI/CD variables to the project setting. Users with a maintainer role can add/update project CI/CD variables.To add/update variables in the project settings:
1) Select Project’s Settings --> CI/CD and then expand the Variables section1.
2) Select Add variable
