# CloudShop Lite — Microservices Demo

This project showcases a microservices architecture using Docker and Kubernetes, featuring:

- **API**: Python Flask backend
- **Frontend**: Python Flask web UI
- **Worker**: Python background job processor
- **Redis**: Caching & message broker

All services are containerized and orchestrated with Kubernetes manifests. The live demo is available at:

**Public URL:** [To be updated after deployment]

---

## Project Structure

```
api/           # Backend Flask app
frontend/      # Web UI Flask app
worker/        # Background job processor
k8s-manifests/ # Kubernetes YAMLs
helm/          # Helm chart for advanced deployment
docs/          # Documentation
ci-cd/         # CI/CD configs
```

## Features

- **Frontend** displays visit count and background job stats
- **API** exposes endpoints for visit tracking and health checks
- **Worker** increments background job count in Redis
- **Redis** enables fast state sharing between services

---

## Quick Start

### 1. Build Docker Images

Navigate to each service directory and build the Docker images:

```bash
cd api && docker build -t api-service .
cd ../frontend && docker build -t frontend-service .
cd ../worker && docker build -t worker-service .
```

### 2. Deploy to Kubernetes

Apply all manifests:

```bash
kubectl apply -f k8s-manifests/
```

This will deploy:
- API, Frontend, Worker, Redis as pods
- Services for API, Frontend (LoadBalancer), Redis

**Frontend** is exposed via LoadBalancer. Access the app at the public URL.

---

### 3. Local Development

You can run each component locally:

```bash
cd api && python app.py
cd frontend && python app.py
cd worker && python worker.py
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

---

## License

MIT — For educational use