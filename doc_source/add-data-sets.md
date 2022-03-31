# AddDataSets<a name="add-data-sets"></a>

**Important**  
As of July 22, 2021, new and existing providers can automatically publish revisions to data sets\. All new products on AWS Data Exchange default to automatic revision publishing\. If you have created existing products on AWS Data Exchange before July 22, 2021, you need to migrate them to automatic revision publishing\.  
For more information, see [Migrating an existing product to automatic revision publishing](updating-products.md#migrate-product)\.

**Note**  
Data sets added via the Catalog API change set of type `AddDataSets` default to the publishing method of the product\.

To add data sets to your AWS Data Exchange product, start a change set of type `AddDataSets`\. To do so, you can use the `StartChangeSet` API operation and specify the change type, the product identifier, the product type, and the details including the data set Amazon Resource Name \(ARN\)\.

## Tutorial: Adding new data sets to a published data product<a name="add-data-sets-tutorial"></a>

This tutorial walks you through detailed steps to add new AWS Data Exchange data sets to a published product\. The tutorial has the following high\-level steps\.

**Topics**
+ [Set up IAM permissions](#data-set-catalog-iam-permissions)
+ [Access the AWS Marketplace Catalog API](#data-set-access-catalog-api)
+ [Get your product ID from the AWS Data Exchange console](#get-data-set-exchange-product-id)
+ [Start a change request](#start-data-set-change-request)
+ [Check the status of your change set](#check-data-set-change-status)

### Set up IAM permissions<a name="data-set-catalog-iam-permissions"></a>

Before you begin, you need AWS Identity and Access Management \(IAM\) permissions for using the AWS Marketplace Catalog API\. These permissions are in addition to the permissions you need for using AWS Data Exchange\.

1. Navigate your browser to the IAM console and sign in using an AWS account that can manage IAM permissions\.

1. From the left navigation pane, choose **Policies**\.

1. Choose **Create policy**\.

1. Choose the **JSON** tab, and provide the following permissions\. This provides full access to the AWS Marketplace Catalog API\. You can restrict access as appropriate for your use case\.

   ```
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Effect": "Allow",
         "Action": [
           "aws-marketplace:CancelChangeSet",
           "aws-marketplace:ListChangeSets",
           "aws-marketplace:DescribeEntity",
           "aws-marketplace:StartChangeSet",
           "aws-marketplace:ListEntities",
           "aws-marketplace:DescribeChangeSet",
           "dataexchange:PublishDataSet"
         ],
         "Resource": "*"
       }
     ]
   }
   ```

1. Choose **Next: Review**\.

1. Provide a name for the policy \(for example, **CatalogAPIFullAccess**\), and then choose **Create Policy**\.

1. Using the IAM console, choose the users, groups, or roles that you want to attach the policy to\.

### Access the AWS Marketplace Catalog API<a name="data-set-access-catalog-api"></a>

To access the AWS Marketplace Catalog API, use the following HTTP client endpoint\.

```
catalog.marketplace.us-east-1.amazonaws.com
```

### Get your product ID from the AWS Data Exchange console<a name="get-data-set-exchange-product-id"></a>

Before you can use the AWS Marketplace Catalog API to publish new data sets, get your product ID from the AWS Data Exchange console\. Navigate to the **Product Dashboard**, and then copy the product ID you would like to publish data sets for\. You may also use the [AWS Marketplace Catalog API](https://docs.aws.amazon.com/marketplace-catalog/latest/api-reference/welcome.html) to find your product ID, using the `ListEntities` action with the **DataProduct@1\.0** entity type\.

### Start a change request<a name="start-data-set-change-request"></a>

**To start a change request to add a data set in your test product**

1. Copy the entity ID that you get by following the instructions in [Get your product ID from the AWS Data Exchange console](#get-data-set-exchange-product-id)\.

1. Make a `StartChangeSet` request with an `AddDataSets` change type\.

**Note**  
For information about working with change sets in the AWS Marketplace Catalog API, see [ Working with change sets](https://docs.aws.amazon.com/marketplace-catalog/latest/api-reference/welcome.html#working-with-change-sets)\. For more information about working with the identifier for entities, see [Identifier](https://docs.aws.amazon.com/marketplace-catalog/latest/api-reference/welcome.html#identifier)\.

**Example request**

```
https://catalog.marketplace.us-east-1.amazonaws.com/StartChangeSet
```

**Example request body**

```
{
    "Catalog": "AWSMarketplace",
    "ChangeSetName": "Adding Data Set to my test Data Product",
    "ChangeSet": [
        {
            "ChangeType": "AddDataSets",
            "Entity": {
                "Identifier": "entity-id@1",
                "Type": "DataProduct@1.0"
            },
            "Details": "{ \"DataSets\": [ { \"Arn\": \"data-set-arn\" } ] }"
        }
    ]
}
```

**Example response**

```
{
  "ChangeSetId": "cs-bnEXAMPLE4mkz9oh",
  "ChangeSetArn": "arn:aws:aws-marketplace:us-east-1:account-id:AWSMarketplace/ChangeSet/cs-bnEXAMPLE4mkz9oh"
}
```

### Check the status of your change set<a name="check-data-set-change-status"></a>

After you use the `StartChangeSet` API operation to start the change request, you can use the `DescribeChangeSet` operation to check its status\. Provide the change set ID returned in the `StartChangeSet` API response\.

**Example request**

```
https://catalog.marketplace.us-east-1.amazonaws.com/DescribeChangeSet?catalog=AWSMarketplace&changeSetId=cs-bnEXAMPLE4mkz9oh
```

**Example request body**

```
{
"changeSetId":"cs-bnEXAMPLE4mkz9oh"
}
```

**Example response**

```
{
    "ChangeSetId": "cs-bnEXAMPLE4mkz9oh",
    "ChangeSetArn": "arn:aws:aws-marketplace:us-east-1:account-id:AWSMarketplace/ChangeSet/cs-bnEXAMPLE4mkz9oh",
    "ChangeSetName": "Adding Data Set to my test Data Product",
    "StartTime": "2018-09-20T19:45:03.115+0000",
    "EndTime": "2018-09-20T19:48:12.517+0000",
    "Status": "SUCCEEDED",
    "FailureDescription": null,
    "ChangeSet": [
        {
            "ChangeType": "AddDataSets",
            "Entity": {
                "Type": "DataProduct@1.0",
                "Identifier": "entity-id@1"
            },
            "ErrorList": []
        }
    ]
}
```

## AddDataSets exceptions<a name="catalog-exceptions-data-sets"></a>

The following exceptions can occur when you use the AWS Marketplace Catalog API with AWS Data Exchange:

**DATA\_SET\_NOT\_FOUND**  
This happens when the requested data set was not found\. To resolve this issue, ensure that there's not a typo in the data set ARN and that your AWS account owns the data set, and try again\.

**INVALID\_INPUT**  
The request couldn't be processed due to input that isn't valid\. To resolve this issue, ensure that there's not a typo in the request and that the product does not exceed the maximum number of allowed data sets\.

**DATA\_SET\_ALREADY\_PUBLISHED**  
This happens when the data set has already been previously added to the product\.

**DATA\_SET\_DUPLICATE\_PROVIDED**  
 This happens when the same data set is provided more than once in the request\.