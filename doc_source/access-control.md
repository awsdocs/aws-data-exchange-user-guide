# Access control<a name="access-control"></a>

To create, update, delete, or list AWS Data Exchange resources, you need permissions to perform the operation and to access the corresponding resources\. To perform the operation programmatically, you also need valid access keys\.

## Overview of managing access permissions to your AWS Data Exchange resources<a name="access-control-overview"></a>

Every AWS resource is owned by an AWS account, and permissions to create or access a resource are governed by permissions policies\. An account administrator can attach permissions policies to AWS Identity and Access Management \(IAM\) identities \(that is, users, groups, and roles\)\. Some services \(such as AWS Lambda\) also support attaching permissions policies to resources\. 

**Note**  
An *account administrator* \(or administrator\) is a user with administrator privileges\. For more information, see [IAM Best Practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) in the *IAM User Guide*\.

When granting permissions, you decide who is getting the permissions, the resources they get permissions for, and the specific actions that you want to allow on those resources\.

**Topics**
+ [AWS Data Exchange resources and operations](#access-control-resources)
+ [Understanding resource ownership](#access-control-owner)
+ [Managing access to resources](#access-control-manage-access-intro)
+ [Specifying policy elements: actions, effects, and principals](#access-control-specify-control-tower-actions)
+ [Specifying conditions in a policy](#specifying-conditions)

### AWS Data Exchange resources and operations<a name="access-control-resources"></a>

In AWS Data Exchange, there are two different kinds of primary resources with different control planes:
+ The primary resources for AWS Data Exchange are *data sets* and *jobs*\. AWS Data Exchange also supports *revisions* and *assets*\.
+ To facilitate transactions between providers and subscribers, AWS Data Exchange also uses AWS Marketplace concepts and resources, including products, offers, and subscriptions\. You can use the AWS Marketplace Catalog API or the AWS Data Exchange console to manage your products, offers, subscription requests, and subscriptions\.

### Understanding resource ownership<a name="access-control-owner"></a>

The AWS account owns the resources that are created in the account, regardless of who created the resources\. Specifically, the resource owner is the AWS account of the [principal entity](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html) \(that is, the AWS account root user, an IAM user, or an IAM role\) that authenticates the resource creation request\. The following examples illustrate how this works\.

#### Resource ownership<a name="resource-ownership"></a>

Any IAM entity in an AWS account with the correct permissions can create AWS Data Exchange data sets\. When an IAM entity creates a data set, their AWS account owns the data set\. Published data products can contain data sets that are owned only by the AWS account that created them\.

To subscribe to an AWS Data Exchange product, the IAM entity needs permissions to use AWS Data Exchange, in addition to the `aws-marketplace:subscribe` IAM permission for AWS Marketplace \(assuming they pass any related subscription verifications\)\. As a subscriber, your account has read access to entitled data sets; however, it does not own the entitled data sets\. Any entitled data sets that are exported to Amazon S3 are owned by the subscriber's AWS account\.

### Managing access to resources<a name="access-control-manage-access-intro"></a>

This section discusses using IAM in the context of AWS Data Exchange\. It doesn't provide detailed information about the IAM service\. For complete IAM documentation, see [What Is IAM?](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html) in the *IAM User Guide*\. For information about IAM policy syntax and descriptions, see [AWS IAM Policy Reference](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies.html) in the *IAM User Guide*\.

A *permissions policy* describes who has access to what\. The following section explains the options for creating permissions policies\.

Policies attached to an IAM identity are referred to as *identity\-based* policies \(IAM policies\)\. Policies attached to a resource are referred to as *resource\-based* policies\. AWS Data Exchange supports only identity\-based policies \(IAM policies\)\. 

**Topics**
+ [Identity\-based policies \(IAM policies\)](#access-control-manage-access-intro-iam-policies)
+ [Resource\-based policies](#access-control-manage-access-intro-resource-policies)

#### Identity\-based policies \(IAM policies\)<a name="access-control-manage-access-intro-iam-policies"></a>

You can attach policies to IAM identities\. For example, you can do the following:
+ **Attach a permissions policy to a user or a group in your account** – To grant a user permissions to create an AWS Data Exchange resource, like a revision, you can attach a permissions policy to a user or group that the user belongs to\.
+ **Attach a permissions policy to a role \(grant cross\-account permissions\)** – You can attach an identity\-based permissions policy to an IAM role to grant cross\-account permissions\. For example, the administrator in Account A can create a role to grant cross\-account permissions to another AWS account \(for example, Account B\) or an AWS service as follows:

  1. Account A administrator creates an IAM role and attaches a permissions policy to the role that grants permissions on resources in Account A\.

  1. Account A administrator attaches a trust policy to the role identifying Account B as the principal who can assume the role\.

  1. Account B administrator can then delegate permissions to assume the role to any users in Account B\. Doing this allows users in Account B to create or access resources in Account A\. The principal in the trust policy can also be an AWS service principal, if you want to grant an AWS service permissions to assume the role\.

  For more information about using IAM to delegate permissions, see [Access Management](https://docs.aws.amazon.com/IAM/latest/UserGuide/access.html) in the *IAM User Guide*\.

AWS Data Exchange provides four managed policies:
+ `AWSDataExchangeFullAccess` 
+ `AWSDataExchangeSubscriberFullAccess` 
+ `AWSDataExchangeProviderFullAccess` 
+ `AWSDataExchangeReadOnly`

For more information about these policies and their permissions, see [AWS managed policies for AWS Data Exchange](security-iam-awsmanpol.md)\. 

##### Amazon S3 permissions<a name="additional-s3-permissions"></a>

When importing assets from Amazon S3 to AWS Data Exchange, you need permissions to write to the AWS Data Exchange service S3 buckets\. Similarly, when exporting assets from AWS Data Exchange to Amazon S3, you need permissions to read from the AWS Data Exchange service S3 buckets\. These permissions are included in the policies mentioned previously, but you can also create your own policy to allow just what you want your users to be able to do\. You can scope these permissions to buckets that contain `aws-data-exchange` in their name and use the [ CalledVia](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-calledvia) permission to restrict the usage of the permission to requests made by AWS Data Exchange on behalf of the principal\.

For example, you could create a policy to allow importing and exporting to AWS Data Exchange that includes these permissions\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
          "Effect": "Allow",
          "Action": "s3:GetObject",
          "Resource": "arn:aws:s3:::*aws-data-exchange*",
          "Condition": {
            "ForAnyValue:StringEquals": {
              "aws:CalledVia":[
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
              "aws:CalledVia":[
                "dataexchange.amazonaws.com"
              ]
            }
          }
        },
    ]
}
```

These permissions allow providers to import and export with AWS Data Exchange\. The policy includes the following permissions and restrictions:
+ **s3:PutObject** and **s3:PutObjectAcl** – These permissions are restricted only to S3 buckets that contain `aws-data-exchange` in their name\. These permissions allows providers to write to AWS Data Exchange service buckets when importing from Amazon S3\.
+ **s3:GetObject** – This permission is restricted to S3 buckets that contain `aws-data-exchange` in their name\. This permission allows customers to read from AWS Data Exchange service buckets when exporting from AWS Data Exchange to Amazon S3\.
+ These permissions are restricted to requests made by using AWS Data Exchange with the IAM `CalledVia` condition\. This allows the S3 `PutObject` permissions to only be used in the context of the AWS Data Exchange console or API\.

**Note**  
Your users may also need additional permissions to read to or write from your own S3 buckets and objects that are not covered in this example\.

For more information about users, groups, roles, and permissions, see [Identities \(Users, Groups, and Roles\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id.html) in the *IAM User Guide*\. 

#### Resource\-based policies<a name="access-control-manage-access-intro-resource-policies"></a>

AWS Data Exchange does not support resource\-based policies\.

Other services, such as Amazon S3, do support resource\-based permissions policies\. For example, you can attach a policy to an S3 bucket to manage access permissions to that bucket\.

### Specifying policy elements: actions, effects, and principals<a name="access-control-specify-control-tower-actions"></a>

To use AWS Data Exchange, you must be an IAM user with the appropriate permissions defined in a IAM policy\.

The following are the most basic policy elements:
+ **Resource** – In a policy, you use an Amazon Resource Name \(ARN\) to identify the resource to which the policy applies\. All AWS Data Exchange API operations support resource level permissions \(RLP\), but AWS Marketplace actions don't support RLP\. For more information, see [AWS Data Exchange resources and operations](#access-control-resources)\.
+ **Action** – You use action keywords to identify resource operations that you want to allow or deny\.
+ **Effect** – You specify the effect \(allow or deny\) when the user requests the specific action\. If you don't explicitly grant access to \(allow\) a resource, access is implicitly denied\. You can also explicitly deny access to a resource, which you might do to make sure that a user cannot access it, even if a different policy grants access\.
+ **Principal** – In identity\-based policies \(IAM policies\), the user that the policy is attached to is the implicit principal\. For resource\-based policies, you specify the user, account, service, or other entity that you want to receive permissions \(applies to resource\-based policies only\)\. AWS Data Exchange doesn't support resource\-based policies\.

For more information about IAM policy syntax and descriptions, see [AWS IAM Policy Reference](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies.html) in the *IAM User Guide*\.

### Specifying conditions in a policy<a name="specifying-conditions"></a>

When you grant permissions, you can use the IAM policy language to specify the conditions when a policy should take effect\. With AWS Data Exchange, the `CreateJob`, `StartJob`, `GetJob`, and `CancelJob` API operations support conditional permissions\. You can provide permissions at the `JobType` level\.


**AWS Data Exchange condition key reference**  

| Condition key | Description | Type | 
| --- | --- | --- | 
| "dataexchange:JobType":"IMPORT\_ASSETS\_FROM\_S3" | Scopes permissions to jobs that import assets from Amazon S3\. | String | 
| "dataexchange:JobType":"IMPORT\_ASSET\_FROM\_SIGNED\_URL" | Scopes permissions to jobs that import assets from a signed URL\. | String | 
| "dataexchange:JobType":"IMPORT\_ASSET\_FROM\_REDSHIFT\_DATA\_SHARES" | Scopes permissions to jobs that import assets from Amazon Redshift\. | String | 
| "dataexchange:JobType":"IMPORT\_ASSET\_FROM\_API\_GATEWAY\_API" | Scopes permissions to jobs that import assets from Amazon API Gateway\. | String | 
| "dataexchange:JobType":"EXPORT\_ASSETS\_TO\_S3" | Scopes permissions to jobs that export assets to Amazon S3\. | String | 
| "dataexchange:JobType":"EXPORT\_ASSETS\_TO\_SIGNED\_URL" | Scopes permissions to jobs that export assets to a signed URL\. | String | 
| "dataexchange:JobType":EXPORT\_REVISIONS\_TO\_S3" | Scopes permissions to jobs that export revisions to Amazon S3\. | String | 

For more information about specifying conditions in a policy language, see [Condition](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html#Condition) in the *IAM User Guide*\. 

To express conditions, you use predefined condition keys\. AWS Data Exchange has the `JobType` condition for API operations\. However, there are AWS wide condition keys that you can use, as appropriate\. For a complete list of AWS wide keys, see the [https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)\.