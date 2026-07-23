# SOC-Monitoring-Incident-Response-Lab

The lab integrates Wazuh SIEM/XDR, Kali Linux, Windows 11, Ubuntu Server and MITRE ATT&CK mapping to simulate real-world attacks and defensive operations.

The objective is to gain practical blue team experience in:

* Log collection
* Threat detection
* Security monitoring
* Incident investigation
* Vulnerability management
* Digital forensics
* MITRE ATT&CK mapping
* Incident response

| Technology        | Purpose                   |
| ----------------- | ------------------------- |
| Wazuh             | SIEM + XDR                |
| Sysmon            | Endpoint telemetry        |
| Windows 11        | Target machine            |
| Ubuntu Server     | Wazuh Manager             |
| Kali Linux        | Attack machine            |
| VirtualBox        | Virtualisation            |
| MITRE ATT&CK      | Threat Mapping            |
| Sigma Rules       | Detection Rules           |
| PowerShell        | Windows Attack Simulation |
| Atomic Red Team   | Attack Simulation         |

# Lab Architecture

                  Internet
                      │
             ┌────────┴────────┐
             │                 │
         Kali Linux      Windows 11
        (Attacker)        (Victim)
             │
             │ Sysmon Logs
             │
      Wazuh Agent
             │
      Ubuntu Wazuh Server
             │
        SOC Analyst

# Project Objectives

✔ Deploy Wazuh SIEM

✔ Install Sysmon

✔ Collect Windows Event Logs

✔ Detect malicious PowerShell

✔ Monitor failed logins

✔ Detect privilege escalation

✔ Investigate phishing activity

✔ Simulate malware execution

✔ Document incident response

## Attack Simulations


### 1.Brute Force Login

Tool

Hydra

MITRE ATT&CK

T1110

Evidence

* Multiple failed logins
* Account lockout
* Event ID 4625


### 2.Malicious PowerShell

Command

powershell.exe -EncodedCommand

MITRE ATT&CK

T1059.001

Detection

* Sysmon Event ID 1
* PowerShell logs
* Wazuh Alert

### 3.Mimikatz Execution

MITRE

T1003

Detection

* Suspicious LSASS access
* Sysmon Event ID 10
* Wazuh Critical Alert

#### 4. Reverse Shell

Kali

nc -lvnp 4444 


Windows

powershell reverse shell

Detection

Network connection

Process creation

Command line logging

### 5. Phishing Email Investigation

Scenario

User receives fake Microsoft login email.

Indicators

Suspicious sender
Shortened URL
Credential harvesting
Fake attachment

MITRE

T1566

Investigation

Email headers

Domain reputation

URL analysis

IOC extraction

## Wazuh Alerts

Examples investigated:

* Malware Detection
* Privilege Escalation
* Brute Force Attack
* New User Creation
* PowerShell Execution
* Suspicious Process Creation
* Windows Defender Alerts

## Incident Response Example

Incident

Suspicious PowerShell Execution

Detection

Wazuh generated a High Severity alert after Sysmon detected an encoded PowerShell command.

Analysis

Reviewed:

* Parent Process
* Command Line
* User Account
* Hash Values
* Network Connections


Mapped to:

MITRE ATT&CK

T1059.001

Containment

* Disabled user account
* Isolated endpoint
* Blocked IP

Eradication

* Removed malicious script
* Performed antivirus scan
* Reset credentials

Recovery

* Restored system
* Verified integrity
* Continued monitoring


Lessons Learned

* Enable PowerShell Logging
* Improve detection rules
* Increase phishing awareness training
