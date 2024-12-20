# DevOps_Orange


































## SSDLC Integration
- The Jenkins pipelines incorporate SSDLC principles by applying the "shift-left" approach, which integrates security testing early in the development lifecycle. This proactive method helps address vulnerabilities before they reach production. 
- Key security measures include code linting, static application security testing, and Docker image scanning

## Credential Management
- **Credentials Storage**: Use Jenkins’ credentials management to securely store sensitive information like API keys and passwords.
- **Environment Variables**: Access credentials via environment variables configured in Jenkins.

## Security Authorization
- **Mixed Security Authorization**: Segment access permissions based on roles and responsibilities.
- **Least Privilege Principle**: Ensure users and services have only the permissions needed for their tasks.










<!-- ```cmd
Monitoring/
|── Prometheus/
|   ├── Docker/
|   └── K8s/
|   
|── Grafana/
|   ├── Docker/
|   |   └── dashboards/
|   └──K8s/
└── Readme.md
``` -->







<!-- [Heading IDs](#heading-ids)

| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |

| Syntax | Description |
| --- | ---- |
| Header | Title |
| Paragraph | Text |
 -->
<!-- 
```cmd
DevOps-Monitoring/
├── Images/
|── Prometheus/
├   ├── Docker/
|   │   └── dashboards.yaml
|   |── K8s/
|   |   └── datasources.yaml
|   └── Linux/
|       |── prometheus.service
|       └── prometheus.yml   
└── Grafana/
    ├── Docker/
    │   └── dashboards.yaml
    └── K8s/
        └── datasources.yaml
``` -->
