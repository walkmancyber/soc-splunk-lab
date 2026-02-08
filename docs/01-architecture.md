# Security Principles & Lab Isolation Model

- The Splunk Enterprise instance runs inside Docker containers with no direct internet exposure.

- Communication between systems is unidirectional:

    - Endpoints → Splunk (log forwarding only)

    - No command or control traffic originates from Splunk.

- Log collection is performed using Splunk Universal Forwarder, minimizing attack surface on the endpoint.

- The Windows VM is network-isolated using NAT, preventing inbound connections from external networks.

- Telemetry is collected via Sysmon, ensuring high-fidelity security events without relying on external agents.

- This architecture emulates a real SOC lab environment, prioritizing containment, visibility, and forensic integrity.

- All offensive activity (malware execution, exploitation, adversary simulation) is performed exclusively inside isolated virtual machines.

## Architecture Overview

This lab simulates a real-world SOC detection pipeline with isolated endpoints and centralized log analysis

![SOC-Lab](../images/SOC-Lab.png)