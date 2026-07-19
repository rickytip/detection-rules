## Description
In Linux systems, files and directories that begin with a dot (.) are hidden by default. Regular users cannot see these files with the standard ls command and must use ls -a to display them. While this feature was originally designed to keep system configuration files from cluttering user views, threat actors frequently abuse this mechanism to conceal malicious files.

Attackers typically create dot-prefixed files in key directories to hide backdoors, malicious scripts, or data theft tools. These hidden files are often placed in locations that regular users rarely check, such as the root directory, temporary directories, or system directories, enabling long-term persistence in the system.

## Challenge Objective
Develop a detection rule that identifies the creation of hidden files in Linux environments while avoiding false positives from legitimate system activities.

## Data Sample
Data source: Sysmon, Sample data:

{
  "Name": "User",
  "Guid": "{ff032593-a8d3-4f13-b0d6-01fc615a0f97}",
  "EventID": "11",
  "Version": "2",
  "Level": "4",
  "Task": "11",
  "Opcode": "0",
  "Keywords": "0x8000000000000000",
  "SystemTime": "2025-03-19T10:39:11.985389000Z",
  "EventRecordID": "46904",
  "ProcessID": "27697",
  "ThreadID": "27697",
  "Channel": "Linux-Sysmon/Operational",
  "Computer": "ubuntu-soclabs",
  "UserId": "0",
  "RuleName": "-",
  "UtcTime": "2025-03-19 10:39:11.986",
  "ProcessGuid": "{09a89e73-9ec6-67da-dd27-700000000000}",
  "ProcessId": "28365",
  "Image": "/usr/bin/python3.12",
  "TargetFilename": "/data/.shellcode",
  "CreationUtcTime": "2025-03-19 10:39:11.986",
  "User": "-",
  "timestamp": "2025-03-19T10:48:57.878466"
}
## References
https://www.atomicredteam.io/docs/atomics/T1564.001#atomic-test-1---create-a-hidden-file-in-a-hidden-directory

## Results
<img width="1112" height="835" alt="Screenshot 2026-07-19 at 2 23 40 AM" src="https://github.com/user-attachments/assets/1f782f31-1191-4389-afa1-fb1a17bc8ca7" />
