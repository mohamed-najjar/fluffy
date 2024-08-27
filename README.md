# Fluffy

This repository contains a pre-configured monitoring and alerting stack using Prometheus, Grafana, Loki, and Alertmanager. The stack is designed for easy deployment on Kubernetes using Helm and Helmfile.

## Features

- **Prometheus**: Metrics collection and storage.
- **Grafana**: Visualization of metrics and logs with pre-configured dashboards.
- **Alertmanager**: Alerting based on metrics from Prometheus.
- **Loki**: Log aggregation and querying.

## Prerequisites

Before deploying the stack, ensure that you have the following prerequisites:

- A running Kubernetes cluster (local or cloud-based).
- Helm 3.x or later installed.
- Helmfile installed.

## Quickstart

Follow these steps to deploy the monitoring stack on your Kubernetes cluster.

### Step 1: Clone the Repository

```bash
git clone git@github.com:mohamed-najjar/fluffy.git
cd fluffy
```
### Step 2: Configure Values
Review and adjust the values.yaml files in each component’s directory (prometheus, grafana, alertmanager, loki) to suit your environment.

### Step 3: Deploy the Stack
Deploy all components using Helmfile:
```bash
helmfile sync
```
### Step 4: Access Grafana
After deployment, you can access Grafana to visualize your metrics and logs.

1. Port-forward to access Grafana locally:
```bash
kubectl port-forward svc/grafana 3000:80
```
2. Open http://localhost:3000 in your browser.
3. The default username is admin, and the password is set in the grafana/values.yaml file.

### Documentation
For detailed information on the architecture, customization, deployment, and troubleshooting, please refer to the following documents:

[Architecture Overview] (./docs/architecture) 
[Customization Guide] (./docs/customization) 
[Deployment Guide] (./docs/deployment) 
[Troubleshooting] (./docs/Troubleshooting) Guide 

Contributing Contributions are welcome! Please open an issue or submit a pull request if you have suggestions for improvements or additional features.