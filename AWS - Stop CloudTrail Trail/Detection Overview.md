## Description
In cloud environments, CloudTrail is a critical log auditing service provided by AWS that records API calls and related activities within an account. By continuously writing logs, CloudTrail supplies essential data for security monitoring and forensic analysis. However, threat actors in the cloud may attempt to stop CloudTrail logging to disrupt monitoring of their actions, thereby evading audits and threat detection. Promptly identifying such activities is vital for maintaining cloud security and compliance.

## Challenge Objective
Detect events where CloudTrail logging has been stopped.

## Data Sample
Data source: CloudTrail, sample data:

{
  "awsRegion": "ap-southeast-2",
  "eventCategory": "Management",
  "eventID": "1dd62ee5-b6fd-471b-85cb-fa3f7e43fb19",
  "eventName": "StopLogging",
  "eventSource": "cloudtrail.amazonaws.com",
  "eventTime": "2025-06-03T07:42:08Z",
  "eventType": "AwsApiCall",
  "eventVersion": "1.11",
  "managementEvent": true,
  "readOnly": false,
  "recipientAccountId": "438465128930",
  "requestID": "b5a52d9b-a4c6-4f3a-9bb4-1b4df9a111e0",
  "requestParameters": {
    "name": "stratus-red-team-ct-stop-trail-sxtxvrkmru"
  },
  "responseElements": null,
  "sourceIPAddress": "43.249.50.235",
  "tlsDetails": {
    "cipherSuite": "TLS_AES_128_GCM_SHA256",
    "clientProvidedHostHeader": "cloudtrail.ap-southeast-2.amazonaws.com",
    "tlsVersion": "TLSv1.3"
  },
  "userAgent": "stratus-red-team_42b2aa2a-ccef-46ae-99a0-ac98addbcb4e",
  "userIdentity": {
    "accessKeyId": "AKIAWMFUO5HRKBD6JQ6D",
    "accountId": "438465128930",
    "arn": "arn:aws:iam::438465128930:user/soclabs-test",
    "principalId": "AIDAWMFUO5HRCBESZ467O",
    "type": "IAMUser",
    "userName": "soclabs-test"
  }
}
## References
https://stratus-red-team.cloud/attack-techniques/AWS/aws.defense-evasion.cloudtrail-stop/

## Results 
<img width="1108" height="776" alt="Screenshot 2026-07-20 at 11 06 41 PM" src="https://github.com/user-attachments/assets/aee10127-93eb-48b4-911f-b9e199da680a" />
