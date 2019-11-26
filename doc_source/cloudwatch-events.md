# CloudWatch Events<a name="cloudwatch-events"></a>

As a subscriber with an active subscription to a product, you receive a CloudWatch event from AWS Data Exchange every time the provider publishes new revisions\. The CloudWatch event contains the `DataSetId` and the list of `RevisionIds` that have been published\. The detail type of the CloudWatch event is set to `Revision Published To Data Set`\.

Here is an example CloudWatch event body for an updated revision:

```
{
    "version": "0",
    "id": "dc529cb6-2e23-4c5f-d020-EXAMPLE92231",
    "detail-type": "Revision Published To Data Set",
    "source": "aws.dataexchange",
    "account": "123456789012",
    "time": "2019-10-10T04:16:28Z",
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