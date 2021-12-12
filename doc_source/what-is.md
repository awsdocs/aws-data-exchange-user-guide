# What is AWS Data Exchange?<a name="what-is"></a>

AWS Data Exchange is a service that makes it easy for AWS customers to find, subscribe to, and use third\-party data in the AWS Cloud\.

As a subscriber, you can find and subscribe to thousands of products from qualified data providers\. Then, you can use the AWS Data Exchange console or APIs to create, view, manage, and access data sets for use across a variety of AWS analytics and machine learning services\. Anyone with an AWS account can be an AWS Data Exchange subscriber\. For information about becoming a subscriber, see [Subscribing to data products on AWS Data Exchange](subscribe-to-data-sets.md)\.

For providers, AWS Data Exchange eliminates the need to build and maintain any data delivery, entitlement, or billing technology\. Providers in AWS Data Exchange have a secure, transparent, and reliable channel to reach AWS customers and grant existing customers their subscriptions more efficiently\. The process for becoming an AWS Data Exchange provider requires a few steps to determine eligibility\. For more information, see [Providing data products on AWS Data Exchange](providing-data-sets.md)\.

**Topics**
+ [What is an AWS Data Exchange product?](#data-exchange-products)
+ [Malware prevention](#ensuring-safe-data)
+ [Supported data sets](#supported-data-sets)
+ [Accessing AWS Data Exchange](#how-to-access)
+ [Pricing](#pricing)
+ [Supported Regions](#supported-regions)
+ [Related services](#related-services)

## What is an AWS Data Exchange product?<a name="data-exchange-products"></a>

A product is the unit of exchange in AWS Data Exchange that is published by a provider and made available for use to subscribers\. When a provider publishes a product, that product is listed on the AWS Data Exchange product catalog as well as AWS Marketplace after being reviewed by AWS against our guidelines and terms and conditions\. Each product you publish is uniquely identiﬁed by its product ID\. 

**Note**  
When a product is initially created and published, all pre\-existing ﬁnalized revisions within its data sets are published at the same time\.

With AWS Data Exchange, providers publish data products and subscribers subscribe to those products\.

Providers can publish and view their products using the AWS Data Exchange console\. Providers can also list and view the details of their existing products using the AWS Marketplace Catalog API\. 

A product has the following parts:
+ **Product details** – This information includes name, descriptions \(both short and long\), logo image, and support contact information\. Providers complete the product details\. 
  + For more information as a subscriber, see [Product subscriptions](product-subscriptions.md)\. 
  + For more information as a provider, see [Product details](product-details.md)\.
+ **Product offers** – Oﬀers deﬁne the terms that subscribers are agreeing to when they subscribe to a product\. To make a product available on AWS Data Exchange, providers must define a public offer\. This offer includes prices and durations, data subscription agreement, refund policy, and the option to create custom offers\. 
  + For more information as a subscriber, see [Private products and offers ](subscribe-to-private-offer.md) and [Bring Your Own Subscription \(BYOS\) offers ](subscribe-to-byos-offer.md)
  + For more information as a provider, see [Creating an offer for AWS Data Exchange products](prepare-offers.md)\.
+ **Data sets** – A product can contain one or more data sets\. A data set in AWS Data Exchange is a dynamic set of data which is versioned through the use of revisions\. Each revision can contain multiple assets\. The provider can decide which revisions within a data set are published to a product\. The provider creates owned data sets, and a subscriber can get access to entitled data sets through a product subscription\. When a subscriber subscribes to a product, they get access to the product’s data sets and some or all of the revisions that have been published to that product for the duration of their subscription\.
  + For more information as a subscriber, see [Data sets and revisions](product-subscriptions.md#product-sub-revisions)
  + For more information as a provider, see [Data in AWS Data Exchange](data-sets.md)\.

**Important**  
Beginning July 22, 2021, new and existing providers have the ability to automatically publish revisions to data sets\. All new products on AWS Data Exchange default to automatic revision publishing\. If you have existing products on AWS Data Exchange before July 22, 2021, you need to migrate them to automatic revision publishing\.  
For more information, see [Migrating an existing product to automatic revision publishing](updating-products.md#migrate-product)\.

## Malware prevention<a name="ensuring-safe-data"></a>

Security and compliance is a shared responsibility between you and AWS\. To promote a safe, secure, and trustworthy service for everyone, AWS Data Exchange scans all S3 object files published by providers before they are made available to subscribers\. If AWS detects malware, the affected asset is removed\.

**Important**  
AWS Data Exchange does not guarantee that the data you consume as a subscriber is free of any potential malware\. We encourage that you conduct your own additional due diligence to ensure compliance with your internal security controls\. You can find anti\-malware and security products in AWS Marketplace\.

## Supported data sets<a name="supported-data-sets"></a>

AWS Data Exchange takes a responsible approach to facilitating data transactions by promoting transparency through use of the service\. AWS Data Exchange reviews permitted data types, restricting products that are not permitted\. Providers are limited to distributing data sets that meet the legal eligibility requirements set forth in the Terms and Conditions for AWS Marketplace Sellers\.

For more information about permitted data types, see [Publishing guidelines](publishing-guidelines.md)\.

**Important**  
As an AWS customer, you are encouraged to conduct your own additional due\-diligence to ensure compliance with any applicable data privacy laws\. If you suspect that a product or other resources on AWS Data Exchange are being used for abusive or illegal purposes, report it using the [Report Amazon AWS abuse form](https://support.aws.amazon.com/#/contacts/report-abuse)\.

## Accessing AWS Data Exchange<a name="how-to-access"></a>

### Subscribers<a name="how-to-access-sub"></a>

As a subscriber, you can explore available AWS Data Exchange products through the following options:
+ [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange) \(**Browse catalog**\)
+ [AWS Marketplace catalog](https://aws.amazon.com/marketplace/search/results?category=d5a43d97-558f-4be7-8543-cce265fe6d9d&FULFILLMENT_OPTION_TYPE=DATA_EXCHANGE&filters=FULFILLMENT_OPTION_TYPE)

### Providers<a name="how-to-access-pro"></a>

As an existing provider, you can access AWS Data Exchange through the following options:
+ Directly through the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange) \(**Publish data**\)
+ Programmatically using the following APIs:
  + **AWS Data Exchange API** – Use the API operations to create, view, update, and delete data sets and revisions\. You can also use these API operations to import and export assets to and from those revisions\. For more information, see the [AWS Data Exchange API Reference](https://docs.aws.amazon.com/data-exchange/latest/apireference)\.
  + **AWS Marketplace Catalog API** – Use the API operations to view and update products on AWS Data Exchange and AWS Marketplace\. For more information, see the [AWS Marketplace Catalog API Reference](https://docs.aws.amazon.com/marketplace-catalog/latest/api-reference/catalog-api-user-guide.html)\.

## Pricing<a name="pricing"></a>

Your AWS Data Exchange subscriptions are displayed in the currency you specified for your AWS account\. You can change your preferred currency for your AWS account in the AWS Billing and Cost Management console\. For instructions, see [Changing which currency you use to pay your bill](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/manage-account-payment.html#manage-account-payment-change-currency) in the *AWS Billing and Cost Management User Guide*\.

**Note**  
 Changing your preferred currency changes your remittance instructions\. To view updated remittance instructions, see your AWS Marketplace invoice or view the **Account Settings** page in the [AWS Billing and Cost Management](https://console.aws.amazon.com/billing/home?#account) console\.

For pricing information, see [ AWS Data Exchange pricing](http://aws.amazon.com/data-exchange/pricing/)\.

## Supported Regions<a name="supported-regions"></a>

AWS Data Exchange has a single, globally available product catalog offered by providers\. Subscribers can see the same catalog regardless of which AWS Region they are using\. The resources underlying the product \(data sets, revisions, assets\) are regional resources that you manage programmatically or through the AWS Data Exchange console in supported Regions\. For information about which Regions are supported, see [Global Infrastructure Region Table](http://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/)\.

## Related services<a name="related-services"></a>


|  | 
| --- |
| The Amazon Redshift data set type is in preview release for AWS Data Exchange and is subject to change\. | 

The following services are related to AWS Data Exchange:
+ **Amazon S3** – One supported asset type for data sets is Amazon S3 object snapshots\. Subscribers can export data sets to Amazon S3 programmatically\. For more information, see [What Is Amazon S3?](https://docs.aws.amazon.com/AmazonS3/latest/dev/Welcome.html) in the *Amazon Simple Storage Service User Guide*\.
+ **Amazon API Gateway** – Another supported asset type for data sets is APIs\. Subscribers can call the API programmatically, call the API from the AWS Data Exchange console, or download the OpenAPI specification file\. For more information, see [What is Amazon API Gateway?](https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html) in the *Amazon API Gateway* Developer Guide\. 
+ \(Preview\) **Amazon Redshift** – AWS Data Exchange supports Amazon Redshift datashare data sets\. Subscribers can get read\-only access to query the data in Amazon Redshift without extracting, transforming, and loading data\. For more information, see [Getting started with Amazon Redshift](https://docs.aws.amazon.com/redshift/latest/gsg/getting-started.html) in the *Amazon Redshift Getting Started Guide* and [Amazon Redshift system overview](https://docs.aws.amazon.com/redshift/latest/dg/welcome.html) in the *Amazon Redshift Database Developer Guide*\.
+ **AWS Marketplace** – AWS Data Exchange allows data sets to be published as products on AWS Marketplace\. AWS Data Exchange providers must be registered as AWS Marketplace sellers, and can use the AWS Marketplace Management Portal or the AWS Marketplace Catalog API\. For information about becoming an AWS Marketplace subscriber, see [What Is AWS Marketplace?](https://docs.aws.amazon.com/marketplace/latest/buyerguide/what-is-marketplace.html) in the *AWS Marketplace Buyer Guide*\. For information about becoming an AWS Marketplace seller, see [What Is AWS Marketplace?](https://docs.aws.amazon.com/marketplace/latest/userguide/what-is-marketplace.html) in the *AWS Marketplace Seller Guide*\.