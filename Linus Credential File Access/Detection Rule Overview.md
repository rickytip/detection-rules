## Detection Detail

## Description
When hackers infiltrate a Linux server, they typically examine the /etc/passwd and /etc/shadow files. By combining these two files, attackers can obtain the system user list and corresponding password hashes, which they can then attempt to crack to retrieve plaintext credentials for privilege escalation or lateral movement to other systems.

## Challenge Objective
Use SIEM query statements to identify operations that view /etc/passwd and /etc/shadow files, such as common file viewing operations like cat /etc/passwd.

## Data Sample
Data source: Sysmon, Sample data:

{
	"EventID": "1",
  "Version": "5",
	"Level": "4",
	"Task": "1",
	"Opcode": "0",
	"Keywords": "0x8000000000000000",
	"EventRecordID": "729530",
	"Correlation": null,
	"Channel": "Linux-Sysmon/Operational",
	"Computer": "sysmonlinux-tcontreras-attack-range-643",
	"RuleName": "-",
	"UtcTime": "2021-12-21 12:53:05.015",
	"ProcessGuid": "{ec2b6afe-ce31-61c1-d009-8b6c8f550000}",
	"ProcessId": "10166",
	"Image": "/bin/cat",
	"FileVersion": "-",
	"Description": "-",
	"Product": "-",
	"Company": "-",
	"OriginalFileName": "-",
	"CommandLine": "cat /etc/passwd",
	"CurrentDirectory": "/home/ubuntu",
	"User": "root",
	"LogonGuid": "{ec2b6afe-0000-0000-0000-000000000000}",
	"LogonId": "0",
	"TerminalSessionId": "6",
	"IntegrityLevel": "no level",
	"Hashes": "-",
	"ParentProcessGuid": "{ec2b6afe-ce31-61c1-6882-af81a3550000}",
	"ParentProcessId": "10164",
	"ParentImage": "/bin/dash",
	"ParentCommandLine": "sh",
	"ParentUser": "root"
}
## Reference: 
https://attack.mitre.org/techniques/T1003/008/

## Results 
<img width="1085" height="727" alt="Screenshot 2026-07-18 at 1 40 49 PM" src="https://github.com/user-attachments/assets/1d2542a4-174d-4cce-a054-e67f4e61e706" />

