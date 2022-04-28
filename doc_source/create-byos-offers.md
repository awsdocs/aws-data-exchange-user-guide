# Create Bring Your Own Subscription offers<a name="create-byos-offers"></a>

As a data provider, you might already have subscribers for your data products\. Bring Your Own Subscription \(BYOS\) offers allow you to migrate and fulfill existing subscriptions with AWS customers at no additional cost\.

With BYOS offers, any billing relationship between you and your subscribers continues\. BYOS offers are not subject to fulfillment fees\. Subscribers receive an AWS Marketplace invoice for the subscription with no charge\. After you create a BYOS offer, we review it and contact you if we have any issues or questions\.

Because the lifecycle of the subscription begins outside of AWS Data Exchange, the workflow for migrating an existing subscription to AWS Data Exchange using BYOS requires collaboration between you and the subscriber\.

**Important**  
With BYOS offers, you're migrating a subscription that pre\-dates the availability of this product on AWS\. AWS might verify your BYOS offer with the existing subscription agreement\. If AWS cannot verify your BYOS offer, the offer and entitlements might be revoked without notice\.

Before creating or accepting a BYOS offer on AWS Data Exchange, the provider and subscriber should perform the following steps together:

**Prerequisites**

1. The provider and the subscriber contact each other about implementing a BYOS AWS Data Exchange solution\.

1. The subscriber provides the AWS account ID that they want to use to subscribe to data products on AWS Data Exchange\.

If you are the provider, follow these steps to create the BYOS offer\.

**To create a BYOS offer**

1. Open your web browser and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. In the navigation pane, under **Publish data**, choose **Products**\.

1. Choose the product that you want to create the BYOS offer for by selecting the option button next to the product name in the **Products** list\.

1. From **Actions**, choose **Create custom offer**\.

1. On the **Select offer type** page, for **Offer types**, select the Bring Your Own Subscription \(BYOS\) option and then choose **Next**\.

1. On the** Enter pre\-existing subscription details** page, for **Existing agreement**, choose **Add file** to upload your pre\-existing subscription and verify that the agreement pre\-dates when you created the product on AWS\.

1. For **Pre\-existing subscription start date**, choose the calendar icon and select the start date\.

1. For **Duration**, enter the number of months applicable\.

1. On **Auto renew terms**, select **Yes** or **No** to specify if the pre\-existing agreement included auto\-renewal upon expiry of the current subscription\.

1. In **Refund policy**, enter information regarding the refund policy stated in your pre\-existing subscription agreement and then choose **Next**\.

1. On the** Enter subscriber details** page, for **Subscriber details**, enter the subscriber's 12\-digit **AWS Account ID** and a **Description** and then choose **Next**\.

1. On the **Review & publish** page, verify all of the information\. Choose **Edit** to make changes to sections if needed\.

1. In the **Acknowledgement** section, select the check box to acknowledge that you're migrating a pre\-existing subscription that pre\-dates the availability of this product on AWS\.

1. Choose **Publish**\.

**Note**  
Auto\-renewal settings can't be changed after the BYOS offer is created\. Only one AWS account can be added to a BYOS\. If multiple accounts are required, create additional BYOS offers\.