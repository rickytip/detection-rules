## Description
When web applications developed in Python contain command execution vulnerabilities, attackers can exploit these vulnerabilities to execute arbitrary system commands. These vulnerabilities typically form a characteristic call chain: the Python process acts as the parent process that invokes system processes.

Once attackers successfully exploit such vulnerabilities, they can execute arbitrary system commands to obtain sensitive information, establish reverse connections, implant backdoors, move laterally within the network, or escalate privileges. In enterprise environments, these vulnerabilities are particularly dangerous because backend services often run with elevated privileges and may handle sensitive business data.

## Challenge Objective
Develop a detection rule to identify suspicious call chains where Python processes execute system commands.

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
  "SystemTime": "2025-03-19T12:40:26.981404000Z",
  "EventRecordID": "47719",
  "ProcessID": "27697",
  "ThreadID": "27697",
  "Channel": "Linux-Sysmon/Operational",
  "Computer": "ubuntu-soclabs",
  "UserId": "0",
  "RuleName": "-",
  "UtcTime": "2025-03-19 12:40:26.979",
  "ProcessGuid": "{09a89e73-bb3a-67da-718a-5561ce5c0000}",
  "ProcessId": "28692",
  "Image": "/usr/sbin/ifconfig",
  "FileVersion": "-",
  "Description": "-",
  "Product": "-",
  "Company": "-",
  "OriginalFileName": "-",
  "CommandLine": "ifconfig",
  "CurrentDirectory": "/data",
  "User": "root",
  "LogonGuid": "{09a89e73-7c26-67da-0000-000004000000}",
  "LogonId": "0",
  "TerminalSessionId": "541",
  "IntegrityLevel": "no level",
  "Hashes": "SHA256=207e6219e9ba3cfeca11fafca3002d0f5a13219d4f4b22ee745df67a71ad6502",
  "ParentProcessGuid": "{09a89e73-baf7-67da-dd27-700000000000}",
  "ParentProcessId": "28688",
  "ParentImage": "/usr/bin/python3.12",
  "ParentCommandLine": "python3",
  "ParentUser": "root",
  "timestamp": "2025-03-19T13:18:28.935464"
}
## References
https://attack.mitre.org/techniques/T1059/006/

## Results
