# Amazon EventBridge events<a name="cloudwatch-events"></a>

AWS Data Exchange is integrated with Amazon EventBridge, formerly called Amazon CloudWatch Events\. EventBridge is an event bus service that you can use to connect your applications with data from a variety of sources\. For more information, see the [https://alpha-docs-aws.amazon.com/eventbridge/latest/userguide/eb-what-is.html](https://alpha-docs-aws.amazon.com/eventbridge/latest/userguide/eb-what-is.html)\.

As a subscriber with an active subscription to a product, you receive an *event* from AWS Data Exchange every time the provider publishes new revisions or adds new data sets to an existing product\. The *event* contains the `DataSetId` and the list of `RevisionIds` that have been published\.

This topic provides detailed information about each event listed in the following table\. 


****  

| Action by provider | Event received by subscriber | Related topic | 
| --- | --- | --- | 
| Adds a data set to a product and publishes it | Data Sets Published to Product | [Events for adding data sets](#events-add-data-sets) | 
| Adds an Amazon Redshift data set to a product and publishes it | Redshift Data Shares Data Sets Published To Product | [Events for adding Amazon Redshift datashare data sets ](#events-add-RS-data-sets) | 
| Adds a data set revision to a product and publishes it | Revision Published To Data Set | [Events for adding revisions](#events-add-revisions) | 
| Revokes revision to a product | Revision Revoked | [Events for revoking revisions](#events-revoke-revisions) | 
| Adds an Amazon Redshift data set revision to a product and publishes it | Revision Published To Redshift Data Shares Data Set | [Events for adding Amazon Redshift datashare data set revisions](#events-add-RS-revision) | 
| Takes an action on their Amazon Redshift resources that might remove access from a subscriber | Action Performed On Redshift Data Share By Provider | [Events for an action performed on an Amazon Redshift resource](#events-RS-action) | 
| Takes an action on their Amazon Redshift resources that removes access from a subscriber | Redshift Data Share Access Lost | [Events for losing access to an Amazon Redshift datashare](#events-RS-lost-access) | 

**Note**  
This feature is currently only supported for revisions for products that contain file\-based data \(Amazon S3 objects\) and products that contain Amazon Redshift data sets\.

Revisions and data sets can be added in the console or programmatically\. For more information about adding these programmatically, see [Using AWS Data Exchange with the AWS Marketplace Catalog API](appendices.md)\.

**Note**  
AWS Data Exchange emits events on a best effort basis\.

## Events for adding data sets<a name="events-add-data-sets"></a>

When a provider adds a data set to a product and publishes it, the subscriber receives an event with the following detail type: `Data Sets Published to Product`\. 

The following is an example event body for an added data set\.

```
{
    "version": "0",
    "id": "dc529cb6-2e23-4c5f-d020-EXAMPLE92231",
    "detail-type": "Data Sets Published To Product",
    "source": "aws.dataexchange",
    "account": "123456789012",
    "time": "2020-07-29T18:24:04Z",
    "region": "us-east-1",
    "resources": [
        "prod-uEXAMPLEabc1d"
    ],
    "detail": {
        "DataSetIds": [
            "4afc623EXAMPLE099e6fcc8EXAMPLEe8",
            "5bgd734EXAMPLE100f7gdd9EXAMPLEe9"
        ]
    }
}
```

## Events for adding Amazon Redshift datashare data sets<a name="events-add-RS-data-sets"></a>

When a provider adds an Amazon Redshift datashare data set to a product and publishes it, the subscriber receives an event with the following detail type: `Redshift Data Shares Data Sets Published To Product`\.

The following is an example event body for an added Amazon Redshift datashare data set\.

```
{
    "version": "0",
    "id": "dc529cb6-2e23-4c5f-d020-EXAMPLE92231",
    "detail-type": "Redshift Data Shares Data Sets Published To Product",
    "source": "aws.dataexchange",
    "account": "123456789012",
    "time": "2021-12-15T18:24:04Z",
    "region": "us-east-1",
    "resources": [
        "aae4c2cdEXAMPLE54f9369dEXAMPLE66"
    ],
    "detail": {
        "RevisionIds": [
            "3afc623EXAMPLE099e6fcc8EXAMPLEe7"
        ]
    }
```

## Events for adding revisions<a name="events-add-revisions"></a>

When a provider adds a data set to a product and publishes it, the subscriber receives an event with the following detail type: `Revision Published To Data Set`\. 

The following is an example event body for an added revision\.

```
{
    "version": "0",
    "id": "dc529cb6-2e23-4c5f-d020-EXAMPLE92231",
    "detail-type": "Revision Published To Data Set",
    "source": "aws.dataexchange",
    "account": "123456789012",
    "time": "2020-07-29T04:16:28Z",
    "region": "us-east-1",
    "resources": [
        "aae4c2cdEXAMPLE54f9369dEXAMPLE66"
    ],
    "detail": {
        "RevisionIds": [
            "3afc623EXAMPLE099e6fcc8EXAMPLEe7"
        ]
    }
}
```

## Events for revoking revisions<a name="events-revoke-revisions"></a>

When a provider revokes a revision to a product and publishes it, the subscriber receives an event with the following detail type: `Revision Revoked`\. 

The following is an example event body for a revoked revision\.

```
{
    "version": "0",
    "id": "dc529cb6-2e23-4c5f-d020-EXAMPLE92231",
    "detail-type": "Revision Revoked",
    "source": "aws.dataexchange",
    "account": "123456789012",
    "time": "2022-02-17T21:25:06Z",
    "region": "us-east-1",
    "resources": [
        "aae4c2cdEXAMPLE54f9369dEXAMPLE66"
     ],
    "detail": {
        "RevisionIds": [
            "3afc623EXAMPLE099e6fcc8EXAMPLEe7"
        ],
    "RevocationComment": "example revocation comment"
    }
}
```

## Events for adding Amazon Redshift datashare data set revisions<a name="events-add-RS-revision"></a>

When a provider adds an Amazon Redshift datashare data set revision to a product and publishes it, the subscriber receives an event with the following detail type: `Revision Published To Redshift Data Shares Data Set`\.

The following is an example event body for an added Amazon Redshift datashare data set revision\.

```
{
    "version": "0",
    "id": "dc529cb6-2e23-4c5f-d020-EXAMPLE92231",
    "detail-type": "Revision Published To Redshift Data Shares Data Set",
    "source": "aws.dataexchange",
    "account": "123456789012",
    "time": "2021-12-15T18:24:04Z",
    "region": "us-east-1",
    "resources": [
        "4afc623EXAMPLE099e6fcc8EXAMPLEe8"
    ],
    "detail": {
        "DataSetIds": [
            "4afc623EXAMPLE099e6fcc8EXAMPLEe8",
            "5bgd734EXAMPLE100f7gdd9EXAMPLEe9"
        ]
    }
}
```

## Events for an action performed on an Amazon Redshift resource<a name="events-RS-action"></a>

When a provider takes an action on their Amazon Redshift resources that *might* remove access from a subscriber, the subscriber receives an event with the following detail type: `Action Performed On Redshift Data Share By Provider`\.

For example, if a provider changes the data share's public accessibility setting from `true` to `false`, the subscriber receives an event\.

The following is an example event body for an action performed on an Amazon Redshift resource\.

```
{
    "version": "0",
    "id": "dc529cb6-2e23-4c5f-d020-EXAMPLE92231",
    "detail-type": "Action Performed On Redshift Data Share By Provider",
    "source": "aws.dataexchange",
    "account": "123456789012",
    "time": "2021-12-15T18:24:04Z",
    "region": "us-east-1",
    "resources": [
        "arn:aws:redshift:us-east-1:098765432123:datashare:01234567-2590-7654-1234-f57ea0081234/test_data_share"
    ],
    "detail": {
        "Message": "This is an example message which explains why you may have lost access.",
        "AssociatedProducts": [
            {
              "ProductId": "aae4c2cdEXAMPLE54f9369dEXAMPLE66",
              "DataSetIds": [ "4afc623EXAMPLE099e6fcc8EXAMPLEe8" ]
            }
        ]
    }
}
```

## Events for losing access to an Amazon Redshift datashare<a name="events-RS-lost-access"></a>

When a provider takes an action on their Amazon Redshift resources that removes access from a subscriber, the subscriber receives an event with the following detail type: `Redshift Data Share Access Lost`\.

For example, if a provider deletes an Amazon Redshift datashare or deletes a cluster, the subscriber receives an event\.

The following is an example event body for losing access to an Amazon Redshift datashare\.

```
{
    "version": "0",
    "id": "dc529cb6-2e23-4c5f-d020-EXAMPLE92231",
    "detail-type": "Redshift Data Share Access Lost",
    "source": "aws.dataexchange",
    "account": "123456789012",
    "time": "2021-12-15T18:24:04Z",
    "region": "us-east-1",
    "resources": [
        "arn:aws:redshift:us-east-1:098765432123:datashare:01234567-2590-7654-1234-f57ea0081234/test_data_share"
    ],
    "detail": {
        "Message": "This is an example message which explains why you may have lost access.",
        "AssociatedProducts": [
            {
              "ProductId": "aae4c2cdEXAMPLE54f9369dEXAMPLE66",
              "DataSetIds": [ "4afc623EXAMPLE099e6fcc8EXAMPLEe8" ]
            }
        ]
    }
}
```

The following table provides a complete list of error codes for detail type `Redshift Data Share Access Lost`\.


| Error code | Message | Description | 
| --- | --- | --- | 
| CLUSTER\_DELETED | The datashare is unavailable because the provider deleted their cluster\. Please contact the provider for more information\. | This message is sent when the datashare is no longer available because the provider deleted the cluster containing the datashare\. | 
| CLUSTER\_ENCRYPTION\_DISABLED | The datashare is unavailable because the provider disabled encryption on their cluster\. Please contact the provider for more information\. | This message is sent when the datashare is no longer available because the provider disabled encryption on their cluster\. To use a datashare, both the provider and the subscriber must have encryption enabled\. | 
| DATASHARE\_DELETED | The datashare is unavailable because the provider deleted the datashare\. Please contact the provider for more information\. | This message is sent when the datashare is no longer available because the provider deleted it\. The provider must create a new datashare so that you can regain access to the data\. | 
| DATASHARE\_DEAUTHORIZED | The datashare is unavailable because the provider deauthorized the datashare\. Please contact the provider for more information\. | This message is sent when the datashare is no longer available because the provider deauthorized the datashare\. The provider must create a new datashare so that you can regain access to the data\. | 
| DATASHARE\_PUBLIC\_CONSUMER\_BLOCKED | You cannot access a non\-publicly accessible datashare from a publicly accessible cluster\. You must turn off public accessibility on your cluster to access this datashare\. Please contact your provider for more information\. |  This message is sent when a provider sets the **Publicly accessible** option to **Disable **on the cluster that contains their datashare\. If the subscriber's cluster has the **Publicly accessible** option set to **Disable**, it will not affect their ability to access the datashare\. For the subscriber to access the datashare, either the subscriber must set the **Publicly accessible** option to **Disable **on their cluster, or the provider must set the **Publicly accessible** option to **Enable **on their cluster\.  | 