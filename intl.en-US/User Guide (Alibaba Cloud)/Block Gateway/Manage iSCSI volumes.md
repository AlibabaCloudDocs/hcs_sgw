# Manage iSCSI volumes

This topic describes how to manage iSCSI volumes in the Cloud Storage Gateway console, including how to create, modify, delete, and view iSCSI volumes.

1.  You have created a block gateway. For more information, see [Create a block gateway](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Manage block gateways.md).
2.  You have added a cache disk to the block gateway. For more information, see [Add a cache disk](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Manage cache disks.md).

    If you need to create an iSCSI volume that has the Cache mode enabled, you must add a cache disk to the block gateway first.


## Create an iSCSI volume

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  Select the region where the target block gateway is deployed.

3.  On the Gateway Clusters page, find and click the target block gateway.

4.  Click Volumes in the left-side navigation pane, and click **Create** in the upper-right corner.

5.  On the **Bucket Setting** tab, set the following parameters, and click **Next**.

    |Parameter|Description|
    |---------|-----------|
    |**Allow Cross-region Bucket**|    -   **Yes**: specifies that you can access the bucket that stays in the different region from the specified gateway.
    -   **No**: specifies that you can access only the bucket that stays in the same region as the specified gateway.
 **Note:** If you select an Internet endpoint of the target bucket to bind your cloud resource to the block gateway, you may be charged for external download traffic. |
    |**Bucket Endpoint**|Specifies the endpoint of an existing bucket.|
    |**Connect to Bucket over SSL**|Specifies whether to connect to a bucket over SSL. Valid values: **Yes** and **No**.|

6.  On the **Basic Information** tab, set the following parameters and click **Next**.

    |Parameter|Description|
    |---------|-----------|
    |**iSCSI Volume Name**|Specify a name for the volume. The name can be up to 31 characters in length and can contain letters and digits.|
    |**Recovery**|Select whether to enable the data recovery function.     -   **Yes**: If you select **Yes**, when the OSS bucket associated with the cloud resource is already used as cloud storage of the volume, the system attempts to restore the volume based on the metadata, such as the volume capacity.
    -   **No**: If you select **No**, the system directly uses the OSS bucket associated with the cloud resource to create a new volume. |
    |**Size**|If you set **Recovery** to **No**, you must set the **Size** parameter. The cache size must be no less than 1 GB and no more than 262,144 GB. |
    |**Mode**|Supports the Write-through mode and Cache mode.     -   **Write Through Mode**: writes files directly to the associated OSS bucket, and reads data directly from the OSS bucket.
    -   **Cache Mode**: writes files to and reads files from a target local cache disk first. Typically, the Cache mode provides higher read and write performance. |
    |**Cache**|If you set **Mode** to **Cache Mode**, you must select a cache disk. Make sure that you have added a cache disk to the block gateway. Otherwise, no cache disk is available.

    -   For more information about cache disks of block gateways deployed on Alibaba Cloud, see [Add a cache disk](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Manage cache disks.md).
    -   For more information about cache disks of on-premises block gateways, see [Add disks](/intl.en-US/User Guide (On-Premises)/Block Gateway/Add disks.md). |
    |**Storage Allocation Unit**|If you set **Recovery** to **No**, you must set the **Storage Allocation Unit** parameter. Valid values: 8 KB, 16 KB, 32 KB, 64 KB, and 128 KB. Default value: 32 KB.|
    |**Authorization Method**|Supports one-way Challenge-Handshake Authentication Protocol \(CHAP\) authentication. If you select **CHAP** from the Authorization Method drop-down list, you must set the following parameters:

     -   **CHAP User Name**: Specify a CHAP username.
    -   **CHAP Password**: Specify a CHAP password. The password must be 12 to 16 characters in length. |

7.  Click Next to go to the **Summary** tab, make sure that the specified information is correct, and then click **OK**.


## Related operations

On the Volumes page, you can also perform the following operations.

|Operation|Description|
|---------|-----------|
|Modify an iSCSI volume|Find the target iSCSI volume and click **Edit** in the Actions column.|
|Delete an iSCSI volume|Find the target iSCSI volume and click **Delete** in the Actions column. When you delete an iSCSI volume, you can choose whether to delete the data stored in the associated OSS bucket at the same time.

 **Note:** If you select the Delete data in the OSS buckets at the same time check box, all data stored in the OSS bucket will be deleted after the iSCSI volume is deleted. Proceed with caution. |
|View iSCSI volume information|Find the target iSCSI volume and click the plus sign \(**+**\) to show the volume information. The volume information includes the operation status, total amount of downloaded data, IP address, capacity, port, whether CHAP is enabled, total amount of uploaded data, whether OSS bucket SSL is used, LUN ID, volume status, and whether the volume is enabled.|

-   [Use volumes from a Windows operating system](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Use iSCSI volumes/Use volumes from a Windows operating system.md)
-   [Use volumes from a Linux operating system](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Use iSCSI volumes/Use volumes from a Linux operating system.md)

