## Description
Multi-factor authentication (MFA) is a critical security control and an AWS best practice. It requires users to provide an additional authentication factor beyond just a username and password. When an IAM user successfully signs in to the AWS Management Console without MFA enabled or bypasses MFA, it indicates a significant authentication security gap.

This issue may result from administrators failing to enforce MFA policies or from malicious actors exploiting configuration weaknesses to circumvent MFA controls. Console access without MFA greatly increases the risk of account compromise, sensitive data exposure, privilege abuse, or lateral movement attacks. Timely detection of such unauthorized login activity is essential for maintaining cloud environment security.

## Challenge Objective
Write a detection rule to identify IAM user login events to the AWS Console that occurred without MFA.

## Data Sample
Data source: CloudTrail,sample data:

{
  "additionalEventData": {
    "LoginTo": "https://console.aws.amazon.com/console/home",
    "MFAUsed": "No",
    "MobileVersion": "No"
  },
  "awsRegion": "us-east-1",
  "eventCategory": "Management",
  "eventID": "e1bf1000-86a4-4a78-81d7-3e1cb123",
  "eventName": "ConsoleLogin",
  "eventSource": "signin.amazonaws.com",
  "eventTime": "2025-06-13T08:18:57Z",
  "eventType": "AwsConsoleSignIn",
  "eventVersion": "1.09",
  "managementEvent": true,
  "readOnly": false,
  "recipientAccountId": "438465128930",
  "requestParameters": null,
  "responseElements": {
    "ConsoleLogin": "Success"
  },
  "sourceIPAddress": "154.84.135.87",
  "tlsDetails": {
    "cipherSuite": "TLS_AES_128_GCM_SHA256",
    "clientProvidedHostHeader": "signin.aws.amazon.com",
    "tlsVersion": "TLSv1.3"
  },
  "userAgent": "stratus-red-team_8cb1ee36-86c3-4241-a32c-163c78cde7b6",
  "userIdentity": {
    "accountId": "438465128930",
    "arn": "arn:aws:iam::438465128930:user/stratus-red-team-nmfalu-sdycehnppn",
    "principalId": "AIDAWMFUO5HRALIVU6YBZ",
    "type": "IAMUser",
    "userName": "stratus-red-team-nmfalu-sdycehnppn"
  }
}
## References
https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-event-reference-aws-console-sign-in-events.html
https://stratus-red-team.cloud/attack-techniques/AWS/aws.initial-access.console-login-without-mfa/

## Results
<img width="1108" height="829" alt="Screenshot 2026-07-22 at 10 08 28 PM" src="https://github.com/user-attachments/assets/751aa005-2f2a-44b0-ab7e-1ff05fe0c60d" />
