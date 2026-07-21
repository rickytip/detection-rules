## Description
In an AWS environment, CloudTrail logs record all critical operations and serve as essential data for security compliance and incident investigation. These CloudTrail logs are typically stored in designated S3 buckets. If the S3 lifecycle rule is configured to retain logs for only one day, the log files will be automatically deleted after a very short retention period, which severely undermines security forensics and auditing capabilities. Threat actors may use API calls to reduce the retention period of S3 lifecycle policies for CloudTrail log buckets to one day, aiming to evade monitoring and destroy crucial evidence.

## Challenge Objective
Write a rule to identify log entries where the S3 bucket lifecycle policy is set to 1 day.

## Data Sample
Data source: CloudTrail, sample data:

{
  "id": 0,
  "additionalEventData": {
    "AuthenticationMethod": "AuthHeader",
    "CipherSuite": "TLS_AES_128_GCM_SHA256",
    "SignatureVersion": "SigV4",
    "bytesTransferredIn": 249,
    "bytesTransferredOut": 0,
    "x-amz-id-2": "xh5MEcTuKcnZOhkUkaUntraTnNm+cqypRhBsAFUecNNm7ZiDPGfxYV2AfQVATfi6OaWQBJ5zrP4="
  },
  "awsRegion": "ap-southeast-2",
  "days": "1",
  "eventCategory": "Management",
  "eventID": "063e61b6-1e6e-4979-98e6-e8ba0cecdba7",
  "eventName": "PutBucketLifecycle",
  "eventSource": "s3.amazonaws.com",
  "eventTime": "2025-06-03T06:29:33Z",
  "eventType": "AwsApiCall",
  "eventVersion": "1.11",
  "managementEvent": true,
  "readOnly": false,
  "recipientAccountId": "438465128930",
  "requestID": "NK72Q1STK5P9MAP3",
  "requestParameters": {
    "Host": "stratus-red-team-ctlr-bucket-dbrzcxpjvn.s3.ap-southeast-2.amazonaws.com",
    "LifecycleConfiguration": {
      "Rule": {
        "Expiration": {
          "Days": 1
        },
        "Filter": {
          "Prefix": "*"
        },
        "ID": "nuke-cloudtrail-logs-after-1-day",
        "Status": "Enabled"
      },
      "xmlns": "http://s3.amazonaws.com/doc/2006-03-01/"
    },
    "bucketName": "stratus-red-team-ctlr-bucket-dbrzcxpjvn",
    "lifecycle": ""
  },
  "resources": [
    {
      "ARN": "arn:aws:s3:::stratus-red-team-ctlr-bucket-dbrzcxpjvn",
      "accountId": "438465128930",
      "type": "AWS::S3::Bucket"
    }
  ],
  "responseElements": null,
  "sourceIPAddress": "43.252.208.19",
  "tlsDetails": {
    "cipherSuite": "TLS_AES_128_GCM_SHA256",
    "clientProvidedHostHeader": "stratus-red-team-ctlr-bucket-dbrzcxpjvn.s3.ap-southeast-2.amazonaws.com",
    "tlsVersion": "TLSv1.3"
  },
  "userAgent": "[stratus-red-team_c4daf3d6-a06f-48c0-9bec-46e00868de7b]",
  "userIdentity": {
    "accessKeyId": "AKIAWMFUO5HRKBD6JQ6D",
    "accountId": "438465128930",
    "arn": "arn:aws:iam::438465128930:user/soclabs-test",
    "principalId": "AIDAWMFUO5HRCBESZ467O",
    "type": "IAMUser",
    "userName": "soclabs-test"
  },
  "_X_ROW_KEY": "row_17"
}
## References
https://stratus-red-team.cloud/attack-techniques/AWS/aws.defense-evasion.cloudtrail-lifecycle-rule/
https://github.com/sbasu7241/AWS-Threat-Simulation-and-Detection/blob/main/aws.defense-evasion.cloudtrail-lifecycle-rule.md

## Results 
<img width="1116" height="773" alt="Screenshot 2026-07-20 at 10 32 39 PM" src="https://github.com/user-attachments/assets/1c048dfa-052a-4499-9422-dced2957922a" />
