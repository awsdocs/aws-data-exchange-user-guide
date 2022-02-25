# Subscribing to a product<a name="subscribing-to-product"></a>

The following topics describe the process of subscribing to a product on AWS Data Exchange using the AWS Data Exchange console\.

**Topics**
+ [Subscribing to a product containing file\-based data](#subscribing-to-data-product)
+ [Subscribing to a product containing APIs](#subscribing-to-API-product)
+ [Subscribing to a product containing Amazon Redshift data sets](#subscribing-to-Redshift-product)
+ [Request a recommendation for a data product](#request-new-products)
+ [Unsubscribe from a product](#unsubscribe-product)

**Note**  
By subscribing to a product, you agree that your use of the product is subject to the provider's offer terms including pricing information and Data Subscription Agreement\.  
You also agree and acknowledge that AWS may share information about the transaction \(including your payment terms and product usage metrics\) with the respective seller, reseller, or underlying provider, as applicable, in accordance with the [AWS Privacy Notice](https://aws.amazon.com/privacy/)\. AWS will issue invoices and collect payments from you on behalf of the provider through your AWS account\. Your use of AWS services remains subject to the AWS Customer Agreement or other agreement with AWS governing your use of such services\.

## Subscribing to a product containing file\-based data<a name="subscribing-to-data-product"></a>

The following topics describe the complete process of subscribing to a product containing file\-based data on AWS Data Exchange by using the AWS Data Exchange console\. 

The process has the following steps:

**Topics**
+ [Step 1: Browse the catalog](#browse-catalog)
+ [Step 2: Subscribe to the product containing the file\-based data](#subscribe-to-data-product)
+ [Step 3: Use the product](#use-product)
+ [Step 4: \(Optional\) Export data after subscribing](#export-data-after-subscribing)

To practice subscribing to and using a product containing file\-based data, see the [Tutorial: Subscribe to AWS Data Exchange Heartbeat on AWS Data Exchange](heartbeat.md)\.

### Step 1: Browse the catalog<a name="browse-catalog"></a>

You can ﬁnd products and review the associated public or custom oﬀers and product details on both AWS Marketplace and AWS Data Exchange\. 

If the provider has issued a private oﬀer to your account, the product is available on the **My product oﬀers page** of the AWS Data Exchange console\. For more information, see [Subscribing to data products on AWS Data Exchange](subscribe-to-data-sets.md)\.

**To browse the catalog for products containing Amazon S3 objects**

1. Open and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. On the left side navigation pane, under **Discover data products**, choose **Browse catalog**\.

1. \(Optional\) Under **Refine results**, choose a specific **Category** to browse specific data products\.

1. Under **Refine results**, use the **Data available through** filter to select **Amazon S3**\.

   

1. \(Optional\) Under **Browse catalog**, enter in a word or phrase and then choose **Search** to view results matching your query\.

### Step 2: Subscribe to the product containing the file\-based data<a name="subscribe-to-data-product"></a>

If you subscribe to a paid product, you are billed on your AWS bill\. You get access to the entitled data set\. For more information, see [Subscribing to data products on AWS Data Exchange](subscribe-to-data-sets.md)\.

**To subscribe to the product containing the file\-based data**

1. Select a data product containing an Amazon S3 object and view its details page\.

   The information on the details page includes a product description, the provider's contact information, and the details of the product's public offer\. The public offer information includes price and durations, the data subscription agreement, and the refund policy\. You can also view the names of the data sets included in the product and the AWS Regions in which they are available\.

   If the provider has issued a custom offer to your account \(for example, a [private offer](subscribe-to-private-offer.md) or [Bring Your Own Subscription \(BYOS\) offer](subscribe-to-byos-offer.md)\), you see those details, too\.

1. In the top right corner, choose **Continue to subscribe**\. 

1. Choose your preferred price and duration combination, choose whether to enable auto\-renewal for the subscription, and review the oﬀer details, including the data subscription agreement\.
**Note**  
Some products require subscription veriﬁcation\. For more information, see [Subscription verification for subscribers](subscription-verification-sub.md)\.

1. Review the pricing information, choose the pricing oﬀer, and then choose **Subscribe**\.
**Note**  
If you subscribe to a paid product, you are prompted to conﬁrm your decision to subscribe\.

1. On the **Set up your ﬁrst export while your subscription processes** page, select the check boxes for the data sets containing the revisions that you would like to export\. Selecting a data set will prepare its most recently published revision to be exported\.

1. Choose an Amazon Simple Storage Service \(Amazon S3\) bucket location or conﬁgure an Amazon S3 key naming pattern\. This will determine where your revisions will be exported\. For more information about using key patterns, see [Key patterns when exporting revisions](jobs.md#revision-export-keypatterns)\.

1. Choose whether to enable or disable automatic revision export\. We recommend that you choose **Enable automatic revision export \- recommended**\.

1. Choose the **Encryption options**, and review the **Amazon S3 pricing**\.
**Note**  
If you choose to export using AWS Key Management Service \(AWS KMS\) encryption, make sure your account has the correct IAM permissions to create and revoke grants on the AWS KMS key you choose\. Without these permissions, automatic export will fail\.

1. Choose **Export** to export the data to Amazon S3, or choose **Skip** if you prefer to wait and export or download later\. For more information about how to export data after subscribing, see [Step 4: \(Optional\) Export data after subscribing](#export-data-after-subscribing)\.
**Note**  
It can take a few minutes for your subscription to become active after you choose **Subscribe**\. If you choose **Export** before the subscription is active, you are prompted to wait until it is complete\.  
After your subscription is active, your export will begin\.  
Navigating away from this page prior to your subscription becoming active will not prevent the subscription from processing\. It will prevent your data export from occurring\.

### Step 3: Use the product<a name="use-product"></a>

You have access to the product data sets according to the terms of the data subscription agreement\. 

You can export the associated assets to Amazon S3 or you can use jobs with a signed URL\. 

For more information, see [Jobs in AWS Data Exchange](jobs.md)\.

### Step 4: \(Optional\) Export data after subscribing<a name="export-data-after-subscribing"></a>

After your subscription is active, you can access the data sets at any time\. 

If you want export or download your data at a later time, including getting new revisions, you can do so from the **Subscriptions** page, using the following steps\.

**To export or download data after subscribing**

1. Open and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. To view your subscriptions, from the left navigation pane, choose **Subscriptions**, and then choose your product\. The data sets that are part of the product are displayed\. You can enable or disable auto\-renewal for your subscription on this page\.

1. When you choose the product's data set, you can view the data set's ID, name, and description\. For more information, see [Data in AWS Data Exchange](data-sets.md)\.

1. On the **Revisions** tab, you can view the data set's revisions, from latest to oldest\. To view the details of a revision, choose its revision ID\.

   The revision's details include its assets, displayed in a table\. 

1. To export one or more assets, select the check boxes, and then choose **Export to Amazon S3** or **Download**\. For more information about how to export data, see [Exporting assets](jobs.md#exporting-assets) and [Exporting revisions](jobs.md#exporting-revisions)\.

**Important**  
We recommend that you consider Amazon S3 security features when exporting data to Amazon S3\. See [Security best practices for Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/dev/security-best-practices.html) for general guidelines and best practices\.

## Subscribing to a product containing APIs<a name="subscribing-to-API-product"></a>

The following topics describe the complete process of subscribing to a product containing APIs on AWS Data Exchange by using the AWS Data Exchange console\. 

The process has the following steps:

**Topics**
+ [Step 1: Browse the catalog](#subscribe-API-product-browse)
+ [Step 2: Subscribe to a product containing APIs](#subscribe-to-API-product)
+ [Step 3: Use an API product](#use-API-product)

To practice subscribing to and using a product containing APIs, see the [Tutorial: Subscribe to AWS Data Exchange for APIs \(Test Product\) on AWS Data Exchange](subscriber-tutorial-api-product.md)\.

### Step 1: Browse the catalog<a name="subscribe-API-product-browse"></a>

You can ﬁnd products and review the associated public or custom oﬀers and product details on both AWS Marketplace and AWS Data Exchange\. 

If the provider has issued a private oﬀer to your account, the product is available on the **My product oﬀers page** of the AWS Data Exchange console\. For more information, see [Subscribing to data products on AWS Data Exchange](subscribe-to-data-sets.md)\.

**To browse the catalog for products containing APIs**

1. Open and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. On the left side navigation pane, under **Discover data products**, choose **Browse catalog**\.

1. \(Optional\) Under **Refine results**, choose a specific **Category** to browse specific data products\.

1. Under **Refine results**, use the **Data available through** filter to select **API**\.

   

1. \(Optional\) Under **Browse catalog**, enter in a word or phrase and then choose **Search** to view results matching your query\.

### Step 2: Subscribe to a product containing APIs<a name="subscribe-to-API-product"></a>

If you subscribe to a paid product, you're billed on your AWS bill\. You get access to the entitled data set\. For more information, see [Subscribing to data products on AWS Data Exchange](subscribe-to-data-sets.md)\.

**To subscribe to the product containing APIs**

1. Select a product containing APIs, and view its details page\.

   The information on the details page includes a product description, the provider's contact information, and the details of the product's public offer\. The public offer information includes price and durations, the data subscription agreement, and the refund policy\. You can also view the names of the data sets included in the product and the AWS Regions in which they are available\.

   If the provider has issued a custom offer to your account \(for example, a [private offer](subscribe-to-private-offer.md) or [Bring Your Own Subscription \(BYOS\) offer](subscribe-to-byos-offer.md)\), you see those details, too\.

1. In the top right corner, choose **Continue to subscribe**\. 

1. Choose your preferred price and duration combination, choose whether to enable auto\-renewal for the subscription, and review the oﬀer details, including the data subscription agreement\.
**Note**  
Some products require subscription veriﬁcation\. For more information, see [Subscription verification for subscribers](subscription-verification-sub.md)\.

1. Review the pricing information, choose the pricing oﬀer, and then choose **Subscribe**\.
**Note**  
If you subscribe to a paid product, you're prompted to conﬁrm your decision to subscribe\.

### Step 3: Use an API product<a name="use-API-product"></a>

The following topics provide details about how to use a product that includes API data sets: 

**Topics**
+ [Viewing an API](#view-the-api)
+ [Downloading the API specification](#download-api-spec)
+ [Making an API call \(console\)](#make-api-call-console)
+ [Making an API call \(AWS CLI\)](#make-api-call-cli)

#### Viewing an API<a name="view-the-api"></a>

**To view an API**

1. Open and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **My subscriptions**, choose **Entitled data**\.

1. Choose a data set\.

1. Under the **Revisions** tab, choose a revision\.

1. Under **API assets**, choose the API\.

1. View the **Asset overview**\.

1. Follow the guidance in the **Integration notes** to call the API\.

#### Downloading the API specification<a name="download-api-spec"></a>

**To download the API specification**

1. Open and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **My subscriptions**, choose **Entitled data**\.

1. Choose a data set\.

1. Under the **Revisions** tab, choose a revision\.

1. Under **API assets**, choose the API\.

1. On the **OpenAPI 3\.0 specification**, choose **Download API specification**\.

   The specification is downloaded onto your local computer\. You can then export the asset to a third\-party tool for SDK generation\.

#### Making an API call \(console\)<a name="make-api-call-console"></a>

You can call a single endpoint in the AWS Data Exchange console\.

**To make an API call from the console**

1. Open and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **My subscriptions**, choose **Entitled data**\.

1. Choose a data set\.

1. Under the **Revisions** tab, choose a revision\.

1. Under **API assets**, choose the API\.

1. For **Integration notes**: 

   1. Choose **Copy** to use the **Base URL**\.

   1. Choose **Copy** to use the **Code structure**\.

   1. Follow the information provided in the specification documentation to call the API\.

#### Making an API call \(AWS CLI\)<a name="make-api-call-cli"></a>

**To make an API call \(AWS CLI\)**
+ Use the `send-api-asset` command to call the API\.

  ```
  $ aws dataexchange send-api-asset \
    --asset-id $ASSET_ID \
    --data-set-id $DATA_SET_ID \
    --revision-id $REVISION_ID \
    --body "..." \
  {
      "headers": {
          ...
      },
      "body": "..."
  }
  ```

## Subscribing to a product containing Amazon Redshift data sets<a name="subscribing-to-Redshift-product"></a>

### Overview for subscribers<a name="subscribe-Redshift-product-overview"></a>

An Amazon Redshift data set is a data set that contains AWS Data Exchange datashares for Amazon Redshift\. Datashares give you read\-only access to the tables, views, schemas, and user\-defined functions that a data provider adds to the datashare\. 

As a data subscriber, you can find and subscribe to products containing Amazon Redshift data sets\. After your subscription starts, you get access to query the data in Amazon Redshift without extracting, transforming, and loading data\. You lose access to a product's datashares after your subscription expires\.

Consider the following:
+ If you are a subscriber, you must have an encrypted Amazon Redshift cluster running on an RA3 instance to query to Amazon Redshift data on AWS Data Exchange\. For more information, see the [Amazon Redshift Database Developer Guide](https://docs.aws.amazon.com/redshift/latest/dg/welcome.html)\.
+ It may take a few minutes to access the datashares after your subscription starts\.

The following sections describe the complete process of becoming an Amazon Redshift datashare product subscriber on AWS Data Exchange by using the AWS Data Exchange console\. The process has the following steps:

**Topics**
+ [Step 1: Browse the catalog](#subscribe-Redshift-product-browse)
+ [Step 2: Subscribe to products containing Amazon Redshift data sets](#subscribe-Redshift-product)
+ [Step 3: Use the AWS Data Exchange datashares for Amazon Redshift](#use-Redshift-product)

To practice subscribing to and using a product containing Amazon Redshift data sets, see the [Tutorial: Subscribe to Worldwide Event Attendance \(Test Product\) on AWS Data Exchange](subscriber-tutorial-RS-product.md)\.

#### Step 1: Browse the catalog<a name="subscribe-Redshift-product-browse"></a>

You can ﬁnd products and review the associated public or custom oﬀers and product details on both AWS Marketplace and AWS Data Exchange\. 

If the provider has issued a private oﬀer to your account, the product is available on the **My product oﬀers page** of the AWS Data Exchange console\. For more information, see [Subscribing to data products on AWS Data Exchange](subscribe-to-data-sets.md)\.

**To browse the catalog for products containing Amazon Redshift data sets**

1. Open and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. On the left side navigation pane, under **Discover data products**, choose **Browse catalog**\.

1. \(Optional\) Under **Refine results**, choose from one of the listed **Categories** to browse specific data products in that category\.

1. Under **Refine results**, use the **Data available through** filter to select **Amazon Redshift**\.

1. \(Optional\) Under **Browse catalog**, enter in a word or phrase and then choose **Search** to view results matching your query\.

#### Step 2: Subscribe to products containing Amazon Redshift data sets<a name="subscribe-Redshift-product"></a>

If you subscribe to a paid product, you're billed on your AWS bill\. You get access to all data sets included in the product\. For more information, see [Subscribing to data products on AWS Data Exchange](subscribe-to-data-sets.md)\.

**To subscribe to a product containing Amazon Redshift data sets**

1. Select a product and view its details page\.

   The information on the details page includes a product description, the provider's contact information, and the details of the product's public offer\. The public offer information includes price and duration, the data subscription agreement, and the refund policy\. You can also view the names of the data sets included in the product and the AWS Regions in which they are available\.

   If the provider has issued a custom offer to your account \(for example, a [private offer](subscribe-to-private-offer.md) or [Bring Your Own Subscription \(BYOS\) offer\)](subscribe-to-byos-offer.md), you see those details, too\.
**Important**  
Be sure to review the date, time, and duration of the cluster’s maintenance window\. During the maintenance window, you will not have access to the datashare\.

1. In the top right corner, choose **Continue to subscribe**\. 

1. Review the **Product offer**, the **Subscription terms**, the **Data sets** that are included in the offer, and the **Support information**\.

1. Choose whether to enable **Offer auto\-renewal** for the subscription
**Note**  
Some products require subscription veriﬁcation\. For more information, see [Subscription verification for subscribers](subscription-verification-sub.md)\.

1. Choose **Subscribe**\.
**Note**  
If you subscribe to a paid product, you're prompted to conﬁrm your decision to subscribe\.

#### Step 3: Use the AWS Data Exchange datashares for Amazon Redshift<a name="use-Redshift-product"></a>

You have access to the product's data sets according to the terms of the data subscription agreement\. As a subscriber, your subscription to a product that includes AWS Data Exchange datashares for Amazon Redshift gives you read\-only access to the tables, views, schemas, and functions within the datashare\.

With a subscription, you can do the following:
+ Query data without having to extract, transform, or load data\.
+ Access the latest provider data as soon as the provider updates it\.

For more information, see [Working with AWS Data Exchange datashares](https://docs.aws.amazon.com/redshift/latest/dg/adx-datashare.html) in the *Amazon Redshift Database Developer Guide*\. 

**Note**  
You lose access to a product's datashares after your subscription expires\.

For more information about how to subscribe to a Amazon Redshift data set, see [Tutorial: Subscribe to Worldwide Event Attendance \(Test Product\) on AWS Data Exchange](subscriber-tutorial-RS-product.md)\.

## Request a recommendation for a data product<a name="request-new-products"></a>

If you're unable to ﬁnd a product in the catalog, you can request personalized recommendations from the [AWS Data Exchange Data Discovery Team](https://aws.amazon.com/data-exchange/discover-data/)\.

**To request a data product recommendation**

1. Open and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. On the left side navigation pane, under **Discover data products**, choose **Request data product**\.

1. Enter specific details about the product you want and then choose **Submit**\.

   You should receive a response from the AWS Data Exchange Data Discovery Team within 2 business days\.

## Unsubscribe from a product<a name="unsubscribe-product"></a>

**Note**  
If you require immediate removal of a subscription, contact AWS Data Exchange Customer Support via the [AWS Support Center](https://console.aws.amazon.com/support/home#/case/create?issueType=customer-service&serviceCode=service-data-exchange )\.

**To unsubscribe from a product**

1. Open and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **My subscriptions**, choose **Subscriptions**\.

1. Select the subscription from which you want to unsubscribe\.

1. Under **Renewal terms**, turn off the **Auto\-renewal enabled** option\.

1. Do not export any more data, and let the subscription run its course\.
**Note**  
For paid products, consult the provider's refund policy\. Contact the provider for any exceptions\.