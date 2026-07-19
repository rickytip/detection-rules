## Description
The DD command is a low-level data manipulation tool in Unix/Linux systems that can directly read and write data blocks. During the post-exploitation phase of malicious activities, attackers frequently use the DD command for destructive operations by directly writing random data, zeros, or null values to files or disk sectors, making the original data physically unrecoverable. Unlike standard deletion, DD overwrite operations bypass most data recovery techniques, causing permanent damage. This technique is commonly used to overwrite critical system files, destroy evidence, erase intrusion traces, or as the final step in ransomware attacks. In mission-critical systems, such attacks can result in extended service outages and irreversible data loss, making timely detection of these malicious activities essential.

## Challenge Objective
Identify suspicious usage patterns of the DD command in systems. Focus on DD commands combined with specific input sources (such as /dev/zero, /dev/urandom, or /dev/null) that output to critical system files, configuration directories, or locations containing large volumes of stored data.

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
  "SystemTime": "2025-03-18T03:48:49.850309000Z",
  "EventRecordID": "38550",
  "ProcessID": "7850",
  "ThreadID": "7850",
  "Channel": "Linux-Sysmon/Operational",
  "Computer": "ubuntu-soclabs",
  "UserId": "0",
  "RuleName": "-",
  "UtcTime": "2025-03-18 03:48:49.849",
  "ProcessGuid": "{09a89e73-ed21-67d8-21ee-960ada5a0000}",
  "ProcessId": "22204",
  "Image": "/usr/bin/dd",
  "FileVersion": "-",
  "Description": "-",
  "Product": "-",
  "Company": "-",
  "OriginalFileName": "-",
  "CommandLine": "dd of=/var/log/auth.log if=/dev/zero count=33 iflag=count_bytes",
  "CurrentDirectory": "/var/log",
  "User": "root",
  "LogonGuid": "{09a89e73-ea7a-67d8-0000-000003000000}",
  "LogonId": "0",
  "TerminalSessionId": "541",
  "IntegrityLevel": "no level",
  "Hashes": "SHA256=51f8ce55882af86c5c9ffd9f1b1ecafec4549e94c6deef6c28e74229dcdc7fb2",
  "ParentProcessGuid": "{09a89e73-ea7a-67d8-2da3-90228e640000}",
  "ParentProcessId": "21909",
  "ParentImage": "/usr/bin/bash",
  "ParentCommandLine": "-bash",
  "ParentUser": "root",
  "timestamp": "2025-05-12T07:01:49.316432"
}
## Reference
https://www.atomicredteam.io/docs/atomics/T1485

## Results 
<img width="1096" height="823" alt="Screenshot 2026-07-18 at 11 49 06 PM" src="https://github.com/user-attachments/assets/e62f2a8d-308b-45c7-a682-ba8cacc631f0" />
