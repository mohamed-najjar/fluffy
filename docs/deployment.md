# START OF FILE: deployment.md

# Deployment Guide

## Prerequisites

1. A running Kubernetes cluster (local or cloud-based).
2. Helm and Helmfile installed on your local machine.

## Step 1: Clone the Repository

```bash
git clone https://github.com/your-org/fluffy.git
cd fluffy
```

## Step 2: Configure Values
Before deploying, review and adjust the values in the values.yaml files for each component (prometheus, grafana, alertmanager, and loki).

## Step 3: Deploy with Helmfile
```bash
helmfile sync
```

This command will deploy all components in the stack: Prometheus, Grafana, Alertmanager, and Loki.

## Step 4: Access Grafana
After deployment, you can access Grafana to view metrics and logs.

Port-forward to access Grafana locally:
```bash
kubectl port-forward svc/grafana 3000:80
```

Open http://localhost:3000 in your browser. The default username is admin, and the password is the one set in the values.yaml file.

## Step 5: Verify Deployment
Check the status of the pods to ensure everything is running correctly:
```bash
kubectl get pods
```

You should see pods for Prometheus, Grafana, Alertmanager, and Loki running successfully.