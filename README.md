# GitLab CI/CD Demo Project

This document outlines the steps to create and trigger a basic CI/CD pipeline in GitLab.

## 1. Local Project Setup

1.  Create a new local directory for your project.
    ```bash
    mkdir gitlab-cicd-demo
    cd gitlab-cicd-demo
    ```

2.  Initialize it as a Git repository.
    ```bash
    git init -b main
    ```

3.  Create the website's main file.
    ```bash
    echo "<h1>Hello GitLab CI/CD!</h1>" > index.html
    ```

4.  Create the GitLab CI/CD configuration file.
    ```bash
    # Create a file named .gitlab-ci.yml and add the content below
    ```

    **`.gitlab-ci.yml`**
    ```yaml
    image: alpine:latest

    stages:
      - build
      - test

    build_website:
      stage: build
      script:
        - mkdir public
        - cp index.html public/
      artifacts:
        paths:
          - public

    test_website:
      stage: test
      script:
        - grep "Hello GitLab CI/CD!" public/index.html
    ```

5.  Add and commit all files.
    ```bash
    git add .
    git commit -m "Initial commit with website and CI pipeline"
    ```

## 2. GitLab Project Setup

1.  On GitLab, create a new, blank project named `gitlab-cicd-demo`.
2.  Do **not** initialize it with a README.
3.  Copy the repository's HTTPS URL from the project page.

## 3. Triggering the Pipeline

1.  Connect your local repository to the remote GitLab repository.
    ```bash
    git remote add origin <PASTE_YOUR_GITLAB_URL_HERE>
    ```

2.  Push your commit to GitLab. This will automatically trigger the pipeline.
    ```bash
    git push -u origin main
    ```

## 4. Verifying the Pipeline

1.  In your GitLab project, navigate to **`Build` > `Pipelines`**.
2.  Observe the status of the latest pipeline run.
3.  Click on the pipeline's status to view the `build` and `test` stages.
4.  Click on each job to view its console output.
