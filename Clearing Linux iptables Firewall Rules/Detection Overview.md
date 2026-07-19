## Description
iptables is a powerful firewall tool in Linux systems responsible for managing network packet filtering and forwarding rules. In enterprise environments, iptables is typically configured with strict rule sets to protect systems from unauthorized access and malicious traffic. However, when attackers gain system privileges, a common tactic is to clear or modify these firewall rules to establish persistent access, open remote connection channels, or enable lateral movement. This behavior is particularly dangerous as it removes critical security boundaries from the system, allowing arbitrary traffic to pass through and exposing the system to various network attack risks.

## Challenge Objective
Create a detection rule to identify behaviors where iptables commands are used to clear or modify firewall rules to allow all traffic.

## Data Sample
Data source: Sysmon, example data:
{
	"Name": "ParentUser", 
	"Guid": "{ff032593-a8d3-4f13-b0d6-01fc615a0f97}", 
	"EventID": "1", 
	"Version": "5", 
	"Level": "4", 
	"Task": "1", 
	"Opcode": "0", 
	"Keywords": "0x8000000000000000", 
	"SystemTime": "2025-03-25T07:37:26.644736000Z", 
	"EventRecordID": "294770", 
	"ProcessID": "1309", 
	"ThreadID": "1309", 
	"Channel": "Linux-Sysmon/Operational", 
	"Computer": "ubuntulog", 
	"UserId": "0", 
	"RuleName": "-", 
	"UtcTime": "2025-03-25 07:37:29.910", 
	"ProcessGuid": "{15b7b743-5d39-67e2-eded-17e9d15b0000}", 
	"ProcessId": "2802", 
	"Image": "/usr/sbin/xtables-nft-multi", 
	"FileVersion": "-", 
	"Description": "-", 
	"Product": "-", 
	"Company": "-", 
	"OriginalFileName": "-", 
	"CommandLine": "iptables -A INPUT -i any -j ACCEPT", 
	"CurrentDirectory": "/home", 
	"User": "root", 
	"LogonGuid": "{15b7b743-0000-0000-0000-000003000000}", 
	"LogonId": "0", 
	"TerminalSessionId": "4", 
	"IntegrityLevel": "no level", 
	"Hashes": "SHA256=a1610dd70bb5ab04180671280df65b0077b680b627c0b6c51480b327732a762d", 
	"ParentProcessGuid": "{15b7b743-5cc4-67e2-2d63-f46def610000}", 
	"ParentProcessId": "2078", 
	"ParentImage": "/usr/bin/bash", 
	"ParentCommandLine": "bash", 
	"ParentUser": "root"
	}
## References
https://www.cyberciti.biz/tips/linux-iptables-how-to-flush-all-rules.html

## Results 
<img width="1118" height="832" alt="Screenshot 2026-07-19 at 3 20 16 PM" src="https://github.com/user-attachments/assets/14168d0d-c7c3-4c5c-904c-51634f678a2a" />
