**Description**

AppArmor is a Linux security module that enforces fine-grained access control policies to restrict the actions and resources that specific applications and processes can access. Adversaries may disable AppArmor to bypass these access restrictions, allowing their malicious tools to perform otherwise prohibited operations. Additionally, disabling AppArmor prevents the generation of policy violation logs, which could otherwise be used to detect suspicious activity.

Disabling AppArmor is a significant security alert, typically indicating that the system may be under targeted attack, requiring immediate response and investigation.

**Challenge Objective:** 
Attempt to write detection rules that identify behaviors in the system that disable or attempt to shut down the AppArmor security module.

Data Sample
"Name": "ParentUser",
"Guid": "{ff032593-a8d3-4f13-b0d6-01fc615a0f97}",
"EventID": "1",
"Version": "5",
"Level": "4",
"Task": "1",
"Opcode": "0",
  "Keywords": "0x8000000000000000",
  "SystemTime": "2025-03-21T06:19:31.078170000Z",
  "EventRecordID": "105383",
  "ProcessID": "45011",
  "ThreadID": "45011",
  "Channel": "Linux-Sysmon/Operational",
  "Computer": "ubuntu-soclabs",
  "UserId": "0",
  "RuleName": "-",
  "UtcTime": "2025-03-21 06:19:31.081",
  "ProcessGuid": "{09a89e73-04f3-67dd-7d97-d307075f0000}",
  "ProcessId": "48832",
  "Image": "/usr/bin/systemctl",
  "FileVersion": "-",
  "Description": "-",
  "Product": "-",
  "Company": "-",
  "OriginalFileName": "-",
  "CommandLine": "systemctl disable apparmor",
  "CurrentDirectory": "/home",
  "User": "root",
  "LogonGuid": "{09a89e73-e005-67dc-0000-000002000000}",
  "LogonId": "0",
  "TerminalSessionId": "1210",
  "IntegrityLevel": "no level",
  "Hashes": "SHA256=8872043fc990d387b8d7f39caa52359e5446f47d04b76008107bf2f7c2eaa232",
  "ParentProcessGuid": "{09a89e73-e005-67dc-2d93-2253f0580000}",
  "ParentProcessId": "48293",
  "ParentImage": "/usr/bin/bash",
  "ParentCommandLine": "-bash",
  "ParentUser": "root",
  "timestamp": "2025-03-21T06:54:46.339673"
}

Reference: https://elastic.github.io/detection-rules-explorer/rules/fac52c69-2646-4e79-89c0-fd7653461010
