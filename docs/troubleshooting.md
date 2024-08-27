# Troubleshooting Guide

 Common Issues

### 1. Pods Stuck in `Pending` State

**Cause:** This is usually due to insufficient resources or missing PersistentVolumeClaims.

**Solution:** Check if your cluster has enough resources (CPU, memory) and ensure that the required PersistentVolumes are available.

```bash
kubectl describe pod <pod-name>
```

### 2. Grafana Not Loading Dashboards
**Cause:** The ConfigMap containing the dashboards might not be mounted correctly.

**Solution:** Verify that the grafana-dashboards ConfigMap is properly created and mounted in the Grafana pod.

```bash
kubectl get configmap grafana-dashboards 
```

## 3. No Alerts Triggering in Alertmanager
***Cause:*** The alerting rules in Prometheus might not be configured correctly or the thresholds are too high.

***Solution:*** Check the Prometheus alerting rules and adjust the thresholds if necessary.

```bash
kubectl logs <prometheus-pod-name>
```

## 4. Loki Logs Not Appearing in Grafana

***Cause:*** Loki might not be scraping logs correctly, or the log query is misconfigured in Grafana.

***Solution:*** Verify Loki's configuration and ensure that the correct labels are being used in your Grafana queries.

```bash
kubectl logs <loki-pod-name>
```

## Logs and Debugging
- Prometheus Logs: Check the logs of the Prometheus pod for any scraping issues.
- Grafana Logs: Check the Grafana pod logs if dashboards are not loading or data sources are failing.
- Alertmanager Logs: Ensure that Alertmanager is properly receiving alerts from Prometheus.
- Loki Logs: Verify that Loki is correctly ingesting and storing logs.

To view logs:
```bash
kubectl logs <pod-name>
```

## Resetting Components
If you encounter persistent issues, you may need to delete and reinstall specific components.

```bash
helm delete <release-name>
helmfile sync
```
This will remove and redeploy the selected components, potentially resolving configuration or state-related issues.