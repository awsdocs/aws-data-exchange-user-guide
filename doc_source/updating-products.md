# Updating products<a name="updating-products"></a>

The following sections describe how to update your products\. The instructions are written with the assumption that you're a provider who is familiar with [Data in AWS Data Exchange](data-sets.md)\. After you publish a product, you can edit the product's details and its public offer\. You can also update the underlying data sets by publishing new revisions to subscribers\. For more information, see [Revisions](data-sets.md#revisions)\.

**Topics**
+ [Updating product and offer details](#update-product-details)
+ [Updating a data dictionary](#update-data-dictionary)
+ [Updating a sample](#update-sample)
+ [Updating custom metadata](#update-custom-metadata)
+ [Publishing a new data set revision using automatic revision publishing](#dynamically-updated-products)
+ [Publishing a new data set revision using manual revision publishing](#manual-publish-revision)
+ [Unpublish a product](#unpublish-product)
+ [Removing a revision](#remove-revision)
+ [Migrating an existing product to automatic revision publishing](#migrate-product)
+ [Revoking revisions](#revoking-revisions)

## Updating product and offer details<a name="update-product-details"></a>

After you publish a product, you can use the AWS Data Exchange console to edit the product details\. You can also edit the product's public or custom offers and change the offer terms\. When you update your product's offer terms, subscribers with an active subscription keep their existing offer terms as long as their subscription is active\. Subscribers who have chosen auto\-renewals use the new offer terms\.

Keep the following in mind when you update products:
+ You can't remove or edit a subscription duration in your offers\. This ensures that existing subscribers retain the ability to renew\. If you no longer want to offer a specific subscription duration, you can unpublish your existing product and then publish a new product\. For more information, see [Unpublish a product](#unpublish-product)\.
+ You can't remove data sets from a product after it is published, regardless of how many subscribers have subscribed to your product\.

**To update a product, data set, or offer details**

1. Open your web browser and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **Publish data**, choose **Products**\.

1. From **Products**, choose the product you want to update\. Make sure its status is **Published**\.

1. From **Product details**, choose **Edit**, and then follow the instructions to edit the product\.

1. From **Data sets**, under **Sensitive information**, choose **Edit**, and then follow the instructions to edit the information\.

1. From **Data evaluation**, update the data dictionary or sample by selecting the option button next to the data dictionary or sample **Name** and then choosing **Actions**\. For more information, see [Updating a data dictionary](#update-data-dictionary) and [Updating a sample](#update-sample)\.

1. Configure your offer, depending on the offer type:
   + If your product is a public offer, from **Public offer**, choose **Edit**, and then follow the instructions to edit the public oﬀer\.
   + If your product is a custom offer, from **Custom offers**, choose **Edit**, and then follow the instructions to edit the custom oﬀer\.
   + If your product is a private offer, from **Private offers**, choose **Edit**, and then follow the instructions to edit the private offer\.

1. Choose **Update**\.

## Updating a data dictionary<a name="update-data-dictionary"></a>

You can update a data dictionary by first removing the existing data dictionary and then uploading a new one\.

**To update a data dictionary**

1. Open your web browser and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **Publish data**, choose **Products**\.

1. From **Products**, choose the product you want to update and confirm its status is **Published**\.

1. Choose the **Data evaluation** tab\.

1. Under **Data dictionary and samples**, expand the data set by choosing the plus icon, and then choose the data dictionary by selecting the option button next to the data dictionary **Name**\.

   1. Choose **Actions**, and then **Remove data dictionary**\.

      The data dictionary is removed\.

   1. Select the option button next to the data set, choose **Actions**, and then **Upload data dictionary**\.

   1. Choose **Add file**\.

   1. Select a new data dictionary and then click **Open**\.

   1. Choose **Upload**\.

1. \(Optional\) Choose the data dictionary by selecting the option button next to the data dictionary **Name**, choose **Actions**, and then choose **Download data dictionary \(CSV\)** to download the data dictionary to your computer\.

## Updating a sample<a name="update-sample"></a>

**To update a sample**

1. Open your web browser and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **Publish data**, choose **Products**\.

1. From **Products**, choose the product you want to update and confirm its status is **Published**\.

1. Choose the **Data evaluation** tab\.

1. Under **Data dictionary and samples**, select the option button next to a data set\.

1. Choose **Actions**, and then choose **Add samples**\.

   1. Choose **Upload samples**\.

   1. Select a new sample from your computer, and then choose **Open**\.

   1. Enter an optional **Description**, and then choose **Add**\.

1. \(Optional\) Select the option button next to the sample **Name**, choose **Actions**, and then choose one of the following actions:
   + **Download selected sample**
   + **Preview sample \(CSV only\)**
   + **Remove selected sample**

## Updating custom metadata<a name="update-custom-metadata"></a>

After you publish a product, you can use the AWS Data Exchange console to edit the product's custom metadata\.

**To update custom metadata**

1. Open your web browser and sign in to the AWS Data Exchange console\.

1. From the left navigation pane, under **Publish data**, choose **Products**\.

1. From **Products**, choose the product you want to update\. Make sure its status is **Published**\.

1. \(Optional\) From **Subscriptions**, choose **View custom metadata**, and view the metadata, and then choose **Close**\.

1. From **Subscriptions**, choose **Edit custom metadata**, and then follow the instructions to edit the metadata\.

1. Choose **Save**\.

## Publishing a new data set revision using automatic revision publishing<a name="dynamically-updated-products"></a>

AWS Data Exchange supports dynamically updated products\. Subscribers subscribe to the product for a certain duration and access all of the published data sets as long as their subscription is active\. For example, a provider might want to provide a product that contains daily closing stock prices for US equities, which would be updated every day with the day’s closing prices\. You can create and finalize new revisions that will be available in your product’s data sets, or add new data sets to your product\. 

Your product includes some or all historical and future revisions as part of a subscription\. For more information, see [Revision access rules](product-details.md#best-practices-revisions)\.

You can use the AWS Data Exchange console or the AWS Marketplace Catalog API to update your products\. For more information, see [Using AWS Data Exchange with the AWS Marketplace Catalog API](appendices.md)\.

In the following procedure, you create and finalize a new revision for a data set that has already been published using the AWS Data Exchange console\. The data set revision is then automatically published to all products the data set belongs to\. For more information, see [Revisions](data-sets.md#revisions)\.

**Important**  
A provider can revoke subscriber access to a revision and then delete the assets of the revision using the console or the AWS Data Exchange API\. For more information, see [Revoking revisions](#revoking-revisions)\.

**To publish a new data set revision to a product**

1. Open your web browser and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. On the left side navigation pane, under **Publish data**, choose **Owned data sets**\.

1. In **Owned data sets**, choose the data set you want to update\. 

1. Navigate to the **Products** tab to make sure that the data set is associated with a published product\.

1. From the **Revisions** tab, choose **Create revision** to open the **Create revision** page\.

   1. \(Optional\) Under **Revision settings**, provide an optional comment for your revision that describes the purpose of the revision\. 

   1. \(Optional\) Under **Add tags – optional**, add tags associated with the resource\.

   1. Choose **Create revision**\.

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
As of July 22, 2021, new and existing providers can automatically publish revisions to data sets\. All new products on AWS Data Exchange default to automatic revision publishing\. If you have created existing products on AWS Data Exchange before July 22, 2021, you need to migrate them to automatic revision publishing\.  
For more information, see [Migrating an existing product to automatic revision publishing](#migrate-product)\.

In the following procedure, you create, finalize, and manually publish a new revision for a data set that has already been published using the AWS Data Exchange console\. For more information, see [Revisions](data-sets.md#revisions)\.

**To manually publish a data set revision to a product**

1. Open your web browser and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

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

1. Open your web browser and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **Publish data**, choose **Products**\.

1. From **Products**, choose the product you want to remove\. Make sure its status is **Published**\.

1. From **Product overview**, choose **Unpublish**, and then follow the instructions to unpublish the product\.
**Important**  
This action can't be undone\.

After you complete these steps, your product's status is **Unpublished**\. An unpublished product can't be published again, but you can create a new product \(with a new product ID\) that has the same data sets, product details, and offer details\.

## Removing a revision<a name="remove-revision"></a>

A provider can revoke subscriber access to a revision and then delete the assets of the revision using the console or the AWS Data Exchange API\. For more information, see [Revoking revisions](#revoking-revisions)\.

You can edit or delete a revision after it's finalized, but before you add it to a product\. For more information, see the following topics:
+ [Edit a revision](publishing-products.md#edit-api-revision)
+ [Delete a revision](publishing-products.md#delete-api-revision)

## Migrating an existing product to automatic revision publishing<a name="migrate-product"></a>

**Important**  
As of July 22, 2021, new and existing providers can automatically publish revisions to data sets\. All new products on AWS Data Exchange default to automatic revision publishing\. If you have created existing products on AWS Data Exchange before July 22, 2021, you need to migrate them to automatic revision publishing\.  
If you have existing products, you can migrate your existing products from manual revision publishing to automatic revision publishing\. Automatic revision publishing simplifies the data set revision publishing process by making your revision immediately available to subscribers when you finalize it\.

**Important**  
The AWS Identity and Access Management \(IAM\) permission `dataexchange:StartChangeSet` is required for self\-service and bulk migration\.

After you have migrated all of your existing products, any future products you create will use automatic revision publishing\.

**Topics**
+ [Migrating a single product](#migrate-existing-product)
+ [Migrating all products](#migrate-all-products)

### Migrating a single product<a name="migrate-existing-product"></a>

**To migrate a single existing product to automatic revision publishing**

1. Open your web browser and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **Publish data**, choose **Products**\.

1. On the **Products** pane, select a product that has **No** under the **Automatic revision publishing** column\.

1. Select the **Actions** dropdown, and then choose **Migrate product to automatic revision publishing**\.

1. Read the information in the **Migrate** dialog box, and then choose **Migrate**\.

1. View the success banner on the top of the **Product detail** page and **Yes** under the **Automatic revision publishing** column\.

1. Repeat for any remaining products\.

### Migrating all products<a name="migrate-all-products"></a>

**To migrate all existing products to automatic revision publishing**

1. Open your web browser and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **Publish data**, choose **Products**\.

1. On the **Migrate product to automatic revision publishing** dialog box that appears, choose **Option 2: Submit a support ticket for bulk migration**\.

1. Click **Create support ticket**\. 

1. Fill out your support ticket request, and the AWS Data Exchange team will migrate all products in your account\.

## Revoking revisions<a name="revoking-revisions"></a>

As a provider, you can revoke subscriber access to a specific revision at any time\. This action is typically done by providers for compliance reasons\. Revoking a revision doesn't delete the underlying assets\. After you have revoked the revision, all subscribers receive an Amazon EventBridge \(formerly known as CloudWatch Events\) notification that the revision has been revoked\. Subscribers can then view the reason for the revoked revision on the AWS Data Exchange console\. Subscribers can’t export or query the data within a revoked revision\.

To be able to revoke revisions, providers who manage their own IAM policies must add `dataexchange:RevokeRevision` as a new action\. Providers who use the [AWS Data Exchange managed policies](https://docs.aws.amazon.com/data-exchange/latest/userguide/security-iam-awsmanpol.html) don't need to make any changes\.

After a revision is revoked, you can delete the assets of the revision by using the console or the AWS Data Exchange `DeleteAsset` API operation\. 

**Topics**
+ [Revoking a revision \(AWS CLI\)](#revoke-rev-sdk)
+ [Revoking a single revision as a provider \(console\)](#revoke-rev-single)
+ [Revoking multiple revisions as a provider \(console\)](#revoke-rev-multi)
+ [Editing a revocation reason as a provider \(console\)](#edit-revoked-rev)
+ [Viewing revoked revisions as a subscriber \(console\)](#view-revoked-rev)

### Revoking a revision \(AWS CLI\)<a name="revoke-rev-sdk"></a>

**To revoke a revision \(AWS CLI\)**

1. Use the `revoke-revision` command to revoke a revision\. 

   ```
   $ aws dataexchange revoke-revision \
   --data-set-id $DATA_SET_ID \
   --revision-id $REVISION_ID \
   --comment 'Revoking Revision Example'
   
   {
   "Id": "ab7859881EXAMPLEdd3e8a4b88fc6a8d",
   "Arn": "arn:aws:dataexchange:us-east-1:427362365172:data-sets/$DATA_SET_ID/revisions/$REVISION_ID",
   "Comment": "Revoking Revision Example",
   "CreatedAt": "2022-03-08T18:54:20.746Z",
   "UpdatedAt": "2022-03-09T20:28:53.105Z",
   "DataSetId": "24d30f8446a878237c35d011e7b22d0b",
   "Finalized": true,
   "Revoked": true,
   "RevokedAt": "2022-03-09T20:28:53.105Z",
   "RevocationComment": "revoking revision example"
   }
   ```

1. After a revision is revoked, you can delete the assets of the revision using the AWS Data Exchange `DeleteAsset` API operation\. 

### Revoking a single revision as a provider \(console\)<a name="revoke-rev-single"></a>

**To revoke revision as a provider \(console\)**

1. Open your web browser and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. In the left side navigation pane, for **Publish data**, choose **Owned data sets**\.

1. In **Owned data sets**, choose the data set that has the revision you want to revoke\.

1. On the **Revisions** tab, under **Revisions**, choose the revision\.

1. On the revision page, under **Revision overview**, for **Actions**, choose **Revoke**\.

1. In the **Revoke revision** dialog box, enter a short description of your reason for revoking the revision\. Subscribers will see this description\.

1. Choose **Revoke**\.

   The **Status** of the revision is set to **Revoked**\.
**Warning**  
This revokes the revision and all of its assets\. Subscribers can view the reason for revocation but can’t access or export the assets\. This action can't be undone\.

1. After a revision is revoked, you can delete the assets of the revision by navigating to the revision page, selecting the assets you want to delete in the **Imported assets** table, and then choosing **Delete**\.

To edit the reason for a revoked revision, see [Editing a revocation reason as a provider \(console\)](#edit-revoked-rev)\.

### Revoking multiple revisions as a provider \(console\)<a name="revoke-rev-multi"></a>

**To revoke multiple revisions as a provider \(console\)**

1. Open your web browser and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. In the left side navigation pane, for **Publish data**, choose **Owned data sets**\.

1. In **Owned data sets**, choose the data set that has the revisions you want to revoke\.

1. On the **Revisions** tab, choose up to 10 revisions\.

1. Choose **Revoke**\.

1. In the **Revoke \{x\} revisions** dialog box, enter a short description of your reason for revoking the revisions\. Subscribers will see this description\. Then, choose **Revoke**\.

   The **Status** of the revisions are set to **Revoked**\.
**Warning**  
This revokes the revisions and all of the assets\. Subscribers can view the reason for revocation but can’t access or export the assets\. This action can't be undone\.

1. After a revision is revoked, you can delete the assets of the revision by navigating to the revision page, selecting the assets you want to delete in the **Imported assets** table, and then choosing **Delete**\.

To edit the reason for a revoked revision, see [Editing a revocation reason as a provider \(console\)](#edit-revoked-rev)\.

### Editing a revocation reason as a provider \(console\)<a name="edit-revoked-rev"></a>

As a provider, you can edit the reason for the revocation after the revision has been revoked\.

**To edit a revocation revision as a provider \(console\)**

1. Open your web browser and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. In the left side navigation pane, for **Publish data products**, choose **Owned data sets**\.

1. In **Owned data sets**, choose the data set that has the revision you revoked\.

1. On the **Revisions** tab, choose the revoked revision\.

1. On the revision page, choose **Edit revocation reason**\.

1. In the **Edit revocation revision** dialog box, enter a short description of your reason for revoking the revision\.

1. Choose **Save**\.

   The **Status** of the revision is set to **Revoked**\.

   The updated revocation reason is displayed on the revision page\.

### Viewing revoked revisions as a subscriber \(console\)<a name="view-revoked-rev"></a>

**To view a revoked revision as a subscriber \(console\)**

1. Open your web browser and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **My subscriptions**, choose **Entitled data**\.

1. Under **Products**, choose a product, and then expand the data set under the product to see a list of revisions\.

1. On the data set page, under the **Revisions** tab, view the **Status** of the revision \(**Published** or **Revoked**\)\.

1. Choose a revision\.

1. View the revision reason on the top of the revision detail page\.