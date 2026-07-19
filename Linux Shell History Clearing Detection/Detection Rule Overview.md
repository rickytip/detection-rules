## Description
In Linux systems, shell commands executed by users are typically recorded in history files (such as ~/.bash_history, ~/.zsh_history, etc.), providing system administrators and security analysts with important evidence for auditing and investigating system activities. However, in intrusion scenarios, attackers often attempt to clear command history to conceal their actions and prevent detection and tracking.

## Challenge Objective
Develop a rule to identify history clearing behaviors in Linux environments.

## Data Sample
Data source: Sysmon, sample data:

{
    "Name": "ParentUser", 
    "Guid": "{ff032593-a8d3-4f13-b0d6-01fc615a0f97}", 
    "EventID": "1", 
    "Version": "5", 
    "Level": "4", 
    "Task": "1", 
    "Opcode": "0", 
    "Keywords": "0x8000000000000000", 
    "SystemTime": "2025-03-27T06:48:18.556872000Z", 
    "EventRecordID": "530733", 
    "ProcessID": "119520", 
    "ThreadID": "119520", 
    "Channel": "Linux-Sysmon/Operational", 
    "Computer": "ubuntulog", 
    "UserId": "0", 
    "RuleName": "-", 
    "UtcTime": "2025-03-27 06:48:18.561", 
    "ProcessGuid": "{15b7b743-f4b2-67e4-41ea-579697600000}", 
    "ProcessId": "121754", 
    "Image": "/usr/bin/rm", 
    "FileVersion": "-", 
    "Description": "-", 
    "Product": "-", 
    "Company": "-", 
    "OriginalFileName": "-", 
    "CommandLine": "rm ~./bash_history", 
    "CurrentDirectory": "/", 
    "User": "root", 
    "LogonGuid": "{15b7b743-0000-0000-0000-000003000000}", 
    "LogonId": "0", 
    "TerminalSessionId": "68", 
    "IntegrityLevel": "no level", 
    "Hashes": "SHA256=8e3faaa5eb4a2a4d0e2788fe442bcac6d604be5a0c5a9f09d08f06e3a3fcf570", 
    "ParentProcessGuid": "{15b7b743-f3d7-67e4-2d23-edb346580000}", 
    "ParentProcessId": "120415", 
    "ParentImage": "/usr/bin/bash", 
    "ParentCommandLine": "bash", 
    "ParentUser": "root"
    }
## References
https://www.atomicredteam.io/docs/atomics/T1070.003

## Results
<img width="1073" height="775" alt="Screenshot 2026-07-19 at 4 14 38 PM" src="https://github.com/user-attachments/assets/7162ecd9-c8ad-4a30-93b5-5e0ea1ad8522" />
