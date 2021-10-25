# Create private offers<a name="private-offer-configuration"></a>

As a data provider, you can provide your data product to a subscriber at terms that are different from the offer terms available to the general public\. For products that are not publicly visible, your private offers are the only terms available to customers, and only customers you create private offers for can see the product\. Private offers allow you to create a custom offer for one or more AWS accounts\. A private offer can be different from other offers in any dimension, including price, duration, payment schedule, data subscription agreement, or refund policy\.

As a provider, after you have created a product, you can then create a private offer and make it available to a group of subscribers of your choosing\. For publicly visible products, you must create a public offer before you can create a private offer\.

**To create a private offer**

1. Sign in to the AWS Management Console and open the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane of the [console](https://console.aws.amazon.com/dataexchange), choose **Products**, and then choose the product for which you want to make a private offer\.

1. From the **Private offer** tab, choose **Create**\.

1. On the **Select Offer Type **page, select **Private offer** or **Renewed private offer**, and choose **Next**\.
**Note**  
Choose **Renewed private offer** if this is a renewal of an expired private offer or a pre\-existing subscription that is being upgraded on AWS Data Exchange\. If you choose this option, AWS might audit and verify that your offer is a renewal or upgrade\. If AWS is unable to do so, then we may revoke the offer and entitlements to your subscribers\.

1. Under **Subscriber AWS account ID**, enter the 12\-digit account number of the account you are creating a private offer for\. Because a single private offer can be extended to multiple accounts, you can add more than one account\.

1. Under **Description**, provide a short description of the account \(for example, the company name of the account\)\.

1. Under **Pricing and duration**, provide the offer details, including the duration and pricing information\.

1. Choose the **Specify payment schedule** check box if you want to distribute the **Total price** to the subscriber over multiple payments\. You can add an **Upfront payment** that will be invoiced at the time of subscription\. You can then choose for the subscriber to make additional monthly or custom payments\. If you choose the **Monthly** option, the dates are automatically populated\. If you choose the **Custom** option, you must enter the invoice dates \(up to 36 payments\)\. 
**Note**  
The **Offer expiration date** is the date by which the subscriber must accept the offer\. The private offer is no longer available for subscribing if it is not accepted by this date\.  
The expiration date must be before the second payment\.  
If you need to expire an offer already created prior to the expiry date, you can return to the offer page, and choose **Expire**\. This will expire the offer for all potential subscribers\.

1. Provide US sales tax and use settings, data subscription agreement, auto\-renewal settings, and support information\.

1. Choose **Next**\. If you selected **Renewed private offer**, you must select the check box to indicate that you acknowledge the terms of the renewed private offer\. 

1. Make sure that the information is correct, and then choose **Publish**\.
**Note**  
After you create the private offer, you can edit all of the fields except for the price and invoice dates\.