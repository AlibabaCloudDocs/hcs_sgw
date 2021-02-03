# Associate a share with multiple OSS buckets

You can associate a share with multiple Object Storage Service \(OSS\) buckets. You can obtain a unified namespace by adding multiple OSS buckets into a file system. After a share is mounted on a CSG agent, each OSS bucket associated with the share is mapped to an individual directory in the on-premises file system of the agent. This topic describes how to associate a share with multiple OSS buckets.

-   A file gateway is created and a cache is added. For more information, see [Create a file gateway](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage file gateways.md) and [Add a cache disk](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage cache disks.md).
-   An OSS bucket is created. For more information, see [Create buckets](/intl.en-US/Quick Start/OSS console/Create buckets.md).

When you associate a share with multiple OSS buckets, take note of the following limits:

-   Only the users in the whitelist can use this feature. If you are not in the whitelist and want to use this feature, submit a ticket.
-   Only Enhanced and Advanced gateways allow you to associate a share with multiple OSS buckets.
-   When you associate a share with multiple OSS buckets, you cannot specify the subdirectories of OSS buckets, or add the share to express sync groups.

## Create a share associated with multiple OSS buckets

To create a share and associate it with multiple OSS buckets, perform the following steps:

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  Select the region where the target file gateway is deployed.

3.  On the Gateway Clusters page, find and click the target file gateway.

4.  Click the Share tab, and then click **Create**.

5.  In the **Bucket Settings** step, set the required parameters as described in [Bucket settings](/intl.en-US/Quick Start/Manage a file gateway in the CSG console.md). Set the **Cross-region Binding** parameter to **Yes**.

6.  In the **Bucket Name** drop-down list, select the buckets. Click **Next**.

7.  In the **Basic Information** step, set the required parameters. Click **Next**.

    **Note:** For more information about the parameters, see [Basic information](/intl.en-US/Quick Start/Manage a file gateway in the CSG console.md).

8.  In the **Advanced Settings** step, set the required parameters and click **Next**.

    **Note:** For more information about the parameters, see [Advanced settings](/intl.en-US/Quick Start/Manage a file gateway in the CSG console.md).

9.  Click Next to go to the **Summary** tab, make sure that the specified information is correct, and then click **OK**.


After the share is created, OSS buckets associated with the share are displayed in the **The name of the OSS bucket** column.

After the share is mounted on an on-premises CSG agent, each OSS bucket associated with the share is mapped to an individual directory in the on-premises file system. For more information about how to mount a share on an on-premises CSG agent, see [Access an NFS share directory](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Access shares/Access an NFS share directory.md) or [Access an SMB share directory](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Access shares/Access SMB shares.md).

## Manage a share associated with multiple OSS buckets

You can change the buckets associated with a share in the Share Advanced Setting dialog box. For example, you can associate more buckets with the share or disassociate buckets from the share.

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  Select the region where the target file gateway is deployed.

3.  On the Gateway Clusters page, find and click the target file gateway.

4.  In the left-side navigation pane of the gateway details page, click **Share**. On the Share page, find the share, and click **Advanced Settings** in the Actions column.

5.  In the **NFS Share Advanced Settings** or **SMB Share Advanced Settings** dialog box, select buckets from the **Bucket Name** drop-down list, or click the **Remove** icon on the right side of a bucket.

6.  Click **OK**.


