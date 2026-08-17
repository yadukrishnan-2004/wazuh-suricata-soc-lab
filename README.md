# Wazuh SIEM with Suricata IDS Integration

## 📌 Project Overview

This project demonstrates the deployment and integration of **Wazuh
SIEM** with **Suricata IDS** in a simulated security lab environment.

The objective was to build a security monitoring pipeline capable of
collecting and analyzing intrusion detection events, validating alerts
through controlled test traffic, and mapping security activity to the
**MITRE ATT&CK** framework.

## 🎯 Objectives

-   Deploy and configure the Wazuh SIEM platform.
-   Deploy a Wazuh agent on the monitored host.
-   Install and configure Suricata IDS.
-   Configure Suricata to generate structured `eve.json` security
    events.
-   Forward Suricata alerts to Wazuh.
-   Create and validate a custom Suricata detection rule.
-   Generate controlled test traffic and verify alerts.
-   Analyze security events through the Wazuh dashboard.
-   Map observed activity to MITRE ATT&CK techniques.

## 🏗️ Lab Architecture

``` text
                 ┌─────────────────────┐
                 │  Test / Attack Host  │
                 │     Kali Linux      │
                 └──────────┬──────────┘
                            │
                     Test Network Traffic
                            │
                            ▼
                 ┌─────────────────────┐
                 │     Suricata IDS    │
                 │  Network Detection  │
                 └──────────┬──────────┘
                            │
                       eve.json
                            │
                            ▼
                 ┌─────────────────────┐
                 │    Wazuh Agent      │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │   Wazuh Manager     │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │   Wazuh Indexer     │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │  Wazuh Dashboard    │
                 │ Alerts & MITRE ATT&CK│
                 └─────────────────────┘
```

## 🛠️ Technologies Used

  Technology     Purpose
  -------------- ----------------------------------------------------
  Wazuh          SIEM, security monitoring and alert analysis
  Suricata       Intrusion Detection System (IDS)
  Kali Linux     Security testing and controlled traffic generation
  Linux          Lab/server environment
  MITRE ATT&CK   Threat technique mapping
  YAML           Suricata configuration
  XML            Wazuh/custom rule configuration
  JSON           Suricata event logging

## 🔧 Implementation

### 1. Wazuh Server Deployment

The Wazuh platform was deployed with its main components:

-   Wazuh Manager
-   Wazuh Indexer
-   Wazuh Dashboard

The dashboard was verified after installation to confirm that the
platform was operational.

### 2. Wazuh Agent Deployment

A Wazuh agent was installed on the monitored host and enrolled with the
Wazuh manager.

The agent status was verified through the Wazuh dashboard before
continuing with the IDS integration.

### 3. Suricata IDS Installation

Suricata was installed on the monitored host and configured as the
network intrusion detection component.

The project used Suricata's `AF_PACKET` capture method for network
traffic monitoring.

### 4. Suricata Configuration

The `suricata.yaml` configuration was updated for the lab environment.

Key configuration areas included:

-   `HOME_NET`
-   `AF_PACKET`
-   Community Flow ID
-   `eve.json` output
-   Suricata rule configuration

Structured JSON logging was enabled so that Suricata security events
could be consumed by Wazuh.

### 5. Suricata Rule Configuration

The Suricata Emerging Threats Open ruleset was updated.

A custom local detection rule was also configured to demonstrate custom
IDS rule authoring and alert generation.

### 6. Wazuh and Suricata Integration

Suricata events generated in `eve.json` were integrated into Wazuh.

The Wazuh agent was configured to monitor the Suricata event log so that
alerts could be collected, decoded, and displayed in the Wazuh
dashboard.

The integration allowed Suricata network security events to be analyzed
alongside Wazuh security telemetry.

## 🧪 Testing & Alert Validation

Controlled test traffic was generated from the lab environment to
validate the detection pipeline.

The testing process included:

1.  Generating controlled network traffic.
2.  Allowing Suricata to inspect the traffic.
3.  Triggering Suricata detection rules.
4.  Recording events in `eve.json`.
5.  Forwarding the events through the Wazuh agent.
6.  Verifying the resulting alerts in Wazuh.
7.  Reviewing alert details and severity.
8.  Analyzing the activity through the Wazuh dashboard.

## 📊 MITRE ATT&CK Mapping

The resulting security events were analyzed using the Wazuh MITRE ATT&CK
integration.

The project included analysis of techniques associated with activities
such as:

-   Credential Access
-   Privilege Escalation
-   Defense Evasion

The Wazuh dashboard was used to review the observed ATT&CK techniques
and endpoint security information.

## 📁 Suggested Repository Structure

``` text
wazuh-suricata-soc-lab/
│
├── README.md
│
├── documentation/
│   └── project-report.pdf
│
├── screenshots/
│   ├── wazuh-dashboard.png
│   ├── wazuh-agent.png
│   ├── suricata-configuration.png
│   ├── suricata-alerts.png
│   ├── wazuh-alert.png
│   └── mitre-attack-dashboard.png
│
├── wazuh/
│   └── custom-rules.xml
│
└── suricata/
    ├── suricata.yaml
    └── local.rules
```

## ✅ Project Results

The project successfully demonstrated:

-   Wazuh SIEM deployment and configuration.
-   Wazuh agent enrollment and monitoring.
-   Suricata IDS installation and configuration.
-   Suricata event generation.
-   Integration of Suricata alerts with Wazuh.
-   Custom detection rule validation.
-   Controlled traffic testing.
-   Security alert visualization in Wazuh.
-   MITRE ATT&CK-based security analysis.

## 📚 Documentation

The complete project report is available in the `documentation/`
directory.

> **Note:** Before publishing the report or screenshots publicly, remove
> or anonymize passwords, API keys, credentials, private IP information,
> usernames, email addresses, and other sensitive environment details.

## ⚠️ Disclaimer

This project was conducted in a controlled lab environment for
educational and cybersecurity learning purposes.

Only perform security testing on systems and networks for which you have
explicit authorization.

## 👤 Author

**\[Your Name\]**

Cybersecurity / SOC Lab Project

------------------------------------------------------------------------
