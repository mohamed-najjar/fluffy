
### **2. `docs/customization.md`**

```markdown
# START OF FILE: customization.md

# Customizing the Monitoring Stack

## Customizing Prometheus

### Scrape Configurations
To add or modify scrape configurations in Prometheus, update the `prometheus/templates/configmap.yaml` file with the desired targets:

```yaml
scrape_configs:
  - job_name: 'custom-job'
    static_configs:
      - targets: ['custom-service:8080']
```
### Alerting Rules
Alerting rules can be customized by editing the prometheus/templates/rules.yaml file.

## Customizing Grafana
### Dashboards
You can add or modify Grafana dashboards by placing your custom JSON files in the grafana/dashboards/ directory and updating the grafana/templates/dashboardConfigMap.yaml.

### Data Sources
To configure additional data sources, update the grafana/templates/configmap.yaml file:

```yaml
datasources.yaml: |-
  apiVersion: 1
  datasources:
    - name: CustomDataSource
      type: prometheus
      url: http://custom-prometheus:9090
      access: proxy
      isDefault: false
```

### Customizing Alertmanager
## Notification Channels
Alertmanager supports multiple notification channels. To add a new channel, update the alertmanager/templates/configmap.yaml:
```yaml
receivers:
  - name: 'slack-notifications'
    slack_configs:
      - api_url: 'https://hooks.slack.com/services/TOKEN'
        channel: '#alerts'
```

### Customizing Loki
## Storage Configuration
Loki's storage can be configured to use various backends like S3, GCS, or local filesystem. Update the loki/values.yaml file to switch storage backends:
```yaml
storage_config:
  boltdb_shipper:
    shared_store: s3
  aws:
    s3: s3://bucket-name
```

