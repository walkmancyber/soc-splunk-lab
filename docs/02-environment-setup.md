# Splunk Initial Setup & Verification
---

## Environment

- Endpoint OS: Windows 10 (Virtual Machine)
- Hypervisor: VMware
- Network Mode: NAT
- SIEM: Splunk Enterprise (Docker)
- Host OS: Windows 11
- Forwarding Port: 9997

## 1. Splunk Startup Verification
---
Splunk Enterprise was deployed using Docker Compose and its successful startup was verified through the following steps.

- Confirmed running containers using:

    `docker ps`

- Accessed the Splunk Web interface at:

    `http://localhost:8000`

## 2. Development Environment Configuration
---

### 2.1 Visual Studio Code

Visual Studio Code was used as the primary editor to manage the lab configuration files, including the docker-compose.yml used to deploy Splunk Enterprise.

![VSC-docker-compose](../images/VSC-docker-compose.png)

### 2.2 WSL Linux Terminal & Docker Desktop

The lab environment was initialized using WSL (Linux terminal) in combination with Docker Desktop.
Docker Desktop was used to confirm that the Splunk container was running correctly and exposing the required ports.

![docker-desktop-wsl](../images/docker-desktop-wsl.png)

## 3. Splunk Web Interface Validation
---

The following image shows the Splunk Web interface after a successful login.
This confirms that Splunk Enterprise is accessible and ready for configuration.

- URL: `http://localhost:8000`

- Initial dashboard displayed correctly after first login.

![Splunk-Web-interface](../images/Splunk-Web-interface.png)

## 4. Windows VM Preparation
---

Windows virtual machine was successfully deployed as part of the lab.
The following steps were completed:

- Windows installation verified.

- Splunk Universal Forwarder downloaded and prepared for installation.

This VM will be used as a log source for forwarding events to Splunk Enterprise.

![VM-windows](../images/VM-windows.png)