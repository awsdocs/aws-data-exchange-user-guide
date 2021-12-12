# AWS managed policies for AWS Data Exchange<a name="security-iam-awsmanpol"></a>

To add permissions to users, groups, and roles, it is easier to use AWS managed policies than to write policies yourself\. It takes time and expertise to [create IAM customer managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html) that provide your team with only the permissions they need\. To get started quickly, you can use our AWS managed policies\. These policies cover common use cases and are available in your AWS account\. For more information about AWS managed policies, see [AWS managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) in the *IAM User Guide*\.

AWS services maintain and update AWS managed policies\. You can't change the permissions in AWS managed policies\. Services occasionally add additional permissions to an AWS managed policy to support new features\. This type of update affects all identities \(users, groups, and roles\) where the policy is attached\. Services are most likely to update an AWS managed policy when a new feature is launched or when new operations become available\. Services do not remove permissions from an AWS managed policy, so policy updates won't break your existing permissions\.

Additionally, AWS supports managed policies for job functions that span multiple services\. For example, the **ViewOnlyAccess** AWS managed policy provides read\-only access to many AWS services and resources\. When a service launches a new feature, AWS adds read\-only permissions for new operations and resources\. For a list and descriptions of job function policies, see [AWS managed policies for job functions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html) in the *IAM User Guide*\.



## AWS managed policy: `AWSDataExchangeFullAccess`<a name="security-iam-awsmanpol-awsdataexchangefullaccess"></a>


|  | 
| --- |
| The updated managed policy for the Amazon Redshift data product feature is in preview release for AWS Data Exchange and is subject to change\. | 

You can attach the `AWSDataExchangeFullAccess` policy to your IAM identities\.

This policy grants administrative permissions that allow full access to AWS Data Exchange and AWS Marketplace actions using the AWS Management Console and SDK\. It also provides select access to Amazon S3 and AWS Key Management Service as needed to take full advantage of AWS Data Exchange\.

**Permissions details**

This policy includes the following permissions:
+ `AWS Data Exchange` – Allows principals full access to AWS Data Exchange\. This includes both providing data products and subscribing to them\.
+ `AWS Marketplace` – Allows principals access to AWS Marketplace for providing products, subscribing to products, and managing product agreements\. This is required to provide or subscribe to data products\.
+ `Amazon S3` – Allows principals to get AWS Data Exchange related objects \(including data product files\) from Amazon Simple Storage Service, and to upload AWS Data Exchange related files to Amazon S3\. This is required for providing and subscribing to data products\.
+ `Amazon Redshift` – Allows principals to view AWS Data Exchange datashares for Amazon Redshift for import and to authorize them\. This is required for providing Amazon Redshift data products\.
+ `AWS KMS` – Allows access to AWS Key Management Service so that data can be encrypted and accessed using keys\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "dataexchange:*"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::*aws-data-exchange*",
            "Condition": {
                "ForAnyValue:StringEquals": {
                    "aws:CalledVia": [
                        "dataexchange.amazonaws.com"
                    ]
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": "s3:GetObject",
            "Resource": "*",
            "Condition": {
                "StringEqualsIgnoreCase": {
                    "s3:ExistingObjectTag/AWSDataExchange": "true"
                },
                "ForAnyValue:StringEquals": {
                    "aws:CalledVia": [
                        "dataexchange.amazonaws.com"
                    ]
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:PutObject",
                "s3:PutObjectAcl"
            ],
            "Resource": "arn:aws:s3:::*aws-data-exchange*",
            "Condition": {
                "ForAnyValue:StringEquals": {
                    "aws:CalledVia": [
                        "dataexchange.amazonaws.com"
                    ]
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetBucketLocation",
                "s3:ListBucket",
                "s3:ListAllMyBuckets"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "aws-marketplace:DescribeEntity",
                "aws-marketplace:ListEntities",
                "aws-marketplace:StartChangeSet",
                "aws-marketplace:ListChangeSets",
                "aws-marketplace:DescribeChangeSet",
                "aws-marketplace:CancelChangeSet",
                "aws-marketplace:GetAgreementApprovalRequest",
                "aws-marketplace:ListAgreementApprovalRequests",
                "aws-marketplace:AcceptAgreementApprovalRequest",
                "aws-marketplace:RejectAgreementApprovalRequest",
                "aws-marketplace:UpdateAgreementApprovalRequest",
                "aws-marketplace:SearchAgreements",
                "aws-marketpalce:GetAgreementTerms"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "aws-marketplace:Subscribe",
                "aws-marketplace:Unsubscribe",
                "aws-marketplace:ViewSubscriptions",
                "aws-marketplace:GetAgreementRequest",
                "aws-marketplace:ListAgreementRequests",
                "aws-marketplace:CancelAgreementRequest"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "kms:DescribeKey",
                "kms:ListAliases",
                "kms:ListKeys"
            ],
            "Resource": "*"
            },
           {
            "Effect": "Allow",
            "Action": ["redshift:AuthorizeDataShare"],
            "Resource": "*",
            "Condition": {
	         "StringEqualsIgnoreCase": {
	          "redshift:ConsumerIdentifier": "ADX"
	         }
	       }
	     },
	     {
            "Effect": "Allow",
            "Action": [
	          "redshift:DescribeDataSharesForProducer",
	          "redshift:DescribeDataShares"
	       ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "apigateway:GET",
            ],
            "Resource": "*"
        }
    ]
}
```

## AWS managed policy: `AWSDataExchangeProviderFullAccess`<a name="security-iam-awsmanpol-awsdataexchangeproviderfullaccess"></a>


|  | 
| --- |
| The updated managed policy for the Amazon Redshift data product feature is in preview release for AWS Data Exchange and is subject to change\. | 

You can attach the `AWSDataExchangeProviderFullAccess` policy to your IAM identities\.

This policy grants contributor permissions that provide data provider access to AWS Data Exchange and AWS Marketplace actions using the AWS Management Console and SDK\. It also provides select access to Amazon S3 and AWS Key Management Service as needed to take full advantage of AWS Data Exchange\.

**Permissions details**

This policy includes the following permissions:
+ `AWS Data Exchange` – Allows principals full access to provide data products on AWS Data Exchange\. Principals can create, update, and remove products on AWS Data Exchange\.
+ `AWS Marketplace` – Allows principals access to AWS Marketplace for providing and subscribing to data products, and managing subscription verification requests\. This is required to provide data products\.
+ `Amazon S3` – Allows principals to get AWS Data Exchange related objects \(including data product files\) from Amazon Simple Storage Service, and to upload AWS Data Exchange related files to Amazon S3\. This is required for providing data products\.
+ `Amazon API Gateway` – Allows principals to get Amazon API Gateway APIs from Amazon API Gateway, and to upload APIs\. This is required for providing Amazon API Gateway API data sets\.
+ `Amazon Redshift` – Allows principals to view AWS Data Exchange datashares for Amazon Redshift for import and to authorize them\. This is required for providing Amazon Redshift data products\.
+ `AWS KMS` – Allows access to AWS Key Management Service so that data can be encrypted and accessed using keys\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "dataexchange:CreateDataSet",
                "dataexchange:CreateRevision",
                "dataexchange:CreateAsset",
                "dataexchange:Get*",
                "dataexchange:Update*",
                "dataexchange:List*",
                "dataexchange:Delete*",
                "dataexchange:TagResource",
                "dataexchange:UntagResource",
                "dataexchange:PublishDataSet",
                "dataexchange:SendApiAsset",
                "tag:GetTagKeys",
                "tag:GetTagValues"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "dataexchange:CreateJob",
                "dataexchange:StartJob",
                "dataexchange:CancelJob"
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "dataexchange:JobType": [
                        "IMPORT_ASSETS_FROM_S3",
                        "IMPORT_ASSET_FROM_SIGNED_URL",
                        "EXPORT_ASSETS_TO_S3",
                        "EXPORT_ASSET_TO_SIGNED_URL",
                        "IMPORT_ASSET_FROM_API_GATEWAY_API",
                        "IMPORT_ASSETS_FROM_REDSHIFT_DATA_SHARES"
                    ]
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::*aws-data-exchange*",
            "Condition": {
                "ForAnyValue:StringEquals": {
                    "aws:CalledVia": [
                        "dataexchange.amazonaws.com"
                    ]
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": "s3:GetObject",
            "Resource": "*",
            "Condition": {
                "StringEqualsIgnoreCase": {
                    "s3:ExistingObjectTag/AWSDataExchange": "true"
                },
                "ForAnyValue:StringEquals": {
                    "aws:CalledVia": [
                        "dataexchange.amazonaws.com"
                    ]
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:PutObject",
                "s3:PutObjectAcl"
            ],
            "Resource": "arn:aws:s3:::*aws-data-exchange*",
            "Condition": {
                "ForAnyValue:StringEquals": {
                    "aws:CalledVia": [
                        "dataexchange.amazonaws.com"
                    ]
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetBucketLocation",
                "s3:ListBucket",
                "s3:ListAllMyBuckets"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "aws-marketplace:DescribeEntity",
                "aws-marketplace:ListEntities",
                "aws-marketplace:DescribeChangeSet",
                "aws-marketplace:ListChangeSets",
                "aws-marketplace:StartChangeSet",
                "aws-marketplace:CancelChangeSet",
                "aws-marketplace:GetAgreementApprovalRequest",
                "aws-marketplace:ListAgreementApprovalRequests",
                "aws-marketplace:AcceptAgreementApprovalRequest",
                "aws-marketplace:RejectAgreementApprovalRequest",
                "aws-marketplace:UpdateAgreementApprovalRequest",
                "aws-marketplace:SearchAgreements",
                "aws-marketpalce:GetAgreementTerms"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "kms:DescribeKey",
                "kms:ListAliases",
                "kms:ListKeys"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": ["redshift:AuthorizeDataShare"],
            "Resource": "*",
            "Condition": {
                "StringEqualsIgnoreCase": {
                  "redshift:ConsumerIdentifier": "ADX"
         }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "redshift:DescribeDataSharesForProducer",
                "redshift:DescribeDataShares"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "apigateway:GET",
            ],
            "Resource": "*"
        }
    ]
}
```

## AWS managed policy: `AWSDataExchangeReadOnly`<a name="security-iam-awsmanpol-awsdataexchangereadonly"></a>

You can attach the `AWSDataExchangeReadOnly` policy to your IAM identities\.

This policy grants read\-only permissions that allow read\-only access to AWS Data Exchange and AWS Marketplace actions using the AWS Management Console and SDK\.

**Permissions details**

This policy includes the following permissions:
+ `AWS Data Exchange` – Allows principals read\-only access to AWS Data Exchange products\. This includes both provided and subscribed data products\.
+ `AWS Marketplace` – Allows principals read\-only access to AWS Marketplace for provided and subscribed products\. This is required to view data products\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "dataexchange:Get*",
                "dataexchange:List*"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "aws-marketplace:ViewSubscriptions",
                "aws-marketplace:GetAgreementRequest",
                "aws-marketplace:ListAgreementRequests",
                "aws-marketplace:GetAgreementApprovalRequest",
                "aws-marketplace:ListAgreementApprovalRequests",
                "aws-marketplace:DescribeEntity",
                "aws-marketplace:ListEntities",
                "aws-marketplace:DescribeChangeSet",
                "aws-marketplace:ListChangeSets",
                "aws-marketplace:SearchAgreements",
                "aws-marketpalce:GetAgreementTerms"
            ],
            "Resource": "*"
        }
    ]
}
```

## AWS managed policy: `AWSDataExchangeSubscriberFullAccess`<a name="security-iam-awsmanpol-awsdataexchangesubscriberfullaccess"></a>

You can attach the `AWSDataExchangeSubscriberFullAccess` policy to your IAM identities\.

This policy grants contributor permissions that allow data subscriber access to AWS Data Exchange and AWS Marketplace actions using the AWS Management Console and SDK\. It also provides select access to Amazon S3 and AWS Key Management Service as needed to take full advantage of AWS Data Exchange\.

**Permissions details**

This policy includes the following permissions:
+ `AWS Data Exchange` – Allows principals full access to the subscriber features of AWS Data Exchange\. This includes subscribing to and accessing data products\.
+ `AWS Marketplace` – Allows principals access to AWS Marketplace for view and subscribing to products\. This is required to subscribe to data products\.
+ `Amazon S3` – Allows principals to view and get AWS Data Exchange related objects \(including data product files\) from Amazon Simple Storage Service\. This is required for accessing subscribed data products\.
+ `AWS KMS` – Allows access to AWS Key Management Service to access data that has been encrypted using keys\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "dataexchange:Get*",
                "dataexchange:List*"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "dataexchange:CreateEventAction",
                "dataexchange:UpdateEventAction",
                "dataexchange:DeleteEventAction",
                "dataexchange:SendApiAsset"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "dataexchange:CreateJob",
                "dataexchange:StartJob",
                "dataexchange:CancelJob"
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "dataexchange:JobType": [
                        "EXPORT_ASSETS_TO_S3",
                        "EXPORT_ASSET_TO_SIGNED_URL",
                        "EXPORT_REVISIONS_TO_S3"
                    ]
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": "s3:GetObject",
            
            "Resource": "arn:aws:s3:::*aws-data-exchange*",
            "Condition": {
                "ForAnyValue:StringEquals": {
                    "aws:CalledVia": [
                        "dataexchange.amazonaws.com"
                    ]
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetBucketLocation",
                "s3:ListBucket",
                "s3:ListAllMyBuckets"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "aws-marketplace:Subscribe",
                "aws-marketplace:Unsubscribe",
                "aws-marketplace:ViewSubscriptions",
                "aws-marketplace:GetAgreementRequest",
                "aws-marketplace:ListAgreementRequests",
                "aws-marketplace:CancelAgreementRequest"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "kms:DescribeKey",
                "kms:ListAliases",
                "kms:ListKeys"
            ],
            "Resource": "*"
        }
    ]
}
```

## AWS Data Exchange updates to AWS managed policies<a name="security-iam-awsmanpol-updates"></a>

The following table provides details about updates to AWS managed policies for AWS Data Exchange since this service began tracking these changes\. For automatic alerts about changes to this page \(and any other changes to this user guide\), subscribe to the RSS feed on the [Document history for AWS Data Exchange](doc-history.md) page\.






| Change | Description | Date | 
| --- | --- | --- | 
|  [ AWSDataExchangeProviderFullAccess](#security-iam-awsmanpol-awsdataexchangeproviderfullaccess) and  [ AWSDataExchangeFullAccess](#security-iam-awsmanpol-awsdataexchangefullaccess) – Update to existing policies  |   Added `apigateway:GET`, a new permission to retrieve an API asset from Amazon API Gateway\.   | December 3, 2021 | 
| [ AWSDataExchangeProviderFullAccess](#security-iam-awsmanpol-awsdataexchangeproviderfullaccess) and [ AWSDataExchangeSubscriberFullAccess](#security-iam-awsmanpol-awsdataexchangesubscriberfullaccess) – Update to existing policies |  Added `dataexchange:SendApiAsset`, a new permission to send a request to an API asset\.  | November 29, 2021 | 
|  [ AWSDataExchangeProviderFullAccess](#security-iam-awsmanpol-awsdataexchangeproviderfullaccess) and [ AWSDataExchangeFullAccess](#security-iam-awsmanpol-awsdataexchangefullaccess) – Update to existing policies  |  Added `redshift:AuthorizeDataShare`, `redshift:DescribeDataSharesForProducer`, and` redshift:DescribeDataShares`, new permissions to authorize access to and create Amazon Redshift datashares\. \(Preview\)  | November 1, 2021 | 
|  [AWSDataExchangeSubscriberFullAccess](#security-iam-awsmanpol-awsdataexchangesubscriberfullaccess) – Update to an existing policy  |  Added `dataexchange:CreateEventAction`, `dataexchange:UpdateEventAction`, and `dataexchange:DeleteEventAction`, new permissions to control access to automatically export new revisions of data sets\.  | September 30, 2021 | 
|  [ AWSDataExchangeProviderFullAccess](#security-iam-awsmanpol-awsdataexchangeproviderfullaccess) and [ AWSDataExchangeFullAccess](#security-iam-awsmanpol-awsdataexchangefullaccess) – Update to existing policies  |  Added `dataexchange:PublishDataSet`, a new permission to control access to publishing new versions of data sets\.  | May 25, 2021 | 
|  [ AWSDataExchangeReadOnly](#security-iam-awsmanpol-awsdataexchangereadonly), [ AWSDataExchangeProviderFullAccess](#security-iam-awsmanpol-awsdataexchangeproviderfullaccess), and [ AWSDataExchangeFullAccess](#security-iam-awsmanpol-awsdataexchangefullaccess) – Update to existing policies  | Added aws\-marketplace:SearchAgreements and aws\-marketplace:GetAgreementTerms to enable viewing subscriptions for products and offers\. | May 12, 2021 | 
|  AWS Data Exchange started tracking changes  |  AWS Data Exchange started tracking changes for its AWS managed policies\.  | April 20, 2021 | 