# GitHub Actions CI/CD Lab Notes

## Task 1 – Hello World Workflow

### Purpose of the Workflow
The purpose of this workflow is to introduce GitHub Actions automation.  
It ensures that on **any push event**, a simple job runs to print  
`Hello GitHub Actions!` in the logs, confirming that the Actions system is working.

### Key Configuration Details
- **Workflow File**: `.github/workflows/hello.yml`  
- **Trigger**: `push` to any branch  
- **Job**: `say-hello` runs on `ubuntu-latest`  
- **Step**: Uses `run` to print a message to the GitHub Actions log  

```yaml
on:
  push:
    branches:
      - '**'
jobs:
  say-hello:
    runs-on: ubuntu-latest
    steps:
      - name: Print Hello Message
        run: echo "Hello GitHub Actions!"

# Secrets Used

None (basic introductory workflow)

Verification

Go to the Actions tab in the App Repository.

Confirm that the workflow executes and logs contain the message.

<img width="1366" height="768" alt="t1 0" src="https://github.com/user-attachments/assets/47814961-4c7a-40bf-b3cd-592c4337995c" />

<img width="1366" height="768" alt="t1 1" src="https://github.com/user-attachments/assets/3bb5e5a2-ce1b-440a-bd38-95a1249210e3" />


## Task 2 – Basic Docker Build & Push
Purpose of the Workflow

This workflow builds and pushes Docker images of the application automatically.
It ensures that:

A Docker image is built on every push to main.

The image is tagged with both:

latest

the commit SHA (for traceability)

The image is then pushed to Docker Hub.

Key Configuration Details

Workflow File: .github/workflows/docker-build.yml

Trigger: push to main branch

Steps:

Checkout code (actions/checkout@v3)

Log in to Docker Hub using GitHub secrets

Build Docker image with latest and commit SHA tags

Push Docker image to Docker Hub

Secrets Used

DOCKER_USERNAME → Docker Hub username, used to authenticate pushes

DOCKER_PASSWORD → Docker Hub password or access token, used for secure login

Verification

Check Actions tab → ensure both tags (latest, <commit_sha>) are built & pushed.

Verify in Docker Hub → repository contains both tags

<img width="1366" height="768" alt="t2 0" src="https://github.com/user-attachments/assets/329e5571-e13b-459b-a89d-96ad437ff187" />

<img width="1366" height="768" alt="t2 1" src="https://github.com/user-attachments/assets/391d6e6a-7b0f-460b-afcb-aac0094fd29a" />

<img width="1366" height="768" alt="t2 2" src="https://github.com/user-attachments/assets/796ba9d1-7747-4841-91bf-06c911dcdabd" />
