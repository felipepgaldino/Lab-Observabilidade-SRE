# SRE Monitoring Lab

Practical observability project using Prometheus, Grafana, Node Exporter and Blackbox Exporter in a Linux environment containerized with Docker.

## Objective

Implement a monitoring stack to simulate real-world infrastructure observability scenarios commonly found in DevOps and SRE environments.

## Technologies

* Ubuntu Linux
* Docker
* Prometheus
* Grafana
* Node Exporter
* Blackbox Exporter
* Nginx

## Architecture

Linux Host → Node Exporter → Prometheus → Grafana
HTTP Probe → Blackbox Exporter → Prometheus

## Project Structure

Lab-Observabilidade-SRE/
│── README.md
│── prometheus/
│   ├── prometheus.yml
│   ├── alerts.yml
│── screenshots/
│── incidents/

## Monitoring Configuration

* scrape interval: 15s
* node metrics collection
* HTTP endpoint validation

## Stress Test Performed

CPU load simulation:

stress --cpu 4 --timeout 60

Memory load simulation:

stress --vm 2 --vm-bytes 512M --timeout 60

## Incident Simulation

Nginx interruption generated:

* probe_success = 0
* target DOWN
* alert firing

## Next Steps

* CPU alert rules
* Email notification
* Docker Compose automation

## Learning Focus

* Observability
* Monitoring
* Infrastructure troubleshooting
* Alerting
* SRE fundamentals
