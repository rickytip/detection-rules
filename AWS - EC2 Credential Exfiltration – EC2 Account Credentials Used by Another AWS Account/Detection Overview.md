## Description
In AWS environments, EC2 instances are automatically assigned temporary IAM credentials to securely access cloud services.

If an attacker exfiltrates temporary credentials from an EC2 instance in one AWS account, they may use these credentials on an EC2 instance in an AWS account they control. This enables unauthorized access to the original account’s cloud resources from an external environment. Such credential exfiltration allows attackers to remotely abuse the original account’s permissions, leading to serious security risks such as data breaches and unauthorized resource manipulation.

Therefore, promptly detecting abnormal use of EC2 credentials in external AWS accounts is critical to ensuring the security of your cloud environment.

## Challenge Objective
Identify all API operations initiated with EC2 instance credentials where the credential’s originating account does not match the account where the API call occurs.

When writing detection queries, please ensure that the eventID field is included in the output results to facilitate subsequent validation.

Data Sample
{
  "id": 1,
  "awsRegion": "ap-southeast-2",
  "eventCategory": "Management",
  "eventID": "d588ddca-7441-4866-9197-3c25a05c4b5d",
  "eventName": "DescribeInstances",
  "eventSource": "ec2.amazonaws.com",
  "eventTime": "2025-05-23T09:01:24Z",
  "eventType": "AwsApiCall",
  "eventVersion": "1.10",
  "identityAccountId": "103164125733",
  "issuerAccountId": "438465128930",
  "managementEvent": true,
  "readOnly": true,
  "recipientAccountId": "438465128930",
  "requestID": "5902cc55-9e7f-4373-bed9-069305dcbf54",
  "requestParameters": {
    "filterSet": {},
    "instancesSet": {}
  },
  "responseElements": null,
  "sourceIPAddress": "101.44.82.95",
  "tlsDetails": {
    "cipherSuite": "TLS_AES_128_GCM_SHA256",
    "clientProvidedHostHeader": "ec2.ap-southeast-2.amazonaws.com",
    "tlsVersion": "TLSv1.3"
  },
  "userAgent": "stratus-red-team_7092f0da-0a76-4b8e-b136-eb5ea1d7d5ec",
  "userIdentity": {
    "accessKeyId": "ASIAWMFUO5HRNCJ7VF5V",
    "accountId": "103164125733",
    "arn": "arn:aws:sts::103164125733:assumed-role/stratus-red-team-ec2-steal-credentials-role/i-02299a25947b0226d",
    "principalId": "AROAWMFUO5HRMMR7MYWAN:i-02299a25947b0226d",
    "sessionContext": {
      "attributes": {
        "creationDate": "2025-05-23T08:59:50Z",
        "mfaAuthenticated": "false"
      },
      "ec2RoleDelivery": "1.0",
      "sessionIssuer": {
        "accountId": "438465128930",
        "arn": "arn:aws:iam::438465128930:role/stratus-red-team-ec2-steal-credentials-role",
        "principalId": "AROAWMFUO5HRMMR7MYWAN",
        "type": "Role",
        "userName": "stratus-red-team-ec2-steal-credentials-role"
      }
    },
    "type": "AssumedRole"
  },
  "userIdentity.type": "AssumedRole"
}
## References
https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_finding-types-iam.html#unauthorizedaccess-iam-instancecredentialexfiltrationinsideaws
https://github.com/sbasu7241/AWS-Threat-Simulation-and-Detection/blob/main/aws.credential-access.ec2-steal-instance-credentials.md

## Results 
