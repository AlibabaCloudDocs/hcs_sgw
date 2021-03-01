# Manage a file gateway in the on-premises gateway console

This topic describes how to configure shares in the on-premises file gateway console.

1.  An Alibaba Cloud account is created and the real-name verification is completed. For more information, see [Create an Alibaba Cloud account](https://www.alibabacloud.com/help/zh/doc-detail/50482.html).

    **Note:** We recommend that you log on to the CSG console as a RAM user. For more information, see [Use RAM to implement account-based access control](/intl.en-US/Best Practice/Use RAM to implement account-based access control.md).

2.  CSG is activated.

    When you log on to the for the first time, activate the CSG service as prompted.

3.  The on-premises file gateway console is deployed. For more information, see [Deploy an on-premises console for a file gateway](/intl.en-US/User Guide (On-Premises)/File Gateway/Deploy an on-premises console for a file gateway.md).
4.  An Object Storage Service \(OSS\) bucket is created. For more information, see [Create buckets](/intl.en-US/Quick Start/OSS console/Create buckets.md).

    **Note:**

    -   CSG supports Standard, Infrequent Access \(IA\), and Archive OSS buckets.
    -   If you do not enable the archive feature when you create a share, you must restore archived files before you perform read operations.
5.  A disk is added. For more information, see [Add disks](/intl.en-US/User Guide (On-Premises)/File Gateway/Add disks.md).

## Step 1: Add a cache disk

Each shared directory of Cloud Storage Gateway \(CSG\) corresponds to a unique cache disk. If you need to create multiple shared directories, you must create multiple cache disks. You can transmit data in a shared directory to Object Storage Service \(OSS\) or synchronize data from OSS to an on-premises device by using a cache disk.

1.  Open your browser, and enter `https://<IP address of the file gateway>` in the address bar to connect to the on-premises file gateway console.

2.  In the dialog box that appears, enter your username and password, and then click **OK**.

3.  In the left-side navigation pane, click **Caches**. On the Caches page, click **Create**.

4.  In the Create Cache dialog box, set the following parameters:

    -   **Disk**: Click **Select**, and then select an available disk in the Select disk dialog box.

        Disks are available only after you add the disks on the deployment platform. For more information, see [Add disks](/intl.en-US/User Guide (On-Premises)/File Gateway/Add disks.md).

    -   **File System**: This parameter is optional. You can select this check box to reuse the data in the specified cache disk. If you delete a share by accident, you can recreate the share and use this feature to restore data.

        **Note:** If no file system exists on the cache disk, the cache disk fails to be created after you select the File System check box.

5.  Click **OK**.


## Step 2: Bind cloud resources

You can create shares that use OSS buckets as backend storage. One bucket corresponds to one share. You can bind multiple cloud resources to a file gateway.

**Note:** By default, the data that is written to a gateway by a client is uploaded in real time to an OSS bucket that is bound to the gateway. You can also specify a latency for the upload operation. The maximum latency is 120 seconds.

1.  In the on-premises file gateway console, click **Cloud Resources** in the left-side navigation pane. On the Cloud Resources page, click **Bind**.

2.  In the Bind Cloud Resource dialog box, set the required parameters. The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Resource Name**|The name of the cloud resource that you want to bind.|
    |**Cross-region Binding**|    -   **Yes**: You can access a bucket that resides in a different region from the specified gateway.
    -   **No**: You can access only a bucket that resides in the same region as the specified gateway.
 **Note:** The time zone of the on-premises file gateway must be the same as that of the OSS bucket. |
    |**Region**|Select a region where the bucket resides.|
    |**Bucket Name**|Select a bucket that you want to bind to the gateway.|
    |**Use SSL**|If you select **Yes**, you can connect to the OSS bucket over SSL.|

3.  Click **OK**.


## Step 3: Create a share

On-premises file gateways support Network File System \(NFS\) shares and Server Message Block \(SMB\) shares. You can create a share based on your business requirements. This section describes how to create an NFS share. For information about how to create an SMB share, see [Manage SMB shares](/intl.en-US/User Guide (On-Premises)/File Gateway/Manage SMB shares.md).

1.  Install an NFS client. For more information, see [Install an NFS client](/intl.en-US/User Guide (On-Premises)/File Gateway/Manage NFS shares.md).

2.  In the on-premises file gateway console, click **NFS** in the left-side navigation pane. On the Files Gateway \(NFS\) page, click **Create**.

3.  In the Create NFS Share dialog box, set the required parameters, and then click **OK**. The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Share Name**|The virtual mount point of the NFS share that you want to create. You can use this share name to mount an NFSv4 share. To mount an NFSv3 share, you must run the `showmount -e <IP address of the gateway>` command to obtain the mount point. |
    |**Read/Write Client IPs**|The IP address or CIDR block of the client that you allow to read data from and write data to the NFS gateway, for example, 192.168.10.10 or 192.168.0.0/24. You can enter multiple IP addresses or CIDR blocks. |
    |**Read-only Client IPs**|The IP address or CIDR block of the client that you allow to only read data from the NFS gateway, for example, 192.168.10.10 or 192.168.0.0/24. You can enter multiple IP addresses or CIDR blocks. |
    |**User Mapping**|Maps an NFS client user to an NFS server user. This parameter is available only when you set **Protocol** to **NFS**.

     -   none: NFS client users are not mapped to the nobody user on the NFS server.
    -   root\_squash: restricts root user permissions. NFS clients that use the root identity are mapped to the nobody user on the NFS server.
    -   all\_squash: restricts all user permissions. No matter what identity an NFS client uses, the client is mapped to the nobody user on the NFS server.
    -   all\_anonymous: restricts all user permissions. No matter what identity an NFS client uses, the client is mapped to the anonymous user on the NFS server. |
    |**Archive**|    -   If you select **Yes**, the archive feature is enabled. You can archive and restore files in a share by using the archive management tool.
    -   If you select **No**, the archive feature is disabled. You cannot manage files by using the archive management tool. When you read data from an archived file, the system initiates a request to restore the file. Latency may occur during the restoration, but no error occurs.
 **Note:** Basic file gateways do not support the **Archive** feature. |
    |**Enabled**|Select whether to enable the specified NFS share. If you do not want to use the NFS share, you can select **No** to disable the NFS share. |
    |**Mode**|Valid values: Cache Mode and Replication Mode.     -   **Replication Mode**: In this mode, two backups are created for all data. One backup is stored in the on-premises cache disk and the other backup is stored in the associated OSS bucket.
    -   **Cache Mode**: In this mode, the backup stored in the on-premises cache disk contains only metadata and frequently accessed user data. The backup stored in the OSS bucket contains all data. |
    |**Reverse Sync**|Specifies whether to synchronize metadata stored in the OSS bucket to the on-premises cache disk. This feature applies to disaster recovery, data restoration, and data sharing scenarios. **Note:** During a reverse synchronization process, the system scans all objects in the bucket. If the number of objects is large, you are charged for calling the OSS API. For more information, see [OSS pricing](https://www.aliyun.com/price/product?spm=a2c4g.11186623.2.26.18277b55Ki5BVd#/oss/detail). |
    |**Encrypt**|Valid values:**None** and **Server-side Encryption**. If you select **Server-side Encryption**, you must set the **Key ID** parameter. You can create a key in the [KMS console](https://kms.console.aliyun.com/). For more information, see [Create a CMK]().

 After you enable the OSS server-side encryption feature, you can bring your own key \(BYOK\). The system supports keys imported from Key Management Service \(KMS\).

 After you enable the OSS server-side encryption feature, the system uses the imported key to encrypt files uploaded to OSS by using the shared directory. You can call the GetObject API operation to check whether the specified file is encrypted. If the value of the x-oss-server-side-encryption field is KMS and the value of the x-oss-server-side-encryption-key-id field is the key ID in the response header, the file is encrypted.

 **Note:**

    -   Only the users in the whitelist can use this feature.
    -   When you create a key in the KMS console, you must select the same region as the specified OSS bucket. |
    |**Bucket Name**|Select an existing bucket.|
    |**Subdirectory**|Enter a subdirectory of the bucket. The Subdirectory field supports only letters and digits.

 **Note:** For version 1.0.38 and later, you can map the root directory of a file system to a subdirectory of a bucket. This allows you to separate file access requests.

You can specify an existing subdirectory or a subdirectory that does not exist in the bucket. After you create the share, the specified subdirectory serves as the root directory, and stores all related files and directories. |
    |**Use Metadata**|Specifies whether to use metadata disks. If you use metadata disks, data disks are separated from metadata disks, and metadata disks are used to store the metadata of shared directories.     -   If you select **Yes**, you must set the **Metadata** and **Data** parameters.
    -   If you select **No**, you must set the **Cache Disk** parameter.
 **Note:** Only the users in the whitelist can use this feature. |
    |**Ignore Deletions**|If you select Yes, the data that is deleted from the on-premises cache disk is not deleted from the OSS bucket. The OSS bucket retains all data.|
    |**NFS V4 Optimization**|Specifies whether to improve the upload efficiency of NFSv4 files. If you enable this feature, Network File System version 3 \(NFSv3\) is no longer supported.|
    |**Sync Latency**|Specify a synchronization latency to upload modified and closed files. The **Sync Latency** feature prevents OSS file fragmentation that is caused by frequent on-premises modifications. Default value: 5. Maximum value: 120. Unit: seconds.|
    |**Max Write Speed**|Specify the maximum write speed. Valid values: 0 to 1280. Unit: MB/s. Default value: 0. The value 0 indicates that the write speed is unlimited.|
    |**Max Upload Speed**|Specify the maximum upload speed. Valid values: 0 to 1280. Unit: MB/s. Default value: 0. The value 0 indicates that the upload speed is unlimited. **Note:** When you customize the maximum write speed and upload speed, make sure that the maximum upload speed is not lower than the maximum write speed. |
    |**Fragmentation Optimization**|Specifies whether to optimize the performance for applications that frequently and randomly read and write small amounts of data. Proceed with caution.|
    |**Upload Optimization**|If you select Yes, cached data is cleared in real time. You can enable this feature if you synchronize only backups to the cloud.|

4.  Click **OK**.

5.  After you create a share, you can access the shared directory by using an NFS client. For more information, see [Access an NFS share directory](/intl.en-US/User Guide (On-Premises)/File Gateway/Access shares/Access an NFS share directory.md).


