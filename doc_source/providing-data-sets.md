# Providing data products on AWS Data Exchange<a name="providing-data-sets"></a>


|  | 
| --- |
| The Amazon Redshift data set type is in preview release for AWS Data Exchange and is subject to change\. | 

At a high level, this is how to use AWS Data Exchange as a provider:

1. **Potential provider registers to be a provider** – Registering allows you to list products on AWS Data Exchange and make them available on AWS Marketplace\. For more information, see [Step 2: Register to be a provider](provider-getting-started.md#provider-registration)\.

1. **The data is eligible to be published on AWS Data Exchange** – You're limited to distributing data sets that meet the legal eligibility requirements set forth in the Terms and Conditions for AWS Marketplace Sellers\. For more information about the types of permitted data, see [Publishing guidelines](publishing-guidelines.md)\.

1. **Provider creates a data set, a revision, and imports assets** – You can create data sets through the AWS Data Exchange console or API\. Then, you can create revisions in the data set, and add assets to that revision\. For more information, see [Data in AWS Data Exchange](data-sets.md)\.

1. **Provider creates a product and its offer** – To create a product, you must provide product details, include one or more data sets, and optionally provide public offer details\. For more information, see [Publishing a new product](publishing-products.md)\.
   + **Products containing Amazon S3 objects** – When an owned data set containing S3 objects is published in a product, AWS Data Exchange creates a copy of the data set\. Subscribers can access that copy of the data set as an entitled data set\.
   + **Products containing Amazon API Gateway APIs** – When an owned data set containing Amazon API Gateway APIs is published in a product, AWS Data Exchange allows requests to the AWS Data Exchange endpoint to proxy through to your Amazon API Gateway API\. Subscribers can view the API and download the API specification as an entitled data set\. Subscribers can also call the API through the AWS Data Exchange console\.
   + **Products containing Amazon Redshift datashares** – When an owned data set containing Amazon Redshift datashares is published in a product, AWS Data Exchange allows requests to the AWS Data Exchange endpoint to proxy through to your Amazon Redshift datashare\. Subscribers can have read\-only access to the tables, views, schemas, and user\-defined functions that you've added to the datashare\.

1. **\(Optional\) Provider enables subscription verification ** – If you enable subscription verification, subscribers must request a subscription to your product\. This gives you an opportunity to review potential subscribers before they access your data sets\. For more information, see [Subscription verification for providers](subscription-verification-pro.md)\.

1. **\(Optional\) Provider creates custom offers for the product** – In addition to a public offer, you can create custom offers, including private and Bring Your Own Subscription \(BYOS\) offers, for select customers\. For more information, see [Creating custom offers](create-custom-offers.md)\.

1. **\(Optional\) Provider publishes new revision** – You can update dynamic data sets over time by creating a new revision using the AWS Data Exchange API or console\. These revisions can then be published\. For more information, see [Revisions](data-sets.md#revisions) or [Updating products](updating-products.md)\.

1. **Provider reviews reports through the AWS Marketplace Management Portal** – Reports are available to all registered AWS Marketplace sellers and are released on a regular cadence \(daily, weekly, or monthly\)\. For more information, see [Provider financials on AWS Marketplace](provider-financials.md)\.

1. **Provider receives funds distributed by AWS Marketplace** – For more information, see [Provider financials on AWS Marketplace](provider-financials.md)\.

## Programmatic access<a name="control-planes"></a>

If you're using AWS Data Exchange programmatically, there are two different sets of resources with two different APIs:
+ **AWS Data Exchange API** – Use these API operations to create, view, update, and delete data sets and revisions\. You can also use these API operations to import and export assets to and from those revisions\. For more information, see the [AWS Data Exchange API Reference](https://docs.aws.amazon.com/data-exchange/latest/apireference)\.
+ **AWS Marketplace Catalog API** – Used by providers to view and update products on AWS Data Exchange and AWS Marketplace\. For more information, see the [AWS Marketplace Catalog API Reference](https://docs.aws.amazon.com/marketplace-catalog/latest/api-reference/catalog-api-user-guide.html)\.

Before you become a data product provider on AWS Data Exchange, review the following topic:
+ [Setting up AWS Data Exchange](setting-up.md)

After you review this topic, you're ready to get started\.

### Related topics<a name="provider-related-topics"></a>
+ [Publishing guidelines](publishing-guidelines.md)
+ [Product details](product-details.md)
+ [Getting started as a provider](provider-getting-started.md)
+ [Publishing a new product](publishing-products.md)
+ [Product description templates](product-description-templates.md)
+ [Updating products](updating-products.md)
+ [Creating an offer for AWS Data Exchange products](prepare-offers.md)
+ [Data in AWS Data Exchange](data-sets.md)