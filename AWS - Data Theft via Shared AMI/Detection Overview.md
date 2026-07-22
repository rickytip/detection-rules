## Description
An Amazon Machine Image (AMI) is a template in AWS environments used for bulk deployment of instances, typically containing the operating system, applications, and environment configurations.

Attackers can modify the launch permissions of an AMI to share it with specific external AWS accounts, allowing those accounts to launch instances and directly access all contents within the AMI.

This process does not require downloading the image file, making it stealthy and often used to bypass traditional perimeter defenses for unauthorized data access.

## Challenge Objective
Write detection rules to identify behaviors where AMIs are shared with other accounts.

## Data Sample
Data source: CloudTrail. Sample data:
{
  "awsRegion": "ap-southeast-2",
  "eventCategory": "Management",
  "eventID": "1d52e5c9-9c38-4888-a654-d08b5d3aae77",
  "eventName": "ModifyImageAttribute",
  "eventSource": "ec2.amazonaws.com",
  "eventTime": "2025-06-11T09:14:18Z",
  "eventType": "AwsApiCall",
  "eventVersion": "1.10",
  "managementEvent": true,
  "readOnly": false,
  "recipientAccountId": "438465128930",
  "requestID": "d8f7f205-d93a-4bee-8f0e-6ba3dd524502",
  "requestParameters": {
    "attributeType": "launchPermission",
    "imageId": "ami-011213ff2fc95b6f6",
    "launchPermission": {
      "add": {
        "items": [
          {
            "userId": "012345678901"
          }
        ]
      }
    }
  },
  "responseElements": {
    "_return": true,
    "requestId": "d8f7f205-d93a-4bee-8f0e-6ba3dd524502"
  },
  "sourceIPAddress": "103.40.79.131",
  "timestamp": "2025-06-11T09:33:21.144594",
  "tlsDetails": {
    "cipherSuite": "TLS_AES_128_GCM_SHA256",
    "clientProvidedHostHeader": "ec2.ap-southeast-2.amazonaws.com",
    "tlsVersion": "TLSv1.3"
  },
  "userAgent": "stratus-red-team_9bccf2c3-1156-4233-b4a9-4a5651db8387",
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
https://stratus-red-team.cloud/attack-techniques/AWS/aws.exfiltration.ec2-share-ami/

## Results
<img width="1121" height="775" alt="Screenshot 2026-07-22 at 11 34 48 AM" src="https://github.com/user-attachments/assets/c32635b6-2c88-4742-8432-2c93b2da3108" />
