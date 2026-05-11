# Ferrari Canary Deployment Demo

A demonstration application showcasing Canary deployment strategy with intentional errors and heavy logging for monitoring purposes.

## Architecture

- **Backend**: Java Spring Boot application with REST API
- **Frontend**: React application with modern UI
- **Database**: PostgreSQL
- **Deployment**: Canary strategy using Argo Rollouts
- **Monitoring**: Instana APM integration

## Features

- ✅ Intentional error generation (20-40% failure rate)
- ✅ Heavy logging for monitoring
- ✅ External API calls for network traffic
- ✅ Background scheduled tasks
- ✅ Canary deployment with progressive traffic shifting
- ✅ Health checks and probes
- ✅ Instana monitoring integration

## Vehicle Models

- 488 GTB (Sports)
- F8 Tributo (Sports)
- Portofino (Convertible)
- Roma (GT)
- SF90 (Hybrid)

## Quick Start

### Prerequisites

- Kubernetes cluster
- ArgoCD installed
- Argo Rollouts installed
- GitHub account for CI/CD

### Deployment

1. **Create namespace**:
```bash
kubectl create namespace ferrari-shop-dev
```

2. **Deploy with ArgoCD**:
```bash
kubectl apply -f gitops/argocd/application.yaml
```

3. **Access the application**:
- Frontend: http://ferrari-shop.local
- Backend API: http://ferrari-shop.local/api

### Local Development

**Backend**:
```bash
cd backend
mvn spring-boot:run
```

**Frontend**:
```bash
cd frontend
npm install
npm start
```

## CI/CD Pipeline

GitHub Actions automatically builds and pushes Docker images to GHCR on push to main/master branch.

## Monitoring

The application generates:
- Heavy application logs
- Intentional errors (20-40% rate)
- External API calls
- Background task logs
- Performance metrics

## Canary Deployment

The backend uses Argo Rollouts with Canary strategy:
- Progressive traffic shifting: 20% → 40% → 60% → 80% → 100%
- 30-second pause between each step
- Automatic rollback on failure
- Traefik-based traffic routing

## License

MIT
