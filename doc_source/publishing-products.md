# Publishing a new product<a name="publishing-products"></a>

The following topics describe the process of publishing a new product on AWS Data Exchange by using the AWS Data Exchange console\. 

**Topics**
+ [Publishing a product containing file\-based data](#publish-data-product)
+ [Publishing a product containing APIs](#publish-API-product)
+ [Publishing a product containing Amazon Redshift datasets](#publish-Redshift-product)

**Important**  
Beginning July 22, 2021, new and existing providers have the ability to automatically publish revisions to data sets\. All new products on AWS Data Exchange default to automatic revision publishing\. If you have created existing products on AWS Data Exchange before July 22, 2021, you need to migrate them to automatic revision publishing\.   
For more information, see [Migrating an existing product to automatic revision publishing](updating-products.md#migrate-product)\.

**Note**  
If you are an existing provider and have not yet migrated all of your products to automatic revision publishing, you will need to manually publish your revision\. For more information, see [Publishing a new data set revision using manual revision publishing](updating-products.md#manual-publish-revision)\.

## Publishing a product containing file\-based data<a name="publish-data-product"></a>

The following topics describe the process of creating a data set and publishing a new product containing file\-based data on AWS Data Exchange by using the AWS Data Exchange console\. The process has the following steps:

**Topics**
+ [Step 1: Create assets](#create-assets)
+ [Step 2: Create a data set](#create-dataset)
+ [Step 3: Create a revision](#create-revision)
+ [Step 4: Import assets to a revision](#import-assets)
+ [Step 5: Publish a new product](#publish-products)
+ [Step 6: \(Optional\) Copy a product](#copy-product)

### Step 1: Create assets<a name="create-assets"></a>

Assets are the *data* in AWS Data Exchange\. For more information, see [Assets](data-sets.md#assets)\.

Before you create and publish a new file\-based data product, you must:

1. Create your files\. 

   AWS Data Exchange supports all file types\.

1. Store your files as objects in Amazon S3 or on your local computer\. 

   For more information about storing files in Amazon S3, see the [Amazon S3 User Guide](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)\.

### Step 2: Create a data set<a name="create-dataset"></a>

Data sets in AWS Data Exchange are dynamic and are versioned using revisions, with each revision containing at least one asset\. For more information, see [Data in AWS Data Exchange](data-sets.md)\.

**To create a data set**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1.  On the left side navigation pane, under **Publish data**, choose **Owned data sets**\.

1. In **Owned data sets**, choose **Create data set** to open the **Data set creation steps** wizard\.

1. In **Select data set type**, choose **Amazon S3 object**\.

1. In **Define data set**, enter a **Name** and **Description** for your data set\. For more information, see [Data set best practices](data-sets.md#data-set-best-practices)\. 

1. \(Optional\) Under **Add tags – optional**, add tags\.

1. Choose **Create**\. 

### Step 3: Create a revision<a name="create-revision"></a>

In the following procedure, you create a revision after you’ve created a data set in the AWS Data Exchange console\. For more information, see [Revisions](data-sets.md#revisions)\.

**To create a revision**

1. On the **Data set overview** section of the data set details page:

   1. \(Optional\) Choose **Edit name** to edit information about your data set\.

   1. \(Optional\) Choose **Delete** to delete the data set\.

1. On the **Revisions** section, choose **Create revision**\.

1. Under **Revision settings**, provide an optional comment for your revision that describes the purpose of the revision\. 

1. \(Optional\) Under **Add tags – optional**, add tags associated with the resource\.

1. Choose **Create**\.

1. Review, edit, or delete your changes from the previous step\. 

### Step 4: Import assets to a revision<a name="import-assets"></a>

 In the following procedure, you import data assets, and then finalize the revision in the AWS Data Exchange console\. For more information, see [Assets](data-sets.md#assets)\. 

**To import assets to the revision**

1. Under the **Imported assets** section of the data set details page, choose either **Import from Amazon S3** or **Upload** \(to upload from your computer\), depending on where the data assets for the data set are currently stored\.

1. Follow the prompts, depending on your selection\. A job is started to import your asset into your data set\. 

1. After the job is finished, the **State** field in the **Jobs** section is updated to **Completed\.**

1. If you have more data to add, repeat Step 1\.

1. Under **Revision overview**, review your revision and its assets\. 

1. Choose **Finalize**\.

You have successfully finalized a revision for a data set\. 

You can edit or delete a revision before you add it to a product\. 

**Topics**
+ [Edit a revision](#edit-revision)
+ [Delete a revision](#delete-revision)

#### Edit a revision<a name="edit-revision"></a>

**To edit the revision after you’ve finalized it**

1. On the **Revision overview**, choose **De\-finalize**\.

   You see a message that the revision is no longer in the finalized state\.

1. To edit the revision, from **Revision overview**, choose **Actions**, **Edit**\.

1. Make your changes, and then choose **Update**\.

1. Review your changes and then choose **Finalize**\.

#### Delete a revision<a name="delete-revision"></a>

**To delete the revision after you’ve finalized it**

1. On the **Revision overview**, choose **Delete**\.

1. Type **Delete** in the **Delete revision** dialog box, and then choose **Delete**\.

**Warning**  
This deletes the revision and all of its assets\. This action cannot be undone\.

### Step 5: Publish a new product<a name="publish-products"></a>

After you've created at least one data set and finalized a revision with assets, you're ready to publish that data set as a part of a product\. For more information, see [Product details](product-details.md)\. Make sure that you have all required details about your product and offer\.

**To publish a new product**

1. From the left navigation pane of the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange), under **Publish data**, choose **Products**\.

1. From **Products**, choose **Publish new product** to open the **Publish new product** wizard\.

1. In the **Product visibility** section, choose your product's **Product visibility options** and **Sensitive information** configuration, and then choose **Next**\. For more information, see [Product visibility](product-details.md#product-visibility) and [Sensitive categories of information](product-details.md#sensitive-information)\.

1. In the **Define product** section, enter information about your product, including name, logo, support contact, web address, categories, and descriptions, and then choose **Next**\. For more information, see [Product details](product-details.md)\.

1. In the **Add data** section, select the check box next to the data sets you want to add\.
**Note**  
The data sets you choose must have a finalized revision\. Data sets without finalized revisions won't be added\.

   1. Choose **Add selected**, and then scroll to **Selected data sets** to review your selection\.

   1. Scroll to **Select revision access rules**, choose the revision access rules that you want to set for data sets included in this product, and then choose **Next**\. For more details, see [Revision access rules](product-details.md#best-practices-revisions)\.

1. If you are creating a public offer, in the **Add public offer** section, configure your offer\. All AWS Data Exchange products with visibility set to **Public** require a public offer\. 

   1. Choose your **Pricing and access duration** options for the subscription\.

      Choose your US sales tax settings, data subscription agreement \(DSA\), and refund policy\. 

   1. \(Optional\) Set **Subscription verification**, which enables you to control who can subscribe to this product\. For more information, see [Subscription verification for providers](subscription-verification-pro.md)\.

   1. Choose your **Oﬀer auto\-renewal** option\. For more information, see [Creating an offer for AWS Data Exchange products](prepare-offers.md)\.

   1. Choose **Next**\.

1. If you are creating a private offer, configure the offer details in the **Add custom offer** section\.

   1. In the **Subscriber account information** section, add at least one subscriber account to which you want to extend the offer\.

   1. Choose your **Pricing and access duration** options for the subscription\.

   1. Choose the **Offer expiration date** by which the subscriber must accept the offer\.

   1. Choose your US sales tax settings, data subscription agreement \(DSA\), and refund policy\.

   1. Choose your **Oﬀer auto\-renewal** option\. For more information, see [Creating an offer for AWS Data Exchange products](prepare-offers.md)\.

   1. Choose **Next**\.

1. In the **Review & publish** section, review your product information and then expand the **Product page preview** to see how it will look after it’s published\.

1. If you're sure that you want to make the product and public offer visible and available to everyone, choose **Publish**\.

You've now completed the manual portion of publishing a data product with a public offer\. AWS Data Exchange prepares and publishes your product\. On the **Product overview** page, the status of your product is **Awaiting approval** and then changes to **Published** after it's published\.

### Step 6: \(Optional\) Copy a product<a name="copy-product"></a>

After you have created your first product, you can copy its details and public offers to create a new product\.

**Note**  
You can copy a public, private, published, or unpublished product\. Custom oﬀers associated with the product will not be copied, but public oﬀers will be copied\.

**To copy a product**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **Publish data**, choose **Products**\.

1. From **Products**, choose the button next to the product you want to copy\.

1. Select the **Actions** dropdown, and then choose **Create copy**\.

1. Continue through the **Publish a new product** workflow, with details already filled in, based on the product you chose in Step 3\. For more information, see [Step 5: Publish a new product](#publish-products)\.
**Important**  
Beginning July 22, 2021, new and existing providers have the ability to automatically publish revisions to data sets\. All new products on AWS Data Exchange default to automatic revision publishing\. If you have created existing products on AWS Data Exchange before July 22, 2021, you need to migrate them to automatic revision publishing\.  
For more information, see [Migrating an existing product to automatic revision publishing](updating-products.md#migrate-product)\.  
If you are copying an existing product that you created before July 22, 2021, you will see two options under **Revision publishing**: **Automatically publish revisions** or **Manually publish revisions**\. We recommend that you choose the first option, to automatically publish revisions\.

## Publishing a product containing APIs<a name="publish-API-product"></a>

### Overview<a name="publish-api-overview"></a>

The following topics describe the process of creating a REST API data set and publishing a new product that contains APIs on AWS Data Exchange\. You can complete the process by using either the AWS Data Exchange console or the AWS Command Line Interface\.

After you have set up your Amazon API Gateway REST API, you can create a new API data set in AWS Data Exchange\. You can then create a revision, and add API assets\.

Creating and publishing an API asset allows subscriber requests to an AWS Data Exchange endpoint to proxy through to your API Gateway API\. You can then add this data set to a product and add pricing\. Then, subscribers can view your product and subscribe to it in the AWS Marketplace catalog and the AWS Data Exchange catalog\.

AWS Data Exchange features are available including revision access rules, private products, private offers, and subscription verification\.

The process has the following steps:

**Topics**
+ [Prerequisites](#publish-api-prereq)
+ [Step 1: Update the API resource policy](#update-API-resource-policy)
+ [Step 2: Create an API data set](#create-api-data-set)
+ [Step 3: Create a revision](#create-api-revision)
+ [Step 4: Add API assets to a revision](#add-api-asset)
+ [Step 5: Publish a new product containing APIs](#publish-api-data-product)
+ [Step 6: \(Optional\) Copy a product](#copy-api-product)

#### Prerequisites<a name="publish-api-prereq"></a>

Before you can publish a product containing APIs, you must meet the following prerequisites:
+ Before you can use any AWS service, including AWS Data Exchange, you must sign up for AWS and create an AWS Identity and Access Management \(IAM\) user account\. For more information, see [Setting up AWS Data Exchange](setting-up.md)\.
+ To create products on AWS Data Exchange, you must register your AWS account as an AWS Marketplace Seller\. Use this account so create your data sets\. The account with the API Gateway resource doesn't need to be in the same account that is creating the data sets\.
+ Your REST API must be on Amazon API Gateway with an integration that uses an appropriate request and response model for accessing your data, such as Amazon DynamoDB or AWS Lambda\. For more information, see [Developing a REST API in API Gateway](https://docs.aws.amazon.com/apigateway/latest/developerguide/rest-api-develop.html) and [Working with REST APIs](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-rest-api.html) in the *Amazon API Gateway Developer Guide*\.
**Note**  
Only public API Gateway APIs are supported\.
+ Your API Gateway REST API must be able to authenticate and authorize calls from the AWS Data Exchange service principal\. Every request from AWS Data Exchange to your API uses the Signature Version 4 \(SigV4\) protocol signed with AWS Data Exchange credentials\. AWS Data Exchange works with custom domains and domain key mappings\.
**Note**  
AWS Data Exchange doesn't support Amazon Cognito, No\-Auth, and AWS Lambda authorizers\.
+ If your API Gateway REST API uses a custom identity system for authentication and authorization, configure it to use IAM authentication and import an OpenAPI schema describing your API\. AWS Data Exchange will invoke your API Gateway REST API with its own service credentials and include subscriber information such as account ID\.
+ Your API Gateway REST API is responsible for integrating with your backend\. To do this, do one of the following: 
  + Attach a long\-lived authentication token to every request that comes through your API Gateway REST API that the backend can verify\.
  + Use API Gateway to invoke a Lambda function that can generate credentials and invoke your API\.

Your API is invoked per the [API integration request specification](#api-request-spec)\.

For more information, see the following topics:

**Topics**
+ [API data set security](#api-data-set-security)
+ [API integration request specification](#api-request-spec)
+ [Header forwarding](#header-forwarding)

##### API data set security<a name="api-data-set-security"></a>

AWS Data Exchange encrypts traffic end to end using Transport Layer Security \(TLS\) 1\.2\. All metadata is encrypted at rest\. AWS Data Exchange will not store subscriber requests or the responses from your backend\. We only extract metering metadata necessary for billing\.

##### API integration request specification<a name="api-request-spec"></a>

An API on AWS Data Exchange passes through all headers \(except for the headers listed in [Header forwarding](#header-forwarding)\), body, http method, path, and query strings as\-is from the customer request and appends the following headers\.

```
// These headers help prevent Confused Deputy attacks.  They enable the SourceAccount
// and SourceArn variables in IAM policies.
'x-amz-source-account': ACCOUNT_ID,
'x-amz-source-arn': `arn:aws:dataexchange:${REGION}:${OWNER_ACCOUNT_ID}:data-sets/${DATA_SET_ID}/revisions/${REVISION_ID}/assets/${ASSET_ID}`,
  
// These headers identify the API Asset in Data Exchange.  
'x-amzn-dataexchange-asset-id': ASSET_ID,
'x-amzn-dataexchange-data-set-id': DATA_SET_ID,
'x-amzn-dataexchange-revision-id': REVISION_ID,

// This header identifies the Data Exchange Product.
'x-amzn-dataexchange-product-id': PRODUCT_ID,
  
// This header identifies the caller of Data Exchange.  It will contain subscriber
// information.
'x-amzn-dataexchange-requester-account-id': REQUESTER_ACCOUNT_ID,

// Providers can attach custom metadata in the form of key/value pairs
// to a particular subscription. We will send these key/value pairs as stringified
// JSON.
'x-amz-dataexchange-subscription-metadata': STRINGIFIED_METADATA,
```

##### Header forwarding<a name="header-forwarding"></a>

AWS Data Exchange removes any headers related to authentication or namespaced to Amazon prior to forwarding it to a provider backend\. Specifically, AWS Data Exchange removes:
+ `Authentication` header
+ Any headers that begin with `x-amz`

The `host` header will be overwritten as a consequence of the proxying\.

#### Step 1: Update the API resource policy<a name="update-API-resource-policy"></a>

If you have an Amazon API Gateway REST API that meets the [Prerequisites](#publish-api-prereq), you must update your API resource policy to grant AWS Data Exchange the ability to invoke your API when a subscriber makes a request to get your API’s schema\.

**To update your API resource policy**

1. Add the following policy to your API’s resource policy:

   ```
   {
   "Effect": "Allow",
   "Principal": {"Service": "dataexchange.amazonaws.com"},
   "Action": "execute-api:Invoke",
   "Resource": "*",
   "Condition": {"StringEquals": {"aws:SourceAccount": "<account-id>"}}
   }
   ```

1. Replace `account-id` with the account that will be creating the API data set\. 

   The account with the API Gateway resource does not need to be in the same account that is creating the data set\.

This policy restricts these permissions to calls made by the AWS Data Exchange service principal and requires that only your account can authorize AWS Data Exchange to integrate with your API\.

**Note**  
If you have a resource policy that explicitly denies AWS Data Exchange from doing this invocation, you must remove or limit this deny\.

You’re now ready to [create an API data set](#create-api-data-set)\.

#### Step 2: Create an API data set<a name="create-api-data-set"></a>

Data sets in AWS Data Exchange are dynamic and are versioned using revisions, with each revision containing at least one asset\. For more information, see [Data in AWS Data Exchange](data-sets.md)\.

You use either the AWS Data Exchange console or the AWS Command Line Interface to create an API data set:
+ [Creating an API data set \(console\)](#create-api-ds-console)
+ [Creating an API data set \(AWS CLI\)](#create-api-ds-cli)

##### Creating an API data set \(console\)<a name="create-api-ds-console"></a>

**To create an API data set \(console\)**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1.  On the left side navigation pane, under **Publish data**, choose **Owned data sets**\.

1. In **Owned data sets**, choose **Create data set** to open the **Data set creation steps** wizard\.

1. In **Select data set type**, choose **Amazon API Gateway API**\.

1. In **Define data set**, enter a **Name** and **Description** for your data set\. For more information, see [Data set best practices](data-sets.md#data-set-best-practices)\. 

1. \(Optional\) Under **Add tags – optional**, add tags\.

1. Choose **Create**\. 

You are now ready to create a revision\. 

##### Creating an API data set \(AWS CLI\)<a name="create-api-ds-cli"></a>

**To create an API data set \(CLI\)**

1. Use the `create-data-set` command to create an API data set: 

   ```
   $ aws dataexchange create-data-set \
   --asset-type API_GATEWAY_API \
   --description 'Data Set Description' \
   --name 'Data Set Name'
   
   {
   "Arn": "arn:aws:dataexchange:us-east-1:123456789012:data-sets/$DATA_SET_ID",
   "AssetType": "API_GATEWAY_API",
   "CreatedAt": "2021-09-11T00:16:46.349000+00:00",
   "Description": "Data Set Description",
   "Id": "$DATA_SET_ID",
   "Name": "Data Set Name",
   "Origin": "OWNED",
   "UpdatedAt": "2021-09-11T00:16:46.349000+00:00"
   }
   ```

1. Note the new Asset Type of `API_GATEWAY_API`\.

You are now ready to create a revision\.

#### Step 3: Create a revision<a name="create-api-revision"></a>

In the following procedure, you create a revision after you’ve created a data set\. For more information, see [Revisions](data-sets.md#revisions)\.

You use either the AWS Data Exchange console or the AWS Command Line Interface to create a revision:
+ [Creating a revision \(console\)](#create-api-revision-console)
+ [Creating a revision \(AWS CLI\)](#create-api-revision-cli)

##### Creating a revision \(console\)<a name="create-api-revision-console"></a>

**To create a revision \(console\)**

1. On the **Data set overview** section of the data set details page:

   1. \(Optional\) Choose **Edit name** to edit information about your data set\.

   1. \(Optional\) Choose **Delete** to delete the data set\.

1. On the **Revisions** section, choose **Create revision**\.

1. Under **Define revision**, provide an optional comment for your revision that describes the purpose of the revision\. 

1. \(Optional\) Under **Add tags – optional**, add tags associated with the resource\.

1. Choose **Create revision**\.

1. Review, edit, or delete your changes from the previous step\. 

You are now ready to [add API assets to the revision](#add-api-asset)\.

##### Creating a revision \(AWS CLI\)<a name="create-api-revision-cli"></a>

**To create a revision \(AWS CLI\)**

1. Use the `create-revision` command to create a revision:

   ```
   $ aws dataexchange create-revision \
   --data-set-id $DATA_SET_ID \
   --comment 'First Atlas Revision'
   {
   "Arn": "arn:aws:dataexchange:us-east-1:123456789012:data-sets/$DATA_SET_ID/revisions/$REVISION_ID",
   "Comment": "First Atlas Revision",
   "CreatedAt": "2021-09-11T00:18:49.160000+00:00",
   "DataSetId": "$DATA_SET_ID",
   "Finalized": false,
   "Id": "$REVISION_ID",
   "UpdatedAt": "2021-09-11T00:18:49.160000+00:00"
   }
   ```

1. [Add the API assets to the revision](#add-api-asset)\.
**Note**  
You will need to know the ID of the API Gateway REST API you want to import as well as the stage\.

#### Step 4: Add API assets to a revision<a name="add-api-asset"></a>

API assets contain the information subscribers need to make calls to your API\. For more information, see [Assets](data-sets.md#assets)\. 

In the following procedure, you import data assets, and then finalize the revision\. 

You use either the AWS Data Exchange console or the AWS CLI to add assets to a revision:
+ [Adding API assets to a revision \(console\)](#add-api-assets)
+ [Adding API assets to a revision \(AWS CLI\)](#add-api-assets-cli)

##### Adding API assets to a revision \(console\)<a name="add-api-assets"></a>

**To add assets to the revision \(console\)**

1. Under the **API assets** section of the data set details page, choose **Add**\.

1. Under **Select API stage**, for **Amazon API Gateway API**, enter an API in the input box or choose one of the following from the drop\-down list:
   + **API in another AWS account** \- this is a cross account API that you have been given permission to access\.
   + **In this AWS account** \- this is an API in your AWS account\.

   1. If you chose **API in another AWS account**, enter the API ID and the API **Stage name** in the input boxes\.

   1. If you chose **In this AWS account**, choose the API **Stage name** from the drop\-down list
**Note**  
You can create a new API stage by choosing **Create new** and following the steps in the **Create new API on Amazon API Gateway** modal\. Once the new stage has been created, repeat Step 2\.

1. Under **Advanced configuration – optional**, you can choose to **Connect existing Amazon API Gateway usage plan** to use the throttling and quota limits as defined in the existing usage plan, and enter the **API key**\.

1. Under **Document API for subscribers**, provide details about the API that the subscribers will see after they subscribe to your product\.

   1. For **API name**, enter a name that subscribers can use to identify the API asset\.
**Note**  
If an **In this AWS account** was selected, the **API name** is automatically populated, which you can modify if necessary\.  
If a **API in another AWS account** was selected, the **API name** is populated with a default name, which you should modify to so the subscriber can easily understand what it is\.

   1. For **OpenAPI 3\.0 specification**, either: 

      1. Enter or copy and paste the OpenAPI 3\.0 specification file\.

      1. Choose **Import from \.JSON file**, and then select the \.json file from your local computer to import\.

         The imported specification appears in the box\.

      1. Choose **Import from Amazon API Gateway**, and then choose a specification to import\.

         The imported specification appears in the box\.

   1. For **Additional documentation \- optional**, enter any additional information that is useful for the subscriber to know about your API\. Markdown is supported\.
**Note**  
You can't edit the OpenAPI specification and additional documentation after you add this asset to a revision\.   
If you want to update this information, and the revision is not finalized, you can replace the asset\.   
If you want to update this information, and the revision is finalized, you can create a new revision with the updated asset\.

1. Choose **Add API stage**\.

   A job is started to import your asset \(in this case, the API\) into your data set\.
**Note**  
If you do not have an API on Amazon API Gateway, you will be prompted to create one\. 

1. After the job is finished, the **State** field in the **Jobs** section is updated to **Completed\.**

1. If you have more APIs to add, repeat Step 2\.

1. Under **Revision overview**, review your revision and its assets\. 

1. Choose **Finalize**\.

You have successfully ﬁnalized a revision for a data set\. 

You can [edit a revision](#edit-api-revision) or [delete a revision](#delete-api-revision) before you add it to a product\. 

You are now ready to [publish a new API data product](#publish-api-data-product)\.

##### Adding API assets to a revision \(AWS CLI\)<a name="add-api-assets-cli"></a>

You can add API assets by running an `IMPORT_ASSET_FROM_API_GATEWAY_API` job\.

**To add API assets to a revision \(AWS CLI\):**

1. Use the `create-job` command to add API assets to the revision:

   ```
   $ aws dataexchange create-job \
     --type IMPORT_ASSET_FROM_API_GATEWAY_API \
     --details '{"ImportAssetFromApiGatewayApi":{"DataSetId":"$DATA_SET_ID","RevisionId":"$REVISION_ID","ApiId":"$API_ID","Stage":"$API_STAGE","ProtocolType":"REST"}}'
   {
       "Arn": "arn:aws:dataexchange:us-east-1:123456789012:jobs/$JOB_ID",
       "CreatedAt": "2021-09-11T00:38:19.875000+00:00",
       "Details": {
           "ImportAssetFromApiGatewayApi": {
               "ApiId": "$API_ID",
               "DataSetId": "$DATA_SET_ID",
               "ProtocolType": "REST",
               "RevisionId": "$REVISION_ID",
               "Stage": "$API_STAGE"
           }
       },
       "Id": "$JOB_ID",
       "State": "WAITING",
       "Type": "IMPORT_ASSET_FROM_API_GATEWAY_API",
       "UpdatedAt": "2021-09-11T00:38:19.875000+00:00"
   }
   
   $ aws dataexchange start-job --job-id $JOB_ID
   $ aws dataexchange get-job --job-id $JOB_ID
   {
       "Arn": "arn:aws:dataexchange:us-east-1:0123456789012:jobs/$JOB_ID",
       "CreatedAt": "2021-09-11T00:38:19.875000+00:00",
       "Details": {
           "ImportAssetFromApiGatewayApi": {
               "ApiId": "$API_ID",
               "DataSetId": "$DATA_SET_ID",
               "ProtocolType": "REST",
               "RevisionId": "$REVISION_ID",
               "Stage": "$API_STAGE"
               "ApiEndpoint": "string",
               "ApiKey": "string",
               "ApiName": "string",            
               "ApiDescription": "string",
               "ApiSpecificationDownloadUrl": "string",
               "ApiSpecificationDownloadUrlExpiresAt": "string"
           }
       },
       "Id": "$JOB_ID",
       "State": "COMPLETED",
       "Type": "IMPORT_ASSET_FROM_API_GATEWAY_API",
       "UpdatedAt": "2021-09-11T00:38:52.538000+00:00"
   }
   ```

1. Use the `list-revision-assets` command to confirm that the new asset was created properly: 

   ```
   $ aws dataexchange list-revision-assets \
     --data-set-id $DATA_SET_ID \
     --revision-id $REVISION_ID
   {
       "Assets": [
       {
           "Arn": "arn:aws:dataexchange:us-east-1:123456789012:data-sets/$DATA_SET_ID/revisions/$REVISION_ID/assets/$ASSET_ID",
           "AssetDetails": {
               "ApiGatewayApiAsset": {
                   "ApiEndpoint": "https://$API_ID.execute-api.us-east-1.amazonaws.com/$API_STAGE",
                   "ApiId": "$API_ID",
                   "ProtocolType": "REST",
                   "Stage": "$API_STAGE"
               }
           },
           "AssetType": "API_GATEWAY_API",
           "CreatedAt": "2021-09-11T00:38:52.457000+00:00",
           "DataSetId": "$DATA_SET_ID",
           "Id": "$ASSET_ID",
           "Name": "$ASSET_ID/$API_STAGE",
           "RevisionId": "$REVISION_ID",
           "UpdatedAt": "2021-09-11T00:38:52.457000+00:00"
       }
       ]
   }
   ```

You are now ready to [publish the API data product](#publish-api-data-product)\. 

##### Edit a revision<a name="edit-api-revision"></a>

**To edit the revision after you’ve finalized it**

1. On the **Revision overview**, choose **De\-finalize**\.

   You see a message that the revision is no longer in the finalized state\.

1. To edit the revision, from **Revision overview**, choose **Actions**, **Edit**\.

1. Make your changes, and then choose **Update**\.

1. Review your changes and then choose **Finalize**\.

##### Delete a revision<a name="delete-api-revision"></a>

**To delete the revision after you’ve finalized it**

1. On the **Revision overview**, choose **Delete**\.

1. Type **Delete** in the **Delete revision** dialog box, and then choose **Delete**\.

**Warning**  
This deletes the revision and all of its assets\. This action cannot be undone\.

#### Step 5: Publish a new product containing APIs<a name="publish-api-data-product"></a>

After you've created at least one data set and finalized a revision with assets, you're ready to publish that data set as a part of a product\. For more information, see [Product details](product-details.md)\. Make sure that you have all required details about your product and offer\.

You use the AWS Data Exchange console or the AWS Marketplace Catalog API to publish a new product containing APIs\. For more information about how to publish a new product using the AWS Marketplace Catalog API, see [Using AWS Data Exchange with the AWS Marketplace Catalog API](appendices.md)\.
+ [Publishing a new product containing APIs \(console\)](#publish-api-product-console)

##### Publishing a new product containing APIs \(console\)<a name="publish-api-product-console"></a>

**To publish a new product containing APIs**

1. From the left navigation pane of the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange), under **Publish data**, choose **Products**\.

1. From **Products**, choose **Publish new product** to open the **Publish new product** wizard\.

1. In the **Product visibility** section, choose your product's **Product visibility options** and **Sensitive information** configuration, and then choose **Next**\. For more information, see [Product visibility](product-details.md#product-visibility) and [Sensitive categories of information](product-details.md#sensitive-information)\.

1. In the **Define product** section, enter information about your product, including name, logo, support contact, web address, categories, and descriptions, and then choose **Next**\. For more information, see [Product details](product-details.md)\.

1. In the **Add data** section, select the check box next to the data sets you want to add\.
**Note**  
The data sets you choose must have a finalized revision\. Data sets without finalized revisions won't be added\.

   1. Choose **Add selected**, and then scroll to **Selected data sets** to review your selection\.

   1. Scroll to **Select revision access rules**, choose the revision access rules that you want to set for data sets included in this product, and then choose **Next**\. For more details, see [Revision access rules](product-details.md#best-practices-revisions)\.

1. If you are creating a public offer, in the **Add public offer** section, configure your offer\. All AWS Data Exchange products with visibility set to **Public** require a public offer\. 

   1. Choose your **Pricing and access duration** options for the subscription\.

   1. Choose your US sales tax settings, data subscription agreement \(DSA\), and refund policy\.

   1. \(Optional\) Set **Subscription verification**, which enables you to control who can subscribe to this product\. For more information, see [Subscription verification for providers](subscription-verification-pro.md)\.

   1. Choose your **Oﬀer auto\-renewal** option\. For more information, see [Creating an offer for AWS Data Exchange products](prepare-offers.md)\.

   1. Choose **Next**\.

1. If you are creating a private offer, configure the offer details in the **Add custom offer** section\.

   1. In the **Subscriber account information** section, add at least one subscriber account to which you want to extend the offer\.

   1. Choose your **Pricing and access duration** options for the subscription\.

   1. Choose the **Offer expiration date** by which the subscriber must accept the offer\.

   1. Choose your US sales tax settings, data subscription agreement \(DSA\), and refund policy\.

   1. Choose your **Oﬀer auto\-renewal** option\. For more information, see [Creating an offer for AWS Data Exchange products](prepare-offers.md)\.

   1. Choose **Next**\.

1. In the **Review & publish** section, review your product information and then expand the **Product page preview** to see how it will look after it’s published\.

1. If you're sure that you want to make the product and public offer visible and available to everyone, choose **Publish**\.

You've now completed the manual portion of publishing a data product with a public offer\. AWS Data Exchange prepares and publishes your product\. On the **Product overview** page, the status of your product is **Awaiting approval** and then changes to **Published** after it's published\.

#### Step 6: \(Optional\) Copy a product<a name="copy-api-product"></a>

After you have created your first product, you can copy its details and public offers to create a new product\.

**Note**  
You can copy a public, private, published, or unpublished product\. Custom oﬀers associated with the product will not be copied, but public oﬀers will be copied\.

**To copy a product**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **Publish data**, choose **Products**\.

1. From **Products**, choose the button next to the product you want to copy\.

1. Select the **Actions** dropdown, and then choose **Create copy**\.

1. Continue through the **Publish a new product** workflow, with details already filled in, based on the product you chose in Step 3\. For more information, see [Step 5: Publish a new product](#publish-products)\.
**Important**  
Beginning July 22, 2021, new and existing providers have the ability to automatically publish revisions to data sets\. All new products on AWS Data Exchange default to automatic revision publishing\. If you have created existing products on AWS Data Exchange before July 22, 2021, you need to migrate them to automatic revision publishing\.  
For more information, see [Migrating an existing product to automatic revision publishing](updating-products.md#migrate-product)\.  
If you are copying an existing product that you created before July 22, 2021, you will see two options under **Revision publishing**: **Automatically publish revisions** or **Manually publish revisions**\. We recommend that you choose the first option, to automatically publish revisions\.

## Publishing a product containing Amazon Redshift datasets<a name="publish-Redshift-product"></a>

### Overview<a name="publish-Redshift-product-overview"></a>

An Amazon Redshift data set contains AWS Data Exchange datashares for Amazon Redshift\. When customers subscribe to a product containing datashares, they are granted read\-only access to the tables, views, schemas, and user\-defined functions that a data provider adds to the datashare\.

As a data provider, you create an AWS Data Exchange for Amazon Redshift datashare in your cluster\. Then, you add to the datashare the schemas, tables, views, and user\-defined functions that you want the subscribers to access\. You then import the datashare to AWS Data Exchange, create a data set, add it to a product, and publish the product\. Subscribers are granted access to the datashare upon subscription\.

The subscriber's cluster must have an encrypted Amazon Redshift cluster running on an RA3 instance to query to Amazon Redshift data\. For more information, see the [Amazon Redshift Database Developer Guide](https://docs.aws.amazon.com/redshift/latest/dg/welcome.html)\.

After you have set up your Amazon Redshift datashare in Amazon Redshift, you can create a new Amazon Redshift data set in AWS Data Exchange\. You can then create a revision, and add Amazon Redshift datashare assets\. This allows requests to the AWS Data Exchange endpoint to proxy through to your Amazon Redshift datashare\. You can then add this data set to a product and add pricing\. Then, prospective subscribers can view your product and subscribe to it in the AWS Data Exchange catalog\.

The following topics describe the process of creating an Amazon Redshift data set and publishing a new product with Amazon Redshift data sets using the AWS Data Exchange console\. The process has the following steps:

**Topics**
+ [Step 1: Create an Amazon Redshift datashare asset](#create-RS-asset)
+ [Step 2: Create an Amazon Redshift data set](#create-RS-data-set)
+ [Step 3: Create a revision](#create-RS-revision)
+ [Step 4: Add Amazon Redshift datashare assets to a revision](#add-RS-assets)
+ [Step 5: Publish a new product containing Amazon Redshift data sets](#publish-RS-product)
+ [Step 6: \(Optional\) Copy a product](#copy-RS-product)

#### Step 1: Create an Amazon Redshift datashare asset<a name="create-RS-asset"></a>

Assets are the data in AWS Data Exchange\. For more information, see [Assets](data-sets.md#assets)\.

**To create an Amazon Redshift datashare asset**

1. Create a datashare within your Amazon Redshift cluster \(must be RA3 type and encrypted\)\. 

   For more information about how to create a datashare, see *Working with AWS Data Exchange datashares as a producer* in the [Amazon Redshift Database Developer Guide](https://docs.aws.amazon.com/redshift/latest/dg/welcome.html)\.
**Note**  
We recommend setting your datashare as publicly accessible\. If you do not, customers with publicly accessible clusters will not be able to consume your data\.

1. [Step 2: Create an Amazon Redshift data set](#create-RS-data-set)\.

#### Step 2: Create an Amazon Redshift data set<a name="create-RS-data-set"></a>

An Amazon Redshift data set includes AWS Data Exchange datashares for Amazon Redshift\. For more information, see [Amazon Redshift data set](data-sets.md#RS-data-set-type)\.

**To create an Amazon Redshift data set**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1.  On the left side navigation pane, under **Publish data**, choose **Owned data sets**\.

1. In **Owned data sets**, choose **Create data set** to open the **Data set creation steps** wizard\.

1. In **Select data set type**, choose **Amazon Redshift datashare**\.

1. In **Define data set**, enter a **Name** and **Description** for your data set\. For more information, see [Data set best practices](data-sets.md#data-set-best-practices)\. 

1. Under **Add tags – optional**, add tags\.

1. Choose **Create**\. 

#### Step 3: Create a revision<a name="create-RS-revision"></a>

In the following procedure, you create a revision after you’ve created a data set in the AWS Data Exchange console\. For more information, see [Revisions](data-sets.md#revisions)\.

**To create a revision**

1. On the **Data set overview** section of the data set details page:

   1. \(Optional\) Choose **Edit name** to edit information about your data set\.

   1. \(Optional\) Choose **Delete** to delete the data set\.

1. On the **Revisions and jobs** section, choose **Create revision**\.

1. Under **Define revision**, provide an optional comment for your revision that describes the purpose of the revision\. 

1. Under **Add tags – optional**, add tags associated with the resource\.

1. Choose **Create**\.

1. Review, edit, or delete your changes from the previous step\. 

#### Step 4: Add Amazon Redshift datashare assets to a revision<a name="add-RS-assets"></a>

 In the following procedure, you add Amazon Redshift datashare assets to a revision, and then finalize the revision in the AWS Data Exchange console\. For more information, see [Assets](data-sets.md#assets)\. 

**To add assets to the revision**

1. Under the **Amazon Redshift datashares** section of the data set details page, choose **Add datashares**\.

1. Under **AWS Data Exchange datashares for Amazon Redshift**, select the datashares and then choose **Add**\.
**Note**  
You can add up to 20 datashares to a revision\.

   A job is started to import your assets into your revision\.

1. After the job is finished, the **State** field in the **Jobs** section is updated to **Completed\.**

1. If you have more data to add, repeat Step 1\.

1. Under **Revision overview**, review your revision and its assets\. 

1. Choose **Finalize**\.

You have successfully finalized a revision for a data set\. 

You can [edit](#edit-revision) or [delete a revision](#delete-revision) before you add it to a product\. 

#### Step 5: Publish a new product containing Amazon Redshift data sets<a name="publish-RS-product"></a>

After you've created at least one data set and finalized a revision with assets, you're ready to publish a product with Amazon Redshift data sets\. For more information, see [Product details](product-details.md)\. Make sure that you have all required details about your product and offer\.

**To publish a new product containing Amazon Redshift data sets**

1. From the left navigation pane of the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange), under **Publish data**, choose **Products**\.

1. From **Products**, choose **Publish new product** to open the **Publish new product** wizard\.

1. In the **Product visibility** section, choose your product's **Product visibility options** and **Sensitive information** configuration, and then choose **Next**\. For more information, see [Product visibility](product-details.md#product-visibility) and [Sensitive categories of information](product-details.md#sensitive-information)\.

1. In the **Define product** section, enter information about your product, including name, logo, support contact, web address, categories, and descriptions, and then choose **Next**\. For more information, see [Product details](product-details.md)\.

1. In the **Add data** section, select the check box next to the data sets you want to add\.
**Note**  
The data sets you choose must have a finalized revision\. Data sets without finalized revisions won't be added\.

   1. Choose **Add selected**, and then scroll to **Selected data sets** to review your selection\.

   1. Scroll to **Select revision access rules**, choose the revision access rules that you want to set for data sets included in this product, and then choose **Next**\. For more details, see [Revision access rules](product-details.md#best-practices-revisions)\.

1. If you are creating a public offer, in the **Add public offer** section, configure your offer\. All AWS Data Exchange products with visibility set to **Public** require a public offer\. 

   1. Choose your price and subscription durations, US sales tax settings, data subscription agreement, and refund policy\. For more information, see [Creating an offer for AWS Data Exchange products](prepare-offers.md)\.

   1. \(Optional\) Set **Subscription verification**, which enables you to control who can subscribe to this product\. For more information, see [Subscription verification for providers](subscription-verification-pro.md)\.

   1. Choose your **Oﬀer auto\-renewal** option\. For more information, see [Creating an offer for AWS Data Exchange products](prepare-offers.md)\.

   1. Choose **Next**\.

1. If you are creating a private offer, configure the offer details in the **Add custom offer** section\.

   1. In the **Subscriber account information** section, add at least one subscriber account to which you want to extend the offer\.

   1. Choose your **Pricing and access duration** options for the subscription\.

   1. Choose the **Offer expiration date** by which the subscriber must accept the offer\.

   1. Choose your US sales tax settings, data subscription agreement \(DSA\), and refund policy\.

   1. Choose your **Oﬀer auto\-renewal** option\. For more information, see [Creating an offer for AWS Data Exchange products](prepare-offers.md)\.

   1. Choose **Next**\.

1. In the **Review & publish** section, review your product information and then expand the **Product page preview** to see how it will look after it’s published\.

1. If you're sure that you want to make the product and public offer visible and available to everyone, choose **Publish**\.

You've now completed the manual portion of publishing a data product with a public offer\. AWS Data Exchange prepares and publishes your product\. On the **Product overview** page, the status of your product is **Awaiting approval** and then changes to **Published** after it's published\.

#### Step 6: \(Optional\) Copy a product<a name="copy-RS-product"></a>

After you have created your first product, you can copy its details and public offers to create a new product\.

**Note**  
You can copy a public, private, published, or unpublished product\. Custom oﬀers associated with the product will not be copied, but public oﬀers will be copied\.

**To copy a product**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **Publish data**, choose **Products**\.

1. From **Products**, choose the button next to the product you want to copy\.

1. Select the **Actions** dropdown, and then choose **Create copy**\.

1. Continue through the **Publish a product** workflow, with details already filled in, based on the product you chose in Step 3\. For more information, see [Step 5: Publish a new product](#publish-products)\.