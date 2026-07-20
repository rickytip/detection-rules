## Description
File timestamps are critical metadata that operating systems use to record a file’s lifecycle, including access time (atime), modification time (mtime), change time (ctime), and on some filesystems, creation time (birthtime).

In Unix/Linux systems, tools like touch can view and modify these timestamps. Specifically, the touch command’s -t and -r parameters allow users to set file timestamps to any arbitrary time or match them with a reference file. While this capability serves legitimate purposes in system administration, it can also be exploited to conceal evidence of intrusion in malicious scenarios.

## Challenge Objective
Develop a rule to identify suspicious file timestamp modifications in Linux/Unix environments. The rule should focus on detecting timestamp manipulation operations performed using tools like touch.

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
    "SystemTime": "2025-04-22T07:10:56.731103000Z", 
    "EventRecordID": "1212492", 
    "ProcessID": "465218", 
    "ThreadID": "465218", 
    "Channel": "Linux-Sysmon/Operational", 
    "Computer": "ubuntulog", 
    "UserId": "0", 
    "RuleName": "-", 
    "UtcTime": "2025-04-22 07:10:56.733", 
    "ProcessGuid": "{15b7b743-4100-6807-5130-c073d15c0000}", 
    "ProcessId": "467060", 
    "Image": "/usr/bin/touch", 
    "FileVersion": "-", 
    "Description": "-", 
    "Product": "-", 
    "Company": "-", 
    "OriginalFileName": "-", 
    "CommandLine": "touch -t 202001010000.00 /etc/shadow", 
    "CurrentDirectory": "/home/admin", 
    "User": "root", 
    "LogonGuid": "{15b7b743-0000-0000-0000-000003000000}", 
    "LogonId": "0", 
    "TerminalSessionId": "246", 
    "IntegrityLevel": "no level", 
    "Hashes": "SHA256=8b0047b0de380f0bac3855400263214e33fbc2995b5637e9104a9de3f738ec82", 
    "ParentProcessGuid": "{00000000-0000-0000-0000-000000000000}", 
    "ParentProcessId": "460145", 
    "ParentImage": "-", 
    "ParentCommandLine": "-", 
    "ParentUser": "-"
    }
## References
https://www.atomicredteam.io/docs/atomics/T1070.006

## Results 
<img width="1062" height="773" alt="Screenshot 2026-07-19 at 8 27 47 PM" src="https://github.com/user-attachments/assets/955f9f96-b6ff-4ed2-a143-fbbf7b51927f" />
