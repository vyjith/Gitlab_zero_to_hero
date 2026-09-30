# GitLab Zero to Hero 🚀

A practical learning repository to understand **GitLab CI/CD from basics to advanced concepts**, with hands-on examples and real-world DevOps scenarios.

## 📚 What This Repository Covers

* GitLab CI/CD fundamentals
* `.gitlab-ci.yml`
* Pipelines
* Stages
* Jobs
* Scripts
* GitLab Runner
* Docker Executor
* Variables
* Artifacts
* Cache
* Dependencies
* Rules
* Manual jobs
* Environment management
* Docker image build and push
* CI/CD best practices
* Real-world deployment scenarios

---

## 🔹 GitLab Pipeline Basics

A GitLab pipeline consists of different **stages**, and each stage contains one or more **jobs**.

### Example

```yaml
stages:
  - build

job-build:
  stage: build
  script:
    - echo "Running the build job"
    - whoami
```

### Understanding the Pipeline

```text
Pipeline
   │
   ▼
Stage
   │
   └── build
         │
         ▼
       Job
         │
         └── job-build
               │
               ├── echo "Running the build job"
               └── whoami
```

### Stage vs Job

| Component      | Purpose                            |
| -------------- | ---------------------------------- |
| `stages`       | Defines the stages of the pipeline |
| `build`        | Name of a stage                    |
| `job-build`    | Name of a job                      |
| `stage: build` | Assigns the job to the build stage |
| `script`       | Commands executed by the job       |

### Important

**Stage is not the actual work.**

A stage is a logical phase of the pipeline.

A **job performs the actual work**.

For example:

```yaml
stages:
  - build
  - test
  - deploy

build-application:
  stage: build
  script:
    - echo "Building application"

test-application:
  stage: test
  script:
    - echo "Running tests"

deploy-application:
  stage: deploy
  script:
    - echo "Deploying application"
```

The pipeline flow is:

```text
build
  ↓
test
  ↓
deploy
```

---

## 🔹 Multiple Jobs in One Stage

A stage can contain multiple jobs.

```yaml
stages:
  - build

build-application:
  stage: build
  script:
    - e
```
