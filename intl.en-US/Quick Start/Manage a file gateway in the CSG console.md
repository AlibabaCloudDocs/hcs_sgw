# Manage a file gateway in the CSG console

This topic describes how to create a file gateway and configure a share in the Cloud Storage Gateway \(CSG\) console.

1.  An Alibaba Cloud account is created and the real-name verification is completed. For more information, see [Create an Alibaba Cloud account](https://www.alibabacloud.com/help/zh/doc-detail/50482.html).

    **Note:** We recommend that you log on to the CSG console as a RAM user. For more information, see [Use RAM to implement account-based access control](/intl.en-US/Best Practice/Use RAM to implement account-based access control.md).

2.  CSG is activated.

    When you log on to the for the first time, activate the CSG service as prompted.

3.  A virtual private cloud \(VPC\) is available in the region where you want to create a cloud file gateway. For more information, see [Create an IPv4 VPC](/intl.en-US/Quick Start/Create an IPv4 VPC network.md).
4.  An Elastic Compute Service \(ECS\) instance is available in the region where you want to create a cloud file gateway. The ECS instance runs in the VPC. For more information, see [Create an ECS instance]().

    **Note:** If your on-premises host is connected to a VPC by using an Express Connect circuit, you can also manage the file gateway on your on-premises host.

5.  An Object Storage Service \(OSS\) bucket is created. For more information, see [Create buckets](/intl.en-US/Quick Start/OSS console/Create buckets.md).

    **Note:**

    -   CSG supports Standard, Infrequent Access \(IA\), and Archive OSS buckets.
    -   If you do not enable the archive feature when you create a share, you must restore archived files before you perform read operations.

## Step 1: Create a file gateway

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  Select the region where you want to create a file gateway.

3.  In the left-side navigation pane, click Gateways. On the Current Gateway Cluster page, select the gateway cluster, and then click **Create**.

    If you have not created a gateway cluster, click **Create Gateway Cluster** on the Overview page to create a gateway cluster.

4.  In the **Gateway Information** step, set the required parameters, and then click **Next**. The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Name**|The name of the gateway that you want to create.|
    |**Location**|The location where you want to deploy the gateway. Valid values: **On-premises** and **Alibaba Cloud**.     -   **On-premises**: specifies an on-premises file gateway that is deployed in your data center. You can deploy an on-premises file gateway either in the CSG console or in the on-premises file gateway console.
    -   **Alibaba Cloud**: specifies a cloud file gateway that is deployed on Alibaba Cloud. You can deploy a cloud file gateway only in the CSG console. |
    |**Type**|The type of the gateway that you want to create. Select **File Gateway**.|

5.  In the **Gateway Configurations** step, set the required parameters, and then click **Next**.

    If you set **Location** to **Alibaba Cloud**, you must set the following parameters in this step.

    |Parameter|Description|
    |---------|-----------|
    |**Edition**|The edition of the gateway that you want to create. Valid values: **Basic**, **Standard**, **Enhanced**, and **Performance Optimized**. For more information, see [Specifications](/intl.en-US/Overview/Specifications.md).|
    |**VPC**|The VPC where you want to deploy the gateway. **Note:** The specified VPC must be the VPC where your ECS instance or on-premises host resides. |
    |**VSwitch**|The vSwitch that is connected to the gateway. **Note:**

    -   The specified vSwitch must be the vSwitch that is connected to your ECS instance or on-premises host.
    -   If no gateway is available in the zone where the specified vSwitch resides, create a vSwitch in another zone. |
    |**Public Network Bandwidth**|The public bandwidth.**Note:**

    -   By default, Public Network Bandwidth is not selected. If you want to use a gateway that resides in another region, you must select and set the Public Network Bandwidth parameter. For more information, see [Upgrade the public bandwidth](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Upgrade the public bandwidth.md).
    -   Valid values: 6 Mbit/s to 200 Mbit/s. |

6.  In the **Billing Information** step, set the required parameters, and then click **Next**. The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Billing Method**|The method that the system uses to calculate fees for the gateway. Valid values: **Pay-as-you-go** and **Subscription**. For more information, see [Billable items and billing methods](/intl.en-US/Pricing/Billable items and billing methods.md). If you select **Subscription**, after you create the file gateway, you are redirected to the Cloud Storage Gateway \(Subscription\) page. Then, you must complete the payment as prompted. For more information, see [Purchase Cloud Storage Gateway](/intl.en-US/Pricing/Subscription/Purchase a gateway.md). |
    |**Expiration Policy**|Select an expiration policy for the gateway. Valid values: **Switch to Pay-as-you-go** and **Release**.|

7.  In the **Confirmation** step, confirm your settings, and then click **OK**.

    -   After you create a cloud file gateway, the system completes the deployment in 5 to 10 minutes. If the **Running** state is displayed in the Status column, the gateway is activated and deployed.
    -   After you create an on-premises file gateway, click **Activate Gateway** in the Actions column. In the Activate Gateway dialog box, set the required parameters to activate the gateway. For more information, see [Activate the gateway](/intl.en-US/User Guide (On-Premises)/File Gateway/Deploy an on-premises console for a file gateway.md).

## Step 2: Add a cache disk

**Note:** This section describes how to create a cache disk for a cloud file gateway. To create a cache disk for an on-premises file gateway, you must go to the platform where the on-premises gateway console is deployed. For more information, see [Add disks](/intl.en-US/User Guide (On-Premises)/File Gateway/Add disks.md).

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  Select the region where the file gateway resides.

3.  In the left-side navigation pane, click Gateways. On the Current Gateway Cluster page, click the file gateway ID to open the Shares page.

4.  In the left-side navigation pane, click **Cache**. On the Cache page, click **Create Cache**.

5.  In the Add Cache dialog box, set the following parameters:

    -   **Capacity**: the size of the cache dick that you want to create. Valid values: 40 GB to 32 TB.
    -   **Type**: the type of the cache disk that you want to create. Valid values: **Ultra Disk**, **Standard SSD**, and **ESSD**.
    **Note:**

    -   Basic gateway: The maximum cache capacity is 1 TB. PL3 is not supported for ESSD.
    -   Standard gateway: The maximum cache capacity is 2 TB.
6.  Click **OK**.

    If you create a subscription file gateway, you are redirected to the Cloud Storage Gateway Cache Disk \(Subscription\) page after you create a cache disk. Then, you must complete the payment as prompted. For more information, see [Purchase a cache disk](/intl.en-US/Pricing/Subscription/Purchase a cache disk.md).


## Step 3: Create a share

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  Select the region where the file gateway resides.

3.  In the left-side navigation pane, click Gateways. On the Current Gateway Cluster page, click the file gateway ID to open the Shares page.

4.  In the left-side navigation pane, click Share. On the Shares page, click **Create**.

5.  In the Bucket Settings step, set the required parameters, and then click **Next**. The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Cross-region Binding**|    -   **Yes**: You can access a bucket that resides in a different region from the specified gateway.
    -   **No**: You can access only a bucket that resides in the same region as the specified gateway. |
    |**Bucket Region**|Select a region where the bucket resides.|
    |**Bucket Name**|You can select an existing bucket from the drop-down list, or enter a subdirectory of the bucket in the Subdirectory field. The Subdirectory field supports only letters and digits.

**Note:**

    -   For version 1.0.38 and later, you can map the root directory of a file system to a subdirectory of a bucket. This allows you to separate file access requests.
    -   You can specify an existing subdirectory or a subdirectory that does not exist in the bucket. After you create the share, the specified subdirectory serves as the root directory, and stores all related files and directories. |
    |**Encrypt**|Valid values: **None** and **Server-side Encryption**. If you select **Server-side Encryption**, you must set the **Key ID** parameter. You can create a key in the [KMS console](https://kms.console.aliyun.com/). For more information, see [Create a CMK]().

After you enable the OSS server-side encryption feature, you can bring your own key \(BYOK\). The system supports keys imported from Key Management Service \(KMS\).

After you enable the OSS server-side encryption feature, the system uses the imported key to encrypt files uploaded to OSS by using the shared directory. You can call the GetObject API operation to check whether the specified file is encrypted. If the value of the x-oss-server-side-encryption field is KMS and the value of the x-oss-server-side-encryption-key-id field is the key ID in the response header, the file is encrypted.

**Note:**

    -   Only the users in the whitelist can use this feature.
    -   When you create a key in the KMS console, you must select the same region as the specified OSS bucket. |
    |**Use SSL to connect Bucket**|If you select **Yes**, you can connect to the OSS bucket over SSL.|

6.  In the **Basic Information** step, set the required parameters, and then click **Next**. The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Share Name**|The name of the Network File System \(NFS\) and Server Message Block \(SMB\) share that you want to create. If you set the Protocol parameter to **NFS**, the share name also specifies the virtual path of NFS version 4 \(NFSv4\). The name must be 1 to 32 characters in length and can contain letters and digits. It cannot start with a digit.

**Note:** |
    |**Protocol**|The name of the protocol that you use to connect to OSS buckets. Valid values: NFS and SMB.     -   The NFS protocol applies to scenarios where you need to access OSS buckets from a Linux operating system.
    -   The SMB protocol applies to scenarios where you need to access OSS buckets from a Windows operating system. |
    |**Cache**|Select an existing cache disk. **Note:** For a cache disk whose capacity is smaller than 5 TB, 20% of the space is used to store metadata. For a cache disk whose capacity is 5 TB or larger, 1 TB of the space is used to store metadata. For example, if you create a cache disk of 40 GB, the available cache space is 32 GB. If you create a cache disk of 20 TB, the available cache space is 19 TB. |
    |**User Mapping**|Maps an NFS client user to an NFS server user. This parameter is available only when you set **Protocol** to **NFS**.

    -   none: NFS client users are not mapped to the nobody user on the NFS server.
    -   root\_squash: restricts root user permissions. NFS clients that use the root identity are mapped to the nobody user on the NFS server.
    -   all\_squash: restricts all user permissions. No matter what identity an NFS client uses, the client is mapped to the nobody user on the NFS server.
    -   all\_anonymous: restricts all user permissions. No matter what identity an NFS client uses, the client is mapped to the anonymous user on the NFS server. |
    |**Archive**|This parameter is available only when you set **Protocol** to **NFS** and **User Mapping** to **none**.     -   If you select **Yes**, the archive feature is enabled. You can archive and restore files in a share by using the archive management tool.
    -   If you select **No**, the archive feature is disabled. You cannot manage files by using the archive management tool. When you read data from an archived file, the system initiates a request to restore the file. Latency may occur during the restoration, but no error occurs.
**Note:** Basic file gateways do not support the **Archive** feature. |
    |**Browsable**|Specifies whether the share can be accessed by using Network Neighborhood.|
    |**Windows Permission Support**|The Windows access control list. For more information, see [Enable Windows access-based enumeration](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Enable Windows access-based enumeration.md).|
    |**Add to Sync Group**|You can enable the express synchronization feature for the share and add the share to a synchronization group. Then, all changes made to the data stored in the associated OSS bucket is synchronized to the on-premises client of the share. After you select the Add to Sync Group check box, the Reverse Sync check box is automatically cleared. **Note:**

    -   To enable this feature, create a synchronization group first. Make sure that the synchronization group and the share use the same OSS bucket. For more information about how to create a synchronization group, see [Express synchronization](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Express synchronization.md).
    -   Only Standard, Enhanced, and Performance Optimized gateways support the express synchronization feature.
    -   The express synchronization feature depends on Alibaba Cloud Message Service \(MNS\). After you add a share to a synchronization group, you are charged for using MNS. For more information, see the "Context" section in [Express synchronization](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Express synchronization.md). |
    |**Advanced Settings**|After you select the **Advanced Settings** check box, the **Advanced Settings** step appears.|

7.  In the **Advanced Settings** step, set the required parameters, and then click **Next**. The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Mode**|    -   **Replication Mode**: In this mode, two backups are created for all data. One backup is stored in the on-premises cache disk and the other backup is stored in the associated OSS bucket.
    -   **Cache Mode**: In this mode, the backup stored in the on-premises cache disk contains only metadata and frequently accessed user data. The backup stored in the OSS bucket contains all data. |
    |**Transfer Acceleration**|This feature accelerates the data transfer speed across regions by using the public bandwidth of the gateway. Before you use this feature, make sure that the transfer acceleration feature is enabled for the associated OSS bucket.|
    |**Fragmentation Optimization**|Specifies whether to optimize the performance for applications that frequently and randomly read and write small amounts of data. Proceed with caution.|
    |**Direct IO Mode**|Data is directly read from and written to the cache disk.|
    |**Upload Optimization**|If you select Yes, cached data is cleared in real time. You can enable this feature if you synchronize only backups to the cloud.|
    |**Reverse Sync**|Specifies whether to synchronize metadata stored in the OSS bucket to the on-premises cache disk. This feature applies to disaster recovery, data restoration, and data sharing scenarios. **Note:**

    -   During a reverse synchronization process, the system scans all objects in the bucket. If the number of objects is large, you are charged for calling the OSS API. For more information, see [OSS pricing](https://www.aliyun.com/price/product?spm=a2c4g.11186623.2.26.18277b55Ki5BVd#/oss/detail).
    -   This parameter is unavailable if you select the **Add to Sync Group** check box in the **Basic Information** step. |
    |**Reverse Sync Interval**|If you set **Reverse Sync** to **Yes**, you must set the **Reverse Sync Interval** parameter. Valid values: 15 to 36000. Default value: 36000. Unit: seconds. **Note:** If the bucket contains a large number of objects, we recommend that you set the interval to a value greater than 3,600 seconds. Otherwise, repeated scans result in frequent OSS API calls. This incurs a large amount of fees. |
    |**Ignore Deletions**|If you select Yes, the data that is deleted from the on-premises cache disk is not deleted from the OSS bucket. The OSS bucket retains all data.|
    |**NFS V4 Optimization**|Specifies whether to improve the upload efficiency of NFSv4 files. If you select Yes, you cannot mount an NFSv3 file system on your on-premises host.|
    |**Sync Latency**|Specify a synchronization latency to upload modified and closed files. The **Sync Latency** feature prevents OSS file fragmentation that is caused by frequent on-premises modifications. Default value: 5. Maximum value: 120. Unit: seconds.|
    |**Replication Mode Advanced Settings**|This parameter is available only when you set **Mode** to **Replication Mode**. After you select the **Replication Mode Advanced Settings** check box, the **Replication Mode Advanced Settings** step appears.|

8.  In the **Replication Mode Advanced Settings** step, set the required parameters, and then click **Next**. The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Configure Directory in Replication Mode**|Specify the files to which the replication mode is applied.     -   If you do not select this check box, the replication mode is applied to all data in the share.
    -   After you select the check box, click **Add Directory** to add directories. The replication mode is applied to the specified directories whereas the rest of the data uses the cache mode.
**Note:**

    -   After you change the mode of a directory from cache to replication, the files in the directory can be synchronized only if the data download feature is enabled. We recommend that you enable the data download feature in replication mode.
    -   You can specify relative directories in the shared root directory. For example, if the actual directory is /mnt/myshare/mydir/ and the mount target is /mnt/myshare, you can enter /mydir/. |
    |**Data Download**|By default, the reverse synchronization and express synchronization features synchronize the metadata between the OSS bucket and the on-premises cache disk. The data download feature allows you to download data in replication mode. After you enable the **Reverse Sync** or [Express synchronization](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Express synchronization.md) feature, you can set **Data Download** to **Yes**. **Note:**

    -   If you download data in replication mode, the capacity of the cache disk must be 1.1 times higher than the size of files to be replicated. You must specify the cache capacity based on the expected growth of the bucket usage.
    -   When you enable the data download feature for the first time, a full scan is triggered. This process may reduce the performance of the gateway. We recommend that you enable the data download feature during off-peak hours and wait for the system to replicate all data.
    -   The data download feature allows only one user to write data to the bucket and multiple users to read data from the bucket at the same time. If multiple users access the bucket at the same time over the gateway or OSS bucket, only one user can upload files to the bucket. Other users can only download data. Data loss may occur if multiple users write data to and read data from the bucket at the same time. Proceed with caution. |
    |**Download Speed Limit**|This parameter is available only when you enable the **Data Download** feature in replication mode. The download speed limit must be at least 0 MB/s and at most 1,280 MB/s. If you set this parameter to 0 MB/s, the download speed is unlimited.|
    |**Reverse Sync Interval**|This parameter is available only when you enable the **Data Download** feature in replication mode. Valid values: 3600 to 36000. Default value: 36000. Unit: seconds. **Note:**

    -   If the bucket contains a large number of objects, we recommend that you set the interval to a value greater than 3,600 seconds. Otherwise, repeated scans result in frequent OSS API calls. This incurs a large amount of fees.
    -   Reverse synchronization is triggered only when you access the directory. To ensure that the data in other directories can be downloaded and new data can be downloaded in real time, use the [Express synchronization](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Express synchronization.md) feature. |

9.  In the **Confirmation** step, confirm your settings, and then click **OK**.

10. After you create a share, you can access the share from a client. For more information, see [Access shares](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Access shares/Access an NFS share directory.md).


