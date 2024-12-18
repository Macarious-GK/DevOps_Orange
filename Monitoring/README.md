
# DevOps Monitoring with Grafana, Prometheus, and Exporters

This project sets up a monitoring solution using **Grafana** and **Prometheus**  to monitor my Django applications.

![Monitoring](/Figures/devops_monitoring.png)

## Monitoring  Overview
### In a monitoring system, there are three key components:

**`The System Being Monitored`**: 
- This refers to the application or infrastructure that needs to be monitored. It must expose its metrics through a dedicated endpoint (`/metrics/`) and make them accessible via a specific port. These metrics provide valuable insights into the system's performance and health.
- Expose app metrics on the endpoint at `http://IP/metrics/`.

**`The Monitoring Tool`**: 
- This tool acts as the central data collection point, pulling metrics from various exporters. Exporters are lightweight services that retrieve system or application metrics. The monitoring tool aggregates and stores this data, making it available for querying. Additionally, it allows users to define thresholds or values for setting up alerts based on these metrics.
- Access Prometheus at `http://IP:9090/`.

**`The Visualization Tool`**: 
- This component is responsible for presenting the collected data in an understandable and actionable format. Using customizable dashboards, it visualizes the metrics collected by the monitoring tool, helping users to analyze trends, monitor system health, and take informed actions when necessary.
- Access Grafana at `http://IP:3000/`.

## Tools

- **`Prometheus`**: An open-source monitoring and alerting toolkit designed for reliability and scalability.  
  ![Prometheus](/Figures/Promethues_working.png)

- **`Grafana`**: A platform for monitoring and observability, used to visualize metrics collected by Prometheus.  
  ![Grafana](/Figures/Grafana_working.png)

- **`Alerting`**: Configuring alerts when the app is down more than 30s.
  ![Alerting](/Figures/Alert_working.png)

