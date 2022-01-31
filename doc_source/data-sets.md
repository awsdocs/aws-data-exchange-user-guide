# Data in AWS Data Exchange<a name="data-sets"></a>

Data is organized in AWS Data Exchange using three building blocks: 
+ **[Assets](#assets)** – A piece of data 
+ **[Revisions](#revisions)** – A container for one or more assets 
+ **[Data sets](#data-sets-concept)** – A series of one or more revisions 

These three building blocks form the foundation of the product that you manage using the AWS Data Exchange console or the AWS Data Exchange API\.

To create, view, update, or delete data sets, you can use the AWS Data Exchange console, the AWS Command Line Interface \(AWS CLI\), your own REST client, or one of the AWS SDKs\. For more information about programmatically managing AWS Data Exchange data sets, see the [AWS Data Exchange API Reference](https://docs.aws.amazon.com/data-exchange/latest/apireference)\.

## Assets<a name="assets"></a>

Assets are the *data* in AWS Data Exchange\. 

The type of asset defines how the data is delivered to the subscriber through the data sets and products that contain it\.

An asset can be any of the following:
+ A file stored on your local computer
+ A file stored as an object in Amazon Simple Storage Service \(Amazon S3\)
+ A REST API created in Amazon API Gateway
+ An Amazon Redshift data set

### Asset structure<a name="assets-structure"></a>

Assets have the following parameters:
+ `DataSetId` – The ID of the data set that contains this asset\.
+ `RevisionId` – The ID of the revision that contains this asset\.
+ `Id` – A unique ID generated when the asset is created\. 
+ `Arn` – A unique identifier for an AWS resource name\.
+ `CreatedAt` and `UpdatedAt` – Date and timestamps for the creation and last update of the asset\.
+ `AssetDetails` – Information about the asset\.
+ `AssetType` – Either a snapshot of an Amazon S3 object, an Amazon API Gateway API, or an Amazon Redshift data set\.

**Example asset resource**  

```
{
    "Name": "automation/cloudformation.yaml",
    "Arn": "arn:aws:dataexchange:us-east-1::data-sets/29EXAMPLE24b82c6858af3cEXAMPLEcf/revisions/bbEXAMPLE74c02f4745c660EXAMPLE20/assets/baEXAMPLE660c9fe7267966EXAMPLEf5",
    "Id": "baEXAMPLE660c9fe7267966EXAMPLEf5",
    "CreatedAt": "2019-10-17T21:31:29.833Z",
    "UpdatedAt": "2019-10-17T21:31:29.833Z",
    "AssetType": "S3_SNAPSHOT",
    "RevisionId": "bbEXAMPLE74c02f4745c660EXAMPLE20",
    "DataSetId": "29EXAMPLE24b82c6858af3cEXAMPLEcf",
    "AssetDetails": {
        "S3SnapshotAsset": {
            "Size": 9423
        }
    }
}
```

### Asset types<a name="asset-types"></a>

#### Amazon S3 object assets<a name="asset-types.title"></a>

With S3 object assets, subscribers can access a copy of the data set as an entitled data set and export the assets\.

A provider \(data set owner\) can both import and export Amazon S3 object assets using the AWS Data Exchange console, programmatically through the AWS CLI, their own REST application, or one of the AWS SDKs\. For more information, about importing S3 assets see [Importing assets from an S3 bucket](jobs.md#importing-from-s3)\. For more information about exporting assets, see [Exporting assets to an S3 bucket](jobs.md#exporting-from-s3)\.

#### API assets<a name="API-asset-type"></a>

With API assets, subscribers can view the API and download the API specification as an entitled data set\. Subscribers can also make API calls to AWS Data Exchange\-managed endpoints, which are then proxied through to provider endpoints\.

A provider \(data set owner\) who has existing Amazon API Gateway API can add an API asset using the AWS Data Exchange console, programmatically through the AWS CLI, or one of the AWS SDKs\. For more information about importing API assets, see [Importing assets from an Amazon API Gateway API](jobs.md#import-API-asset)\.

**Note**  
Currently, the `SendApiAsset` operation is not supported for the following SDKs:  
AWS SDK for \.NET
AWS SDK for C\+\+
SDK for Java 2\.x

Providers who do not have an existing Amazon API Gateway API must create one before adding an API asset to their product\. For more information, see [Developing a REST API in API Gateway](https://docs.aws.amazon.com/apigateway/latest/developerguide/rest-api-develop.html) in the *Amazon API Gateway Developer Guide*\.

#### Amazon Redshift datashare assets<a name="RS-asset-type"></a>

 With Amazon Redshift datashare assets, subscribers can get read\-only access to query the data in Amazon Redshift without extracting, transforming, and loading data\. 

 For more information about importing Amazon Redshift datashare assets, see [Importing assets from an AWS Data Exchange datashare for Amazon Redshift](jobs.md#import-RS-asset)\.

## Revisions<a name="revisions"></a>

A revision is a *container* for one or more assets\. 

You use revisions to update data in Amazon S3\. For example, you can group a collection of \.csv ﬁles or a single \.csv ﬁle and a dictionary to create a revision\. As new data is available, you create revisions and add assets\. After you create and finalize the revision using the AWS Data Exchange console, that revision will be immediately available to subscribers\. For more information, see [Publishing a new product](publishing-products.md)\.

**Important**  
Beginning July 22, 2021, new and existing providers have the ability to automatically publish revisions to data sets\. All new products on AWS Data Exchange default to automatic revision publishing\. If you have created existing products on AWS Data Exchange before July 22, 2021, you need to migrate them to automatic revision publishing\.  
For more information, see [Migrating an existing product to automatic revision publishing](updating-products.md#migrate-product)\.

**Note**  
If you are an existing provider and have not yet migrated all of your products to automatic revision publishing, you can create, add, and publish revisions using the AWS Data Exchange console or the AWS Marketplace Catalog API\.  
If you choose the API, use the [StartChangeSet](https://docs.aws.amazon.com/marketplace-catalog/latest/api-reference/API_StartChangeSet.html) AWS Marketplace Catalog API operation\. Revisions are uniquely identified by their Amazon Resource Name \(ARN\)\. For more information, see [Using AWS Data Exchange with the AWS Marketplace Catalog API](appendices.md)\.

Keep the following in mind:
+ To be finalized, a revision must contain at least one asset\.
+ It is your responsibility to ensure that the assets are correct before you finalize your revision\.
+ A finalized revision published to at least one product cannot be unfinalized or changed in any way\.
+ After the revision is ﬁnalized, it is automatically published to your products\.

### Revision structure<a name="revisions-structure"></a>

Revisions have the following parameters:
+ `DataSetId` – The ID of the data set that contains this revision\.
+ `Comment` – A comment about the revision\. This field can be 128 characters long\. 
+ `Finalized` – Either true or false\. Used to indicate whether the revision is finalized\.
+ `Id` – The unique identifier for the revision generated when it's created\.
+ `Arn` – A unique identifier for an AWS resource name\.
+ `CreatedAt` and `UpdatedAt` – Date and timestamps for the creation and last update of the revision\. Entitled revisions are created at the time of publishing\.

**Example revision resource**  

```
        {
            "UpdatedAt": "2019-10-11T14:13:31.749Z",
            "DataSetId": "1EXAMPLE404460dc9b005a0d9EXAMPLE2f",
            "Comment": "initial data revision",
            "Finalized": true,
            "Id": "e5EXAMPLE224f879066f9999EXAMPLE42",
            "Arn": "arn:aws:dataexchange:us-east-1:123456789012:data-sets/1EXAMPLE404460dc9b005a0d9EXAMPLE2f/revisions/e5EXAMPLE224f879066f9999EXAMPLE42",
            "CreatedAt": "2019-10-11T14:11:58.064Z"
        }
```

## Data sets<a name="data-sets-concept"></a>

A data set in AWS Data Exchange is a *collection* of data that can change over time\. 

When subscribers access an Amazon S3 data set, they're accessing a speciﬁc revision in the data set\. This structure enables providers to change the data available in data sets over time without having to worry about changes to historical data\.

When subscribers access an API data set, they're accessing a data set that contains API assets, which enable subscribers to make API calls to AWS Data Exchange\-managed endpoints, which are then proxied through to provider endpoints\.

When subscribers access an Amazon Redshift data set, they're accessing an AWS Data Exchange datashare for Amazon Redshift\. This datashare gives subscribers read\-only access to the schemas, tables, views, and user\-defined functions that the provider has added to the datashares\. 

To create, view, update, or delete data sets, providers can use the AWS Data Exchange console, AWS CLI, your own REST client, or one of the AWS SDKs\. For more information about programmatically managing AWS Data Exchange data sets, see the [AWS Data Exchange API Reference](https://docs.aws.amazon.com/data-exchange/latest/apireference/welcome.html)\.

**Topics**
+ [Owned data sets](#owned-data-sets)
+ [Entitled data sets](#entitled-data-sets)
+ [Data set types](#data-set-types)
+ [AWS Regions and data sets](#data-set-regions)
+ [Data set structure](#data-set-structure)
+ [Data set best practices](#data-set-best-practices)

### Owned data sets<a name="owned-data-sets"></a>

A data set is owned by the account that created it\. Owned data sets can be identified using the `origin` parameter, which is set to `OWNED`\.

### Entitled data sets<a name="entitled-data-sets"></a>

Entitled data sets are a read\-only view of a provider's owned data sets\. Entitled data sets are created at time of product publishing and are made available to subscribers who have an active subscription to the product\. Entitled data sets can be identified using the `origin` parameter, which is set to `ENTITLED`\.

As a data subscriber, you can view and interact with your entitled data sets using the AWS Data Exchange API or in the AWS Data Exchange console\.

As a data provider, you also have access to the entitled data set view that your subscribers see\. You can do so using the AWS Data Exchange API, or by choosing the data set name in the product page in the AWS Data Exchange console\.

### Data set types<a name="data-set-types"></a>

The following data set types are supported in AWS Data Exchange: 
+ [Amazon S3 object data set](#S3-object-data-set-type)
+ [API data set](#api-data-set-type)
+ [Amazon Redshift data set](#RS-data-set-type)

#### Amazon S3 object data set<a name="S3-object-data-set-type"></a>

An Amazon S3 object data set is a data set that contains flat files permitted by Amazon S3\.

As a data subscriber, you can export data either locally \(download to your computer\) or to your Amazon S3 bucket\.

As a data provider, you can import any type of flat file from your Amazon S3 bucket and add it to the data set\.

#### API data set<a name="api-data-set-type"></a>

An API data set is data set that contains API assets\. API assets enable subscribers to make API calls to AWS Data Exchange\-managed endpoints, which are then proxied through to provider endpoints\.

As a data provider, you create an API in Amazon API Gateway and add it to the data set to license access to your API upon subscription\.

#### Amazon Redshift data set<a name="RS-data-set-type"></a>

An Amazon Redshift data set includes AWS Data Exchange datashares for Amazon Redshift\. When you subscribe to a data set with datashares, you are added as a consumer of the datashare\. This gives you read\-only access to the schemas, tables, views, and user\-defined functions the provider has added to the datashares\.

As a data subscriber, you can create a database from the datashare in Amazon Redshift and then query live data without extracting, transforming, and loading files\. You are automatically granted access to the datashare when your subscription is activated and lose access after your subscription expires\.

As a data provider, you create a datashare in Amazon Redshift and add it to the data set to license access to your datashare upon subscription\.

### AWS Regions and data sets<a name="data-set-regions"></a>

Your data sets can be in any supported AWS Region, but all data sets in a single product must be in the same AWS Region\.

### Data set structure<a name="data-set-structure"></a>

Data sets have the following parameters:
+ `Name` – The name of the data set\. This value can be up to 256 characters long\.
+ `Description` – A description for the data set\. This value can be up to 16,348 characters long\.
+ `AssetType` – Defines the type of assets the data set contains\.
+ `Origin` – A property that defines the data set as `Owned` by the account \(for providers\) or `Entitled` to the account \(for subscribers\)\. 
+ `Id` – An ID that uniquely identifies the data set\. Data set IDs are generated at data set creation\. Entitled data sets have a different ID than the original owned data set\.
+ `Arn` – A unique identifier for an AWS resource name\.
+ `CreatedAt` and `UpdatedAt` – Date and timestamps for the creation and last update of the data set\.

**Note**  
As a provider, you can change some properties for owned data sets, like the **Name** or **Description**\. Updating properties in an owned data set won't update the properties in the corresponding entitled data set\.

**Example data set resource**  

```
{
    "Origin": "OWNED", 
    "AssetType": "S3_SNAPSHOT", 
    "Name": "MyDataSetName", 
    "CreatedAt": "2019-09-09T19:31:49.704Z", 
    "UpdatedAt": "2019-09-09T19:31:49.704Z", 
    "Id": "fEXAMPLE1fd9a5c8b0d2e6fEXAMPLEe1", 
    "Arn": "arn:aws:dataexchange:us-east-2:123456789109:data-sets/fEXAMPLE1fd9a5c8b0d2e6fEXAMPLEe1", 
    "Description": "This is my data set's description that describes the contents of the data set."
}
```

### Data set best practices<a name="data-set-best-practices"></a>

As a provider, when you create and update data sets, keep the following best practices in mind:
+ The name of the data set is visible in the product details in the catalog\. We recommend that you choose a concise, descriptive name so customers easily understand the content of the data set\.
+ The description is visible to subscribers who have an active subscription to the product\. We recommend that you include coverage information and the features and benefits of the data set\.

## Tags<a name="data-set-tags"></a>

You can add tags to your owned data sets and their revisions\. When you use tagging, you can also use tag\-based access control in AWS Identity and Access Management \(IAM\) policies to control access to these data sets and revisions\.

Entitled data sets can't be tagged\. Tags of owned data sets and their revisions are not propagated to their corresponding entitled versions\. Specifically, subscribers, who have read\-only access to entitled data sets and revisions, won't see the tags of the original owned data set\.

**Note**  
Currently, assets and jobs don't support tagging\.