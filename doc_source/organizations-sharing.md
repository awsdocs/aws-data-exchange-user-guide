# Sharing license subscriptions in an organization<a name="organizations-sharing"></a>

When you subscribe to AWS Data Exchange products, an agreement is created that grants you license to use those products\. If your AWS account is a member of an organization, you can share that license for AWS Data Exchange products with the other accounts in that organization\.

**Note**  
For more information about AWS Organizations, see the [AWS Organizations User Guide](https://docs.aws.amazon.com/organizations/latest/userguide/)\.

The following topics outline the process of sharing the licenses across accounts\.

**Topics**
+ [Prerequisites for license sharing](#license-sharing-prereqs)
+ [Viewing your licenses](#view-share-licenses)
+ [Sharing your licenses](#share-licenses)

## Prerequisites for license sharing<a name="license-sharing-prereqs"></a>

Before you can share licenses for data products, you must first set up license sharing for your organization\. Complete the following tasks to set up license sharing for your organization:
+ Give AWS Marketplace permission to manage licenses on your behalf so that it can create the associated license grants when you purchase or share your licenses\. For more information, see [Service\-linked roles for AWS Marketplace](https://docs.aws.amazon.com/marketplace/latest/buyerguide/buyer-using-service-linked-roles.html) in the *AWS Marketplace Buyer Guide*\.
+ Set up AWS License Manager for first use\. For more information, see [ Getting started with AWS License Manager](https://docs.aws.amazon.com/license-manager/latest/userguide/getting-started.html) in the *AWS License Manager User Guide*\.

## Viewing your licenses<a name="view-share-licenses"></a>

The following topics outline the process of viewing your licenses\.

**Topics**
+ [Viewing all licenses](#view-all-licenses)
+ [Viewing a single license](#view-single-licenses)

### Viewing all licenses<a name="view-all-licenses"></a>

You can use the AWS License Manager console to view all of the licenses for AWS Data Exchange products that you purchased\.

**To view all licenses for your subscribed products**

1. Sign in to the [AWS Management Console](https://console.aws.amazon.com/marketplace/)\.

1. Open the [AWS License Manager console](https://console.aws.amazon.com/license-manager)\.

1. In the left navigation pane, choose **Granted licenses**\.

1. View all the licenses for your subscribed products\.

### Viewing a single license<a name="view-single-licenses"></a>

You can use the AWS Data Exchange console to view a single license for an AWS Data Exchange product that you purchased\.

**To view a license for a single subscription**

1. Sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. Under ****My subscriptions****, choose ****Subscriptions****\.

1. Choose a subscription\.

   

1. Under **License**, choose a link\.

1. View the details on the **License detail** page\.

## Sharing your licenses<a name="share-licenses"></a>

You can manage and share your licenses with other accounts in your organization by using AWS License Manager\.

For more details about using License Manager with AWS managed licenses, see [ Granted licenses](https://docs.aws.amazon.com/license-manager/latest/userguide/granted-licenses.html) and [Seller issued licenses](https://docs.aws.amazon.com/license-manager/latest/userguide/granted-licenses.html) in the *AWS License Manager User Guide*\.