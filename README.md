# SRE Observability Lab

Practical observability project using Prometheus, Grafana and Node Exporter in a Linux environment containerized with Docker.

---

## Objective

Implement a monitoring stack to simulate real infrastructure observability scenarios commonly used in DevOps and Site Reliability Engineering environments.

---

## Technologies Used

* Linux Ubuntu Server
* Docker
* Prometheus
* Grafana
* Node Exporter

---

## Architecture

Linux Host → Node Exporter → Prometheus → Grafana

---

## Project Structure

sre-observability-lab/
│── README.md
│── prometheus/
│   └── prometheus.yml
│── screenshots/
│   └── dashboard.png
│── alerts/
│   └── future-alert-rules.yml

---

## Prometheus Configuration

```yaml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'node'
    static_configs:
      - targets: ['node-exporter:9100']
```

---

## Running the Environment

### Create Docker network

```bash
docker network create monitoring
```

### Run Prometheus

```bash
docker run -d --name prometheus -p 9090:9090 -v $(pwd)/prometheus.yml:/etc/prometheus/prometheus.yml --network monitoring prom/prometheus
```

### Run Node Exporter

```bash
docker run -d --name node-exporter -p 9100:9100 --network monitoring prom/node-exporter
```

### Run Grafana

```bash
docker run -d --name grafana -p 3000:3000 --network monitoring grafana/grafana
```

---

## Dashboard Import

Grafana Dashboard ID:

1860

---

## Stress Test

Generate CPU load:

```bash
stress --cpu 4 --timeout 60
```

Generate memory load:

```bash
stress --vm 2 --vm-bytes 512M --timeout 60
```

---

## Dashboard Evidence

![Dashboard](screenshots/dashboard.png)

---

## Next Steps

* Create CPU alerts
* Configure email notifications
* Simulate incidents
* Add centralized logging

---

## Learning Focus

* Observability
* Monitoring
* Linux metrics
* Infrastructure troubleshooting
* SRE fundamentals
