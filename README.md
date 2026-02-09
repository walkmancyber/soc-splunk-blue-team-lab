# SOC Blue Team Lab with Splunk

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
| [**doc01-architecture**](docs/01-architecture.md) | Lab architecture |
| [**doc02 Environment Setup**](docs/02-environment_setup.md) | Splunk deployment and environment preparation |
| [**doc03 Forwarder Installation**](docs/03-forwarder_installation.md) | Sysmon64 and Splunk Universal Forwarder installation and configuration |
| [**doc04 Fix Sysmon Even Colletions Issue**](docs/04-Fix_Sysmon_Event_Collection_Issue.md)| Investigation and resolution of Sysmon ingestion issue |
| **doc05-detections** | Basic detections and validation queries **Comming soon** |

## Current Status

- Splunk Enterprise deployed and accessible.
- Windows logs successfully ingested.
- Sysmon events collected and searchable.
- Lab ready for detection development and analysis.

## Notes

This project is intended as a personal learning lab and reflects the actual
steps, issues, and solutions encountered during setup and validation.
