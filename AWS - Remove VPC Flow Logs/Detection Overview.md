## Description
VPC Flow Logs are a critical AWS feature used to capture IP traffic information for network interfaces within a VPC.

By sending this log data to CloudWatch Logs or S3, security teams can analyze network traffic, detect threats, and perform compliance audits. Flow logs are essential for identifying abnormal communications, investigating security incidents, and meeting regulatory requirements.

If VPC Flow Logs are deleted, network traffic will no longer be continuously recorded. Attackers may exploit this to evade monitoring, conceal malicious activities within the cloud environment, and reduce the traceability of security incidents.

## Challenge Objective
Detect API calls that delete VPC Flow Log configurations and identify key operational events that may disrupt network traffic monitoring.

## Data Sample
Data source: CloudTrail. Data example:

{
  "awsRegion": "ap-southeast-2",
  "eventCategory": "Management",
  "eventID": "4f7fcc9c-b68f-4238-800f-0216a167e5e7",
  "eventName": "DeleteFlowLogs",
  "eventSource": "ec2.amazonaws.com",
  "eventTime": "2025-06-03T09:31:05Z",
  "eventType": "AwsApiCall",
  "eventVersion": "1.10",
  "managementEvent": true,
  "readOnly": false,
  "recipientAccountId": "438465128930",
  "requestID": "9dae3e11-addb-45c7-b564-66f4ceedf949",
  "requestParameters": {
    "DeleteFlowLogsRequest": {
      "FlowLogId": {
        "content": "fl-0b99f482856f6f98b",
        "tag": 1
      }
    }
  },
  "responseElements": {
    "DeleteFlowLogsResponse": {
      "requestId": "9dae3e11-addb-45c7-b564-66f4ceedf949",
      "unsuccessful": "",
      "xmlns": "http://ec2.amazonaws.com/doc/2016-11-15/"
    }
  },
  "sourceIPAddress": "103.40.79.165",
  "tlsDetails": {
    "cipherSuite": "TLS_AES_128_GCM_SHA256",
    "clientProvidedHostHeader": "ec2.ap-southeast-2.amazonaws.com",
    "tlsVersion": "TLSv1.3"
  },
  "userAgent": "stratus-red-team_66ba5136-69f9-47b6-8401-bf7bf446bab4",
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
https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DeleteFlowLogs.html
https://stratus-red-team.cloud/attack-techniques/AWS/aws.defense-evasion.vpc-remove-flow-logs/

## Results 
<img width="1109" height="770" alt="Screenshot 2026-07-20 at 11 33 48 PM" src="https://github.com/user-attachments/assets/05a304fc-5d6b-44e4-91b2-2b9d617f31f4" />
