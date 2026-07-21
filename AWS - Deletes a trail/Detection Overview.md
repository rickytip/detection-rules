## Description
In cloud environments, AWS CloudTrail is a critical auditing service that records various operations and changes within an account. By calling the DeleteTrail API, you can remove a specified CloudTrail tracking configuration. Once deleted, the Trail configuration will no longer collect or record new logs, making it impossible to continuously audit subsequent operations. Attackers may leverage this operation to bypass security monitoring and traceability, enabling further unauthorized activities. Therefore, identifying DeleteTrail operations is essential for maintaining cloud platform security.

## Challenge Objective
Write detection rules based on logs to identify API calls that delete a Trail.

## Data Sample
Data source: CloudTrail, data sample:

{
  "awsRegion": "ap-southeast-2",
  "eventCategory": "Management",
  "eventID": "4616cc30-d42f-4894-9f05-dd563cb6ab69",
  "eventName": "DeleteTrail",
  "eventSource": "cloudtrail.amazonaws.com",
  "eventTime": "2025-05-30T08:32:04Z",
  "eventType": "AwsApiCall",
  "eventVersion": "1.11",
  "managementEvent": true,
  "readOnly": false,
  "recipientAccountId": "438465128930",
  "requestID": "72bde529-8e2a-491a-9bd0-ec718634457c",
  "requestParameters": {
    "name": "stratus-red-team-cloudtraild-trail-noupmcidtl"
  },
  "responseElements": null,
  "sourceIPAddress": "43.249.50.235",
  "tlsDetails": {
    "cipherSuite": "TLS_AES_128_GCM_SHA256",
    "clientProvidedHostHeader": "cloudtrail.ap-southeast-2.amazonaws.com",
    "tlsVersion": "TLSv1.3"
  },
  "userAgent": "stratus-red-team_1a878966-1c80-406d-ab5a-e6c2e92dfa50",
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
https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_DeleteTrail.html
https://stratus-red-team.cloud/attack-techniques/AWS/aws.defense-evasion.cloudtrail-delete/
