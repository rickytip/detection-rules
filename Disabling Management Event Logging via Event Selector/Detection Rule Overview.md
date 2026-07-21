## Description
AWS CloudTrail provides comprehensive operational visibility for cloud environments by logging both management and data events. By default, a trail records all management events, including permission changes, policy modifications, and critical resource operations. However, if the trail’s event selector is maliciously altered using the PutEventSelectors API to capture only data events and exclude management events, all subsequent management operations will go unrecorded. This evasion technique significantly weakens security auditing and threat detection—it’s a common tactic attackers use to bypass defenses after compromising an AWS environment. Promptly identifying such abnormal configuration changes is critical for maintaining cloud security and compliance.

## Challenge Objective
Write a detection rule to identify calls to the PutEventSelectors API.

## Data Sample
Data source: CloudTrail, data sample:
{
  "awsRegion": "ap-southeast-2",
  "eventCategory": "Management",
  "eventID": "122d5564-548a-4cc0-a597-1ac5263dcef8",
  "eventName": "PutEventSelectors",
  "eventSource": "cloudtrail.amazonaws.com",
  "eventTime": "2025-05-30T09:39:37Z",
  "eventType": "AwsApiCall",
  "eventVersion": "1.11",
  "managementEvent": true,
  "readOnly": false,
  "recipientAccountId": "438465128930",
  "requestID": "63f6e40c-f9d7-4253-abad-e0db6f9482b8",
  "requestParameters": {
    "eventSelectors": [
      {
        "dataResources": [
          {
            "type": "AWS::S3::Object",
            "values": []
          },
          {
            "type": "AWS::Lambda::Function",
            "values": []
          }
        ],
        "excludeManagementEventSources": [],
        "includeManagementEvents": false,
        "readWriteType": "ReadOnly"
      }
    ],
    "trailName": "stratus-red-team-ctes-trail-yuffsbtkgj"
  },
  "responseElements": {
    "eventSelectors": [
      {
        "dataResources": [
          {
            "type": "AWS::S3::Object",
            "values": []
          },
          {
            "type": "AWS::Lambda::Function",
            "values": []
          }
        ],
        "excludeManagementEventSources": [],
        "includeManagementEvents": false,
        "readWriteType": "ReadOnly"
      }
    ],
    "trailARN": "arn:aws:cloudtrail:ap-southeast-2:438465128930:trail/stratus-red-team-ctes-trail-yuffsbtkgj"
  },
  "sourceIPAddress": "43.249.50.236",
  "tlsDetails": {
    "cipherSuite": "TLS_AES_128_GCM_SHA256",
    "clientProvidedHostHeader": "cloudtrail.ap-southeast-2.amazonaws.com",
    "tlsVersion": "TLSv1.3"
  },
  "userAgent": "stratus-red-team_4c51dc9f-d719-4e13-b1cc-109d7bc7077d",
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
https://stratus-red-team.cloud/attack-techniques/AWS/aws.defense-evasion.cloudtrail-event-selectors/
https://github.com/RhinoSecurityLabs/Cloud-Security-Research/tree/master/AWS/cloudtrail_guardduty_bypass

## Results 
<img width="1110" height="827" alt="Screenshot 2026-07-20 at 4 59 55 PM" src="https://github.com/user-attachments/assets/060d5a0c-0cce-49ad-a941-3a4b0ed454a3" />
