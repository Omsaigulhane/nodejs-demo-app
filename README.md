# Node.js DevOps CI/CD App

A minimal Express.js application created for a DevOps internship to demonstrate a working CI/CD pipeline.

## Routes

| Method | Path      | Response                                       |
|--------|-----------|------------------------------------------------|
| GET    | `/`       | `Hello! My DevOps CI/CD pipeline is working.` |
| GET    | `/health` | `{ "status": "healthy" }` (HTTP 200)           |

## Getting Started

### Prerequisites
- Node.js >= 18
- npm

### Install dependencies
```bash
npm install
```

### Run locally
```bash
npm start
# Server starts on http://localhost:3000
```

### Run tests
```bash
npm test
```

## Docker

### Build the image
```bash
docker build -t devops-cicd-app .
```

### Run the container
```bash
docker run -p 3000:3000 devops-cicd-app
```

### Override port
```bash
docker run -p 8080:8080 -e PORT=8080 devops-cicd-app
```

## Project Structure

```
.
├── app.js              # Express application
├── Dockerfile          # Multi-stage Docker build
├── .dockerignore       # Files excluded from the Docker image
├── package.json        # Project metadata and scripts
└── tests/
    └── app.test.js     # Node.js built-in test runner tests
```
