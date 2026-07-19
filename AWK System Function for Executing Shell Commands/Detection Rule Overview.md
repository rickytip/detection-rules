## Description
AWK is a powerful text processing tool widely used in log analysis and system administration. Its system() function allows AWK scripts to execute arbitrary shell commands, providing tremendous flexibility. However, this capability also introduces potential security risks. Malicious users may exploit AWK’s system() function to execute unauthorized commands on systems, particularly when AWK runs as root or with privileged user permissions, potentially leading to privilege escalation or complete system compromise.

## Challenge Objective
Create a detection rule to identify the use of the system() function to execute shell commands through AWK commands (including awk, gawk, nawk, or mawk variants). The rule should account for common command structures, such as system() calls within BEGIN{} blocks, commands passed through variables, and command execution during file processing.

## Data Samples
{
	"Name": "ParentUser", 
	"Guid": "{ff032593-a8d3-4f13-b0d6-01fc615a0f97}", 
	"EventID": "1", 
	"Version": "5", 
	"Level": "4", 
	"Task": "1", 
	"Opcode": "0", 
	"Keywords": "0x8000000000000000", 
	"SystemTime": "2025-03-24T06:43:56.202384000Z", 
	"EventRecordID": "153787", 
  "ProcessID": "195011", 
	"ThreadID": "195011", 
	"Channel": "Linux-Sysmon/Operational", 
	"Computer": "ubuntulog", 
	"UserId": "0", 
	"RuleName": "-", 
	"UtcTime": "2025-03-24 06:43:56.206", 
	"ProcessGuid": "{15b7b743-ff2c-67e0-5d53-490000000000}", 
	"ProcessId": "200606", 
	"Image": "/usr/bin/gawk", 
	"FileVersion": "-", 
	"Description": "-", 
	"Product": "-", 
	"Company": "-", 
	"OriginalFileName": "-", 
	"CommandLine": "awk BEGIN{system(\"cat /etc/passwd\")}", 
	"CurrentDirectory": "/home", 
	"User": "root", 
	"LogonGuid": "{15b7b743-0000-0000-0000-000003000000}", 
	"LogonId": "0", 
	"TerminalSessionId": "96", 
	"IntegrityLevel": "no level", 
	"Hashes": "SHA256=b951dad211e5b2fcb1fa989a483c52ca3ce80b9353668307989826b114ce8e0c", 
	"ParentProcessGuid": "{15b7b743-fc8d-67e0-2d73-045c095a0000}", 
	"ParentProcessId": "196492", 
	"ParentImage": "/usr/bin/bash", 
	"ParentCommandLine": "bash", 
	"ParentUser": "root"
	}
  ## References: 
  https://gtfobins.org/gtfobins/awk/#shell
  https://www.baeldung.com/linux/shell-functions-awk-scripts

  ## Results 
  <img width="1106" height="816" alt="Screenshot 2026-07-18 at 9 25 04 PM" src="https://github.com/user-attachments/assets/6ee1be98-4bc7-4870-9e4d-57903dcb13aa" />
