## Description
The immutable attribute in Linux systems is an important mechanism for protecting critical files. Files with this attribute cannot be modified or deleted even by the root user until the attribute is removed. During security incidents, attackers who have gained system privileges often use the chattr tool to remove these protective attributes, preparing for subsequent system file modifications, backdoor installations, or system damage. This operation is rare in normal system administration but serves as a critical preliminary step in attack chains. Monitoring and identifying abnormal removal of immutable attributes is valuable for early detection of system intrusion signs.

## Challenge Objective
Identify behaviors that use the chattr command to remove file immutable attributes. Focus on command patterns that include "-i" or "i-" in the parameters.

## Data Sample
Data source: Sysmon, Data sample:
{
  "Name": "ParentUser",
  "Guid": "{ff032593-a8d3-4f13-b0d6-01fc615a0f97}",
  "EventID": "1",
  "Version": "5",
  "Level": "4",
  "Task": "1",
  "Opcode": "0",
  "Keywords": "0x8000000000000000",
  "SystemTime": "2025-03-14T10:24:18.236731000Z",
  "EventRecordID": "20463",
  "ProcessID": "7850",
  "ThreadID": "7850",
  "Channel": "Linux-Sysmon/Operational",
  "Computer": "ubuntu-soclabs",
  "UserId": "0",
  "RuleName": "-",
  "UtcTime": "2025-03-14 10:24:18.235",
  "ProcessGuid": "{09a89e73-03d2-67d4-652e-35147f5d0000}",
  "ProcessId": "9660",
  "Image": "/usr/bin/chattr",
  "FileVersion": "-",
  "Description": "-",
  "Product": "-",
  "Company": "-",
  "OriginalFileName": "-",
  "CommandLine": "chattr -i /etc/passwd",
  "CurrentDirectory": "/",
  "User": "root",
  "LogonGuid": "{09a89e73-a5e8-67d3-0000-000002000000}",
  "LogonId": "0",
  "TerminalSessionId": "8",
  "IntegrityLevel": "no level",
  "Hashes": "SHA256=b99f7278f6407a7a1119e344d2f4b6e4fb852c94181fd3b32ff6987c1db5e419",
  "ParentProcessGuid": "{00000000-0000-0000-0000-000000000000}",
  "ParentProcessId": "2297",
  "ParentImage": "-",
  "ParentCommandLine": "-",
  "ParentUser": "-",
  "timestamp": "2025-05-12T07:19:52.413773"
}
## References 
https://linuxize.com/post/chattr-command-in-linux/

## Results 
<img width="1137" height="789" alt="Screenshot 2026-07-19 at 12 58 18 AM" src="https://github.com/user-attachments/assets/4b9af8c9-59cb-4e7c-8d88-9046dfbb5931" />
