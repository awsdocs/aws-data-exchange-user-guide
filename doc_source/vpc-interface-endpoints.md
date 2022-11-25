# AWS Data Exchange and interface VPC endpoints \(AWS PrivateLink\)<a name="vpc-interface-endpoints"></a>

You can establish a private connection between your virtual private cloud \(VPC\) and AWS Data Exchange by creating an *interface VPC endpoint*\. Interface endpoints are powered by [AWS PrivateLink](http://aws.amazon.com/privatelink), a technology that enables you to privately access AWS Data Exchange API operations without an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection\. Instances in your VPC don't need public IP addresses to communicate with AWS Data Exchange API operations\. Traffic between your VPC and AWS Data Exchange does not leave the Amazon network\. 

Each interface endpoint is represented by one or more [Elastic Network Interfaces](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-eni.html) in your subnets\. 

**Note**  
Every AWS Data Exchange action, except for `SendAPIAsset`, is supported for VPC\. 

For more information, see [Interface VPC endpoints \(AWS PrivateLink\)](https://docs.aws.amazon.com/vpc/latest/userguide/vpce-interface.html) in the *Amazon VPC User Guide*\. 

## Considerations for AWS Data Exchange VPC endpoints<a name="vpc-endpoint-considerations"></a>

Before you set up an interface VPC endpoint for AWS Data Exchange, ensure that you review [Interface endpoint properties and limitations](https://docs.aws.amazon.com/vpc/latest/userguide/vpce-interface.html#vpce-interface-limitations) in the *Amazon VPC User Guide*\. 

AWS Data Exchange supports making calls to all of its API operations from your VPC, with the exception of `SendAPIAsset` as noted above\. 

By default, full access to AWS Data Exchange is allowed through the endpoint\. You can restrict what access is allowed by using VPC endpoint policies.  For more information, see the [VPC endpoint policy section](#creating-a-vpc-endpoint-policy-for-aws-data-exchangea-namevpc-endpoint-policy) lower down the document, and [Controlling access to services with VPC endpoints](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-endpoints-access.html) in the *Amazon VPC User Guide*\.

## Creating an interface VPC endpoint for AWS Data Exchange<a name="vpc-endpoint-create"></a>

You can create a VPC endpoint for the AWS Data Exchange service using either the Amazon VPC console or the AWS Command Line Interface \(AWS CLI\)\. For more information, see [Creating an interface endpoint](https://docs.aws.amazon.com/vpc/latest/userguide/vpce-interface.html#create-interface-endpoint) in the *Amazon VPC User Guide*\.

Create a VPC endpoint for AWS Data Exchange using the following service name: 
+ com\.amazonaws\.*region*\.dataexchange

If you enable private DNS for the endpoint, you can make API requests to AWS Data Exchange using its default DNS name for the AWS Region, for example, `com.amazonaws.us-east-1.dataexchange`\.

For more information, see [Accessing a service through an interface endpoint](https://docs.aws.amazon.com/vpc/latest/userguide/vpce-interface.html#access-service-though-endpoint) in the *Amazon VPC User Guide*\.

## Creating a VPC endpoint policy for AWS Data Exchange<a name="vpc-endpoint-policy"></a>

You can attach an endpoint policy to your VPC endpoint that controls access to AWS Data Exchange\. The policy specifies the following information:
+ The principal that can perform actions
+ The actions that can be performed
+ The resources on which actions can be performed

For more information, see [Controlling access to services with VPC endpoints](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-endpoints-access.html) in the *Amazon VPC User Guide*\. 

**Example: VPC endpoint policy for AWS Data Exchange actions**  
The following is an example of an endpoint policy for AWS Data Exchange\. When attached to an endpoint, this policy grants access to the listed AWS Data Exchange actions for all principals on all resources\.

This example VPC endpoint policy allows full access only to the AWS Identity and Access Management \(IAM\) user `bts` in AWS account `123456789012` from `vpc-12345678`\. The IAM user `readUser` is allowed to read the resources, but all other IAM principals are denied access to the endpoint\.

```
{ 
    "Id": "example-policy",
    "Version": "2012-10-17",
    "Statement": [ 
        {
            "Sid": "Allow administrative actions from vpc-12345678",
            "Effect": "Allow", 
            "Principal": {
                "AWS": [
                    "arn:aws:iam::123456789012:user/bts"
                ]
            }, 
            "Action": "*", 
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "aws:sourceVpc": "vpc-12345678"
                }
            }
        },
        {
            "Sid": "Allow ReadOnly actions",
            "Effect": "Allow", 
            "Principal": {
                "AWS": [
                    "arn:aws:iam::123456789012:user/readUser"
                ]
            }, 
            "Action": [
                "dataexchange:list*",
                "dataexchange:get*"
            ], 
            "Resource": "*",
        }
    ]
}
```