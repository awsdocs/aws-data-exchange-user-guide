# Getting started as a subscriber<a name="subscriber-getting-started"></a>

The following topics describe the complete process of becoming a data product subscriber on AWS Data Exchange using the AWS Data Exchange console\. The process has the following steps:

**Topics**
+ [Step 1: Set up AWS Data Exchange](#subscriber-prereqs)
+ [Step 2: Browse the catalog](#browse-catalog)
+ [Step 3: \(Optional\) Request a recommendation for a data product](#request-new-products)
+ [Step 4: \(Optional\) Evaluate products containing data dictionaries and samples](#evaluate-products)
+ [Step 5: Subscribe to and access a product](#subscribe-to-product)

## Step 1: Set up AWS Data Exchange<a name="subscriber-prereqs"></a>

Before you can use AWS Data Exchange, you must sign up for AWS and create an AWS Identity and Access Management \(IAM\) user\. For more information, see [Setting up AWS Data Exchange](setting-up.md)\.

**To set up AWS Data Exchange**

1. Sign up for an AWS account\. For more information, see [Sign up for AWS](setting-up.md#setting-up-aws-sign-up)\.

1. Create an IAM user\. For more information, see [Create an IAM user](setting-up.md#setting-up-create-iam-user)\.

## Step 2: Browse the catalog<a name="browse-catalog"></a>

You can ﬁnd products and review the associated public or custom oﬀers and product details on both AWS Marketplace and AWS Data Exchange\. 

If the provider has issued a private oﬀer to your account, the product is available on the **My product oﬀers page** of the AWS Data Exchange console\. For more information, see [Subscribing to data products on AWS Data Exchange](subscribe-to-data-sets.md)\.

**To browse the catalog**

1. Open and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. In the left side navigation pane, under **Discover data products**, choose **Browse catalog**\.

1. Enter a term or phrase in the **Search** bar and then choose **Search**\.

1. \(Optional\) Under **Browse catalog**, enter in a word or phrase and then choose **Search** to view results matching your query\.

1. \(Optional\) Under **Refine results**, choose from one of the specific **Categories** to browse specific data products\.

1. \(Optional\) Under **Reﬁne results**, use the **Data available through** ﬁlter and select:
   + **Amazon S3** to find products containing file\-based data
   + **Amazon Redshift** to find products containing Amazon Redshift datashares
   + **API** to find products containing APIs

1. Select a product from the list of returned results and review its product details page\.

## Step 3: \(Optional\) Request a recommendation for a data product<a name="request-new-products"></a>

If you're unable to ﬁnd a product in the catalog, you can request personalized recommendations from the [AWS Data Exchange Data Discovery Team](https://aws.amazon.com/data-exchange/discover-data/)\.

**To request a data product recommendation**

1. Open and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. In the left side navigation pane, under **Discover data products**, choose **Request data product**\.

1. Enter specific details about the product you want\.

1. \(Optional\) Expand the **Additional details** and complete the fields as directed\.

1. Choose **Submit**\.

   You should receive a response from the AWS Data Exchange Data Discovery Team within 2 business days\.

## Step 4: \(Optional\) Evaluate products containing data dictionaries and samples<a name="evaluate-products"></a>

A provider might include a data dictionary and samples of the data set with their product\. To help you determine if the product’s data set will meet your needs, you can view and download the data dictionary and samples before you subscribe\. For more information, see [Data dictionaries and samples](product-subscriptions.md#dictionaries-and-samples)\.

You can perform the following actions to help with your evaluation of a product’s data sets:
+ [View a data dictionary](#view-data-dictionary)
+ [Download a data dictionary](#download-data-dictionary)
+ [View and download all data dictionaries](#view-download-all-dictionaries) \(for products containing multiple data sets\)
+ [Preview a sample](#preview-sample) 
+ [Download a sample](#download-sample) 

### Viewing a data dictionary<a name="view-data-dictionary"></a>

A provider can add one data dictionary per data set that you can view\.

**To view a data dictionary**

1. On the product detail page, choose the **Data dictionary and samples** tab\.

1. View the data dictionary in one of the following ways:
   + Scroll down to the product **Overview** section to see the data dictionary under **View data dictionaries**\. 
   + Choose the **Data dictionaries and samples** tab, expand a data set row, choose the option button next to a data dictionary, and then choose **View all data dictionaries**\.

1. \(Optional\) Enter a keyword or phrase into the **Search** bar to search across all data sets and all tables\.

1. \(Optional\) Modify your search and filters as necessary\.

### Downloading a data dictionary<a name="download-data-dictionary"></a>

A provider can add one data dictionary per data set that you can download\.

**To download a data dictionary**

1. On the product detail page, choose the **Data dictionary and samples** tab\.

1. Expand the data set row by choosing the expand icon \(plus icon to the left of the data set name\)\.

1. Choose the option button next to a data dictionary name\.

1. Choose **Download**\.

   The data dictionary file is downloaded to your computer\.

### Viewing and downloading all data dictionaries<a name="view-download-all-dictionaries"></a>

If the product has multiple data sets, the provider might add a data dictionary for each data set\. To evaluate all the data sets, you might want to view and download all data dictionaries \.

**To view and download all data dictionaries**

1. On the product detail page, choose the **Data dictionary and samples** tab\.

1. Choose **View all data dictionaries**\.

1. In the **View data dictionaries** dialog box, choose the **Download \(CSV\)** to download the \.csv file\.

   The \.csv file is downloaded to your computer\.

1. Choose **Close** to close the dialog box\.

### Previewing a sample<a name="preview-sample"></a>

**To preview a sample**

1. On the product detail page, choose the **Data dictionary and samples** tab\.

1. Expand the data set by choosing the expand icon \(plus icon to the left of the data set name\)

1. Choose the option button next to a sample name\.

1. Choose **Preview sample \(CSV only\)** to preview the sample\.

   1. \(Optional\) In the preview dialog box, choose **Download** to download the CSV file\.

       The CSV file is downloaded to your computer\.

   1. Choose **Close** to close the dialog box\.

### Downloading a sample<a name="download-sample"></a>

**To download a sample**

1. On the product detail page, choose the **Data dictionary and samples** tab\.

1. Expand the data set by choosing the expand icon \(plus icon to the left of the data set name\)

1. Choose the option button next to a sample name\.

1. Choose **Download**\.

   The sample is downloaded to your computer\.

## Step 5: Subscribe to and access a product<a name="subscribe-to-product"></a>

After you discover a product in the AWS Data Exchange catalog and determine that it meets your needs, you can subscribe to the product and then access the product\. 

If you subscribe to a paid product, you are billed on your AWS bill\. You get access to the entitled data set\. For more information, see [Subscribing to data products on AWS Data Exchange](subscribe-to-data-sets.md)\.

For more information about how to subscribe to products containing different types of data sets, see the following: 
+ [Subscribing to and accessing a product containing file\-based data](subscribing-to-product.md#subscribing-to-data-product)
+ [Subscribe to and access a product containing APIs](subscribing-to-product.md#subscribing-to-API-product)
+ [Subscribe to and access a product containing Amazon Redshift data sets](subscribing-to-product.md#subscribing-to-Redshift-product)