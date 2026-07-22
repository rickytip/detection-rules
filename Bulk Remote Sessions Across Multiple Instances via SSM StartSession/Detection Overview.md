## Description
AWS Systems Manager (SSM) Session Manager enables remote access to EC2 instances through the StartSession feature, significantly improving operational efficiency.

However, in day-to-day production environments, initiating StartSession operations on multiple instances within a short period is unusual. This pattern is often associated with privilege abuse, automation script errors, or potential lateral movement.

Promptly identifying such bulk remote sessions helps mitigate risks associated with sensitive operations in cloud environments.

## Challenge Objective
Write a detection rule to identify bulk SSM StartSession requests targeting multiple EC2 instances within a short timeframe.
## Data Sample
Data Source: CloudTrail,Sample Data:
{
  "awsRegion": "ap-southeast-2",
  "eventCategory": "Management",
  "eventID": "4c7f3fc2-246a-4031-a52c-7f5bd5598152",
  "eventName": "StartSession",
  "eventSource": "ssm.amazonaws.com",
  "eventTime": "2025-06-11T07:56:17Z",
  "eventType": "AwsApiCall",
  "eventVersion": "1.11",
  "managementEvent": true,
  "readOnly": false,
  "recipientAccountId": "438465128930",
  "requestID": "9755b84d-cd48-4f5b-b0b2-2f74913e75fd",
  "requestParameters": {
    "target": "i-04d7335c90a5d6d90"
  },
  "responseElements": {
    "sessionId": "soclabs-test-t59j8gpq2ta8hniozstbnphqs8",
    "streamUrl": "wss://ssmmessages.ap-southeast-2.amazonaws.com/v1/data-channel/soclabs-test-t59j8gpq2ta8hniozstbnphqs8?role=publish_subscribe&cell-number=AAEAAalu7PsrZyX5JWeaX5JmQAE5lZ2o6duIyGUcmGnOADBdAAAAAGhJNqE6pXgftpeIKBZ2IhYhQfv6ftq5WyoJGma4NmkZP9tmCeIPV1Ap",
    "tokenValue": "HIDDEN_DUE_TO_SECURITY_REASONS"
  },
  "sourceIPAddress": "154.84.135.88",
  "tlsDetails": {
    "cipherSuite": "ECDHE-RSA-AES128-GCM-SHA256",
    "clientProvidedHostHeader": "ssm.ap-southeast-2.amazonaws.com",
    "tlsVersion": "TLSv1.2"
  },
  "userAgent": "stratus-red-team_2922d9ca-30f3-47ee-8f7d-52e14ac84d7e",
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
https://stratus-red-team.cloud/attack-techniques/AWS/aws.execution.ssm-start-session/

## Results 
<img width="1106" height="819" alt="Screenshot 2026-07-22 at 12 19 39 AM" src="https://github.com/user-attachments/assets/313a1876-df54-4da0-9069-65f2391cd0a7" />
