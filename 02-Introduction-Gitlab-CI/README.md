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
    - echo "Building application"

build-docker-image:
  stage: build
  script:
    - echo "Building Docker image"
```

Both jobs belong to the same `build` stage.

```text
             ┌── build-application
             │
build stage ─┤
             │
             └── build-docker-image
```

When there are no dependencies between them, GitLab can execute jobs in the same stage in parallel, depending on available runners.

---

## 🛠️ Basic GitLab CI/CD Structure

A typical `.gitlab-ci.yml` file looks like:

```yaml
stages:
  - build
  - test
  - deploy

build:
  stage: build
  script:
    - echo "Build application"

test:
  stage: test
  script:
    - echo "Run tests"

deploy:
  stage: deploy
  script:
    - echo "Deploy application"
```

---

## 📂 Repository Structure

```text
Gitlab-zero-to-hero/
│
├── README.md
│
├── 01-gitlab-basics/
│   └── .gitlab-ci.yml
│
├── 02-stages-and-jobs/
│   └── .gitlab-ci.yml
│
├── 03-gitlab-runner/
│   └── README.md
│
├── 04-docker-runner/
│   └── .gitlab-ci.yml
│
├── 05-variables/
│   └── .gitlab-ci.yml
│
├── 06-artifacts/
│   └── .gitlab-ci.yml
│
├── 07-cache/
│   └── .gitlab-ci.yml
│
└── 08-real-world-pipeline/
    └── .gitlab-ci.yml
```

---

## 🎯 Learning Goal

The goal of this repository is to move from:

```text
GitLab Basics
      ↓
GitLab CI/CD
      ↓
GitLab Runner
      ↓
Docker Executor
      ↓
Build & Test
      ↓
Artifacts & Cache
      ↓
Docker Image
      ↓
Container Registry
      ↓
Deployment
      ↓
Production CI/CD
```

---

## 👨‍💻 DevOps Focus

This repository is created as a **hands-on DevOps learning project**.

The examples are intentionally simple at the beginning and gradually move toward production-style GitLab CI/CD pipelines.

### Topics to Practice

* Linux
* Git
* GitLab
* GitLab CI/CD
* Docker
* Kubernetes
* Terraform
* AWS
* CI/CD automation

---

## 🚀 Getting Started

Clone the repository:

```bash
git clone git@github.com:vyjith/Gitlab_zero_to_hero.git
cd Gitlab-zero-to-hero
```

Create a `.gitlab-ci.yml` file:

```yaml
stages:
  - build

job-build:
  stage: build
  script:
    - echo "Hello GitLab CI/CD"
    - whoami
```

Commit and push:

```bash
git add .
git commit -m "Add first GitLab pipeline"
git push
```

GitLab will detect the `.gitlab-ci.yml` file and create a pipeline.

---

## 📌 Key Concept

> **Pipeline → Stages → Jobs → Scripts**

For example:

```text
Pipeline
   │
   ├── Build Stage
   │      ├── Build Application Job
   │      └── Build Docker Image Job
   │
   ├── Test Stage
   │      ├── Unit Test Job
   │      └── Security Scan Job
   │
   └── Deploy Stage
          └── Deploy Application Job
```

---

## 📖 Progress

* [x] GitLab stages and jobs
* [x] GitLab Runner
* [ ] Docker Executor
* [ ] GitLab Variables
* [ ] Artifacts
* [ ] Cache
* [ ] Rules
* [ ] Manual Jobs
* [ ] Docker Build
* [ ] Container Registry
* [ ] Kubernetes Deployment
* [ ] Production CI/CD Pipeline

---

⭐ **Learning GitLab CI/CD by building real pipelines step by step.**
