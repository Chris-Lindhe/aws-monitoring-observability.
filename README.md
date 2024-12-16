# aws-monitoring-observability.
A project showcasing monitoring and observability in AWS using CloudWatch, Prometheus, and Grafana

## Table of Contents
- [Overview](#overview)
- [Architecture](#architecture)
- [Technologies Used](#technologies-used)
- [Setup Guide](#setup-guide)
- [Dashboards](#dashboards)
- [Future Enhancements](#future-enhancements)


## Overview
This project demonstrates how to set up monitoring and observability in AWS. It uses:
- **CloudWatch** for collecting system metrics.
- **Prometheus** for scraping metrics.
- **Grafana** for visualization.

Use cases include monitoring EC2 instances, system performance, and creating alert mechanisms.


## Architecture
The architecture includes:
- EC2 instance with AWS CloudWatch Agent for system metrics.
- Prometheus server for scraping metrics from CloudWatch and Node Exporter.
- Grafana for visualization and dashboard creation.

![Architecture Diagram](architecture-diagram.png)

## Technologies Used
- **AWS CloudWatch**: Monitoring system metrics (CPU, memory, disk, etc.).
- **Prometheus**: Open-source monitoring system.
- **Grafana**: Visualization and alerting platform.
- **Node Exporter**: Collecting system metrics from EC2.
- **EC2**: Hosting services and applications.

### Prerequisites
- AWS account with EC2 and CloudWatch access.
- IAM user or role with the `CloudWatchReadOnlyAccess` policy.
- SSH access to an EC2 instance.
- Basic knowledge of AWS and Linux commands.

### Setup Instructions
1. **Create an EC2 Instance**:
   - Launch an Amazon Linux 2 or Ubuntu instance.
   - Open ports 22 (SSH), 9100 (Node Exporter), and 3000 (Grafana).

2. **Install AWS CloudWatch Agent**:
   - Configure and start the CloudWatch Agent.
   - Use the provided [cloudwatch-agent-config.json](setup/cloudwatch-agent-config.json) file.

3. **Install Prometheus and Node Exporter**:
   - Set up Prometheus on a separate EC2 instance.
   - Use the provided [prometheus.yml](setup/prometheus.yml) configuration file.

4. **Install Grafana**:
   - Set up Grafana and connect it to Prometheus and CloudWatch.
   - Add [CloudWatch credentials](#aws-cloudwatch-integration).

5. **Verify Metrics and Dashboards**:
   - Open Grafana (`http://<grafana-server-ip>:3000`).
   - Import the provided [Grafana dashboard JSON](dashboards/grafana-dashboard.json).

## Dashboards
- **System Metrics Dashboard**:
  - Displays CPU, memory, disk usage, and network metrics.
  ![System Metrics Dashboard](dashboards/screenshots/system-metrics-dashboard.png)

- **Prometheus Metrics Dashboard**:
  - Monitors Node Exporter and Prometheus-specific metrics.
  ![Prometheus Metrics Dashboard](dashboards/screenshots/prometheus-dashboard.png)

- **CloudWatch Dashboard**:
  - Integrates CloudWatch metrics directly into Grafana.
  ![CloudWatch Dashboard](dashboards/screenshots/cloudwatch-dashboard.png)

Download dashboard JSON: [grafana-dashboard.json](dashboards/grafana-dashboard.json)

## Future Enhancements
- Automate setup with Terraform or CloudFormation.
- Use AWS Lambda for custom metric collection.
- Implement alerting with Slack or PagerDuty integrations.
