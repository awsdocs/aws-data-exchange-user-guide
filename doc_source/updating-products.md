# Updating products<a name="updating-products"></a>

The following sections describe how to update your products\. The instructions are written with the assumption you're a provider who's familiar with [Data in AWS Data Exchange](data-sets.md)\. After you publish a product, you can edit the product's details and its public offer\. You can also update the underlying data sets by publishing new revisions to subscribers\. For more information, see [Revisions](data-sets.md#revisions)\.

## Updating product and offer details<a name="update-product-details"></a>

After you publish a product, you can use the AWS Data Exchange console to edit the product details\. You can also edit the product's public or custom offers and change the offer terms\. When you update your product's offer terms, subscribers with an active subscription keep their existing offer terms as long as their subscription is active\. Subscribers who have chosen auto\-renewals use the new offer terms\.

Keep the following in mind when you update products:
+ You can't remove or edit a subscription duration in your offers\. This ensures that existing subscribers retain the ability to renew\. If you no longer want to offer a specific subscription duration, you can unpublish your existing product and then publish a new product\. For more information, see [Unpublish a product](#unpublish-product)\.
+ You can't remove data sets from a product after it is published, regardless of how many subscribers have subscribed to your product\.

**To update a product, data set, and/or offer details**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **Publish data**, choose **Products**\.

1. From **Products**, choose the product you want to update\. Make sure its status is **Published**\.

1. From **Product details**, choose **Edit**, and then follow the instructions to edit the product\.

1. From **Data sets**, Under **Sensitive information**, choose **Edit**, and then follow the instructions to edit the information\.

1. If your product is a public offer, from **Public offer**, choose **Edit**, and then follow the instructions to edit the public oﬀer\.

1. If your product is a public offer, from **Custom offers**, choose **Edit**, and then follow the instructions to edit the custom oﬀer\.

1. If your product is a private offer, fFrom **Private offers**, choose **Edit**, and then follow the instructions to edit the offer\.

1. Choose **Update**\.

## Publishing a new data set revision using automatic revision publishing<a name="dynamically-updated-products"></a>

AWS Data Exchange supports dynamically updated products\. Subscribers subscribe to the product for a certain duration and access all of the published data sets as long as their subscription is active\. For example, a provider might want to provide a product that contains daily closing stock prices for US equities, which would be updated every day with the day’s closing prices\. You can create and finalize new revisions that will be available in your product’s data sets, or add new data sets to your product\. 

Your product includes some or all historical and future revisions as part of a subscription\. For more information, see [Revision access rules](product-details.md#best-practices-revisions)\.

You can use the AWS Data Exchange console or the AWS Marketplace Catalog API to update your products\. For more information, see [Using AWS Data Exchange with the AWS Marketplace Catalog API](appendices.md)\.

In the following procedure, you create and finalize a new revision for a data set that has already been published using the AWS Data Exchange console\. The data set revision is then automatically published to all products the data set belongs to\. For more information, see [Revisions](data-sets.md#revisions)\.

**Important**  
Any revision that is part of a product is immutable and can't be edited, changed, or deleted\. If you need to remove published content for compliance reasons, contact [ AWS Support](https://console.aws.amazon.com/support/home#/case/create?issueType=customer-service) or send an email message to [dataexchangehelp@amazon\.com](mailto://dataexchangehelp@amazon.com)\.

**To publish a new data set revision to a product**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. On the left side navigation pane, under **Publish data**, choose **Owned data sets**\.

1. In **Owned data sets**, choose the data set you want to update\. 

1. Navigate to the **Products** tab to make sure that the data set is associated with a published product\.

1. From the **Revisions** tab, choose **Create revision** to open the **Create revision** page\.

   1. \(Optional\) Under **Revision settings**, provide an optional comment for your revision that describes the purpose of the revision\. 

   1. \(Optional\) Under **Add tags – optional**, add tags associated with the resource\.

   1. Choose **Create**\.

      Your new revision is created\.

1. Under the **Jobs** section, choose either **Import from Amazon S3** or **Upload** \(to upload from your computer\), depending on if the assets you want to include are stored in an Amazon S3 bucket you own or on your local computer\.

   1. Follow the prompts, depending on your selection\. A job is started to import your asset into your data set\.

   1. After the job is ﬁnished, the **State** ﬁeld in the **Jobs** section is updated to **Completed**\.

1. Under **Revision overview**, review your revision and its assets, and then choose **Finalize**\.

The revision has been published to the product and is now available to subscribers\.

### Suggested approach for historical data<a name="historical-data-approach"></a>

Some dynamic products contain historical content that subscribers can access\. For example, if your product includes a 30\-year history of daily closing stock price for US equities, subscribers would get access to that data in addition to the dynamic updates every day\.

For these kinds of products that contain a historical record of data, a best practice is to publish all historical data in a single revision of the data set\. You can use the optional comment for the revision to indicate that this revision is a single upload of all data history from a specific date\. 

If the single historical revision contains a time series of multiple objects, you might consider labeling your object names to describe the underlying data periodicity\. For example, if your single revision of history contains 200 files each with a week of historical data, you can name each file with a date for the week the data history begins\.

### Suggested approaches for updates<a name="update-approach"></a>

You can dynamically update your data sets in a number of ways\. Here are three example approaches, all of which create a new revision for each update, but the content of the new revision is different\.
+ **Use a new revision for each update that contains only the items that have changed since the last revision** – Your revision size would be smaller because only those items that have changed are updated\. This approach is suitable for data sets for which the updates affect only a small subset of the data and subscribers are focused only on the items that have changed\.
+ **Use a new revision for each update that contains the updated data** – The new revision contains a full updated file\. All items are included in the new revision, including those that have not changed since the last revision\. This approach is convenient for subscribers who want to maintain a single up\-to\-date file for your data\. Subscribers export the latest revision's asset or assets to the same destination and override the previous file or files\.
+ **Use a new revision for each update that contains the full history and updated data** – The new revision contains the full history of the data, including the latest state of the data and the history of the previous revisions\. This approach is more storage\-heavy\. It's suitable for data sets for which subscribers are interested in the latest comprehensive view of the data's history, including any potential past corrections or adjustments\. In this approach, each revision is self\-suﬃcient and provides a full view of the data set history with no dependency on previous revisions\.

## Publishing a new data set revision using manual revision publishing<a name="manual-publish-revision"></a>

**Important**  
Beginning July 22, 2021, new and existing providers have the ability to automatically publish revisions to data sets\. All new products on AWS Data Exchange default to automatic revision publishing\. If you have created existing products on AWS Data Exchange before July 22, 2021, you need to migrate them to automatic revision publishing\.  
For more information, see [Migrating an existing product to automatic revision publishing](#migrate-product)\.

In the following procedure, you create, finalize, and manually publish a new revision for a data set that has already been published using the AWS Data Exchange console\. For more information, see [Revisions](data-sets.md#revisions)\.

**To manually publish a data set revision to a product**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. On the left side navigation pane, under **Publish data**, choose **Owned data sets**\.

1. In **Owned data sets**, choose the data set you want to update\. 

1. Navigate to the **Products** tab to make sure that the data set is associated with a published product\.

1. From the **Revisions** tab, choose **Create revision** to open the **Create revision** page\.

   1. \(Optional\) Under **Revision settings**, provide an optional comment for your revision that describes the purpose of the revision\. 

   1. \(Optional\) Under **Add tags – optional**, add tags associated with the resource\.

   1. Choose **Create**\.

      Your new revision is created\.

1. Under the **Jobs** section, choose either **Import from Amazon S3** or **Upload** \(to upload from your computer\), depending on if the assets you want to include are stored in an Amazon S3 bucket you own or on your local computer\.

   1. Follow the prompts, depending on your selection\. A job is started to import your asset into your data set\.

   1. After the job is ﬁnished, the **State** ﬁeld in the **Jobs** section is updated to **Completed**\.

1. Under **Revision overview**, review your revision and its assets, and then choose **Finalize**\.

   The revision is now read\-only and not available to subscribers\. To make it available to subscribers, you have to add the revision to a product and then publish it\.

1. Under **Products**, choose **Add to products**, or choose **Add to products** from the success banner at the top of the console\.

1. On the **Add to products** window, select the product to which the revision will be published, and then choose **Publish**\.

The revision has been published to the product and is now available to subscribers\.

## Unpublish a product<a name="unpublish-product"></a>

After your product is published, it's available for all to find and subscribe to, based on the product's visibility settings\. You can unpublish a product if you want to achieve any of the following results:
+ Remove a product you created for the [Publishing a new product](publishing-products.md) exercise\.
+ Clean up your resources\.
+ Remove a product from the publicly listed products on AWS Data Exchange\.
+ Stop subscribers from auto\-renewing your product\.

Keep the following in mind when you unpublish a product:
+ You can unpublish a product whenever you want\.
+ If you unpublish a product, it is no longer visible in the AWS Data Exchange catalog or on AWS Marketplace\.
+ Subscribers with an active subscription maintain access to the data product until the term of their subscription expires\.
+ Active subscriptions that expire after you have unpublished your product are not renewed, even if the subscriber has enabled auto\-renewal\.
+ Existing subscribers can still view the product details until their subscription expires\.

**To unpublish a product**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **Publish data products**, choose **Products**\.

1. From **Products**, choose the product you want to remove\. Make sure its status is **Published**\.

1. From **Product overview**, choose **Unpublish**, and then follow the instructions to unpublish the product\.
**Important**  
This action can't be undone\.

After you complete these steps, your product's status is **Unpublished**\. An unpublished product can't be published again, but you can create a new product \(with a new product ID\) that has the same data sets, product details, and offer details\.

## Removing a revision<a name="remove-revision"></a>

Any revision published to a product is immutable and can't be edited, changed, or deleted, unless it needs to be removed for compliance reasons\. Contact [ AWS Support](https://console.aws.amazon.com/support/home#/case/create?issueType=customer-service) or send an email message to [dataexchangehelp@amazon\.com](mailto://dataexchangehelp@amazon.com) for help\.

## Migrating an existing product to automatic revision publishing<a name="migrate-product"></a>

**Important**  
Beginning July 22, 2021, new and existing providers have the ability to automatically publish revisions to data sets\. All new products on AWS Data Exchange default to automatic revision publishing\. If you have created existing products on AWS Data Exchange before July 22, 2021, you need to migrate them to automatic revision publishing\.  
If you have existing products, you can migrate your existing products from manual revision publishing to automatic revision publishing\. Automatic revision publishing simplifies the data set revision publishing process by making your revision immediately available to subscribers when you finalize it\.

**Important**  
The AWS Identity and Access Management \(IAM\) permission `dataexchange:StartChangeSet` is required for self\-service and bulk migration\.

After you have migrated all of your existing products, any future products you create will use automatic revision publishing\.

## Migrating a single product<a name="migrate-existing-product"></a>

**To migrate a single existing product to automatic revision publishing**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **Publish data**, choose **Products**\.

1. On the **Products** pane, select a product that has **No** under the **Automatic revision publishing** column\.

1. Select the **Actions** dropdown, and then choose **Migrate product to automatic revision publishing**\.

1. Read the information in the **Migrate** dialog box, and then choose **Migrate**\.

1. View the success banner on the top of the **Product detail** page and **Yes** under the **Automatic revision publishing** column\.

1. Repeat for any remaining products\.

## Migrating all products<a name="migrate-all-products"></a>

**To migrate all existing products to automatic revision publishing**

1. Open your web browser and go to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **Publish data**, choose **Products**\.

1. On the **Migrate product to automatic revision publishing** dialog box that appears, choose **Option 2: Submit a support ticket for bulk migration**\.

1. Click **Create support ticket**\. 

1. Fill out your support ticket request, and the AWS Data Exchange team will migrate all products in your account\.