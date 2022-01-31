# Tutorial: Subscribe to AWS Data Exchange Heartbeat on AWS Data Exchange<a name="heartbeat"></a>

AWS Data Exchange Heartbeat \(Test product\) is a free product that subscribers can use to understand how to interact with an AWS Data Exchange product subscription\. You can use it for testing purposes and to get familiar with the AWS Data Exchange API and concepts\.

AWS Data Exchange Heartbeat contains a single data set named **Heartbeat**\. Approximately every 15 minutes, a new revision is published to this data set\.

## <a name="what-is-heartbeat"></a>

### Example content of a revision<a name="revision-example"></a>

Each new revision contains two assets:
+ Epoch asset
+ Manifest asset

### Epoch asset<a name="epoch-asset"></a>

Each AWS Data Exchange Heartbeat revision contains a JSON file Amazon Simple Storage Service \(Amazon S3\) object that contains a single array\. The array's name is `TimestampsSinceLastRevision`, and its value is a list of each UNIX Epoch second that has elapsed since the last revision\.

The name of the asset is in the form `Epoch{start}-{end}.json` where `{start}` and `{end}` represent the Epoch seconds corresponding to the period of time covered by the revision\.

### Manifest asset<a name="manifest-asset"></a>

Each AWS Data Exchange Heartbeat revision contains a JSON file S3 object that contains metadata about the revision and the schema of the Epoch asset JSON file\. The name of the asset is in the form `Manifest{start}-{end}.json` where `{start}` and `{end}` represent the Epoch seconds corresponding to the period of time covered by the revision\. The following example shows the content of a manifest file\.

```
{
        "manifestSchemaVersion":"1.0",
        "schema":"{
                \"type\":\"object\",
                \"properties\":{
                    \"TimestampsSinceLastRevision\":{
                        \"type\":\"array\",
                        \"description\":\"List of epoch timestamps in seconds.\",
                        \"items\":{
                            \"type\":\"number\",
                            \"description\":\"Epoch timestamp in seconds.\"
                         }
                     }
                 }
        }",
        "startTimestamp":1554898111,
        "endTimestamp":1554905311,
        "numberOfTimestamps":7201
}
```

## Subscribing to AWS Data Exchange Heartbeat on AWS Data Exchange<a name="how-to-subscribe"></a>

The following procedure shows how to browse the AWS Data Exchange catalog to find and subscribe to AWS Data Exchange Heartbeat\.

**To find and subscribe to AWS Data Exchange Heartbeat**

1. Open and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, choose **Browse catalog**\.

1. From the search bar, enter **AWS Data Exchange Heartbeat** and press **Enter**\. Choose the product to view its details page\.

1. In the top right corner, choose **Continue to subscribe**\. 

1. Choose your preferred price and duration combination, choose whether to enable auto\-renewal for the subscription, and review the offer details, including the data subscription agreement\.
**Note**  
AWS Data Exchange Heartbeat doesn't require subscription verification, but some products do\. For more information, see [Subscription verification for subscribers](subscription-verification-sub.md)\.

1. Review the pricing information, choose the pricing offer, and then choose **Subscribe**\.
**Note**  
AWS Data Exchange Heartbeat is a free product\. If you subscribe to a paid product, you are prompted to confirm your decision to subscribe\.

1. On the **Set up your first export** page, select the check boxes for the data sets containing the revisions you would like to export\. Selecting a data set will prepare its most recently published revision to be exported\.

1. Choose an Amazon S3 bucket location or configure an Amazon S3 key naming pattern\. This will determine where your revisions will be exported\. For more information about using key patterns, see [Key patterns when exporting revisions](jobs.md#revision-export-keypatterns)\.

1. Choose **Export** to export the data to Amazon S3, or choose **Skip** if you'd rather wait and export or download later\.

**Note**  
It can take a few minutes for your subscription to become active after you choose **Subscribe**\. If you choose **Export** before the subscription is active, you are prompted to wait until it is complete\. After your subscription is active, your export will begin\.  
Navigating away from this page prior to your subscription becoming active will not prevent the subscription from processing\. It will prevent your data export from occurring\.