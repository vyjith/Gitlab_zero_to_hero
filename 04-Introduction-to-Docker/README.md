# Introduction

* Docker is a software containarization platform

## So I am going to write a basic Docker image so you can use the following image file as Dockerfile

```yaml
FROM nginx:latest
WORKDIR /usr/share/nginx/html
COPY index.html .
EXPOSE 80
```

## The following command we will use in our upcoming section



* docker build -t registry.gitlab.com/your-namespace/your-repo/my-html-app:latest .
* docker login registry.gitlab.com
* docker push registry.gitlab.com/your-namespace/your-repo/my-html-app:latest
