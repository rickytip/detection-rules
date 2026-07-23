## Description
In AWS cloud environments, S3 buckets are often used to store and share sensitive data. Misconfigured or maliciously altered bucket policies can lead to sensitive data leaks.

Attackers may add policy statements to the bucket policy document that grant access to external or fictitious AWS accounts, bypassing existing permission controls and enabling long-term unauthorized access.

These types of backdoors are often difficult to detect in a timely manner, posing risks to data security and compliance. Therefore, it is crucial to quickly identify and mitigate such policy risks.

## Challenge Objective
Write detection rules to identify suspicious authorization actions targeting S3 bucket policies.

## Data Sample
Data source: CloudTrail, Example data:

{
  "additionalEventData": {
    "AuthenticationMethod": "AuthHeader",
    "CipherSuite": "TLS_AES_128_GCM_SHA256",
    "SignatureVersion": "SigV4",
    "bytesTransferredIn": 416,
    "bytesTransferredOut": 0,
    "x-amz-id-2": "ZDchP4lVDO5wDm0M+J6kUQZ2gbLMjJc9cmWq2GwX77G/S4qAO1jVY7y/zN92qA6CMy8LhjHKX7Q="
  },
  "awsRegion": "ap-southeast-2",
  "eventCategory": "Management",
  "eventID": "85da6631-a4b5-47dc-b296-95574e53b41a",
  "eventName": "PutBucketPolicy",
  "eventSource": "s3.amazonaws.com",
  "eventTime": "2025-06-13T07:42:48Z",
  "eventType": "AwsApiCall",
  "eventVersion": "1.11",
  "managementEvent": true,
  "readOnly": false,
  "recipientAccountId": "438465128930",
  "requestID": "PR6ZGT0VKVR5TKCJ",
  "requestParameters": {
    "Host": "stratus-red-team-bdbp-ypyjcgrxup.s3.ap-southeast-2.amazonaws.com",
    "bucketName": "stratus-red-team-bdbp-ypyjcgrxup",
    "bucketPolicy": {
      "Statement": [
        {
          "Action": [
            "s3:GetObject",
            "s3:GetBucketLocation",
            "s3:ListBucket"
          ],
          "Effect": "Allow",
          "Principal": {
            "AWS": "arn:aws:iam::193672423079:root"
          },
          "Resource": [
            "arn:aws:s3:::stratus-red-team-bdbp-ypyjcgrxup/*",
            "arn:aws:s3:::stratus-red-team-bdbp-ypyjcgrxup"
          ]
        }
      ],
      "Version": "2012-10-17"
    },
    "policy": ""
  },
  "resources": [
    {
      "ARN": "arn:aws:s3:::stratus-red-team-bdbp-ypyjcgrxup",
      "accountId": "438465128930",
      "type": "AWS::S3::Bucket"
    }
  ],
  "responseElements": null,
  "sourceIPAddress": "154.84.135.91",
  "tlsDetails": {
    "cipherSuite": "TLS_AES_128_GCM_SHA256",
    "clientProvidedHostHeader": "stratus-red-team-bdbp-ypyjcgrxup.s3.ap-southeast-2.amazonaws.com",
    "tlsVersion": "TLSv1.3"
  },
  "userAgent": "[stratus-red-team_14d5debf-0347-40de-b838-7e3ad36da5bf]",
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
https://docs.aws.amazon.com/AmazonS3/latest/API/API_PutBucketPolicy.html
https://stratus-red-team.cloud/attack-techniques/AWS/aws.exfiltration.s3-backdoor-bucket-policy/

# Results 
<img width="833" height="779" alt="Screenshot 2026-07-22 at 9 52 39 PM" src="https://github.com/user-attachments/assets/bbaccfec-0648-40e2-b57c-0ba8bdf4f4e6" />
