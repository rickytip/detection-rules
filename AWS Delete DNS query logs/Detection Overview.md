## Description
AWS Route 53 is Amazon’s scalable Domain Name System (DNS) service whose query logging feature records all DNS resolution requests, which is critical for security analysis and incident response. Malicious actors frequently attempt to clear these logs to conceal their activity traces, particularly during lateral movement, C2 communications, or data exfiltration phases.

When AWS Route 53 DNS query logs are deleted, security teams lose the ability to track suspicious domain resolutions, resulting in potential malicious activities going undetected and uninvestigated. This defense evasion technique is typically part of a larger attack chain used to hide the attacker’s presence. Timely detection of DNS log clearing behavior is essential for identifying possible intrusions and maintaining a complete security posture in AWS environments.

## Challenge Objective
Detect the deletion of Route 53 DNS resolver query logs in AWS environments. The log data contains API calls recorded by AWS CloudTrail, and you need to focus on API calls related to Route 53 DNS log deletion operations.

## Data Sample
Data source: CloudTrail, data sample:
{
  "eventVersion": "1.08",
  "userIdentity": {
    "type": "IAMUser",
    "principalId": "AIDAWMFUO5HRCBESZ467O",
    "arn": "arn:aws:iam::438465128930:user/soclabs-test",
    "accountId": "438465128930",
    "accessKeyId": "AKIAWMFUO5HRKBD6JQ6D",
    "userName": "soclabs-test"
  },
  "eventTime": "2025-05-14T09:30:56Z",
  "eventSource": "route53resolver.amazonaws.com",
  "eventName": "DeleteResolverQueryLogConfig",
  "awsRegion": "ap-southeast-2",
  "sourceIPAddress": "43.249.50.237",
  "userAgent": "stratus-red-team_0f12f065-7e47-459b-93e7-9b0c69339f9f",
  "requestParameters": {
    "resolverQueryLogConfigId": "rqlc-ba781297ce9c4009",
    "originSequenceNumber": 0
  },
  "responseElements": {
    "resolverQueryLogConfig": {
      "id": "rqlc-ba781297ce9c4009",
      "ownerId": "438465128930",
      "status": "DELETING",
      "shareStatus": "NOT_SHARED",
      "associationCount": 0,
      "arn": "arn:aws:route53resolver:ap-southeast-2:438465128930:resolver-query-log-config/rqlc-ba781297ce9c4009",
      "name": "stratus-red-team-dns-delete-config-tegswbeaqu",
      "destinationArn": "arn:aws:s3:::stratus-red-team-dns-delete-bucket-tegswbeaqu",
      "creatorRequestId": "tf-r53-resolver-query-log-config-20250514093052358300000001",
      "creationTime": "2025-05-14T09:30:53.409548947Z"
    }
  },
  "requestID": "a3a61ac6-951d-49b7-b96b-4263a7a06520",
  "eventID": "34544f2d-96b4-4e12-aaee-10ea3bc4f940",
  "readOnly": false,
  "eventType": "AwsApiCall",
  "managementEvent": true,
  "recipientAccountId": "438465128930",
  "eventCategory": "Management",
  "tlsDetails": {
    "tlsVersion": "TLSv1.3",
    "cipherSuite": "TLS_AES_128_GCM_SHA256",
    "clientProvidedHostHeader": "route53resolver.ap-southeast-2.amazonaws.com"
  },
  "timestamp": "2025-05-16T03:10:03.175119"
}
## References
https://stratus-red-team.cloud/attack-techniques/AWS/aws.defense-evasion.dns-delete-logs/

## Results 
<img width="1069" height="774" alt="Screenshot 2026-07-19 at 10 14 55 PM" src="https://github.com/user-attachments/assets/2c8faec9-e283-49a6-a607-07959bca780a" />
