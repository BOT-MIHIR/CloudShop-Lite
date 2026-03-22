
# CloudShop Lite Deployment by BOT-MIHIR

This project demonstrates a microservices architecture deployed on Kubernetes, including:

- **API**: Python Flask backend service
- **Frontend**: Python Flask web interface
- **Worker**: Python background job handler
- **Redis**: In-memory data store for caching and messaging

All components are containerized with Docker and managed via Kubernetes manifests and Helm charts.

The live demo is available at:

**Public URL:** [http://a42ec1aa062b9405387fc7b9d766a850-879456498.us-east-1.elb.amazonaws.com:3000/](http://a42ec1aa062b9405387fc7b9d766a850-879456498.us-east-1.elb.amazonaws.com:3000/)

---

## Project Structure

```
API/           # Flask API service
Frontend/      # Flask web UI
Worker/        # Background worker service
k8s-manifests/ # Kubernetes deployment files
helm/          # Helm chart for deployment
.github/       # CI/CD workflows
```

## Features

- **Frontend** shows visit counter and job statistics
- **API** provides endpoints for tracking visits and health status
- **Worker** processes background jobs and updates Redis
- **Redis** facilitates data sharing across services

---

## Quick Start

### 1. Build Docker Images

Build the Docker images for each service:


### 2. Deploy to Kubernetes

Apply all manifests:

```bash
kubectl apply -f k8s-manifests/
```

This will deploy:
- API, Frontend, Worker, Redis as pods
- Services for API, Frontend (LoadBalancer), Redis

**Frontend** is exposed via LoadBalancer. Access the app at the public URL above.

---

### 3. Local Development

You can run each component locally:

```bash
cd API && python app.py
cd Frontend && python app.py
cd Worker && python worker.py
```


---

## Requirements

- Docker
- Kubernetes (minikube, kind, or cloud cluster)
- Python 3.x
- Redis

---

## Environment Variables

- `REDIS_HOST`: Hostname for Redis (default: `localhost` or `redis-service` in k8s)
- `API_URL`: API endpoint for Frontend (default: `http://localhost:5000` or `http://api-service:5000` in k8s)

---

## Cloud & Production Notes

- Update image repositories in manifests for your registry
- Use Helm for advanced configuration and upgrades
- Secure environment variables and secrets for production
