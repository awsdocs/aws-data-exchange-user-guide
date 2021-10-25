# AWS Data Exchange quotas<a name="limits"></a>

The following sections provide information about the service quotas, endpoints, AWS Region export guidelines across Regions, and constraints related to resource fields for AWS Data Exchange for an AWS account\. 



## Service quotas<a name="service-quotas"></a>

For information about service quotas, see [AWS Data Exchange endpoints and quotas](https://docs.aws.amazon.com/general/latest/gr/dataexchange.html) in the *AWS General Reference*\.

## Service endpoints<a name="api-endpoints"></a>

For information about service endpoints, see [AWS Data Exchange endpoints and quotas](https://docs.aws.amazon.com/general/latest/gr/dataexchange.html) in the *AWS General Reference*\.



## Export and import guidelines<a name="export-import-guidelines"></a>

The following table provides guidelines for export and import jobs\. For more information, see [AWS Regions and data sets](data-sets.md#data-set-regions)\.


|  **Resource, descriptor, or operation**  |  **Maximum value**  |  **Description**  | 
| --- | --- | --- | 
| File size for assets imported from a signed URL | 5 GB | The maximum size, in GB, of an asset that can be imported using IMPORT\_ASSET\_FROM\_SIGNED\_URL\. | 
| File size of a cross\-Region revision export to Amazon Simple Storage Service \(Amazon S3\) | 100 GB | The maximum size, in GB, of a revision that can be exported to a different Region from the provider data set using an ExportRevision job\. | 
| Number of assets that can be imported from a signed URL in a single job | 1 | The number of assets that can be imported using a single IMPORT\_ASSET\_FROM\_SIGNED\_URL job\.  | 
| Number of assets that can be exported to Amazon S3 in a single cross\-Region ExportRevision job | 2,000 | The number of assets that can be exported from one Region to another from the provider data set using an ExportRevision job\. | 
| Number of assets that can be exported to Amazon S3 in a single ExportRevision job | 10,000 | The number of assets that can be exported to Amazon S3 using an ExportRevision job\. | 
| Number of revisions that can be exported to Amazon S3 in a single ExportRevision job | 1 | The number of revisions that can be exported to Amazon S3 using an ExportRevision job\. | 
| Event actions per resource | 5 | The maximum number of event actions per resource\. | 
| Event actions per account | 50 | The maximum number of event actions per account\. | 

 

## Constraints for resource fields<a name="limits-on-resource-fields"></a>

The following table provides constraints related to resource fields that providers encounter in the AWS Data Exchange console when creating data sets, revisions, products, and product offers\. The table also provides constraints related to resource fields that subscribers encounter when making subscription requests\.


|  **Resource**  |  **Field** |  **Maximum length or size**  | 
| --- | --- | --- | 
| Dataset | Name | 256 characters | 
| Dataset | Description | 16,384 characters | 
| Revision | Comment | 128 characters | 
| Product details | Name | 72 characters | 
| Product details | Short description | 500 characters | 
| Product details | Long description | 30,000 characters | 
| Product details | Logo | 100 KB | 
| Product offer | DSA | 10 MB | 
| Product offer | Refund policy | 200 characters | 
| Subscription request | company name | 40 characters | 
| Subscription request | name | 40 characters | 
| Subscription request | email address | 100 characters | 
| Subscription request | intended use\-case | 500 characters | 