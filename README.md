# Node.js DevOps CI/CD App

A minimal Express.js application developed for DevOps Internship Task 1: **Automate Code Deployment Using a CI/CD Pipeline**.

GitHub Actions automatically runs tests, builds a Docker image, and pushes it to Docker Hub whenever code is pushed to the `main` branch.

## Features

- Express.js application with a health-check endpoint
- Automated testing using Node.js's built-in test runner
- Docker containerization
- CI/CD automation using GitHub Actions
- Docker image publishing to Docker Hub

## Application Routes

| Method | Path | Response |
|---|---|---|
| GET | `/` | `Hello! My DevOps CI/CD pipeline is working.` |
| GET | `/health` | `{"status":"healthy"}` (HTTP 200) |

## Tech Stack

- Node.js and Express.js
- Git and GitHub
- GitHub Actions
- Docker and Docker Hub

## Getting Started

### Prerequisites

- Node.js >= 18
- npm
- Docker (optional, for containerized execution)

### Install dependencies

```bash
npm install
```

### Run locally

```bash
npm start
```

Open `http://localhost:3000`.

### Run tests

```bash
npm test
```

## Docker

### Pull the published image

```bash
docker pull omsaigulhane01/nodejs-demo-app:latest
```

### Run the container

```bash
docker run -d --name nodejs-demo-app -p 3000:3000 omsaigulhane01/nodejs-demo-app:latest
```

### Verify the application

```bash
curl http://localhost:3000/
curl http://localhost:3000/health
```

### Stop and remove the container

```bash
docker rm -f nodejs-demo-app
```

## CI/CD Pipeline

Workflow file: `.github/workflows/main.yml`

The workflow triggers on pushes to `main` and supports manual execution using `workflow_dispatch`.

### Pipeline stages

1. Check out the repository source code.
2. Set up Node.js.
3. Install dependencies using `npm ci`.
4. Run automated tests using `npm test`.
5. Build the Docker image after tests succeed.
6. Log in to Docker Hub using GitHub Actions secrets.
7. Push the image to Docker Hub.

The Docker build-and-push job depends on the test job, so it runs only after the tests succeed.

### Required GitHub Secrets

Configure the following under **Settings → Secrets and variables → Actions**:

- `DOCKERHUB_USERNAME`
- `DOCKERHUB_TOKEN`

Never commit access tokens or credentials to the repository.

## Docker Hub Image

`omsaigulhane01/nodejs-demo-app:latest`

[View Docker Hub Repository](https://hub.docker.com/r/omsaigulhane01/nodejs-demo-app)

## Project Structure

```text
.
├── .github/
│   └── workflows/
│       └── main.yml
├── tests/
│   └── app.test.js
├── app.js
├── Dockerfile
├── .dockerignore
├── .gitignore
├── package.json
├── package-lock.json
└── README.md
```

## Verification Results

- Automated tests: 3 passed, 0 failed
- GitHub Actions test job: successful
- Docker build-and-push job: successful
- Docker image pulled successfully from Docker Hub
- Container started successfully
- Health endpoint returned `healthy`
- Home endpoint returned the expected application message

## Repository

[GitHub Repository](https://github.com/Omsaigulhane/nodejs-demo-app)

**DevOps Internship — Task 1: CI/CD Pipeline Automation**
