## Description
SSH port forwarding and tunneling is a technique that uses the SSH protocol to establish encrypted channels, allowing users to transmit data through these secure tunnels. It’s commonly used to securely traverse firewall restrictions to access internal resources.

In network attack scenarios, attackers typically exploit SSH tunneling techniques after gaining initial access to establish covert channels for lateral movement, data exfiltration, and bypassing network security controls. Since SSH traffic is encrypted and SSH connections are often considered legitimate in enterprise environments, attacks based on SSH tunnels are more difficult to detect. Identifying such behavior is crucial for timely discovery of potential network threats and ensuring security.

## Challenge Objective
Identify suspicious SSH tunnels and port forwarding operations. Focus on behaviors that include port forwarding parameters (such as -D, -L, -R) in SSH command lines to detect possible tunneling or forwarding activities.

## Data Sample
Data source: Sysmon, Sample data:

{
  "Name": "ParentUser",
  "Guid": "{ff032593-a8d3-4f13-b0d6-01fc615a0f97}",
  "EventID": "1",
  "Version": "5",
  "Level": "4",
  "Task": "1",
  "Opcode": "0",
  "Keywords": "0x8000000000000000",
  "SystemTime": "2025-03-21T03:48:53.317288000Z",
  "EventRecordID": "104113",
  "ProcessID": "45011",
  "ThreadID": "45011",
  "Channel": "Linux-Sysmon/Operational",
  "Computer": "ubuntu-soclabs",
  "UserId": "0",
  "RuleName": "-",
  "UtcTime": "2025-03-21 03:48:53.320",
  "ProcessGuid": "{09a89e73-e1a5-67dc-41c0-0eec9a5c0000}",
  "ProcessId": "48367",
  "Image": "/usr/bin/ssh",
  "FileVersion": "-",
  "Description": "-",
  "Product": "-",
  "Company": "-",
  "OriginalFileName": "-",
  "CommandLine": "ssh -R 8080:localhost:80 user@10.232.100.3",
  "CurrentDirectory": "/home",
  "User": "root",
  "LogonGuid": "{09a89e73-e005-67dc-0000-000002000000}",
  "LogonId": "0",
  "TerminalSessionId": "1210",
  "IntegrityLevel": "no level",
  "Hashes": "SHA256=cd0f2cd4cff42bcaca5a1bd6659467d2210678785b96204ea4a5f76af87dba58",
  "ParentProcessGuid": "{09a89e73-e005-67dc-2d93-2253f0580000}",
  "ParentProcessId": "48293",
  "ParentImage": "/usr/bin/bash",
  "ParentCommandLine": "-bash",
  "ParentUser": "root",
  "timestamp": "2025-03-21T03:57:05.192284"
}

## References 
https://builtin.com/software-engineering-perspectives/ssh-port-forwarding

## Results 
<img width="1117" height="823" alt="Screenshot 2026-07-19 at 2 58 34 PM" src="https://github.com/user-attachments/assets/865fcfe6-0aab-45a6-8b71-f93f7a333327" />
