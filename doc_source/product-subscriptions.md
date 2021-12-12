# Product subscriptions<a name="product-subscriptions"></a>

All AWS Data Exchange products are subscription\-based\. When you subscribe to a product, you agree to the product's offer terms, including the price, duration, payment schedule, data subscription agreement, and refund policy\. When you subscribe to a product, you pay according to the payment schedule chosen by the provider for the duration that you subscribed to\.

**Important**  
The data subscription agreement \(DSA\) sets forth the provider’s terms and conditions for the data product\. The use of any data product subscribed to on AWS Data Exchange must also be in compliance with the AWS Customer Agreement or other agreement governing your use of AWS services\.

Each product's public offer terms can contain one or more price and duration combinations\. When you subscribe to a product, you can choose the duration of the subscription\. You can also choose whether you would like to enable auto\-renewal for that subscription, if the provider has enabled it for the product\.

**Important**  
If the data provider has indicated that the product contains any categories of sensitive or personal data, for example, mobile IDs, it will be displayed with the product details\. For more information about the categories of sensitive data, see [Sensitive categories of information](product-details.md#sensitive-information)\.  
If the data provider has indicated that the product contains protected health information \(PHI\) subject to the Health Insurance Portability and Accountability Act of 1996 \(HIPAA\), you may not export the product's data sets into your AWS account unless such AWS account is designated as a HIPAA account \(as defined in the AWS Business Associate Addendum found in [AWS Artifact](https://docs.aws.amazon.com/artifact/latest/ug/what-is-aws-artifact.html)\)\.

After a subscription is processed and active, it appears on your AWS bill according to the payment schedule as part of your AWS Marketplace charges\. For more information, see [AWS Marketplace Paying for Products](https://docs.aws.amazon.com/marketplace/latest/buyerguide/buyer-paying-for-products.html)\.

During the duration of your subscription, you can view and access all the product's data sets\. You can also export the data sets' assets in jobs\. For more information, see [Jobs in AWS Data Exchange](jobs.md)\. Once a subscription has expired, you can no longer view or export the data sets\.

**Note**  
For information about data sets and revisions, including details about what you have access to in your subscription, see [Data sets and revisions](#product-sub-revisions)\.

If a provider decides to unpublish a product, you still have access to the data sets as long as your subscription is active\. However, you cannot auto\-renew the subscription when it expires\.

You can view all of your active product subscriptions and auto\-renewal status on the **Subscriptions** page of the AWS Data Exchange console\. Visit the **Entitled data sets **page to find and access all of your entitled data sets in a specific AWS Region, based on your active subscriptions\.

**Important**  
If you enable auto\-renew, and the product's offer terms have changed at the time of renewal, then the new product offer terms \(including new price and new DSA\) apply\. This ensures that you keep access to the data regardless of potential changes to offer terms\.

When you subscribe to a data product, we might share your contact information with the provider\. For more information, see [What Information Do You Share with the Software Seller about the Customers of a Product?](https://docs.aws.amazon.com/marketplace/latest/buyerguide/buyer-security.html#what-information-do-you-share-with-the-software-seller-about-the-customers-of-a-product.html)\.

When you purchase a data product on AWS Data Exchange that has an upfront commitment, you will receive an invoice from Amazon Web Services \(AWS\) immediately\. You can see charges for each data product by name in the Detail section of the invoice\. You will receive separate bills for usage of AWS infrastructure and analytics services such as Amazon Simple Storage Service \(Amazon S3\) or Amazon Athena\. You can read more about AWS Billing and Cost Management in [ Paying for products](https://docs.aws.amazon.com/marketplace/latest/buyerguide/buyer-paying-for-products.html) in the *AWS Marketplace Buyer Guide*\.

## Data sets and revisions<a name="product-sub-revisions"></a>

Every product in AWS Data Exchange is made up of one or more data sets, each with one or more revisions\. Data sets in AWS Data Exchange are typically different data, and revisions are newer or modified versions of the same data\. For more information about data sets and revisions, see [Data in AWS Data Exchange](data-sets.md)\.

Each revision may contain all the data for the data set \(updated for the revision\), or just the new data since the previous revision\. It is even possible that each revision has completely different data\. What data to provide in each revision is up to the data provider\.

When you subscribe to a product, you have access to all data sets in the product\. When the data provider creates the offer, they give you access to 0 or more historical revisions, up to all historical revisions\. They can also give you access to future revisions that are made available during your subscription period\. The terms of the subscription are shown on the product details page in the AWS Data Exchange console\.

After you subscribe to a product containing Amazon S3 objects, you can manually export each revision or asset individually, or you can select to automatically export new revisions to your Amazon S3 buckets \(up to 5 buckets maximum\) when the provider publishes new revisions\. For more information, see [Subscribing to a product containing file\-based data](subscribing-to-product.md#subscribing-to-data-product)\. For more information about how to export revisions, see [Exporting revisions](jobs.md#exporting-revisions)\.

After you subscribe to a product containing an Amazon API Gateway API, you can view and invoke the data provider's API\. For more information, see [Subscribing to a product containing APIs](subscribing-to-product.md#subscribing-to-API-product)\.

After you subscribe to a product containing Amazon Redshift datashares, you get access to query the data in Amazon Redshift\. For more information, see [Subscribing to a product containing Amazon Redshift datashares \(preview\)](subscribing-to-product.md#subscribing-to-Redshift-product)\. 