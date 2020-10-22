# Release notes

This topic provides the release notes of Cloud Storage Gateway \(CSG\).

|Version|Release date|Description|Documentation|
|-------|------------|-----------|-------------|
|**v1.5.2**|October 21, 2020|Optimization of user experience:-   The metadata stored in the local cache disks of file gateways can be defragmented with higher efficiency.
-   File gateways and block gateways can access Object Storage Service \(OSS\) at a higher speed.

|None|
|**v1.5.1**|August 27, 2020|New features:-   The memory usage of file systems is reduced.
-   Service linked roles can be assigned to CSG.

|-   [Service linked roles]() |
|**v1.5.0**|June 30, 2020|New features: -   The number of active messages in a synchronization group can be displayed.
-   The duplicate mode is globally supported in CSG.

|-   [Replicate data](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Replicate data.md) |
|Optimization of user experience: -   Renamed files can pass the CRC.
-   The performance of data duplication in the duplicate mode is improved.
-   The stability of NFS access to file gateways is enhanced.
-   The load time of large file sharing systems is shortened. |
|Available in the following new region: -   China \(Heyuan\) |
|**v1.4.0**|April 10, 2020|New features: -   File gateways support the data duplication feature in the duplicate mode. This feature is available only to selected users.
-   The duplicate mode can be enabled and disabled. This feature is available only to selected users.
-   The duplicate mode allows you to add and delete directories. This feature is available only to selected users.

|-   [Replicate data](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Replicate data.md)
-   [Monitoring](/intl.en-US/User Guide (On-Premises)/File Gateway/Monitoring.md)
-   [Deploy the local file gateway console](/intl.en-US/User Guide (On-Premises)/File Gateway/Deploy the local file gateway console.md) |
|Optimization of user experience: -   Express synchronization supports synchronization across regions.
-   The instructions for file gateways include the description of UTF-8 verification of the file names.
-   File gateways display the status of both download and upload queues.
-   The passwords of file gateways that are deployed in data centers can be reset.
-   On-premises file gateways allow Log Service to collect log data. |
|Available in the following new regions: -   Japan \(Tokyo\) |
|**v1.3.0**|March 6, 2020|New features: -   The transfer acceleration feature is supported by file gateways.
-   The duplicate mode of file gateways is enhanced to replicate data to local clients. This feature is available only to selected users.

|-   [Enable transfer acceleration](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Enable transfer acceleration.md)
-   [Integration with Cloud Monitor](/intl.en-US/Best Practice/Features/Integration with Cloud Monitor.md) |
|Optimization of user experience: -   CSG supports API operations.
-   CSG can be integrated with Cloud Monitor.
-   The upload performance of big files in file gateways is improved.
-   CSG allows you to pay for network bandwidth upgrades. |
|Available in the following new regions: -   Malaysia \(Kuala Lumpur\)
-   US \(Silicon Valley\)
-   US \(Virginia\) |
|**v1.2.0**|January 8, 2020|New features: -   File gateways of the Enhanced and Advanced models support disk encryption by using a bring-your-own-key \(BYOK\) solution. This feature is available only to selected users.
-   File gateways allow you to associate multiple OSS buckets with the same share.

|[Associate a share with multiple OSS buckets](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Associate a share with multiple OSS buckets.md)|
|Optimization of user experience: -   File gateways support fragment optimization by using the Network File System version 4 \(NFSv4\) protocol. If multiple requests for to upload a file to the OSS bucket are sent, the request is processed only once. File gateways cannot mount shares to local clients over NFSv3.
-   The express synchronization feature is optimized on the NFS client side. Metadata updates can be discovered by NFS clients in time. |
|**v1.1.0**|December 26, 2019|New features: -   File gateways support express synchronization. This feature detects data changes in OSS buckets without the need for a full scan. Express synchronization allows a single user to write data to and multiple users to read data from the same gateway at the same time.
-   File gateways support Windows access-based enumeration \(ABE\). Together with the Active Directory \(AD\) service, this feature can separate access requests from different accounts.

|-   [Express synchronization](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Express synchronization.md)
-   [Enable Windows access-based enumeration](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Enable Windows access-based enumeration.md) |
|Optimization of user experience: -   The specification of CSG can be upgraded.
-   CSG supports automatic renewal of subscriptions. |
|Available in the following new regions: -   China \(Chengdu\)
-   Indonesia \(Jakarta\) |

