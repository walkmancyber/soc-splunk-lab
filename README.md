# SOC Lab with Splunk

This project is a hands-on SOC Blue Team laboratory focused on log ingestion,
analysis, threat detection, and basic incident investigation using Splunk
Enterprise.

The lab documents the setup process, troubleshooting steps, and validation
performed while building a functional log collection environment from scratch.

## Objectives

- Learn Splunk Enterprise fundamentals.
- Deploy and configure a basic SIEM environment.
- Ingest and analyze Windows logs.
- Collect Sysmon telemetry using Splunk Universal Forwarder.
- Practice basic SOC investigation workflows.
- Maintain clear and structured technical documentation.

## Project Architecture

The following diagram illustrates the overall lab architecture, including log
sources, data flow, and core components.

![Lab Architecture](images/doc01/SOC-Lab-Architecture-Overview.png)

## Environment

- **Host OS:** Windows 11  
- **Endpoint OS:** Windows 10 (Virtual Machine)  
- **Hypervisor:** VMware  
- **Containerization:** Docker / Docker Compose  
- **SIEM:** Splunk Enterprise (Docker)  
- **Log Source:** Sysmon  
- **Log Forwarder:** Splunk Universal Forwarder  
- **Forwarding Port:** `9997`

## Documentation Index

| Document | Description |
|--------|-------------|
| [**Architecture**](docs/01_architecture.md) | Lab architecture |
| [**Environment Setup**](docs/02_environment_setup.md) | Splunk deployment and environment preparation |
| [**Forwarder Installation**](docs/03_forwarder_installation.md) | Sysmon64 and Splunk Universal Forwarder installation and configuration |
| [**Fix Sysmon Even Colletions Issue**](docs/04_fix_sysmon_event_collection_issue.md)| Investigation and resolution of Sysmon ingestion issue |
| [**Sysmon EventID1 Investigation**](docs/05_sysmon_eventid1_investigation.md)| No EventID=1 |
| [**Windows Security Log**](docs/06_Windows_Security_Log.md)| Ensure process creation visibility independent of Sysmon. |
| **Detections** | Basic detections and validation queries **Comming soon** |

## Current Status

- Splunk Enterprise deployed and accessible.
- Windows logs successfully ingested.
- Sysmon events collected and searchable.
- Lab ready for detection development and analysis.

## Notes

This project is intended as a personal learning lab and reflects the actual
steps, issues, and solutions encountered during setup and validation.
