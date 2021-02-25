# Billable items and billing methods

This topic describes the billable items and billing methods of Cloud Storage Gateway \(CSG\).

For more information about the pricing of CSG resources, see [CSG pricing](https://www.aliyun.com/price/product?spm=5176.144914.752642.btn2.4fb67d70aqt177#/hcs_sgw/detail).

## Billable items

CSG provides cloud gateways and on-premises gateways. These gateways have different billable items.

-   Cloud gateways

    You are charged for gateways that are deployed on Alibaba Cloud based on their specifications, cache types, and public bandwidth. The following formulas show the billable items of the two billing methods:

    -   Pay-as-you-go: Hourly gateway fee = Price of gateway specification per hour + Cache capacity \(GB\) × Price of 1 GB per hour + Public bandwidth \(Mbit/s\) × Price of 1 Mbit/s per hour
    -   Subscription: Yearly or monthly subscription gateway fee = Subscription fee of gateway specification + Cache capacity \(GB\) × Price of 1 GB per year or month + Public bandwidth \(Mbit/s\) × Price of 1 Mbit/s per year or month
    **Note:** Public Network Bandwidth: By default, Public Network Bandwidth is not selected. If you want to use a gateway that resides in another region or perform express synchronization across regions, you must select Public Network Bandwidth. The public bandwidth less than 5 Mbit/s is provided free of charge. You are charged if the public bandwidth is 6 Mbit/s or higher.

-   On-premises gateways

    On-premises gateways run with your own virtual machines and cache resources. You are charged by Alibaba Cloud only for the gateway software license.


## Billing methods

CSG supports the subscription and pay-as-you-go billing methods.

-   Pay-as-you-go: CSG resource fee = Actual consumed resources × Unit price. The actual consumed resources are calculated by hour. The hourly consumed resources are calculated in the next hour. The fee of the actual consumed resources is deducted from your account balance. For example, if you receive a bill at 09:30, the bill covers the resources consumed from 08:00 to 09:00.

    **Note:** The billing system has latency. Therefore, you may not receive the bill for the previous hour on time. For example, the bill you receive at 09:30 may cover the resources consumed from 07:00 to 08:00.

-   [Subscription](/intl.en-US/Pricing/Subscription/Purchase a gateway.md): You are charged by using the subscription billing method. This billing method provides more discounts than the pay-as-you-go billing method in a billing cycle.

## Other fees

When you use the CSG service, the following fees may be incurred:

-   Fees for using Object Storage Service \(OSS\)

    If you use OSS resources in the CSG console, you are charged for data storage, traffic, requests, and data retrieval when you access OSS buckets from gateways. For more information about the related fees, see [OSS pricing](https://www.aliyun.com/price/product?spm=a2c4g.11186623.2.13.12847b552H1YA7#/oss/detail).

    -   Storage fees: If files are written to gateways and you upload the files to OSS, these files occupy the space of OSS buckets.
    -   Traffic fees: If you select an internal endpoint of OSS, you are not charged for read and write traffic. If you select an Internet endpoint of OSS, you are charged for the outbound traffic over the Internet when you read files from gateways.
    -   Request fees: You are charged when you upload or download files by using a file gateway or a block gateway. If the reverse synchronization feature is enabled for a file gateway, the file gateway retrieves a list of files and metadata from the related OSS bucket when you open a folder. In this case, request fees are incurred. A block gateway uploads files as fixed-size fragments. To upload large files, the gateway generates more fragments. In this case, request fees are incurred.
    -   Data retrieval fees: You are charged for the volume of data that is read from an OSS bucket. The volume of data transmitted over the Internet is included in the billable item "outbound traffic over the Internet". You can run the restore command to restore an archived object. After you restore the object, the data retrieval fee is calculated based on the volume of restored data. If you run the restore command again, no data retrieval fee is incurred.

        **Note:** Data retrieval fees are only applicable to OSS objects of the Infrequent Access \(IA\) and Archive types.

-   Fees for using Log Service

    After you enable the log monitoring feature for a gateway, system logs are collected and sent to a specified Logstore in Log Service. For information about the related fees, see [Log Service pricing](https://www.aliyun.com/price/product?spm=a2c4g.11186623.2.13.12847b552H1YA7#/sls/detail).

-   Fees for using Key Management Service \(KMS\)

    After you enable the server-side encryption feature for a share, OSS calls related KMS API operations to query and generate keys. Then, OSS encrypts and decrypts data stored in the related OSS bucket by using the keys. If you enable the gateway-side encryption feature, CSG calls related KMS API operations to query and generate keys. Then, CSG encrypts and decrypts data stored in the related OSS bucket by using the keys. For information about the related fees, see [KMS pricing](/intl.en-US/Pricing/Billing.md).

-   Fees for using transfer acceleration in OSS

    After you enable the transfer acceleration feature for a share, the public bandwidth of the gateway is used to increase the speed of cross-region data transmission. For information about the related fees, see [Transfer acceleration fees](https://help.aliyun.com/document_detail/59636.html#title-dtc-l5t-9gt).


