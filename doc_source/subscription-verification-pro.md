# Subscription verification for providers<a name="subscription-verification-pro"></a>

As a provider, you have the option to enable subscription verification for your data product\. When enabled, potential subscribers must complete a form about who they are and what they intend to do with the data before they can subscribe\. You must review and approve each request from prospective subscribers\.

**Note**  
Subscription verification is automatically enabled for all public products from Extended Provider Program providers that contain non\-public, personal information\.

Approving subscription requests to your product can be useful when you have restricted or regulated products, or you have products that you want to limit access to\.

The form requires the following information:
+ Prospective subscriber's contact details, including contact name, company name, and email address
+ Prospective subscriber's intended use case
+ Prospective subscriber's AWS account ID

**Important**  
The subscriber must enter information in each field, but AWS Data Exchange doesn't review or validate the information\. You're solely responsible for reviewing and verifying the information that the subscriber provides\.

If you change the product offer terms after a subscriber makes the request, the terms for that subscriber reflect the terms as they were at the time of the request, not the updated terms\. Examples of changes to terms include the price, refund policy, or data subscription agreement\. If you changed the product offer terms after the request was submitted, a message is displayed in the approval pane of the AWS Data Exchange console to indicate there is a difference between current terms and the terms in place when the request was made\. 

The AWS Data Exchange console maintains a history of requests\. You control when you delete the subscriber’s contact details and personally identifiable information \(PII\)\.

 You can view, approve, or decline all subscription verification requests for all of your products on the **Subscription verification** page under **Publish data** on the AWS Data Exchange console\. 

**Note**  
Each subscription request is uniquely identified using its ID\. The ID is visible to both the provider and the subscriber\. You can use the subscription request ID in your communications with the subscriber\.

## Email notifications<a name="email-notifications-pro"></a>

You will receive an email message to your AWS account email address to notify you when a request is received, or when its status has changed to cancelled or expired\. Although most subscription request status changes result in an email notification, the delivery of these email messages is on a best\-effort basis\.

**Note**  
You will not receive email notifications for subscription request status changes that you have initiated yourself \(for example, when you approve a subscription\)\.

## Approve or decline requests<a name="approve-or-decline-requests"></a>

After you receive the subscription request, you have 45 days to approve or reject it\. If you don't approve the request in that period of time, the request expires\. Potential subscribers can resubmit a rejected request at any time, any number of times\.

**Important**  
The subscriber information you collect through subscription verification must be used in accordance with AWS Marketplace Terms and Conditions\.

### Approving requests<a name="approve-request"></a>

**To approve a subscription request**

1. Open your web browser and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **Publish data**, choose **Subscription verification**\.

1. From **Subscription verification**, choose **View pending requests**\.

1. Choose **Approve**\.

### Approving requests for products containing APIs<a name="approve-add-custom-metadata"></a>

You can approve a subscription request for a product containing APIs\. You can also add custom metadata to product containing APIs that is sent in the header of each AWS Data Exchange request for the specific subscription\. The custom metadata isn't visible to subscribers\.

**To approve a subscription request for a product containing APIs**

1. Open your web browser, and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **Publish data**, choose **Subscription verification**\.

1. From **Subscription verification**, choose **View pending requests**\.

1. Choose **Approve and add custom API metadata**\.

1. On the modal, enter the key\-value pair and then choose **Approve and add custom API metadata**\.
**Note**  
You can add additional key\-value pairs if necessary by choosing **Add** and then entering an additional key\-value pair\.

1. You are returned to the **Subscription verification** page\. A message informs you that you have successfully accepted the subscription request\.

1. To view the custom metadata, go to **Products**, select your product with APIs and then select the **Subscriptions** tab\.

1. Under **Public and custom subscriptions**, you can:

   1.  Select the subscription, and choose **View custom metadata** to see the key\-value pairs you added\.

   1.  Select the subscription, and choose **Edit custom metadata** to edit, add, or remove the key\-value pairs for this subscription\.
**Note**  
If you add three or more key\-value pairs, the **Custom metadata for APIs** column in the **Public and custom subscriptions** table displays the first key\-value pair, and then displays the number of key\-value pairs underneath the first key\-value pair\. For example: **`keyExample-valueExample` \+2 more**

### Declining requests<a name="decline-request"></a>

**To decline a subscription request**

1. Open your web browser and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **Publish data**, choose **Subscription verification**\.

1. From **Subscription verification**, choose **View pending requests**\.

1. Choose **Decline**\.