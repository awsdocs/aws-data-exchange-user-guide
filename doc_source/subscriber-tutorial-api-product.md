# Tutorial: Subscribe to AWS Data Exchange for APIs \(Test Product\) on AWS Data Exchange<a name="subscriber-tutorial-api-product"></a>

AWS Data Exchange for APIs \(Test Product\) is a free product that is made available to subscribers to understand how to interact with an AWS Data Exchange product containing API data sets\. You can use this product for testing purposes and to learn how to make API calls to providers in order to retrieve API\-based data\.

AWS Data Exchange for APIs \(Test Product\) contains an API data set named **AWS Data Exchange for APIs \(Test Product\)** that is in the US East \(N\. Virginia\) Region\.

## Subscribing to AWS Data Exchange for APIs \(Test Product\) on AWS Data Exchange<a name="subscribe-to-API-test-product"></a>

The following procedure shows how to browse the AWS Data Exchange catalog to find and subscribe to AWS Data Exchange for APIs \(Test Product\)\.

**To find and subscribe to AWS Data Exchange for APIs \(Test Product\)**

1. Open and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, choose **Browse catalog**\.

1. From the search bar, enter **AWS Data Exchange for APIs** and press **Enter**\. 

1. Choose the **AWS Data Exchange for APIs \(Test Product\)** and view its details page\.

1. In the top right corner, choose **Continue to subscribe**\. 

1. Choose the **Product offer**\.
**Note**  
AWS Data Exchange for APIs \(Test Product\) is a free product\.

1. Review the **Subscription terms**, **Data sets**, and **Support information**\.

1. Choose whether to enable **Offer auto\-renewal** for the subscription\. 
**Note**  
AWS Data Exchange for APIs \(Test Product\) doesn't require subscription verification, but some products do\. For more information, see [Subscription verification for subscribers](subscription-verification-sub.md)\.

1. Choose **Subscribe**\.

It can take a few minutes for your subscription to become active after you choose **Subscribe**\. Navigating away from this page before your subscription becomes active will not prevent the subscription from processing\. 

## Using AWS Data Exchange for APIs \(Test Product\)<a name="tutorial-use-api-test-product"></a>

You can interact with AWS Data Exchange for APIs \(Test Product\) in the following ways:

**Topics**
+ [Viewing the API](#tutorial-view-api)
+ [Downloading the API specification](#tutorial-download-api-spec)
+ [Making an API call](#tutorial-make-api-call-console)

### Viewing the API<a name="tutorial-view-api"></a>

**To view the API**

1. Open and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **My subscriptions**, choose **Entitled data**\.

1. Choose the product titled ****AWS Data Exchange** for APIs \(Test Product\)** and then choose the **AWS Data Exchange for APIs** data set\.

1. Under the **Revisions** tab, choose a revision\.

1. Under **API assets**, choose the API\.

1. View the **Asset overview**\.

1. Follow the guidance in the **Integration notes** to call the API\.

### Downloading the API specification<a name="tutorial-download-api-spec"></a>

**To download the API specification**

1. Open and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **My subscriptions**, choose **Entitled data**\.

1. Choose the product titled ****AWS Data Exchange** for APIs \(Test Product\)** and then choose the **AWS Data Exchange for APIs** data set\.

1. Under the **Revisions** tab, choose a revision\.

1. Under **API assets**, choose the API\.

1. On the **OpenAPI 3\.0 specification**, choose **Download API specification**\.

   The specification is downloaded onto your local computer\. You can then export the asset to a third\-party tool for SDK generation\.

### Making an API call<a name="tutorial-make-api-call-console"></a>

You can call a single endpoint in the AWS Data Exchange console\.

**To make an API call from the console**

1. Open and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **My subscriptions**, choose **Entitled data**\.

1. Choose the product titled ****AWS Data Exchange** for APIs \(Test Product\)** and then choose the **AWS Data Exchange for APIs** data set\.

1. Under the **Revisions** tab, choose the revision\.

1. Under **API assets**, choose the API\.

   You will see the sample **Code structure** and **OpenApi 3\.0 specification** to structure your API request, which you can use in the AWS Command Line Interface to call the API\. 

1. Under **Integration notes**, choose **Copy** to copy the **Code structure** and then paste it into the AWS CLI\.

1. Replace the sample values with the parameter key\-value pairs you need using the information in the specification documentation\.

   Following is a sample API request for **AWS Data Exchange for APIs \(Test Product\)**\.

   ```
   aws dataexchange send-api-asset \
     --data-set-id 8d494cba5e4720e5f6072e280daf70a8 \
     --revision-id b655d5be3da04fcbdca21a5a2932d789 \
     --asset-id 8550cfab16b444a794402f2c3f11eae1 \
     --method POST \
     --path "someresource" \
     --query-string-parameters 'param1=value1,param2=value2' \
     --request-headers 'header=header_value' \
     --body "{\"body_param\":\"body_param_value\"}"
   ```