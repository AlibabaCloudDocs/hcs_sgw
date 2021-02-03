# Express synchronization

Multiple on-premises Cloud Storage Gateway \(CSG\) agents are connected to an Object Storage Service \(OSS\) bucket by using a file gateway. If data changes occur in the OSS bucket, you can use the express synchronization feature to synchronize these changes to all the connected agents.

-   A file gateway is created and a cache is added. For more information, see [Create a file gateway](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage file gateways.md) and [Add a cache disk](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage cache disks.md).
-   An OSS bucket is created. For more information, see [Create buckets](/intl.en-US/Quick Start/OSS console/Create buckets.md).
-   A Network File System \(NFS\) or Server Message Block \(SMB\) share is created and configured between a file gateway and an OSS bucket. For more information, see [Manage shares](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage shares.md).
-   Message Service \(MNS\) is activated and authorized. For more information, see [Activate Message Service]().

When you configure the express synchronization feature, you can add one or more shares to a synchronization group if these shares are connected to the same OSS bucket. All data changes in the bucket are simultaneously synchronized to the CSG agents mapped to the shares in the synchronization group. You do not need to separately synchronize data changes from these shares. This improves the efficiency and accuracy of data synchronization.

**Note:** Only standard, enhanced, and advanced gateways support the express synchronization feature.

Express synchronization must be used in combination with MNS. If you enable express synchronization, you are charged for using MNS.

A bill is generated for MNS topics and queues on a daily basis. Each synchronization group is counted as one topic, and each share added to the synchronization group is counted as one queue. For example, assume that less than 20 million MNS API requests are made and the service region is US \(Virginia\). The price of each topic is USD 0.45 per day, and the price of each queue is USD 0.11 per day. In this case, if you create one synchronization group and add two shares to the group, the monthly fee is USD 20.10. The fee is calculated by using the following formula: \(0.45 + 0.11 × 2\) × 30 = 20.10. For more information, see [Pricing of MNS](https://cn.aliyun.com/price/product?spm=5176.7944397.207973.oss3.28b7b241YpZtk8#/mns/detail).

## Create a synchronization group

To enable express synchronization, you must create a synchronization group and add shares to the group. Data is synchronized by using these shares.

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  In the upper-left corner of the console, select the region where the file gateway is deployed.

3.  In the left-side navigation pane, click **Express Sync**.

4.  On the **Sync Group List** page, click **Create**.

5.  In the **Create Sync Group** wizard, set the following parameters on the **Basic Information** tab, and click **Next**.

    |Parameter|Description|
    |---------|-----------|
    |**Sync Group Name**|Enter the name of the synchronization group. **Note:** The synchronization group name must be 1 to 128 characters in length, and can contain letters, digits, periods \(.\), underscores \(\_\), and hyphens \(-\). It must start with a letter. |
    |**OSS Region**|Select the region of the OSS bucket from which you want to synchronize data.|
    |**Bucket Name**|Select the name of the OSS bucket. You can select only one OSS bucket for a synchronization group. All data changes in the bucket are synchronized to the CSG agents mapped to the shares in the group. **Note:** If no share is connected to the OSS bucket, no OSS bucket is available in the drop-down list. In this case, you must create a share in the file gateway to map your CSG agent to the OSS bucket. For more information, see [Manage shares](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage shares.md). |
    |**Bucket Subdirectory**|Select a subdirectory if you want to synchronize data from a specific subdirectory of the bucket.|

6.  On the **Set Sync Group** tab of the **Create Sync Group** wizard, select the shares in the **Optional Shares** section and click the **\>** icon to add the shares to the synchronization group. These shares are displayed in the **Selected Shares** section. Afterward, click **Next**.

    To remove a share from the synchronization group, you can select the share in the **Selected Shares** section and click the **<** icon.

    **Note:** After you add an NFS share to a synchronization group, you must specify the noac parameter when you mount the share on your CSG agent. This allows you to view the synchronization result at the earliest opportunity. For more information about mounting methods, see the examples in [Access an NFS share directory](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Access shares/Access an NFS share directory.md).

7.  On the **Summary** tab of the **Create Sync Group** wizard, confirm the information of the synchronization group, and click **OK**.


## Manage a synchronization group

After you create a synchronization group, all data changes in the OSS bucket are automatically synchronized to the CSG agents mapped to the shares in the synchronization group. You can manage a synchronization group in the following ways:

-   View the details of a synchronization group.

    Go to the **Sync Group List** page, and click the synchronization group name in the **Sync Group Name** column or click **Details** in the **Actions** column.

    In the **Sync Group Details** dialog box, you can view the details of the synchronization group. You can also click the List icon ![](../images/p68714.png) to view the details in a list, or click the Map icon ![](../images/p68715.png) to view the details on a map. The **Sync Group Details** dialog box shows the basic information of the synchronization group and the shares in the group. You can also view the following information from the list.

    |Item|Description|
    |----|-----------|
    |**Message Topic Name**|The name of the MNS topic that is used by the synchronization group.|
    |**Shared Status**|The status of a share in the synchronization group. The statuses include:     -   **Full Data Sync Awaiting**: indicates that the share is added to the synchronization group for the first time and is waiting for the initial full synchronization.
    -   **Full Data Sync in Progress**: indicates that the share is being used for the first time to synchronize full data from the OSS bucket.
    -   **Sync Normal**: indicates that no synchronization error has occurred to the share.
    -   **Express Sync Disabled**: indicates that the express synchronization feature is disabled for the share.
    -   **Message Queue Inaccessible**: indicates that the queue corresponding to the share cannot be accessed.
    -   **Message Topic Inaccessible**: indicates that the topic corresponding to the share cannot be accessed.
    -   **Message Queue and Topic Inaccessible**: indicates that the queue and topic corresponding to the share cannot be accessed. |
    |**Message Queue Name**|The name of the MNS queue that is used by the synchronization group.|

-   Add a share to or remove a share from a synchronization group.

    You can click **Settings** in the **Actions** column for the target synchronization group. In the **Set Sync Group** dialog box, add a share to or remove a share from the synchronization group. To add a share, follow the instructions in Step 6 in the Create a synchronization group section.

-   Delete a synchronization group.

    If you want to delete a synchronization group, click**Delete** in the **Actions** column for the target synchronization group. In the dialog box that appears, click **OK**.


