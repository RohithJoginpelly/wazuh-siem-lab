Here is a polished README you can paste into your **Wazuh SIEM Lab** repo. It is structured to look more professional, recruiter-friendly, and easy to scan, while keeping your screenshots and incident analysis front and center. [github](https://github.com/Pontipek/Wazuh-SIEM-Lab/blob/main/README.md)

# Wazuh SIEM Lab



## Overview

This project demonstrates the deployment and use of a Security Information and Event Management (SIEM) platform using Wazuh. The goal of the lab was to simulate common attacker behavior, generate security events, and analyze how a SOC detects and responds to suspicious activity using centralized log monitoring and alerting. [documentation.wazuh](https://documentation.wazuh.com/current/index.html)

## Project Objective

- Deploy a working SIEM environment.
- Collect and analyze system and security logs.
- Simulate common cyber attacks.
- Detect threats using Wazuh rules.
- Perform basic incident analysis.

## Lab Architecture

```text
[ Windows Server ] ---> Wazuh Agent
[ Ubuntu Server ] ---> Wazuh Manager ---> Wazuh Indexer ---> Dashboard
                        ↑
                   Log Sources (auth.log, system logs)
```

## Setup

- Installed Wazuh Manager, Indexer, and Dashboard.
- Configured the Wazuh Agent on Windows Server.
- Fixed SSL and authentication issues.
- Connected all components successfully.
- Verified that all services were running.

## Attack Simulation

The following attack scenarios were simulated to generate security events:

- Failed SSH login attempts.
- Invalid user login attempts.
- Sudo privilege escalation attempts.
- File integrity monitoring through test file creation.

Example commands used:

```bash
sudo -k
sudo ls
ssh fakeuser@localhost
sudo useradd attacker
touch /etc/test_alert
```

## Alert Detection

The Wazuh dashboard captured the simulated activity and generated alerts for authentication failures, brute-force style behavior, privilege escalation attempts, and file integrity monitoring events. [wazuh](https://wazuh.com)

## Incident Analysis

### SSH Brute Force Attack

**Attack Method:** Multiple failed SSH login attempts using an invalid user.

**Logs Observed:**
- Failed password for invalid user.
- Connection closed after repeated attempts.

**Wazuh Detection:**
- Authentication failure alerts generated.

**Analysis:**
This indicates a brute-force attack attempting to guess login credentials.

**Mitigation:**
- Use SSH key authentication.
- Disable password login.
- Implement Fail2Ban.

### Sudo Authentication Failure

**Attack Method:** Incorrect sudo password attempts.

**Logs Observed:**
- sudo authentication failure logs.

**Wazuh Detection:**
- Privilege escalation alerts triggered.

**Analysis:**
This shows an unauthorized attempt to gain root access.

**Mitigation:**
- Limit sudo access.
- Enable logging and monitoring.
- Review privileged accounts regularly.

### File Integrity Monitoring

**Action:** Created a file in `/etc`.

**Logs Observed:**
- File creation detected.

**Wazuh Detection:**
- File integrity alert generated.

**Analysis:**
This shows that system file monitoring is active and able to detect changes in critical directories.

**Mitigation:**
- Monitor critical directories.
- Alert on unauthorized changes.
- Investigate all unexpected file modifications.

## Evidence

### Wazuh Alert Dashboard



### SSH Brute Force Evidence



### Sudo Failure Evidence



### File Integrity Monitoring Evidence



## Results

- Successfully generated and monitored real-time alerts.
- Detected multiple attack patterns.
- Verified alert severity levels in the dashboard.
- Demonstrated log collection and analysis workflow.
- Mapped incident activity to common SOC-style response actions.

## Skills Gained

- SIEM deployment and configuration.
- Log analysis and monitoring.
- Security event detection.
- Attack simulation techniques.
- Basic incident response.
- File integrity monitoring.
- SSH and privilege escalation analysis.

## Tools Used

- Wazuh SIEM.
- Ubuntu Linux.
- Windows Server.
- SSH.
- Filebeat.

## Future Improvements

- Implement automated response with Fail2Ban.
- Integrate additional log sources such as web server or firewall logs.
- Add MITRE ATT&CK mapping to alerts.
- Deploy in a cloud environment such as AWS.
- Add real-time alert notifications.

## Conclusion

This lab demonstrates how a SIEM can collect logs, detect suspicious behavior, and support SOC-style incident analysis. It shows the importance of centralized monitoring, alert triage, and continuous hardening of endpoints and infrastructure. [documentation.wazuh](https://documentation.wazuh.com/current/index.html)
