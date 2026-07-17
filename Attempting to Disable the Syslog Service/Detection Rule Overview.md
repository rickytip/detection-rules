Description
The Syslog service is a core component for system and application logging, playing a critical role in security monitoring. The log data it collects provides essential evidence for detecting and analyzing security events. However, attackers may attempt to disable or shut down the Syslog service to hide their activities or prevent the system from recording critical behaviors. This action could render security monitoring ineffective, increasing the risk of further system exploitation. Therefore, promptly identifying attempts to disable the Syslog service is a necessary measure to ensure system security and integrity.

Challenge Objective
Write rules to identify attempts to disable or shut down the Syslog service in Linux systems, considering all possible commands or operations that could be used to deactivate the service.

Data Sample
Data source: Sysmon, sample data:
{  "Name": "ParentUser",  
"Guid": "{ff032593-a8d3-4f13-b0d6-01fc615a0f97}",  
"EventID": "1",  
"Version": "5",  
"Level": "4",  
"Task": "1",  
"Opcode": "0",  
"Keywords": "0x8000000000000000",  
"SystemTime": "2025-03-20T06:36:41.581212000Z",  
"EventRecordID": "95855",  
"ProcessID": "45011",  
"ThreadID": "45011",  
"Channel": "Linux-Sysmon/Operational",  
"Computer": "ubuntu-soclabs",  
"UserId": "0",  
"RuleName": "-",  
"UtcTime": "2025-03-20 06:36:41.585",  
"ProcessGuid": "{09a89e73-b779-67db-7dc7-d94a515e0000}",  
"ProcessId": "45236",  
"Image": "/usr/bin/systemctl",  
"FileVersion": "-",  
"Description": "-",  
"Product": "-",  
"Company": "-",  
"OriginalFileName": "-",  
"CommandLine": "systemctl disable rsyslog",  
"CurrentDirectory": "/root",  
"User": "root",  
"LogonGuid": "{09a89e73-8668-67db-0000-000002000000}",  
"LogonId": "0",  
"TerminalSessionId": "1034",  
"IntegrityLevel": "no level",  
"Hashes": "SHA256=8872043fc990d387b8d7f39caa52359e5446f47d04b76008107bf2f7c2eaa232",  
"ParentProcessGuid": "{00000000-0000-0000-0000-000000000000}",  
"ParentProcessId": "43774",  
"ParentImage": "-",  
"ParentCommandLine": "-",  
"ParentUser": "-",  
"timestamp": "2025-03-20T06:41:17.733850"}

Reference: https://filestore.fortinet.com/docs.fortinet.com/fsiem/Public_Resource_Access/7_5_1/rules/PH_RULE_TH_Linux_disable_syslog.htm
