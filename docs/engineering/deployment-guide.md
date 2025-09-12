# Deployment Guide

## Table of Contents
1. [Prerequisites](#prerequisites)
2. [Environment Setup](#environment-setup)
3. [Deployment Process](#deployment-process)
4. [Rollback Procedure](#rollback-procedure)
5. [Monitoring](#monitoring)
6. [Troubleshooting](#troubleshooting)

## Prerequisites

### Infrastructure Requirements
- Kubernetes cluster (EKS, GKE, or AKS)
- PostgreSQL database (RDS, Cloud SQL, or self-hosted)
- Object storage (S3, GCS, or Azure Blob Storage)
- Redis for caching
- Monitoring stack (Prometheus + Grafana)
- Logging system (ELK or similar)

### Required Tools
- `kubectl` configured with cluster access
- Helm 3.x
- Terraform 1.0+
- AWS/GCP/Azure CLI (as applicable)
- `jq` for JSON processing

## Environment Setup

### 1. Clone the Repository
```bash
git clone https://github.com/Amivero-LLC/amivero-dev-resources.git
cd amivero-dev-resources
```

### 2. Install Dependencies
```bash
# Install Python dependencies
pip install -r requirements.txt

# Install pre-commit hooks
pre-commit install
```

### 3. Configure Environment Variables
Create a `.env` file in the project root with the following variables:

```env
# Application
ENVIRONMENT=production
SECRET_KEY=your-secret-key
ALLOWED_HOSTS=.amivero.com

# Database
DB_NAME=amivero_prod
DB_USER=amivero
DB_PASSWORD=secure-password
DB_HOST=db.amivero.com
DB_PORT=5432

# AWS/GCP/Azure Credentials (as needed)
AWS_ACCESS_KEY_ID=your-access-key
AWS_SECRET_ACCESS_KEY=your-secret-key
AWS_REGION=us-east-1

# Email Settings
EMAIL_HOST=smtp.sendgrid.net
EMAIL_PORT=587
EMAIL_USE_TLS=True
EMAIL_HOST_USER=apikey
EMAIL_HOST_PASSWORD=your-sendgrid-key

# Feature Flags
FEATURE_FLAG_NEW_UI=false
```

## Deployment Process

### 1. Infrastructure Provisioning

#### Using Terraform
```bash
cd infrastructure/terraform

# Initialize Terraform
terraform init

# Review changes
terraform plan

# Apply changes
terraform apply
```

### 2. Database Migrations
```bash
# Run migrations
alembic upgrade head

# Seed initial data (if needed)
python manage.py loaddata initial_data.json
```

### 3. Kubernetes Deployment

#### Using Helm
```bash
# Add the repository (if needed)
helm repo add amivero https://charts.amivero.com
helm repo update

# Install/upgrade the release
helm upgrade --install amivero amivero/amivero \
  --namespace amivero \
  --values values-production.yaml \
  --set image.tag=v1.0.0 \
  --atomic \
  --timeout 10m
```

### 4. Verify Deployment
```bash
# Check pod status
kubectl get pods -n amivero

# Check service status
kubectl get svc -n amivero

# Check ingress
kubectl get ingress -n amivero

# View logs
kubectl logs -n amivero deployment/amivero-web
```

## Rollback Procedure

### 1. Identify Bad Release
```bash
# List releases
helm list -n amivero

# View release history
helm history amivero -n amivero
```

### 2. Rollback to Previous Version
```bash
# Rollback to previous version
helm rollback amivero <revision> -n amivero

# Or rollback to specific version
helm upgrade --install amivero amivero/amivero \
  --namespace amivero \
  --version <previous-version> \
  --reuse-values
```

## Monitoring

### Application Metrics
- Prometheus endpoint: `/metrics`
- Health check: `/health`
- Readiness check: `/ready`
- Liveness check: `/live`

### Logging
- Logs are collected by Fluentd and stored in Elasticsearch
- Access Kibana at: `https://kibana.amivero.com`

### Alerts
- Critical alerts are sent to PagerDuty
- Non-critical alerts are sent to Slack

## Troubleshooting

### Common Issues

#### Database Connection Issues
```bash
# Check database connection
kubectl exec -it <pod-name> -n amivero -- pg_isready -h $DB_HOST -p $DB_PORT

# Check database logs
kubectl logs -n amivero <database-pod-name>
```

#### Application Not Starting
```bash
# Check pod status
kubectl describe pod <pod-name> -n amivero

# Check container logs
kubectl logs -n amivero <pod-name> -c <container-name>

# Check events
kubectl get events -n amivero --sort-by='.metadata.creationTimestamp'
```

#### Performance Issues
```bash
# Check resource usage
kubectl top pods -n amivero

# Get pod metrics
kubectl describe hpa -n amivero

# Check slow queries (if using PostgreSQL)
kubectl exec -it <postgres-pod> -n amivero -- psql -U $DB_USER -c "SELECT * FROM pg_stat_activity WHERE state = 'active'"
```

### Getting Help
- Check the [troubleshooting guide](link-to-troubleshooting-guide)
- Open an issue in the repository
- Contact the DevOps team at devops@amivero.com
