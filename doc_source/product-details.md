# Product details<a name="product-details"></a>

When you publish a product on the AWS Data Exchange console, you must provide the product's details\. This section covers some best practices to consider when you're preparing product details\.

**Topics**
+ [Product visibility](#product-visibility)
+ [Sensitive categories of information](#sensitive-information)
+ [Product name](#product-name)
+ [Product logo](#product-logo)
+ [Support contact](#product-support)
+ [Product categories](#product-categories)
+ [Short description](#product-short-description)
+ [Long description](#product-long-description)
+ [Revision access rules](#best-practices-revisions)
+ [Data dictionaries](#data-dictionaries-pro)
+ [Samples](#samples-pro)

## Product visibility<a name="product-visibility"></a>

When you create a product, you choose its visibility\. **Product visibility** can be either **Public** or **Private**:
+ **Public** – The product is visible in the public catalog in the AWS Data Exchange console and AWS Marketplace\. Public products must have a public offer associated with them, and they might also have custom offers\.
+ **Private** – The product is *not* publicly visible in the public catalogs of either AWS Data Exchange or AWS Marketplace, and can only have custom offers created for it\. Only the specific accounts for whom you have created a custom offer can see the product and subscribe to it\. Subscribers can view custom offers created for them on their **My product offers** tab of AWS Data Exchange\.

**Note**  
You can't modify the visibility of a product after it has been created\.

For more information about creating a product \(with either public or private visibility\), see [Step 5: Publish a new product](publishing-products.md#publish-products)\.

## Sensitive categories of information<a name="sensitive-information"></a>

When you create a product, you must specify whether your product contains any personal data or sensitive categories of data\. Sensitive categories of information includes biometric or genetic data; health data; racial or ethnic origin; political opinions; religious or philosophical beliefs; sex or sexual orientation; trade union membership; personal payment or financial information \(for example, credit history\); or other similar categories of information\. Personal data is data that can be used to identity a person\.

Choose one of the following options:

1. **No personal data that is not otherwise publicly available, and no sensitive categories of information**

   Choose this option if your product does not contain any personal data that is not otherwise publicly available, and no sensitive categories of information\.

1. **No personal data but contains sensitive categories of information**

   Choose this option if your product contains non\-personal sensitive information, such as aggregated diversity data or anonymized financial data\.

1. **Personal data that is not otherwise publicly available but does not include protected health information \(PHI\) subject to the Health Insurance Portability and Accountability Act of 1996 \(HIPAA\) \[Preview\]**

   Choose this option if your product contains personal data that is not otherwise publicly available\. The product must not include protected health information \(PHI\) subject to HIPAA\. Product may contain personal information such as email addresses, social security numbers, biometrics, or mobile IDs\.

1. **Protected Health Information \(PHI\) subject to the Health Insurance Portability and Accountability Act of 1996 \(HIPAA\)** 

   Choose this option if your product contains protected health information \(PHI\) subject to HIPAA\. The product may contain information such as patient information disclosed by a covered entity\.
**Important**  
This fourth option is only available for private products\. Public products may not contain such data\.

**Note**  
The third and fourth options are only available to eligible providers enrolled in the Extended Provider Program who have agreed to the Extended Provider Program Addendum to the Terms and Conditions for AWS Marketplace Providers\. The Extended Provider Program is currently in preview and subject to Section 2 of the [AWS Service Terms](https://aws.amazon.com/service-terms/) \(under *Betas and Previews*\)\. For information about eligibility, contact [AWS Support](https://console.aws.amazon.com/support/home#/case/create?issueType=customer-service) or send an email message to [dataexchangehelp@amazon\.com](mailto://dataexchangehelp@amazon.com)\.  
The fourth option is only available to eligible providers who have agreed to the AWS Business Associate Addendum, as well as the AWS Data Exchange Addendum to the AWS Business Associate Addendum\.

Indicating that your product contains sensitive categories of information or personal data results in the display of a message on the product's page on AWS Data Exchange to alert prospective customers\.

**Warning**  
If you are not enrolled in the Extended Provider Program, listing a product with data or information described in the third and fourth options is a violation of our [Publishing guidelines](publishing-guidelines.md)\. AWS removes any product that breaches these guidelines and can suspend the provider from future use of the service\.

For more information about creating a product and setting the sensitivity status of the data, see [Step 5: Publish a new product](publishing-products.md#publish-products)\.

## Product name<a name="product-name"></a>

Subscribers will search for the names of products, so make your product name something meaningful\.

## Product logo<a name="product-logo"></a>

The product logo appears in the AWS Data Exchange product catalog on the console and on AWS Marketplace\. The supported formats for the logo are \.png, \.jpg, and \.jpeg\.

## Support contact<a name="product-support"></a>

As a provider, you must include valid contact information\. This can be a managed email alias or case management system link for customers to use to get help when they have questions about your product\. We strongly recommend that you don't use a personal email address because the address is publicly visible\.

## Product categories<a name="product-categories"></a>

All products fit into one or more categories\. By specifying up to two categories for your product, you help subscribers filter and find your products in AWS Data Exchange and AWS Marketplace\.

## Short description<a name="product-short-description"></a>

The product short description text appears on the tiles in the product catalog portion of the AWS Data Exchange console\. We recommend that you provide a concise description of your product for this ﬁeld\.

## Long description<a name="product-long-description"></a>

Subscribers see the product long description in the product detail page after the product is published\. We recommend that you list the product's features, beneﬁts, usage, and other information speciﬁc to the product\.

Product information in the description must accurately represent the data being provided to subscribers\. This includes data coverage \(for example, 30,000 financial instruments or 10,000 location coordinates\) and data set update frequency \(for example, daily updates or weekly updates\)\.

**Note**  
You can use Markdown templates as a starting point for the long description of a number of popular product types\. For more information, see [Product description templates](product-description-templates.md)\.

### Product description additional information<a name="product-provide-info"></a>

In order to make your product description compelling to prospective subscribers, we recommend you add the following information to your product description:
+  *Data due diligence questionnaire \(DDQ\)* – Typically includes responses to questions regarding the firm selling a data set\. Examples of the information in a DDQ includes the process that a provider goes through to collect the data, or quality control procedures and questions regarding regulatory compliance\.
+  *Data set schemas* – Provide prospective users with detailed descriptions of the structure and format of your data sets\. Examples of the information in a data set schema include the identification of a primary key, field names, field definitions, expected output types for each field \(for example, string, integer\), and acceptable enumerations for each field \(for example, 0%–100%\)\.
+ *Trial product listings* – Many prospective subscribers request trials of data sets before paying for a subscription\. Trial products can be published on AWS Data Exchange for subscribers to subscribe to like regular paid products\.
+  *Sample files* – Sample files are typically smaller versions, or older, out\-of\-date versions of full production data sets\. These sample files give prospective users insights into the outputs they can expect before purchasing a subscription\.
+  *Product fact sheets* – These can be documents, web links, or both to provide subscribers with more granular statistics on the coverage of your data sets, typical use cases for your data sets, and any other factors that differentiate your data sets\.

For information about adding links in the description, see [Include links in your product description](#best-practices-links-in-listing)\.

### Include links in your product description<a name="best-practices-links-in-listing"></a>

The long description for an AWS Data Exchange product supports Markdown, which allows you to include links in your product's details page\. The following procedure shows you how to add links to websites in your AWS Data Exchange product description\. 

**To include embedded links in your product listing**

1. Log into the AWS console and navigate to an [Amazon S3 bucket](https://console.aws.amazon.com/s3) that your AWS Data Exchange user account has access to\. The contents of this bucket are publicly readable\.

1. Upload the files \(for example, documents such as PDF files or Microsoft Excel files\) that you want to include in your product listing into the Amazon Simple Storage Service \(Amazon S3\) bucket\. After the upload is complete, make sure you set the file or files to have public read access permissions\.

1.  Choose one of the uploaded files\. In the **Overview** tab, you will see a URL for the file\. Copy the URL to your clipboard\.

1. Open the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. Choose the product you want to update, and then choose **Edit**\.

1. From **Product Description**, use the following Markdown formats to link to relevant files \(using the URL link you copied previously\) or to another URL, like your website\.
   +  To link to a file stored in an S3 bucket: 

      \*\*\_\[*File name*\]\(*Object URL from Amazon S3*\)\_\*\* 

      *Description of the object*\. 
   +  To link to a trial product listing on AWS Data Exchange: 

      \*\*\_\[*Website Title\]*\(*URL*\)\_\*\* 

      *Description of the website*\. 

1. Choose **Save Changes**\. After a few minutes your AWS Data Exchange product listing page should be updated with the new links\.

## Revision access rules<a name="best-practices-revisions"></a>

Revision access rules specify which revisions subscribers can access when they subscribe to your product\. You choose options for subscribers to get historical and future revisions\.
+ *Historical revision options* – Historical revisions are revisions that you published prior to the subscription start date\. You have three options for historical revisions:
  + **All pre\-existing revisions published prior to subscription** – Give your subscribers access to all historical revisions\.
  + **A fixed number of trailing revisions published prior to subscription** – You choose how many historical revisions your subscribers have access to \(from 1 to 100\)\.
  + **No historical revisions** – Your subscribers get no access to historical revisions\. With this option, your subscribers will initially have no data available, until you publish your next revision after their subscription starts\.
+ *Future revision options* – Future revisions are revisions that you publish after subscription start\. You have two options for future revisions:
  + **All future revisions published during subscription duration** – Give your subscribers access to all revisions that you publish until their subscription expires\.
  + **No future revisions** – Your subscribers get no access to future revisions\.

**Note**  
You can't choose both **No historical revisions** and **No future revisions**\. That would create a product with no revisions and no data\.

## Data dictionaries<a name="data-dictionaries-pro"></a>

A *data dictionary* is a visual representation of the contents of your data set\. 

Subscribers can view and download a data dictionary before they subscribe to your product to evaluate if your product meets their needs\.

You can add one data dictionary to each data set, with a maximum size of 1 MB\. The accepted file type for a data dictionary is \.csv\. 

When you create a data dictionary, you include details about what columns are included in the data set and their meaning\. Your data dictionary must conform to the AWS Data Exchange data dictionary template\. You can download the **blank data dictionary template** from the AWS Data Exchange console\. AWS Data Exchange also provides an **example data dictionary** for you to view as an example\.

**Note**  
A data dictionary is attached to a product and associated with a data set\. If you want to have more than one data dictionary for potential subscribers to evaluate, you can create two or more versions of the same product with the same data sets\. Then, add a different data dictionary to each product\.

For more information about how to add a data dictionary to a product, see [Publishing a new product](publishing-products.md)\.

## Samples<a name="samples-pro"></a>

A *sample* is a small part of the data in your product that is intended to show what the entire data set is like\.

Subscribers can view and download samples before they subscribe to your product to evaluate if your product meets their needs\.

You can upload up to 10 samples to each data set with a maximum size of 50 MB\. The accepted file formats for samples are any file type accepted by Amazon S3\. Samples in \.csv format can be previewed\.

**Note**  
Samples are attached to a product and associated with a data set\. If you want to have more than 10 samples for potential subscribers to evaluate, you can create two or more versions of the same product with the same data sets\. Then, add up to 10 samples to each product\.

For more information about how to add a sample to a product, see [Publishing a new product](publishing-products.md)\.