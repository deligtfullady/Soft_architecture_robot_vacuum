# k–l. Self-checking и метрики

## k. Self-checking

Компонент `HealthAggregator`:
- Probe каждого: API Gateway, BL services, DB, Vendor adapter  
- Метрики: `up`, `latency_ms`  
- Endpoint: `GET /tech/health` (liveness), `GET /tech/ready`  
- Экспорт в **Prometheus**, дашборды **Grafana**

## l. Инфраструктурные метрики

| Ресурс | Метрики |
|--------|---------|
| CPU | usage %, throttle |
| Memory | rss, working set, OOM |
| Disk | volume used %, iops |
| Network | RPS, error rate, latency p95 |
| App | jobs_started, vendor_api_errors, mqtt_reconnects |
