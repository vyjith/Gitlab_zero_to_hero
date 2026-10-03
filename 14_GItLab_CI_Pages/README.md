# Git lab CI pages

GitLab Pages allows you to publish static websites directly from your repository inGitLa

* We can host our site on our own GitLab instance or over GitLab.com for free.
* We can also connect our custom domains and TLS certificate.

## How it works

1. Project: Create a project in GitLab, be it public, or private.
2. Content: Store your website's files within the project repository.
3. Deployment Folder: GitLab Pages specifically deploys content located inthe public folder within your repository.
4. CI/CD  Configuration:  Define  a  configuration  file  named  .gitlab-ci.yml  toinstruct GitLab CI/CD on building and deploying your website.
5. Pages Job: Within the .gitlab-ci.yml file, you'll define a specific job named"pages" to initiate the GitLab Pages deployment process.
6. Domains: You can choose to use either:
   * GitLab  default  domain:  Your  website  will  be  accessible  under  asubdomain like your-username.gitlab.io
   * Custom domain: If you own a domain, you can configure it with GitLabPages for a personalized website address.

```yaml
pages:
  script:
    - mkdir public
    - cp *.html public/
  artifacts:
    path:
      - public
```
