# CI/CD Pipeline with GitHub Actions and Docker

A small Flask app that is tested, built into a Docker image and pushed to Docker Hub
automatically on every push to the `main` branch, then deployed on a local Kubernetes
cluster (Minikube). Built for DevOps Internship Project 4 (Elevate Labs).

- Docker image: https://hub.docker.com/r/teenarana/cicd-demo-app
- Report: [CICD_Pipeline_Report.pdf](CICD_Pipeline_Report.pdf)

## How it works
1. Push code to the `main` branch.
2. GitHub Actions runs `pytest` (the `test` job).
3. If the tests pass, the `build-and-push` job builds the Docker image and pushes it to Docker Hub
   with two tags: `latest` and the commit ID.
4. Minikube pulls the new image: `kubectl rollout restart deployment cicd-demo`.

## Tools
Python, Flask, Pytest, Docker, Docker Compose, GitHub Actions, Docker Hub, Minikube, kubectl

## Project files
- `app.py`, `test_app.py`, `requirements.txt` - the application and its tests
- `Dockerfile`, `docker-compose.yml` - containerisation
- `.github/workflows/ci-cd.yml` - the CI/CD pipeline
- `K8s/deployment.yaml`, `K8s/service.yaml` - Kubernetes manifests

## Screenshots

### 1. App running locally with Docker Compose (Version 1)
![Local app](screenshots/01-local-app-version1.png)

### 2. Health endpoint
![Health endpoint](screenshots/02-local-health-endpoint.png)

### 3. Container started with docker compose and verified with docker ps
![Docker compose running](screenshots/03-docker-compose-running.png)

### 4. Container shown in Docker Desktop
![Docker Desktop](screenshots/04-docker-desktop-container.png)

### 5. GitHub Actions pipeline: test and build-and-push both successful
![GitHub Actions](screenshots/05-github-actions-green-run.png)

### 6. Workflow file used by the run
![Workflow file](screenshots/06-workflow-file.png)

### 7. Image published on Docker Hub (latest and commit-ID tags)
![Docker Hub tags](screenshots/07-dockerhub-tags.png)

### 8. App served from Minikube after the update (Version 2)
![Minikube Version 2](screenshots/08-minikube-app-version2.png)
