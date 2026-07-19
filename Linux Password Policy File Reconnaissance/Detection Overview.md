Description
Password policy configurations in Linux systems are crucial for maintaining system security. These policies are typically defined in specific configuration files such as /etc/login.defs (which defines password expiration times, history records, etc.) and /etc/pam.d/common-password (PAM module configuration). During normal system administration, administrators occasionally need to view these files for configuration adjustments. However, in penetration testing or malicious intrusion scenarios, attackers often examine these files to understand password policy restrictions and develop more precise attack strategies. For example, by understanding password minimum length, complexity requirements, and expiration times, attackers can optimize password guessing strategies or identify accounts likely using weak passwords.

Challenge Objective
Create a rule to identify behaviors where common text viewing tools (such as cat, vim, etc.) are used to access Linux password policy configuration files. Files of interest include /etc/login.defs, /etc/pam.d/common-password, and other files containing password policies.

Data Sample
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
    "SystemTime": "2025-04-02T06:20:20.337444000Z", 
    "EventRecordID": "628883", 
    "ProcessID": "169385", 
    "ThreadID": "169385", 
    "Channel": "Linux-Sysmon/Operational", 
    "Computer": "ubuntulog", 
    "UserId": "0", 
    "RuleName": "-", 
    "UtcTime": "2025-04-02 06:20:20.338", 
    "ProcessGuid": "{15b7b743-d724-67ec-e1fc-11470b560000}", 
    "ProcessId": "172402", 
    "Image": "/usr/bin/vim.basic", 
    "FileVersion": "-", 
    "Description": "-", 
    "Product": "-", 
    "Company": "-", 
    "OriginalFileName": "-", 
    "CommandLine": "vim /etc/pam.d/common-password", 
    "CurrentDirectory": "/home", 
    "User": "root", 
    "LogonGuid": "{15b7b743-0000-0000-0000-000002000000}", 
    "LogonId": "0", 
    "TerminalSessionId": "92", 
    "IntegrityLevel": "no level", 
    "Hashes": "SHA256=1ffb5584b21833f650b45754309c3af8fb9a5a8b8a46df26cd396e2b6529f0d3", 
    "ParentProcessGuid": "{00000000-0000-0000-0000-000000000000}", 
    "ParentProcessId": "162880", 
    "ParentImage": "-", 
    "ParentCommandLine": "-", 
    "ParentUser": "-"
    }
References
https://www.atomicredteam.io/docs/atomics/T1201
https://detection.fyi/sigmahq/sigma/linux/auditd/lnx_auditd_password_policy_discovery/

## Results
<img width="1080" height="773" alt="Screenshot 2026-07-19 at 5 52 54 PM" src="https://github.com/user-attachments/assets/20ca4ef8-aeca-4009-b15e-a307b3ae8af0" />
