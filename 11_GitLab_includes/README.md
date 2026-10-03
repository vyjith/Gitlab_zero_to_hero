# GitLab includes

### The include keyword is used in the .gitlab-ci.yml file to include externalYAML files. This helps in modularizing the CI/CD configuration and reusingcommon settings or templates across multiple projects.


#### Possible inclueds

- [include:local](https://docs.gitlab.com/ci/yaml/#includelocal)
- [include:project](https://docs.gitlab.com/ci/yaml/#includeproject)
- [include:remote](https://docs.gitlab.com/ci/yaml/#includeremote)
- [include:template](https://docs.gitlab.com/ci/yaml/#includetemplate)


## Include Example

## Project strcuture

```yaml
gitlab-project/
│
├── .gitlab-ci.yml
│
└── .gitlab/
    └── ci/
        ├── build.yml
        └── test.yml
```

1. Main .gitlab-ci.yml

```yaml
include:
  - local: '.gitlab/ci/build.yml'
  - local: '.gitlab/ci/test.yml'

stages:
  - build
  - test
```
2. .gitlab/ci/build.yml

```yaml
build_job:
  stage: build
  script:
    - echo "Building application"
    - echo "Build completed"
```

3. .gitlab/ci/test.yml

```yaml
test_job:
  stage: test
  script:
    - echo "Running tests"
    - echo "Tests completed"
```

## How it works:

```yaml
.gitlab-ci.yml
      |
      | include:local
      |
      +---------> .gitlab/ci/build.yml
      |                 |
      |                 v
      |             build_job
      |
      +---------> .gitlab/ci/test.yml
                        |
                        v
                    test_job
```
