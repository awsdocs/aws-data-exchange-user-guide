# Jobs in AWS Data Exchange<a name="jobs"></a>

AWS Data Exchange jobs are asynchronous import or export operations\. 

As a provider, you can create and manage your data sets that you want to publish to a product\. You can download \(export\) or copy your assets or revisions to Amazon Simple Storage Service \(Amazon S3\) or a signed URL\. In addition, providers can import assets from an Amazon API Gateway API or import assets from an Amazon Redshift data set\.

As a subscriber, you can view and access the data sets that you have an entitlement to through a subscription\. You can use the API operations to download \(export\) or copy your entitled data sets to Amazon S3 for use with a variety of AWS analytics and machine learning services\.

To create or copy assets or copy revisions through jobs, you can use the AWS Management Console, AWS Command Line Interface \(AWS CLI\), your own REST application, or one of the AWS SDKs\.

Jobs are deleted 90 days after they are created\.

**Topics**
+ [Job properties](#job-properties)
+ [AWS Regions and jobs](#jobs-regions)
+ [Importing assets](#importing-assets)
+ [Exporting assets](#exporting-assets)
+ [Exporting revisions](#exporting-revisions)
+ [Key patterns when exporting revisions](#revision-export-keypatterns)

## Job properties<a name="job-properties"></a>

Jobs have the following properties:
+ **Job ID** – An ID generated when the job is created that uniquely identifies the job\. 
+ **Job type** – The following job types are supported: 
  + Import from Amazon Simple Storage Service \(Amazon S3\)
  + Import from signed URL
  + Import from Amazon API Gateway API
  + Import from an AWS Data Exchange datashare for Amazon Redshift
  + Export from Amazon S3
  + Export from signed URL
+ **Amazon Resource Name \(ARN\)** – A unique identifier for AWS resources\.
+ **Job state** – The job states are `WAITING`, `IN_PROGRESS`, `COMPLETED`, `CANCELLED`, `ERROR`, or `TIMED_OUT`\. When a job is created, it's in the `WAITING` state until the job is started\.
+ **Job details** – Details of the operation to be performed by the job, such as export destination details or import source details\.

**Example job resource**  

```
{
    "Arn": "arn:aws:dataexchange:us-east-1:123456789012:jobs/6cEXAMPLE818f7c7a23b3d0EXAMPLE1c",
    "Id": "6cEXAMPLE818f7c7a23b3d0EXAMPLE1c",
    "State": "COMPLETED",
    "Type": "IMPORT_ASSETS_FROM_S3",
    "CreatedAt": "2019-10-11T14:12:24.640Z",
    "UpdatedAt": "2019-10-11T14:13:00.804Z",
    "Details": {
        "ImportAssetsFromS3": {
            "AssetSources": [
                {
                    "Bucket": "DOC-EXAMPLE-BUCKET",
                    "Key": "MyKey"
                }
            ],
            "DataSetId": "14EXAMPLE4460dc9b005a0dEXAMPLE2f",
            "RevisionId": "e5EXAMPLE224f879066f999EXAMPLE42"
        }
    }
}
```

## AWS Regions and jobs<a name="jobs-regions"></a>

If you import or export an asset to or from an Amazon S3 bucket that is in an AWS Region that is different than the data set's Region, your AWS account is charged for the data transfer costs, according to Amazon S3 data transfer pricing policies\. 

If you export assets to a signed URL, your AWS account is charged for data transfer costs from Amazon S3 to the internet according to [Amazon S3 pricing policies](https://aws.amazon.com/s3/pricing/)\.

## Importing assets<a name="importing-assets"></a>

You can import assets to a revision in the following ways:

**Topics**
+ [Importing assets from an S3 bucket](#importing-from-s3)
+ [Importing assets from a signed URL](#importing-from-url)
+ [Importing assets from an Amazon API Gateway API](#import-API-asset)
+ [Importing assets from an AWS Data Exchange datashare for Amazon Redshift](#import-RS-asset)

### Importing assets from an S3 bucket<a name="importing-from-s3"></a>

When you import assets from Amazon S3 to AWS Data Exchange, the AWS Identity and Access Management \(IAM\) permissions you use must include the ability to write to the AWS Data Exchange service S3 buckets and to read from the S3 bucket where your assets are stored\. You can import from any S3 bucket you have permission to access, regardless of ownership\. For more information, see [Amazon S3 permissions](access-control.md#additional-s3-permissions)\.

You can import up to 100 assets in a single job\.

**Topics**
+ [Importing assets from an S3 bucket \(AWS SDKs\)](#import-assets-s3-prog)
+ [Importing assets from an S3 bucket \(console\)](#import-assets-via-console)

#### Importing assets from an S3 bucket \(AWS SDKs\)<a name="import-assets-s3-prog"></a>

**To import assets from an Amazon S3 bucket \(AWS SDKs\)**

1. Create a `CreateJob` request of type `IMPORT_ASSETS_FROM_S3`\. 

1. Include the following in the request:
   + `AssetSources`
     + `Bucket`
     + `Key`
   + `DataSetID`
   + `RevisionID`

1. Start the `CreateJob` request with a `StartJob` operation that requires the `JobId` returned in step 1\.

1. \(Optional\) Update the assets' name property after they are created\.

#### Importing assets from an S3 bucket \(console\)<a name="import-assets-via-console"></a>

**To import an asset from an S3 bucket \(console\)**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. In the left side navigation pane, for **Publish data**, choose **Owned data sets**\.

1. In **Owned data sets**, choose the data set that has the revision you want to update\.

1. On the **Revisions** tab, choose **Create revision** to open the **Create revision** page\.

   1. For **Revision settings**, provide an optional comment for your revision that describes the purpose of the revision\.

   1. For **Add tags – optional**, add tags associated with the resource\.

   1. Choose **Create**\.

      Your new revision is created\.

1. For the **Jobs** section, choose **Import from Amazon S3**\.

1. Follow the prompts in the **Import from Amazon S3** window, and then choose **Import assets**\. 

   A job is started to import your asset into your data set\. After the job is ﬁnished, the **State** ﬁeld in the **Jobs** section is updated to **Completed**\.

### Importing assets from a signed URL<a name="importing-from-url"></a>

You can use signed URLs to import assets that are not stored in Amazon S3\. 

**Topics**
+ [Importing assets from a signed URL \(AWS SDKs\)](#import-asset-signed-url-prog)
+ [Importing assets from a signed URL \(console\)](#import-asset-signed-url-via-console)

#### Importing assets from a signed URL \(AWS SDKs\)<a name="import-asset-signed-url-prog"></a>

**To import assets from a signed URL \(AWS SDKs\)**

1. Create a `CreateJob` request of type `IMPORT_ASSET_FROM_SIGNED_URL`\.

1. Include the following in the request:
   + `AssetName`
   + `DataSetID`
   + `Md5Hash`
   + `RevisionID`

1. Start the `CreateJob` request with a `StartJob` operation that requires the `JobId` returned in step 1\.

1. \(Optional\) Update the assets' name property after they are created\.

1. Note that the response details include the `SignedUrl` that you can use to import your file\. 

**Note**  
The signed URL expires one hour after it's created\.

#### Importing assets from a signed URL \(console\)<a name="import-asset-signed-url-via-console"></a>

**To import an asset from a signed URL \(console\)**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. In the left side navigation pane, for **Publish data**, choose **Owned data sets**\.

1. In **Owned data sets**, choose the data set that has the asset you want to update\.

1. On the **Revisions** tab, choose **Create revision** to open the **Create revision** page\.

   1. For **Revision settings**, provide an optional comment for your revision that describes the purpose of the revision\.

   1. For **Add tags – optional**, add tags associated with the resource\.

   1. Choose **Create**\.

      Your new revision is created\.

1. For the **Jobs** section, choose **Upload**\.

1. Follow the prompts in the upload window, and then choose **Open**\.

   A job is started to import your asset into your data set\. After the job is ﬁnished, the **State** ﬁeld in the **Jobs** section is updated to **Completed**\.

### Importing assets from an Amazon API Gateway API<a name="import-API-asset"></a>

When you import assets from Amazon API Gateway to AWS Data Exchange, the AWS Identity and Access Management \(IAM\) permissions you use must include the ability to write to the AWS Data Exchange service S3 buckets and to read from the S3 bucket where your assets are stored\. 

#### Importing API assets from an Amazon API Gateway API \(AWS SDKs\)<a name="import-api-asset-prog"></a>

**Note**  
Currently, the `SendApiAsset` operation is not supported for the following SDKs:  
AWS SDK for \.NET
AWS SDK for C\+\+
AWS SDK for Java 2\.x

**To import assets from an Amazon API Gateway API \(AWS SDKs\)**

1. Create a `CreateJob` request of type `IMPORT_ASSET_FROM_API_GATEWAY_API`\.

1. Include the following in the request:
   + `ApiID`
   + `DataSetID`
   + `ProtocolType`
   + `RevisionID`
   + `Stage`

1. Start the `CreateJob` request with a `StartJob` operation that requires the `JobId` returned in step 1\.

1. \(Optional\) Poll the `GetJob` operation to wait for the Job to complete\.

1. \(Optional\) Update the assets' name property after they are created\.

#### Importing API assets from an Amazon API Gateway API \(console\)<a name="import-api-asset-console"></a>

**To import an asset from an Amazon API Gateway API \(console\)**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. In the left side navigation pane, for **Publish data**, choose **Owned data sets**\.

1. In **Owned data sets**, choose the data set that has the asset you want to update\.

1. On the **Revisions** tab, choose **Create revision** to open the **Create revision** page\.

   1. For **Revision settings**, provide an optional comment for your revision that describes the purpose of the revision\.

   1. For **Add tags – optional**, add tags associated with the resource\.

   1. Choose **Create**\.

      Your new revision is created\.

1. For the **API assets** section, choose **Add API stage**\.

1. On the **Add API stage** page, select the **Amazon API Gateway API** and the **Stage name** from your AWS account or another account\.

1. For **Document API for subscribers**:

   1. Update the **API name** to a clear and concise name that subscribers can understand\.

   1. Document the OpenAPI 3\.0 specification by entering the specification in the field, importing the specification by choosing **Import from \.JSON file**, or importing the specification by choosing **Import from Amazon API Gateway**\.

1. Choose **Add API stage**\.

   A job is started to import your API assets into your data set\. After the job is ﬁnished, the **State** ﬁeld in the **Jobs** section is updated to **Completed**\.

### Importing assets from an AWS Data Exchange datashare for Amazon Redshift<a name="import-RS-asset"></a>

#### Importing assets from an AWS Data Exchange datashare for Amazon Redshift \(AWS SDKs\)<a name="import-RS-asset-prog"></a>

**To import assets from an AWS Data Exchange datashare for Amazon Redshift \(AWS SDKs\)**

1. Create a `CreateJob` request of type `IMPORT_ASSETS_FROM_REDSHIFT_DATA_SHARES`\.

1. Include the following in the request:
   + `AssetSources`
     + `DataShareArn`
   + `DataSetID`
   + `RevisionID`

1. Start the `CreateJob` request with a `StartJob` operation that requires the `JobId` returned in step 1\.

1. \(Optional\) Poll the `GetJob` operation to wait for the Job to complete\.

1. \(Optional\) Update the assets' name property after they are created\.

#### Importing assets from an AWS Data Exchange datashare for Amazon Redshift \(console\)<a name="import-RS-asset-console"></a>

**To import an asset from an ADE datashare \(for Amazon Redshift console\)**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. In the left side navigation pane, for **Publish data**, choose **Owned data sets**\.

1. In **Owned data sets**, choose the data set that has the asset you want to update\.

1. On the **Revisions** tab, choose **Create revision** to open the **Create revision** page\.

   1. For **Revision settings**, provide an optional comment for your revision that describes the purpose of the revision\.

   1. For **Add tags – optional**, add tags associated with the resource\.

   1. Choose **Create**\.

      Your new revision is created\.

1. For the **AWS Data Exchange datashares for Amazon Redshift** section, choose **Add datashares**\.

1. On the **Add AWS Data Exchange datashare to revision** page, select the datashare or datashares that you want to add\.

1. Choose **Add datashare\(s\)**\.

   A job is started to import your assets into your data set\. After the job is ﬁnished, the **State** ﬁeld in the **Jobs** section is updated to **Completed**\.

## Exporting assets<a name="exporting-assets"></a>

Both providers and subscribers can export assets from a published revision of a product\. There are two ways you can export assets:

**Topics**
+ [Exporting assets to an S3 bucket](#exporting-from-s3)
+ [Exporting assets to a signed URL](#Exporting-from-url)

### Exporting assets to an S3 bucket<a name="exporting-from-s3"></a>

When you export assets to Amazon S3, the IAM permissions you use must include the ability to read from the AWS Data Exchange service S3 buckets and to write to the S3 bucket where your assets are stored\. You can export to any S3 bucket you have permission to access, regardless of ownership\. For more information, see [Amazon S3 permissions](access-control.md#additional-s3-permissions)\.

AWS Data Exchange supports configurable encryption parameters when exporting data sets to Amazon S3\. In your export job details, you can specify the Amazon S3 server\-side encryption configuration you want to apply to the exported objects\. You can choose to use server\-side encryption with Amazon S3\-Managed Keys \(SSE\-S3\) or server\-side encryption with AWS KMS keys stored in AWS Key Management Service \(SSE\-KMS\)\. For more information, see [Protecting data using server\-side encryption](https://docs.aws.amazon.com/AmazonS3/latest/dev/serv-side-encryption.html) in the *Amazon Simple Storage Service User Guide*\. 

**Important**  
We recommend that you consider Amazon S3 security features when exporting data to Amazon S3\. See [Security best practices for Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/dev/security-best-practices.html) for general guidelines and best practices\.

**Important**  
If the provider has marked a product as containing protected health information \(PHI\) subject to the Health Insurance Portability and Accountability Act of 1996 \(HIPAA\), you may not export the product's data sets into your AWS account unless such AWS account is designated as a HIPAA account \(as defined in the AWS Business Associate Addendum found in [AWS Artifact](https://docs.aws.amazon.com/artifact/latest/ug/what-is-aws-artifact.html)\)\.

You can export up to 100 assets in a single job\.

**Topics**
+ [Exporting assets to an S3 bucket \(AWS SDKs\)](#export-assets-s3-prog)
+ [Exporting assets to an S3 bucket as a subscriber \(console\)](#export-asset-s3-console-sub)
+ [Exporting assets to an S3 bucket as a provider \(console\)](#export-asset-s3-console-prov)

#### Exporting assets to an S3 bucket \(AWS SDKs\)<a name="export-assets-s3-prog"></a>

**To export assets to an S3 bucket \(AWS SDKs\)**

1. Create a `CreateJob` request of type `EXPORT_ASSETS_TO_S3`\.

1. Include the following in the request:
   + `AssetDestinations`
     + `AssetID`
     + `Bucket`
     + `Key`
   + `DataSetID`
   + `Encryption`
     + `KmsKeyArn`
     + `Type`
   + `RevisionID`

1. Start the `CreateJob` request with a `StartJob` operation that requires the `JobId` returned in step 1\.

1. \(Optional\) Update the assets' name property after they are created\.

**Note**  
For information about exporting an entire revision as a single job, see [Exporting revisions](#exporting-revisions)\.

#### Exporting assets to an S3 bucket as a subscriber \(console\)<a name="export-asset-s3-console-sub"></a>

**To export an asset to an S3 bucket as a subscriber \(console\)**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. In the left side navigation pane, for **My subscriptions**, choose **Entitled data**\.

1. In **Entitled data**, choose the product that has the revision you want to export\.

1. In **Entitled data sets**, choose the data set\.

1. On the **Revisions** tab, choose the revision\.

1. From the **Assets** tab, select the check box next to the assets that you want to export\.

1. Select **Export actions** and then choose **Export selected assets to Amazon S3**\.

1. Follow the prompts in the **Export to Amazon S3** window and then choose **Export**\. 

   A job is started to export your asset\. After the job is ﬁnished, the **State** ﬁeld in the **Jobs** section is updated to **Completed**\.

#### Exporting assets to an S3 bucket as a provider \(console\)<a name="export-asset-s3-console-prov"></a>

**To export an asset to an S3 bucket as a provider \(console\)**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. In the left side navigation pane, for **Publish data**, choose **Owned data sets**\.

1. In **Owned data sets**, choose the data set that has the asset you want to export\.

1. Navigate to the **Products** tab to make sure that the data set is associated with a published product\.

1. From the **Revisions** tab, select the revision\.

1. For the **Imported assets** section, select the check box next to the asset name\.

1. Select **Export actions** and then choose **Export selected assets to Amazon S3**\.

1. Follow the prompts in the **Export to Amazon S3** window and then choose **Export**\. 

   A job is started to export your asset\. After the job is ﬁnished, the **State** ﬁeld in the **Jobs** section is updated to **Completed**\.

### Exporting assets to a signed URL<a name="Exporting-from-url"></a>

You can use signed URLs to export assets that are not stored in Amazon S3\. 

**Topics**
+ [Exporting assets to a signed URL \(AWS SDKs\)](#export-asset-URL-prog)
+ [Exporting assets to a signed URL as a subscriber \(console\)](#export-asset-url-sub)
+ [Exporting assets to a signed URL as a provider \(console\)](#export-asset-URL-console-pro)

#### Exporting assets to a signed URL \(AWS SDKs\)<a name="export-asset-URL-prog"></a>

You can use signed URLs to export assets to destinations other than S3 buckets\. 

**To export assets to a signed URL \(AWS SDKs\)**

1. Create a `CreateJob` request of type `EXPORT_ASSET_TO_SIGNED_URL`\.

1. Include the following in the request:
   + `AssetID`
   + `DataSetID`
   + `RevisionID`

1. Start the `CreateJob` request with a `StartJob` operation that requires the `JobId` returned in step 1\.

1. \(Optional\) Update the assets' name property after they are created\.

1. Note that the response details include the `SignedUrl` that you can use to import your file\. 

**Note**  
The signed URL expires one hour after it's created\.

#### Exporting assets to a signed URL as a subscriber \(console\)<a name="export-asset-url-sub"></a>

**To export an asset to a signed URL as a subscriber \(console\)**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. In the left side navigation pane, for **My subscriptions**, choose **Entitled data**\.

1. In **Entitled data**, choose the product that has the revision you want to export\.

1. In **Entitled data sets**, choose the data set\.

1. On the **Revisions** tab, choose the revision\.

1. From the **Assets** tab, select the check box next to the assets that you want to export\.

1. Select **Export actions** and then choose **Download selected assets**\.

   A job is started to export your asset\. After the job is ﬁnished, the **State** ﬁeld in the **Jobs** section is updated to **Completed**\.

#### Exporting assets to a signed URL as a provider \(console\)<a name="export-asset-URL-console-pro"></a>

**To export an asset to a signed URL as a provider \(console\)**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. In the left side navigation pane, for **Publish data**, choose **Owned data sets**\.

1. In **Owned data sets**, choose the product that has the revision you want to export\.

1. Navigate to the **Products** tab to make sure that the data set is associated with a published product\.

1. On the **Revisions** tab, choose the revision\.

1. For the **Imported assets **section, select the check box next to the asset name\.

1. Select **Export actions** and then choose **Download selected assets**\.

   A job is started to export your asset\. After the job is ﬁnished, the **State** ﬁeld in the **Jobs** section is updated to **Completed**\.

## Exporting revisions<a name="exporting-revisions"></a>

Both providers and subscribers can export revisions of a data set to an S3 bucket that they have permissions to access\. 

AWS Data Exchange supports configurable encryption parameters when exporting revisions to Amazon S3\. In your export job details, you can specify the Amazon S3 server\-side encryption configuration you want to apply to the exported objects\. You can choose to use server\-side encryption with Amazon S3\-Managed Keys \(SSE\-S3\) or server\-side encryption with KMS keys stored in AWS Key Management Service \(SSE\-KMS\)\. For more information, see [Protecting data using server\-side encryption](https://docs.aws.amazon.com/AmazonS3/latest/dev/serv-side-encryption.html) in the *Amazon Simple Storage Service Developer Guide*\.

**Important**  
If the provider has marked a product as containing protected health information \(PHI\) subject to the Health Insurance Portability and Accountability Act of 1996 \(HIPAA\), you may not export the product's data sets into your AWS account unless such AWS account is designated as a HIPAA account \(as defined in the AWS Business Associate Addendum found in [AWS Artifact](https://docs.aws.amazon.com/artifact/latest/ug/what-is-aws-artifact.html)\)\.

**Topics**
+ [Exporting revisions to an S3 bucket \(AWS SDKs\)](#export-rev-s3-prog)
+ [Exporting revisions to an S3 bucket as a provider \(console\)](#export-rev-s3-console-pro)
+ [Exporting revisions to an S3 bucket as a subscriber \(console\)](#export-rev-s3-console-sub)
+ [Automatically exporting revisions to an S3 bucket as a subscriber](#auto-export-rev-s3-console-sub)

### Exporting revisions to an S3 bucket \(AWS SDKs\)<a name="export-rev-s3-prog"></a>

**To export a revision to an S3 bucket \(AWS SDKs\)**

1. Create a `CreateJob` request of type `EXPORT_REVISIONS_TO_S3`\. 

1. Include the following in the request:
   + `DataSetId`
   + `Encryption`
     + `KmsKeyArn`
     + `Type`
   + `RevisionDestinations`
     + `Bucket`
     + `KeyPattern`
     + `RevisionId`

1. Start the `CreateJob` request with a `StartJob` operation that requires the `JobId` returned in step 1\.

1. The newly created assets have a name property equal to the original S3 object's key\. The Amazon S3 object key defaults to the key pattern `${Asset.Name}`\. 

   You can update the assets' name property after they are created\.

   For more information about key patterns, see [Key patterns when exporting revisions](#revision-export-keypatterns)\.

### Exporting revisions to an S3 bucket as a provider \(console\)<a name="export-rev-s3-console-pro"></a>

**To export a revision to an S3 bucket as a provider \(console\)**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. In the left side navigation pane, for **Publish data**, choose **Owned data sets**\.

1. In **Owned data sets**, choose the product that has the revision you want to export\.

1. Navigate to the **Products** tab to make sure that the data set is associated with a published product\.

1. On the **Revisions** tab, choose the revision\.

1. For the **Imported assets **section, select the check box next to the asset name\.

1. Select **Export actions** and then choose **Export selected assets to Amazon S3**\.

1. Follow the prompts in the **Export to Amazon S3** window and then choose **Export**\.

   A job is started to export your asset\. After the job is ﬁnished, the **State** ﬁeld in the **Jobs** section is updated to **Completed**\.

### Exporting revisions to an S3 bucket as a subscriber \(console\)<a name="export-rev-s3-console-sub"></a>

**To export a revision to an S3 bucket as a subscriber \(console\)**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. In the left side navigation pane, for **My subscriptions**, choose **Entitled data**\.

1. In **Entitled data**, choose the product that has the revision you want to export\.

1. In **Entitled data sets**, choose the data set\.

1. On the **Revisions** tab, select the revision, and then choose **Export to Amazon S3**\.

1. In **Export revision to Amazon S3**, select a destination option, Amazon S3 bucket folder destination, configure encryption options, and then choose **Export**\.

   A job is started to export your revision\. After the job is ﬁnished, the **State** ﬁeld in the **Jobs** section is updated to **Completed**\.

### Automatically exporting revisions to an S3 bucket as a subscriber<a name="auto-export-rev-s3-console-sub"></a>

When the provider publishes new revisions, you can select to automatically export new revisions to your Amazon S3 bucket\. You can export new revisions to up to five S3 buckets\. New revisions will automatically appear in the S3 buckets you have selected\. 

**Topics**
+ [Prerequisites for S3 bucket policy permissions](#auto-export-rev-s3-bucket-policy-prereq)
+ [Automatically exporting revisions to an S3 bucket as a subscriber \(console\)](#auto-export-rev-s3-console-sub-proc)
+ [Automatically exporting revisions to an S3 bucket as a subscriber \(AWS SDKs\)](#auto-export-rev-s3-prog-sub)

**Note**  
To automatically export revisions to an S3 bucket of your choice, your S3 bucket must have a bucket policy with permissions set to allow AWS Data Exchange to export data into it\. For more information, see [Prerequisites for S3 bucket policy permissions](#auto-export-rev-s3-bucket-policy-prereq)\.

#### Prerequisites for S3 bucket policy permissions<a name="auto-export-rev-s3-bucket-policy-prereq"></a>

Before you can automatically export revisions to an S3 bucket, your S3 bucket must have a bucket policy with permissions set to allow AWS Data Exchange to export data into it\. The following procedures provide information about how to either edit your existing S3 bucket policy or create an S3 bucket policy with these permissions\.

**Topics**
+ [Editing an existing S3 bucket policy](#bucket-policy-prereq-existing-s3-bucket-policy)
+ [Creating an S3 bucket policy](#bucket-policy-prereq-create-s3-bucket-policy)

##### Editing an existing S3 bucket policy<a name="bucket-policy-prereq-existing-s3-bucket-policy"></a>

If your S3 bucket has a bucket policy, complete the following procedure to allow AWS Data Exchange to export data to it\.

**To edit an existing S3 bucket policy**

1. Navigate to the bucket to which you want to export revisions\.

1. Select the **Permissions** tab, and choose **Edit** in the bucket policy section\.

1. Copy the following statement and paste it at the end of the statement list\.

   ```
       {
         "Effect": "Allow",
         "Principal": {
         "Service": "dataexchange.amazonaws.com"
         },
         "Action": [
           "s3:PutObject",
           "s3:PutObjectAcl"
         ],
         "Resource": "arn:aws:s3:::<BUCKET-NAME>/*",
         "Condition": {
           "StringEquals": { 
             "aws:SourceAccount": "<AWS ID>"
           }
         }
       }
   ```

1. Replace `<BUCKET-NAME>` with the name of your S3 bucket and replace `<AWS ID>` with your AWS ID\.

1. Choose **Save changes**\.

1. If you want to add more buckets as a destination for your auto\-export jobs, repeat the procedure, starting from Step 1\.

##### Creating an S3 bucket policy<a name="bucket-policy-prereq-create-s3-bucket-policy"></a>

If your S3 bucket does not have a bucket policy, complete the following procedure to create an S3 bucket policy to allow AWS Data Exchange to export data to it\.

**To create an S3 bucket policy**

1. Navigate to the bucket to which you want to export revisions\.

1. Select the **Permissions** tab, and choose **Edit** in the bucket policy section\.

1. Copy the following full bucket policy and paste it into the bucket policy editor\.

   ```
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Effect": "Allow",
         "Principal": {
         "Service": "dataexchange.amazonaws.com"
         },
         "Action": [
           "s3:PutObject",
           "s3:PutObjectAcl"
         ],
         "Resource": "arn:aws:s3:::<BUCKET-NAME>/*",
         "Condition": {
           "StringEquals": { 
             "aws:SourceAccount": "<AWS ID>"
           }
         }
       }
     ]
   }
   ```

1. Replace `<BUCKET-NAME>` with the name of your S3 bucket and replace `<AWS ID>` with your AWS ID\.

1. Choose **Save changes**\.

1. If you want to add more buckets as a destination for your auto\-export jobs, repeat the procedure, starting from Step 1\.

#### Automatically exporting revisions to an S3 bucket as a subscriber \(console\)<a name="auto-export-rev-s3-console-sub-proc"></a>

**Note**  
To automatically export revisions to an S3 bucket of your choice, your S3 bucket must have a bucket policy with permissions set to allow AWS Data Exchange to export data into it\. For more information, see [Prerequisites for S3 bucket policy permissions](#auto-export-rev-s3-bucket-policy-prereq)\.

**To automatically export a revision to an S3 bucket as a subscriber \(console\)**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. In the left side navigation pane, for **My subscriptions**, choose **Entitled data**\.

1. In **Entitled data**, choose the product that has the revision you want to export\.

1. In **Entitled data sets**, choose the data set\.

1. On the **Revisions** tab, under **Auto\-export job destinations**, choose **Actions** and then choose **Add auto\-export job destination**\.

1. In **Add auto\-export job destination**, choose either the **Simple** or **Advanced** destination option\.

   1. If you choose the **Simple** option, select the Amazon S3 bucket folder destination from the dropdown list and the encryption options, and then choose **Add bucket destination**\.

   1. If you choose the **Advanced** option, select the Amazon S3 bucket folder destination from the dropdown list, select the [Key naming pattern](#revision-export-keypatterns) and append it to the path\.

1. Review the **Output**\.

1. Set the **Encryption options**, review the **Amazon S3 pricing**, and then choose **Add bucket destination**\.

   The Amazon S3 bucket destination appears on the **Revisions** tab under **Auto\-export job destinations**\.

   A job is started to automatically export your revision\. After the job is ﬁnished, the **State** ﬁeld in the **Jobs** section is updated to **Completed**\.

   To add another destination, choose **Actions**, and then **Add auto\-export job destination**\.

   To edit, select the destination you want to edit, choose **Actions**, and then **Edit destination configuration**\.

   To delete, choose **Actions**, and then choose **Remove auto\-export job destination**\.

#### Automatically exporting revisions to an S3 bucket as a subscriber \(AWS SDKs\)<a name="auto-export-rev-s3-prog-sub"></a>

**Note**  
To automatically export revisions to an S3 bucket of your choice, your S3 bucket must have a bucket policy with permissions set to allow AWS Data Exchange to export data into it\. For more information, see [Prerequisites for S3 bucket policy permissions](#auto-export-rev-s3-bucket-policy-prereq)\.

**To automatically export a revision to an S3 bucket \(AWS SDKs\)**

1. Create a `Create_Event_Action` request\. 

1. Include the following in the request:
   + `Action`
     + `ExportRevisionToS3`
       + `Encryption`
         + `KmsKeyArn`
         + `Type`
     + `RevisionDestination`
       + `Bucket`
       + `KeyPattern`
   + `Event`
     + `RevisionPublished`
       + `DataSetId`

1. The Amazon S3 object key defaults to the key pattern `{Revision.CreatedAt}/{Asset.Name}`\. 

   For more information about key patterns, see [Key patterns when exporting revisions](#revision-export-keypatterns)\.

## Key patterns when exporting revisions<a name="revision-export-keypatterns"></a>

When you export a revision, each asset becomes an object in the S3 bucket\. The names of the objects are based on a key pattern that you provide\. You can use dynamic references that represent asset attributes to create a pattern for the names that are automatically generated during the export\. Use the dynamic references shown in the following table\.


| Dynamic references | Description | 
| --- | --- | 
| $\{Asset\.Id\} | The Id of the asset\. | 
| $\{Asset\.Name\} | The name of the asset\. | 
| $\{Revision\.CreatedAt\} | The UTC date and time the revision was created, in the following format: YYYY\-MM\-DDTHH:MM:SSZ\. For example: 2021\-10\-08T16:33:19\.787Z | 
| $\{Revision\.CreatedAt\.Day\} | The day of the month the revision was created\. | 
| $\{Revision\.CreatedAt\.Month\} | The month the revision was created\. | 
| $\{Revision\.CreatedAt\.Year\} | The year the revision was created\. | 
| $\{Revision\.Id\} | The Id of the revision being exported\. | 

You can use these dynamic references to create the key patterns for your asset names\. You must include at least one of the two `Asset` dynamic references, which are `${Asset.Name}` and `${Asset.Id}`\.

For example, using **$\{Revision\.Id\}/$\{Asset\.Name\}** as a key pattern results in Amazon S3 objects that use the revision Id and asset name \(separated by a slash\) as the object name\.

If you export a revision with the Id `testRevisionId` that has two assets named `asset1` and `asset2`, then the assets are exported to the following locations in Amazon S3:
+ `<bucket>/testRevisionId/asset1`
+ `<bucket>/testRevisionId/asset2`

**Note**  
Your resulting objects must have unique names\. If they have the same names as existing objects in the S3 bucket, your export will overwrite existing objects\. If the revision you are exporting has non\-unique names \(for example, two assets with the same name\), the export will fail\. The only dynamic reference that is unique is `${Asset.Id}`\.