# Manage shares

This topic describes how to manage shares in the Cloud Storage Gateway \(CSG\) console. You can create, delete, and configure Network File System \(NFS\) and Server Message Block \(SMB\) shares.

1.  A gateway is created. For more information, see [Create a file gateway](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage file gateways.md).
2.  A cache disk is added to the gateway. For more information, see [Add a cache disk](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage cache disks.md).
3.  You have created an Object Storage Service \(OSS\) bucket. For more information, see [Create buckets](/intl.en-US/Quick Start/OSS console/Create buckets.md).

    **Note:**

    -   CSG supports Standard, IA, and Archive OSS buckets.
    -   If you do not enable the archive feature when you create a share, you must restore archived files before you can read them.

## Create a share

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  Select the region where the file gateway is located.

3.  On the Gateway Clusters page, find and click the target file gateway.

4.  Click the Share tab, and then click **Create**.

5.  On the Bucket Setting tab, set the following parameters and click **Next**.

    |Parameter|Description|
    |---------|-----------|
    |**Cross-Region Binding**|    -   **Yes**: You can access OSS buckets that are not deployed in the same region as the gateway.
    -   **No**: You can only access OSS buckets that are deployed in the same region as the gateway. |
    |**Bucket Endpoint**|Select the endpoint of the target bucket.|
    |**Bucket Name**|You can select an existing bucket from the drop-down list, or enter a subdirectory of the target bucket in the Path Prefix field. The Path Prefix field supports only letters and digits.

 **Note:**

    -   Beginning with version 1.0.38, you can map the root directory of a file system to a subdirectory of a bucket to allow separate file access between users.
    -   You can specify an existing subdirectory or a subdirectory that does not exist in the bucket. After you create the share, the specified subdirectory works as the root directory, and stores all related files and directories. |
    |**Encryption**|You can select **No Encryption** or **Server Side Encryption**. If you select **Server Side Encryption**, you must also set the **CMK ID** parameter. You can log on to the [KMS console](https://kms.console.aliyun.com/) and create a key. For more information, see [Create a CMK]().

 After you enable OSS server-side encryption, you can provide your own key. The system supports keys imported from Key Management Service \(KMS\).

 After OSS server-side encryption is enabled, the system automatically uses the imported key to encrypt files uploaded to OSS through the shared directory. You can call the GetObject operation to check whether the specified file has been encrypted. In the response header, if the x-oss-server-side-encryption field value is KMS and the x-oss-server-side-encryption-key-id field value is the key ID, it indicates that the file has been encrypted.

 **Note:**

    -   This feature is available to selected users only.
    -   When you create a key in the KMS console, you must select the same region as the target OSS bucket. |
    |**Connect to Bucket Using SSL**|If you select **Yes**, you can connect to the OSS bucket over SSL.|

6.  On the **Basic Information** tab, set the following parameters and click **Next**.

    |Parameter|Description|
    |---------|-----------|
    |**Share Name**|Specify a name for the share. If you set the Protocol parameter to **NFS**, the share name also specifies the virtual path of Network File System version 4 \(NFSv4\). The name must be 1 to 32 characters in length and can contain letters and digits. It cannot start with a digit.

 **Note:** File gateways earlier than V1.0.35 do not allow you to mount a share on an on-premises directory over NFSv3. You must run the showmount -e <IP address of the destination gateway\> command to obtain the directory to which the share is mounted. |
    |**Protocol**|Select NFS or SMB as needed.     -   The NFS protocol applies to scenarios where you need to access Object Storage Service \(OSS\) buckets from a Linux operating system.
    -   The SMB protocol applies to scenarios where you need to access OSS buckets from a Windows operating system. |
    |**Cache**|Select an existing cache disk. **Note:** For a cache disk smaller than 5 TB, 20% of the space is used to store metadata. For a cache disk of 5 TB or larger, 1 TB of the space is used to store metadata. For example, if you create a cache disk of 40 GB, the actual available cache space is 32 GB. If you create a cache disk of 20 TB, the actual available cache space is 19 TB. |
    |**User Mapping**|Maps an NFS client user to an NFS server user. This parameter is required only when you set the **Protocol** parameter to **NFS**.

     -   none: NFS client users are not mapped to "nobody" on the NFS server.
    -   root\_squash: restricts the permissions of the root user. NFS clients that use the root identity are mapped to "nobody" on the NFS server.
    -   all\_squash: restricts the permissions of all users. No matter what identity an NFS client uses, the client is always mapped to "nobody" on the NFS server.
    -   all\_anonymous: restricts the permissions of all users. No matter what identity an NFS client uses, the client is always mapped to "anonymous" on the NFS server. |
    |**Archive**|You can enable this feature only if you set **Protocol** to **NFS**.     -   If you select **Yes**, archiving is enabled. Reading an archived file initiates a request to restore the file. The request does not trigger error messages. However, the request increases the latency to read the file.
    -   If you select **No**, archiving is disabled. Reading an archived file initiates a request to restore the file. You must restore the archived file first. Otherwise, an error message appears.
 **Note:** File gateways of the Basic type do not support the **Archive** feature. |
    |**Add to Sync Group**|For example, assume that you enable the express synchronization feature for the share and add the share to a sync group. Changes of the data stored in the associated OSS bucket will be synchronized to the on-premises CSG agent of the share. If you select the Join Sync Group check box, the Remote Sync check box is automatically cleared. **Note:**

    -   To enable this feature, create a sync group first. Make sure that the sync group and the share use the same OSS bucket. For more information, see [Express synchronization](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Express synchronization.md).
    -   Only standard, enhanced, and advanced gateways support the express synchronization feature.
    -   The express synchronization feature must work with Alibaba Cloud Message Service. After you add a share to a sync group, you are charged for Message Service. For more information, see the background information in [Express synchronization](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Express synchronization.md). |
    |**Advanced Settings**|If you select **Advanced Settings**, the **Advanced Settings** tab appears.|

7.  On the **Advanced Settings** tab, set the following parameters, and then click **Next**.

    |Parameter|Description|
    |---------|-----------|
    |**Cache Mode**|    -   **Replication Mode**: In this mode, two backups of all data are created. One is stored in the on-premises cache disk and the other is stored in the associated OSS bucket.
    -   **Cache Mode**: In this mode, the backup stored in the on-premises cache disk only contains metadata and user data that is frequently accessed. The backup stored in the OSS bucket contains all data. |
    |**Transfer Acceleration**|This feature accelerates the data transfer rate across regions by using the public bandwidth of the gateway. Before you use this feature, make sure that the associated OSS bucket enables this feature.|
    |**Fragmentation Optimization**|Specifies whether to optimize the performance for applications that frequently and randomly read and write small amounts of data. You can enable this feature based on your needs.|
    |**Direct IO Mode**|Data is directly read from and written to the cache disk.|
    |**Upload Optimization**|This feature releases cache in real time. You can enable this feature if you synchronize only backups to the cloud.|
    |**Reverse Sync**|Specify whether to synchronize metadata stored in the OSS bucket to the on-premises cache disk. This feature applies to disaster recovery, data restoration, and data sharing scenarios. **Note:**

    -   During a remote sync process, the system scans all objects in the bucket. If the number of objects is large, you are charged for calling the OSS API. For more information, see [Pricing of OSS](https://www.aliyun.com/price/product?spm=a2c4g.11186623.2.26.18277b55Ki5BVd#/oss/detail).
    -   If you have selected the **Add to Sync Group** check box on the **Basic Information** tab, this option is unavailable. |
    |**Reverse Sync Interval**|If you set **Reverse Sync** to **Yes**, you must set the **Reverse Sync Interval** parameter. Valid values: 15 to 36000. Default value: 36000. Unit: seconds. **Note:**

    -   If the bucket contains a large number of objects, we recommend that you set the interval to a value greater than 3,600 seconds. Otherwise, repeated scans result in frequent OSS API calls. This incurs a large amount of fees.
    -   If you configure the cache mode for the share and download data, you must set the interval between 3,600 seconds and 36,000 seconds. |
    |**Ignore Deletions**|During the data synchronization process, the OSS bucket ignores all delete operations. The backup stored in the OSS bucket contains all data.|
    |**NFS V4 Optimization**|This feature improves the efficiency of uploading files when you mount a share on your CSG agent over Network File System version 4 \(NFSv4\). If you enable this feature, Network File System version 3 \(NFSv3\) is no longer supported.|
    |**Sync Latency**|You can specify a period of time to delay the upload of files that you have modified and closed. The **Sync Latency** feature prevents OSS file fragmentation caused by frequent on-premises modifications. Default value: 5. Maximum value: 120. Unit: seconds.|
    |**Replication Mode Advanced Settings**|If you set **Cache Mode** to **Replication Mode**, you can select the **Replication Mode Advanced Settings** check box. The **Replication Mode Advanced Settings** tab appears.|

8.  On the **Replication Mode Advanced Settings** tab, set the following parameters, and then click **Next**.

    |Parameter|Description|
    |---------|-----------|
    |**Configure Directory in Replication Mode**|This parameter specifies the files to which the replication mode is applied.     -   If you do not select this check box, the replication mode is applied to all data in the share.
    -   After you select the check box, click **Add Directory** to add directories. The replication mode is applied to the specified directories whereas the rest of the data adopts cache mode.
 **Note:**

    -   If you change the mode of a directory from cache to replication, the files in the directory can be synchronized only when the data replication feature is also enabled. We recommend that you enable data replication.
    -   You can specify relative directories in the shared root directory. For example, if the specified directory is /mnt/myshare/mydir/ and the mount target is /mnt/myshare, you can enter /mydir/. |
    |**Data Download**|By default, the remote sync and the express synchronization features synchronize the metadata between the OSS bucket and the CSG agent. The data replication feature allows you to replicate all data or data of specific directories to the CSG agent. After you enable **Reverse Sync** or [Express synchronization](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Express synchronization.md), you can select **Yes** to enable **Data Download**. **Note:**

    -   Data replication requires the capacity of the cache disk to be 1.1 times larger than the file size to be replicated. Specify the cache capacity based on the expected growth of the bucket usage.
    -   When you enable data replication for the first time, a full scan is triggered. This process may reduce the performance of the gateway. Enable data replication during off-peak hours and wait for the system to replicate all of the data.
    -   Data replication allows only one user to write data to the bucket and multiple users to read data from the bucket at the same time. If multiple users access the bucket at the same time over the gateway or OSS bucket, only one user can upload files to the bucket, and other users can only download data. If multiple users access the bucket at the same time over the gateway or OSS bucket, only one user can upload files to the bucket, and other users can only download data. |
    |**Download Speed Limit**|After you enable **Data Download**, set this parameter. The download speed must not be lower than 0 MB/s and not be higher than 1,280 MB/s. If you set this parameter to 0 MB/s, it indicates that the download speed is not limited.|
    |**Reverse Sync Interval**|After you enable **Data Download**, set this parameter. Valid values: 3600 to 36000. Default value: 36000. Unit: seconds. **Note:**

    -   If the bucket contains a large number of objects, we recommend that you set the interval to a value greater than 3,600 seconds. Otherwise, repeated scans result in frequent OSS API calls. This incurs a large amount of fees.
    -   Remote sync is triggered only when the shared directory is accessed. We recommend that you enable express synchronization. This ensures that existing and incremental data in the shared directory can be synchronized to the CSG agent if no user accesses the directory. For more information, see [Express synchronization](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Express synchronization.md). |

9.  Click Next to go to the **Summary** tab, make sure that the specified information is correct, and then click **OK**.


## Configure an NFS share

If you select the **NFS** protocol when you create a share, click **Settings** in the Actions column to configure the NFS share.

1.  On the Share page, find the target share, and then click **Settings** in the Actions column.

2.  In the NFS Share Settings dialog box, set the following parameters.

    -   **User Mapping**: Select an NFS identity mapping to map NFS client users to NFS server users.
        -   none: NFS client users are not mapped to "nobody" on the NFS server.
        -   root\_squash: restricts the permissions of the root user. NFS clients that use the root identity are mapped to "nobody" on the NFS server.
        -   all\_squash: restricts the permissions of all users. No matter what identity an NFS client uses, the client is always mapped to "nobody" on the NFS server.
        -   all\_anonymous: restricts the permissions of all users. No matter what identity an NFS client uses, the client is always mapped to "anonymous" on the NFS server.
    -   **Read/Write Clients**: Specify IP addresses or CIDR blocks allowed to read and write the NFS share.

        For example, enter 192.168.10.10 or 192.168.0.0/24. You can enter multiple IP addresses or CIDR blocks.

    -   **Read-only Clients**: Specify IP addresses or CIDR blocks that can be used to only read the NFS share.

        For example, enter 192.168.10.10 or 192.168.0.0/24. You can enter multiple IP addresses or CIDR blocks.

    -   **Write Speed Limit**: The maximum write speed is 1,280 MB/s. The default value, 0, indicates that the write rate is not limited.
    -   **Upload Speed Limit**: The maximum upload speed is 1,280 MB/s. The default value, 0, indicates that the upload speed is not limited.

        **Note:** When you customize the maximum write speed and upload speed, make sure that the maximum upload speed is no lower than the maximum write speed.


## Configure an SMB share

If you select the **SMB** protocol when you create a share, you can click **Set** in the Actions column to configure the SMB share.

1.  On the Share page, find the share and click **Settings** in the Actions column.

2.  In the SMB Share Settings dialog box, set the following parameters.

    -   **Browsable**: Specify whether the share can be discovered by Network Neighborhood.
    -   **Read/write Users**: Specify users who can read and write the SMB share.
    -   **Read-only Users**: Specify users who can only read the SMB share.

        **Note:** If you grant a user both the read-only and read and write permissions, only the read-only permission takes effect.

    -   **Write Speed Limit**: The maximum write speed is 1,280 MB/s. The default value, 0, indicates that the write speed is not limited.
    -   **Upload Speed Limit**: The maximum upload speed is 1,280 MB/s. The default value, 0, indicates that the upload speed is not limited.

        **Note:** When you customize the maximum write speed and upload speed, make sure that the maximum upload speed is no lower than the maximum write speed.


## Other supported operations

On the Share page, you can also perform the following operations.

|Action|Description|
|------|-----------|
|Change advanced settings|Find the share and click **Advanced Settings** in the Actions column. For more information, see [Create a share](#section_qgs_5th_jol).|
|Delete a share|Find the share and click **Delete** in the Actions column. **Note:**

-   This operation does not delete the data stored in the associated OSS bucket.
-   This operation does not remove the attached cache disk.
-   This operation does not delete the data stored in the attached cache disk.
-   If you create another share, you must attach a cache disk and an OSS bucket to the share. |
|Restart NFS shares|Click **Restart NFS Shares** to restart all the shares connected to the gateway.|
|Restart SMB shares|Click **Restart SMB Shares** to restart all the SMB shares connected to the gateway.|
|Hide tasks|Click **Hide Tasks** to hide the task list at the bottom of the page.|
|View the upload and download queues|Find the share, and click the plus sign \(**+**\) next to the share name to view the upload and download queues. -   If the number of objects in the upload queue is not 0, one or more objects are waiting to be uploaded to the associated OSS bucket.
-   If the number of objects in the download queue is not 0, one or more objects are waiting to be downloaded.
-   If the numbers of files in the upload and download queues are both 0, data is synchronized between the gateway and the OSS bucket. |

[Access a share](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Access shares/Access NFS shares.md)

