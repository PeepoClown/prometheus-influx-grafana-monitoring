# Monitoring with prometheus -> influxdb-> grafana
Docker compose configuration for monitoring system that received metrics by prometheus, then send it into a
influxdb storage and visualize graphs in grafana.
![img](https://i.ibb.co/HDkrDJG/Screenshot-2022-06-19-at-23-10-52.png)

## Prometheus
### - global configuration
```yaml
global:
  scrape_interval: 15s
  scrape_timeout: 15s
  evaluation_interval: 15s
```

### - scrapes configuration
```yaml
scrape_configs:
  - job_name: 'prometheus-metrics'
    metrics_path: '/paths/to/metrics'
    scrape_interval: 5s
    static_configs:
      - targets: ['APP-HOST:APP-PORT']
```

### - remote write configuration
```yaml
remote_write:
  - url: http://INFLUX-HOST:8086/api/v1/prom/write?db=DB-NAME
```
