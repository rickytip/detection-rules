## Description
Amazon Simple Email Service (SES) is a widely used cloud-based email delivery service, commonly adopted for business notifications and communications.

If an AWS account’s access key is obtained by an unauthorized individual, that person may use a series of API calls to enumerate SES configuration details, verified identities, and quotas. This information can then be leveraged to prepare for large-scale spam or phishing campaigns.

If such reconnaissance activities are not detected and blocked in time, they can easily lead to the misuse of email services, resulting in business risks and sensitive data leaks.

## Challenge Objective
Develop detection rules to identify SES enumeration activities, with particular attention to scenarios where SES configuration queries（GetAccountSendingEnabled）, quota queries（GetSendQuota）, identity enumeration（ListIdentities）, and identity verification status checks（GetIdentityVerificationAttributes）occur simultaneously. Focus on identifying suspicious activity where the same user or access key triggers multiple related API calls within a short period.

## Data Sample
Data source: CloudTrail,Data sample:
{
  "additionalEventData": {
    "SignatureVersion": "4"
  },
  "awsRegion": "ap-southeast-2",
  "eventCategory": "Management",
  "eventID": "e52e7a78-438a-4851-b53f-6b77c566c293",
  "eventName": "ListIdentities",
  "eventSource": "ses.amazonaws.com",
  "eventTime": "2025-06-11T03:15:12Z",
  "eventType": "AwsApiCall",
  "eventVersion": "1.11",
  "managementEvent": true,
  "readOnly": true,
  "recipientAccountId": "438465128930",
  "requestID": "ee8376a6-8bab-4e97-adb6-fb2f83491db5",
  "requestParameters": null,
  "responseElements": null,
  "sourceIPAddress": "185.36.195.158",
  "tlsDetails": {
    "cipherSuite": "TLS_AES_128_GCM_SHA256",
    "clientProvidedHostHeader": "email.ap-southeast-2.amazonaws.com",
    "tlsVersion": "TLSv1.3"
  },
  "userAgent": "stratus-red-team_0e29771f-4865-4a38-9429-1b06c0b2978e",
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
https://aws.amazon.com/cn/ses/
https://stratus-red-team.cloud/attack-techniques/AWS/aws.discovery.ses-enumerate/

## Results 
<img width="1113" height="832" alt="Screenshot 2026-07-21 at 11 56 27 PM" src="https://github.com/user-attachments/assets/4ac34fcc-5ba2-491c-b530-c5eff5930e84" />
