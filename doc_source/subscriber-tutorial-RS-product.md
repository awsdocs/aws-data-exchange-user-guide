# Tutorial: Subscribe to Worldwide Event Attendance \(Test Product\) on AWS Data Exchange<a name="subscriber-tutorial-RS-product"></a>

Worldwide Event Attendance \(Test Product\) is a free product that helps subscribers understand how to subscribe to and interact with an AWS Data Exchange product containing Amazon Redshift data sets\. You can use this product for testing purposes and to learn how to query, analyze, and build applications within minutes\.

Worldwide Event Attendance \(Test Product\) contains an Amazon Redshift data set named **Worldwide Event Data \(Test Data\)** that is in the US East \(N\. Virginia\) AWS Region\.

**Note**  
A subscription to this product might require Amazon Redshift cluster infrastructure, which could incur extra costs\. To query the Amazon Redshift data, an Amazon Redshift cluster running on an RA3 instance is required\. 

You use the AWS Data Exchange console to find and subscribe to Worldwide Event Attendance \(Test Product\)\. Then, you can use either the Amazon Redshift console or SQL commands to query the datashare\.

## Subscribing to Worldwide Event Attendance \(Test Product\) on AWS Data Exchange<a name="subscribe-to-test-product"></a>

The following procedure shows how to browse the AWS Data Exchange catalog to find and subscribe to Worldwide Event Attendance \(Test Product\)\.

**To find and subscribe to Worldwide Event Attendance \(Test Product\)**

1. Open and sign in to the [AWS Data Exchange console](https://console.aws.amazon.com/dataexchange)\.

1. From the left navigation pane, under **Discover data products**, choose **Browse catalog**\.

1. From the search bar, enter **Worldwide Event Attendance \(Test Product\)** and press **Enter**\. 

1. Choose the **Worldwide Event Attendance \(Test Product\)** to view its details page\.

   1. \(Optional\) To view the data dictionary, scroll down to the product **Overview** section to see the data dictionary under **Data dictionaries**\.

   1. \(Optional\) To download the data dictionary, choose the **Data dictionary and samples** tab, choose the option button next to **Data dictionary**, and then choose **Download**\.

   1. \(Optional\) To preview the sample, choose the option button next to the sample name \(**Worldwide Event Attendance Sample\.csv**\), and then choose **Preview sample \(CSV only\)**\.

   1. \(Optional\) To download the sample, choose the option button next to the sample name \(**Worldwide Event Attendance Sample\.csv**\), and then choose **Download**\.

      If you are previewing the sample, you can also choose **Download** in the sample preview dialog box\.

1. In the top right corner, choose **Continue to subscribe**\. 

1. Choose your preferred price and duration combination, choose whether to enable auto\-renewal for the subscription, and review the offer details, including the data subscription agreement\.
**Note**  
Worldwide Event Attendance \(Test Product\) doesn't require subscription verification, but some products do\. For more information, see [Subscription verification for subscribers](subscription-verification-sub.md)\.

1. Review the pricing information, choose the pricing offer, and then choose **Subscribe**\.
**Note**  
Worldwide Event Attendance \(Test Product\) is a free product\. If you subscribe to a paid product, you are prompted to confirm your decision to subscribe\.

It can take a few minutes for your subscription to become active after you choose **Subscribe**\. 

Navigating away from this page prior to your subscription becoming active will not prevent the subscription from processing\.

## Querying Worldwide Event Attendance \(Test Product\) data on Amazon Redshift \(console\)<a name="query-RS-data-console"></a>

The following procedure shows how to set up and query the datashare using the Amazon Redshift console\.

**To query Worldwide Event Attendance \(Test Product\) data on Amazon Redshift \(console\)**

1. Open and sign in to the Amazon Redshift console\.

1. Choose **Clusters**, and choose your existing RA3 cluster\.

1. Choose the **Datashares** tab\.

1. Select the datashare you want to create the database from\.

1. Under **Subscriptions to AWS Data Exchange datashares**, choose **Create database from datashare**\.

1. In **Create database from datashare**, enter the **Database name** for your new database, and then choose **Create**\. 

1. Choose the **Marketplace** icon on the navigation pane, and open the **Query editor**\. 

1. Under **Resources**, select a database and a schema\. 

1. Run the following SQL query\. 

   `select * from database.schema.table`

## Querying Worldwide Event Attendance \(Test Product\) data on Amazon Redshift \(SQL\)<a name="query-RS-data-SQL"></a>

The following procedure shows how to set up and query the datashare using the SQL commands\.

**To query Worldwide Event Attendance \(Test Product\) data on Amazon Redshift \(SQL\)**

1. To find the datashare, run the following command\.

    `SHOW DATASHARES [ LIKE 'namepattern' ]`

    This command lists all datashares, including the one from Worldwide Event Attendance \(Test Product\), in addition to the provider's `account_id` and `namespace`\. For more information, see [Show Datashares](https://docs.aws.amazon.com/redshift/latest/dg/r_SHOW_DATASHARES.html) in the *Amazon Redshift Database Developer Guide*\.

1. Run the following command to create a database from the datashare\.

    `CREATE DATABASE database_name`

    `FROM DATASHARE datashare_name OF ACCOUNT account_id NAMESPACE namespace_guid`

   For more information, see [Create Database](https://docs.aws.amazon.com/redshift/latest/dg/r_CREATE_DATABASE.html) in the *Amazon Redshift Database Developer Guide*\.

1. Run the following SQL query\. 

   `select * from database.schema.table`