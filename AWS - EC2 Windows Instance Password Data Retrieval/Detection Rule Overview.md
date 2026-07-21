## Description
In the AWS cloud environment, the EC2 service allows users to obtain the administrator password for Windows instances through a specific API. By calling the ec2:GetPasswordData interface, users can retrieve the encrypted RDP login credentials. Because this operation is usually performed only during instance initialization or when a password is lost, abnormal or frequent password data retrievals may indicate unauthorized access to sensitive credentials. Promptly identifying such activity is critical to securing cloud accounts and preventing potential data breaches.

## Challenge Objective
Write detection rules to identify password data retrieval activities targeting Windows EC2 instances in an AWS environment, with a focus on ec2:GetPasswordData API call events.

## Data Sample
Data source: CloudTrail. Data sample:
{
	"eventVersion": "1.10",
	"userIdentity": {
		"type": "AssumedRole",
		"principalId": "AROAWMFUO5HRBIZZWIQFB:aws-go-sdk-1747987156903996000",
		"arn": "arn:aws:sts::438465128930:assumed-role/stratus-red-team-ec2-get-password-data-role/aws-go-sdk-1747987156903996000",
		"accountId": "438465128930",
		"accessKeyId": "ASIAWMFUO5HRDXEZX5B3",
		"sessionContext": {
			"sessionIssuer": {
				"type": "Role",
				"principalId": "AROAWMFUO5HRBIZZWIQFB",
				"arn": "arn:aws:iam::438465128930:role/stratus-red-team-ec2-get-password-data-role",
				"accountId": "438465128930",
				"userName": "stratus-red-team-ec2-get-password-data-role"
			},
			"attributes": {
				"creationDate": "2025-05-23T07:59:18Z",
				"mfaAuthenticated": "false"
			}
		}
	},
	"eventTime": "2025-05-23T07:59:19Z",
	"eventSource": "ec2.amazonaws.com",
	"eventName": "GetPasswordData",
	"awsRegion": "ap-southeast-2",
	"sourceIPAddress": "160.30.128.229",
	"userAgent": "stratus-red-team_527a0ec4-4ea6-42df-b410-e840b8dbb6c9",
	"errorCode": "Client.UnauthorizedOperation",
	"errorMessage": "You are not authorized to perform this operation. User: arn:aws:sts::438465128930:assumed-role/stratus-red-team-ec2-get-password-data-role/aws-go-sdk-1747987156903996000 is not authorized to perform: ec2:GetPasswordData on resource: arn:aws:ec2:ap-southeast-2:438465128930:instance/* because no identity-based policy allows the ec2:GetPasswordData action. Encoded authorization failure message: ijFt0D2xT___D5vQp5BGY4x2xdSt3r4Ax9EvTiY2zHwvUZaW3XnZ3BEYN3bdATaD_jIOGlMkKOOWCkUrNMu61dwIOoYgoKvO9abJBToAzeG1nUHcsWDjBRYCj83RLpSiRpd8FhUfUUnnaNqeVAdr4vNdSU2kIc2ifE70j-eKD_MnueNz_Di3KNYbRHur6U9L9Y5Mw6whKjrSFN_7JILCcP1-rGuIl6zo23vgbInTGECIhr9AU2bQB1pm28MoW85xeaeHHdYXz5J_wnGkklDaG4aok7fFhs4WJXYR_6OzAYeasKEOxT81AswkrS6Kt81gOc8ChQwDogZz6E2d0TcQnnHKKIQnPlXv8qftwMxvasvNImo5MbJOu3ahSJ-eCEGtGx3hWEMJiUUw6vGWKqiGpmjOknrmmxA6sFdrmx9AUqZabdiYRe0hmkChEKK3UFZ6-5XG7oSHRjnRiwQ-VX5ohWNYTOetfgMtcYkCL-3yTgVdhzILIoY6MVLznNX80E56xqSocDOLoj_Ur525X7ZrMuxg0t2Qb8hQJk4cN_Mc_DGr_mh3bMuXolTtzvER89CQ5qXHpAFiqsoTWYI",
	"requestParameters": {
		"instanceId": "i-hproo47ezlhz8pxv"
	},
	"responseElements": null,
	"requestID": "7c8c42fa-8982-4078-9c8b-2d960bee7963",
	"eventID": "ddc3c0f4-cc94-457f-acac-0e690cd538a5",
	"readOnly": true,
	"eventType": "AwsApiCall",
	"managementEvent": true,
	"recipientAccountId": "438465128930",
	"eventCategory": "Management",
	"tlsDetails": {
		"tlsVersion": "TLSv1.3",
		"cipherSuite": "TLS_AES_128_GCM_SHA256",
		"clientProvidedHostHeader": "ec2.ap-southeast-2.amazonaws.com"
	}
}

## References
https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_GetPasswordData.html

## Results
<img width="1078" height="781" alt="Screenshot 2026-07-19 at 10 56 52 PM" src="https://github.com/user-attachments/assets/985a6e74-9f15-40f1-b7df-dbc154d98d08" />
