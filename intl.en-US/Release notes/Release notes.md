# Release notes

This topic provides the release notes of Cloud Storage Gateway \(CSG\).

|Version|Release date|Description|Documentation|
|-------|------------|-----------|-------------|
|**v1.6.1**|January 5, 2021|Optimization of user experience:-   The remote sync feature is optimized.

|N/A|
|**v1.6.0**|November 27, 2020|New features:-   NFS shares, SMB shares, and iSCSI volumes can be mounted over IPv6 in the China \(Hohhot\) region.
-   The AccessKey pairs of on-premises gateways can be changed.

Optimization of user experience:

-   The read and write performance of file gateway shares is optimized.
-   The file system capacity of file gateway is improved. The capacity is increased to 128 TB for basic gateways, 256 TB for standard gateways, 512 TB for enhanced gateways, and 1 P for advanced gateways.

|-   [t2001589.md\#]() |
|**v1.5.2**|October 21, 2020|Optimization of user experience:-   The metadata stored in the on-premises cache disks of file gateways can be defragmented with higher efficiency.
-   File gateways and block gateways can access Object Storage Service \(OSS\) at a higher speed.

|N/A|
|**v1.5.1**|August 27, 2020|New features:-   The memory usage of file systems is reduced.
-   Service linked roles can be assigned to CSG.

|-   [Service linked roles](/intl.en-US/Overview/Service linked roles for CSG.md) |
|**v1.5.0**|June 30, 2020|New features: -   The number of active messages in a synchronization group can be displayed.
-   The replication mode is globally supported in CSG.

|-   [Replicate data](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Replicate data.md) |
|Optimization of user experience: -   Renamed files can pass the cyclic redundancy check \(CRC\).
-   The performance of data duplication in replication mode is improved.
-   The stability of NFS access to file gateways is enhanced.
-   The load time of large file sharing systems is shortened. |
|Newly supported region: -   China \(Heyuan\) |
|**v1.4.0**|April 10, 2020|New features: -   Data can be duplicated by using file gateways in replication mode. This feature is available only to the users in the whitelist.
-   Replication mode can be enabled or disabled. This feature is available only to the users in the whitelist.
-   Directories can be added or deleted in replication mode. This feature is available only to the users in the whitelist.

|-   [Replicate data](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Replicate data.md)
-   [Monitoring](/intl.en-US/User Guide (On-Premises)/File Gateway/Monitoring.md)
-   [Deploy the on-premises console of file gateways](/intl.en-US/User Guide (On-Premises)/File Gateway/Deploy the local file gateway console.md) |
|Optimization of user experience: -   Express synchronization across regions is supported.
-   The description for the UTF-8 verification of the file names is included in the instructions for file gateways.
-   The statuses of download and upload queues can be displayed for file gateways.
-   The passwords of on-premises gateways can be reset.
-   Log data can be collected by Log Service by using on-premises gateways. |
|Newly supported region: -   Japan \(Tokyo\) |
|**v1.3.0**|March 6, 2020|New features: -   The transfer acceleration feature is supported by file gateways.
-   The replication mode of file gateways is enhanced to automatically replicate data to on-premises clients. This feature is available only to the users in the whitelist.

|-   [Enable transfer acceleration](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Enable transfer acceleration.md)
-   [Integration with Cloud Monitor](/intl.en-US/Best Practice/Features/Integration with Cloud Monitor.md) |
|Optimization of user experience: -   CSG supports API operations.
-   CSG can be integrated with Cloud Monitor.
-   The upload performance of big files in file gateways is improved.
-   Paying for network bandwidth upgrades is supported. |
|Newly supported regions: -   Malaysia \(Kuala Lumpur\)
-   US \(Silicon Valley\)
-   US \(Virginia\) |
|**v1.2.0**|January 8, 2020|New features: -   Disk encryption based on a bring-your-own-key \(BYOK\) solution is supported for file gateways of the Enhanced and Advanced types. This feature is available only to the users in the whitelist.
-   File gateways allow you to associate multiple OSS buckets with the same share.

|[Associate a share with multiple OSS buckets](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Associate a share with multiple OSS buckets.md)|
|Optimization of user experience: -   Fragment optimization based on the Network File System version 4 \(NFSv4\) protocol is supported for file gateways. If multiple requests for uploading a file to the OSS bucket are sent, only one of the requests is processed. File gateways cannot mount shares on on-premises clients over NFSv3.
-   The express synchronization feature is optimized on the NFS client side. Metadata updates can be discovered by NFS clients in time. |
|**v1.1.0**|December 26, 2019|New features: -   Express synchronization is supported for file gateways. This feature detects data changes in OSS buckets without the need for a full scan. Express synchronization allows a single user to write data to and multiple users to read data from the same gateway at the same time.
-   Windows access-based enumeration \(ABE\) is supported for file gateways. This feature can be used together with the Active Directory \(AD\) service to separate access requests from different accounts.

|-   [Express synchronization](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Express synchronization.md)
-   [Enable Windows access-based enumeration](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Enable Windows access-based enumeration.md) |
|Optimization of user experience: -   The specifications of CSG can be upgraded.
-   Automatic renewal of subscriptions is supported. |
|Newly supported regions: -   China \(Chengdu\)
-   Indonesia \(Jakarta\) |

