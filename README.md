# 📊 Monitoring & Alerting with Prometheus, Grafana & Alertmanager

## 📌 Overview

This project implements a **complete monitoring and alerting solution** using:

* Prometheus (metrics collection)
* Grafana (visualization)
* Alertmanager (alert notifications)

Supports **dynamic EC2 discovery** for scalable monitoring.

---

## 🧠 Key Features

* Dynamic EC2 service discovery
* Real-time monitoring dashboards
* Email-based alerting
* Custom alert rules
* Automated instance onboarding

---

## 🏗️ Architecture

1. Node Exporter → exposes metrics
2. Prometheus → scrapes metrics
3. Alertmanager → handles alerts
4. Grafana → visualizes data

---

## 📂 Project Structure

```id="mon1"
.
├── alert-rules/
│   ├── cpu-utilisation.yaml
│   ├── ram-usage.yaml
│   ├── instance-down.yaml
│
├── prometheus.yaml
├── alertmanager.yaml
├── prometheus.service
├── alertmanager.service
└── node_exporter.service
```

---

## ⚙️ Prometheus Configuration

### 🔹 Static Scraping

```yaml id="mon2"
- job_name: "node-1"
  static_configs:
    - targets: ["172.31.2.67:9100"]
```

---

### 🔹 Dynamic EC2 Scraping

```yaml id="mon3"
ec2_sd_configs:
  - region: us-east-1
    filters:
      - name: "tag:MonitoringThroughScraping"
        values: ["true"]
```

👉 Automatically discovers EC2 instances

---

## 🚨 Alert Rules

Example:

```yaml id="mon4"
expr: CPU usage > 70%
for: 1m
```

Alerts:

* High CPU
* High RAM
* Instance down

---

## 📧 Alertmanager

```yaml id="mon5"
receivers:
- name: gmail-alerts
```

* Sends email notifications

---

## 📊 Grafana

* Connected Prometheus as datasource
* Created dashboards:

  * CPU usage
  * Memory
  * Node health

---

## 🚀 How to Run

1. Start Prometheus
2. Start Alertmanager
3. Start Node Exporter
4. Configure Grafana datasource

---

## 🎯 Benefits

* Scalable monitoring
* Automated discovery
* Real-time alerts
* Improved observability

---

## 👨‍💻 Author

Sai Pavan – DevOps Engineer
