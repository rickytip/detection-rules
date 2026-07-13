# Description
In APT attacks, attackers often attempt to steal sensitive data from target networks. For extremely large files, advanced attackers employ chunked data transfer techniques - splitting data into smaller packets for transmission to avoid detection by security devices.

This technique effectively bypasses security measures based on transfer volume monitoring because the size of each data packet is carefully controlled to remain below security thresholds. Meanwhile, attackers can steal large amounts of data by increasing transmission frequency or extending transmission time, ultimately achieving data leakage. This slow data exfiltration method is more difficult for traditional security tools to detect and poses a serious threat to an organization’s data security.

Challenge Objective
Identify suspicious behavior in Linux systems using the split command for file splitting. This operation indicates that a user is breaking large files into fixed-size chunks, possibly in preparation for subsequent data exfiltration.

Data Sample
{  "Name": "ParentUser",  
"Guid": "{ff032593-a8d3-4f13-b0d6-01fc615a0f97}",  
"EventID": "1",  
"Version": "5",  
"Level": "4",  
"Task": "1",  
"Opcode": "0",  
"Keywords": "0x8000000000000000",  
"SystemTime": "2025-03-20T02:35:47.766713000Z",  
"EventRecordID": "92148",  "ProcessID": "27697",  
"ThreadID": "27697",  
"Channel": "Linux-Sysmon/Operational",  
"Computer": "ubuntu-soclabs",  
"UserId": "0",  "RuleName": "-",  
"UtcTime": "2025-03-20 02:35:47.765",  
"ProcessGuid": "{09a89e73-7f03-67db-618c-d0a2e6560000}",  
"ProcessId": "43592",  
"Image": "/usr/bin/split",  
"FileVersion": "-",  
"Description": "-",  
"Product": "-",  
"Company": "-",  
"OriginalFileName": "-",  
"CommandLine": "split -b 50000 admin-data split_",  
"CurrentDirectory": "/data",  
"User": "root",  
"LogonGuid": "{09a89e73-7c26-67da-0000-000004000000}",  
"LogonId": "0",  
"TerminalSessionId": "541",  
"IntegrityLevel": "no level",  
"Hashes": "SHA256=0689b44064c892b5cb11f710c8fd86c79308965511afe630feec883bcb7b3e88",  
"ParentProcessGuid": "{09a89e73-7c26-67da-2da3-d56fef610000}",  
"ParentProcessId": "27254",  
"ParentImage": "/usr/bin/bash",  
"ParentCommandLine": "-bash",  
"ParentUser": "root",  
"timestamp": "2025-03-20T03:15:56.932476"}
