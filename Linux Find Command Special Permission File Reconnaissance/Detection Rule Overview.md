## Description
The Find command is a powerful tool for file searching in Unix/Linux systems, frequently used by system administrators and regular users to locate files meeting specific criteria. However, due to find command’s flexibility and rich functionality, it has also become one of the preferred tools for attackers conducting system reconnaissance.

In penetration testing and malicious attack scenarios, the find command is commonly used to search for files with specific permissions (such as SUID/SGID files), find writable directories, discover files containing sensitive information, identify potential privilege escalation vulnerabilities, and collect system configuration information.

## Challenge Objective
Construct a rule to identify suspicious find command usage behaviors in the system. The rule should be able to distinguish between normal file search operations and command patterns that may indicate system reconnaissance activities. Special attention should be paid to combinations of find command with specific parameters, such as the -perm parameter for searching SUID/SGID files, the -user parameter for finding files owned by specific users, and the -type parameter for searching specific file types.

## Data Sample
Data source: Sysmon, data sample:

{
    "Name": "ParentUser", 
    "Guid": "{ff032593-a8d3-4f13-b0d6-01fc615a0f97}", 
    "EventID": "1", 
    "Version": "5", 
    "Level": "4", 
    "Task": "1", 
    "Opcode": "0", 
    "Keywords": "0x8000000000000000", 
    "SystemTime": "2025-04-03T02:46:49.391274000Z", 
    "EventRecordID": "738805", 
    "ProcessID": "169385", 
    "ThreadID": "169385", 
    "Channel": "Linux-Sysmon/Operational", 
    "Computer": "ubuntulog", 
    "UserId": "0", 
    "RuleName": "-", 
    "UtcTime": "2025-04-02 08:51:35.741", 
    "ProcessGuid": "{15b7b743-fa97-67ec-c1ec-3c460d640000}", 
    "ProcessId": "227633", 
    "Image": "/usr/bin/find", 
    "FileVersion": "-", 
    "Description": "-", 
    "Product": "-", 
    "Company": "-", 
    "OriginalFileName": "-", 
    "CommandLine": "find / -type f -mtime -1", 
    "CurrentDirectory": "/home", 
    "User": "root", 
    "LogonGuid": "{15b7b743-0000-0000-0000-000002000000}", 
    "LogonId": "0", 
    "TerminalSessionId": "123", 
    "IntegrityLevel": "no level", 
    "Hashes": "SHA256=ac1ea1c5391de921aca1572f1bf25d03707beb3887b27c16a5b4948fd553941b", 
    "ParentProcessGuid": "{15b7b743-f325-67ec-2d93-ed0410570000}", 
    "ParentProcessId": "216093", 
    "ParentImage": "/usr/bin/bash", 
    "ParentCommandLine": "bash", 
    "ParentUser": "root"
    }
    ## References
    https://github.com/SaiSathvik1/Linux-Privilege-Escalation-Notes
    https://www.atomicredteam.io/docs/atomics/T1083
    
  ## Results 
  <img width="1112" height="835" alt="Screenshot 2026-07-19 at 2 23 40 AM" src="https://github.com/user-attachments/assets/45eaf6d8-74c0-4c5b-bc29-ec09715077c7" />
