# Splunk Universal Forwarder – Sysmon Event Collection Issue

## Objective

Document an issue encountered during the lab where **Sysmon events were not initially visible in Splunk Enterprise**, despite correct installation and configuration of Sysmon and the Splunk Universal Forwarder.

This document describes the observed behavior, the investigation performed, and the configuration change that allowed event ingestion to function correctly.

## Issue Description

During the lab setup, the following conditions were observed:

- Sysmon installed and running on the Windows endpoint.
- Splunk Universal Forwarder installed and running.
- Port `9997` reachable from the endpoint.
- Forwarder connected to Splunk Enterprise.
- No Sysmon events visible in Splunk searches.

This indicated that the issue was not related to basic connectivity or installation.

## Investigation

### Forwarder Log Review

To investigate the issue, the Splunk Universal Forwarder logs were reviewed.

Log file location on the **Windows endpoint VM**:

`C:\Program Files\SplunkUniversalForwarder\var\log\splunk\splunkd.log`

The following error was repeatedly observed:

![errorCode5-AccessDenied](../images/doc04/errorCode5-AccessDenied.png)

## Analysis

The `errorCode=5` value indicates an access-related issue.

At this point, the following had already been confirmed:

- Sysmon events existed locally in Windows Event Viewer.
- `inputs.conf` was correctly configured to collect Sysmon events.
- The forwarder was connected to the Splunk receiving port.

Based on this, the issue was identified as a **permission-related problem affecting access to the Sysmon event log channel**.

## Root Cause

The Splunk Universal Forwarder Windows service was running under a restricted service account `This account`.

This account did not have sufficient privileges to subscribe to the `Microsoft-Windows-Sysmon/Operational` event log channel.

## Solution

### Change Forwarder Service Account

On the **Windows endpoint VM**:

1. Open the Windows Services manager:

`services.msc`

![errorCode5-AccessDenied](../images/doc04/win-r-run-services.png)

2. Locate the **SplunkForwarder** service.
3. Open **Properties**.

`SplunkForwarder`

![errorCode5-AccessDenied](../images/doc04/services-main.png)

4. Navigate to the **Log On** tab.
5. Change the service account from:

`This account`

to:

`Local System account`

![errorCode5-AccessDenied](../images/doc04/log-on-local-system-account.png)

6. **Apply** the change and **restart the service**.

### Validation

After restarting the Splunk Universal Forwarder service:

- Sysmon events became visible in **Splunk Enterprise**. 

`http://localhost:8000`

- Events could be queried using:

`index=main source="WinEventLog:Microsoft-Windows-Sysmon/Operational"`

![Splunk-Web-Validation](../images/doc04/Splunk-Web-Validation.png)

The `splunkd.log` file continued to display access-related warnings; however, these did not prevent event ingestion.

Validation was performed by confirming the presence of Sysmon events in Splunk rather than relying solely on forwarder log output.

## Current State

- Sysmon events are being collected and indexed.
- The Splunk Universal Forwarder is operational.
- Event ingestion is functioning as expected.
- The lab is ready for further detection development.

### Notes

- Forwarder log warnings may persist even when data ingestion is functional.
- Event presence in Splunk was used as the primary validation method.
