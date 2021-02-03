# Manage SMB shares

This topic describes how to manage Server Message Block \(SMB\) shares in the on-premises file gateway console. You can create, delete, disable, and modify SMB shares. You can also configure AD or LDAP and add SMB users.

1.  A cache disk is added to the gateway. For more information, see [Add a cache disk](/intl.en-US/User Guide (On-Premises)/File Gateway/Manage cache disks.md).
2.  Cloud resources are bound. For more information, see [Bind a cloud resource](/intl.en-US/User Guide (On-Premises)/File Gateway/Manage cloud resources.md).

SMB is a network protocol that facilitates network communication between servers and clients or between network nodes. You can use this protocol to share files. SMB requires both a client and a server.

Cloud Storage Gateway \(CSG\) acts as an SMB server and provides the file sharing service. When you access CSG from a Windows-based client, CSG receives a request from the client and returns a response.

To use the SMB service, you must configure a share directory in the CSG console, create an SMB user, and specify user permissions.

## Create an SMB share

1.  Open your browser, and in the address bar, enter `https://<IP address of the target file gateway>` to connect to the local file gateway console.

2.  In the dialog box that appears, enter the username and password, and click **OK**.

3.  On the **SMB** page, click **Create** in the upper-right corner.

4.  In the Create SMB Share dialog box, set the following parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Share Name**|The name of the SMB share.|
    |**Read-only Users**|The list of users who have read-only access to the SMB share.|
    |**Read/Write Users**|The list of users who have read and write access to the SMB share.|
    |**Enable**|Specify whether to enable SMB sharing. If you do not want to enable SMB sharing, you can select **No** to disable SMB sharing. |
    |**Browsable**|Specify whether the SMB share can be discovered by network neighbors.|
    |**Mode**|Valid values: Cache Mode and Replication Mode.     -   **Replication Mode**: In this mode, two backups of all data are created. One is stored in the on-premises cache disk and the other is stored in the OSS bucket.
    -   **Cache Mode**: In this mode, the backup stored in the on-premises cache disk contains only metadata and user data that is frequently accessed. The backup stored in the OSS bucket contains all data. |
    |**Reverse Sync**|Specify whether to synchronize metadata stored in the OSS bucket to the on-premises cache disk. This feature is suitable for disaster recovery, data restoration, and data sharing scenarios. **Note:** During a remote sync process, the system scans all objects in the bucket. If the number of objects is large, you are charged for calling the OSS API. For more information, see [Pricing of OSS](https://www.aliyun.com/price/product?spm=a2c4g.11186623.2.26.18277b55Ki5BVd#/oss/detail). |
    |**Encryption Type**|You can select **None** or **Server-side Encryption**. If you select **Server-side Encryption**, you must also set the **ID** parameter. You can log on to the [KMS console](https://kms.console.aliyun.com/) and create a key. For more information, see [Create a CMK]().

 After you enable OSS server-side encryption, you can bring your own key \(BYOK\). The system supports keys imported from Key Management Service \(KMS\).

 After OSS server-side encryption is enabled, the system uses the imported key to encrypt files uploaded to OSS by using a share directory. You can call the GetObject operation to check whether the specified file is encrypted. In the response header, if the x-oss-server-side-encryption field value is KMS and the x-oss-server-side-encryption-key-id field value is the key ID, the file is encrypted.

 **Note:**

    -   This feature is available only to selected users.
    -   When you create a key in the KMS console, you must select the same region as the OSS bucket. |
    |**Bucket Name**|Select an existing bucket.|
    |**Subdirectory**|Specify a subdirectory of the bucket. The subdirectory name can contain only letters and digits.

 **Note:** File gateways V1.0.38 and later allow you to map the root directory of a file system to a subdirectory of a bucket. This enables separate file access between users.

You can specify an existing subdirectory or a subdirectory that does not exist in the bucket. After you create a share, the specified subdirectory serves as the root directory, and stores all related files and directories. |
    |**Cache Use**|Specifies whether to enable metadata disks. If you use metadata disks, data disks are separated from metadata disks, and metadata disks are used to store metadata of share directories.     -   If you select **Yes**, you must set the **Metadata** and **Data** parameters.
    -   If you select **No**, you must set the **Cache Disk** parameter.
 **Note:** This feature is available only to selected users. |
    |**Ignore Deletion**|During the data synchronization process, the OSS bucket ignores all delete operations. The backup stored in the OSS bucket contains all data.|
    |**Sync Latency**|You can specify a synchronization latency to upload files that you have modified and closed. The **Sync Latency** feature avoids OSS file fragmentation caused by frequent on-premises modifications. The default value is 5 seconds and the maximum value is 120 seconds.|
    |**Write Speed Limit**|Specify the maximum speed of writing data. Valid values: 0 to 1280. Unit: MB/s. Default value: 0, which indicates that the upload rate is not limited.|
    |**Upload Speed Limit**|Specify the maximum speed of uploading data. Valid values: 0 to 1280. Unit: MB/s. Default value: 0, which indicates that the upload rate is not limited. **Note:** When you customize the maximum write speed and upload speed, make sure that the maximum upload speed is not lower than the maximum write speed. |
    |**Fragmentation Optimization**|Specifies whether to optimize the performance for applications that frequently and randomly read and write small amounts of data. You can enable this feature based on your needs.|
    |**Upload Optimization**|This feature releases cache in real time. You can enable this feature if you synchronize only backups to the cloud.|


## AD and LDAP

Active Directory \(AD\) and Lightweight Directory Access Protocol \(LDAP\) are standard application protocols used to query and change directory information. Select the AD or LDAP service that you want to join and configure the settings.

-   You can join an AD domain only after you complete the DNS settings.
-   You can join either an AD or LDAP domain.
-   The permissions of the current AD domain user, LDAP user, and on-premises user override each other and whichever configured last takes effect. After you join or leave an AD domain, or connect to or disconnect from an LDAP server, the user permissions configured in the CIFS share are automatically removed.
-   The AD feature supports 64-bit Windows Server 2016 Datacenter and Windows Server 2012 R2 Datacenter.
-   The LDAP feature supports 64-bit CentOS 7.4 with OpenLDAP 2.4.44.

## Configure AD settings

1.  Configure the DNS server.

    1.  In the on-premises console of file gateways, click **About**.

    2.  In the Network Configuration section, click **Update DNS**.

    3.  In the Update DNS dialog box, enter the IP addresses of DNS servers. Click **OK**.

        In the **DNS server** field, specify the IP address of the AD server to resolve the AD domain name.

2.  Join an AD domain.

    1.  Choose **SMB** \> **AD/LDAP**.

    2.  In the Windows AD section, click **Join AD**.

    3.  In the Join AD dialog box, set the following parameters. Click **OK**.

        -   **Server IP Address**: Enter the IP address of the AD server.
        -   **Username**: Enter the username of the administrator.
        -   **Password**: Enter the password of the administrator.
        After the connection is established, the status of Connected under **Windows Active Directory \(AD\)** changes to **Yes**.

        **Note:** After you join the AD domain, the on-premises user permissions configured in the SMB share are removed.


## Configure LDAP

1.  In the on-premises console of file gateways, choose **SMB** \> **AD/LDAP**.

2.  In the LDAP section, click **Join LDAP**.

3.  In the Connect LDAP Server dialog box, set the following parameters and click **OK**.

    -   **Server IP Address**: Enter the IP address of the LDAP server, which is the directory system agent.
    -   **TLS Support**: Specify the method used by the system to communicate with the LDAP server.
    -   **Base DN**: Specify the LDAP domain, for example, dc=iftdomain, or dc=ift.local.
    -   **Root DN**: Specify the root DN, for example, cn=admin, dc=iftdomain, or dc=ift.local.
    -   **Password**: Enter the password of the root directory.
    After the connection is established, the status of Connected under **Lightweight Directory Access Protocol \(LDAP\)** becomes **Yes**.

    **Note:** After you join the LDAP domain, the on-premises user permissions configured in the SMB share are removed.


## Add an SMB user

If you have not joined a domain, you can create an SMB user to access Cloud Storage Gateway.

-   If you have joined an AD domain, you can view all AD users on the SMB Users page.
-   If you have joined an LDAP domain, you can view all LDAP users that have a Samba password on the SMB Users page.
-   If you have joined an LDAP domain but have not configured a Samba password, click **Create** to add a Samba password for the LDAP users on the **SMB user** page.

    We recommend that you specify the same password for both Samba and LDAP.


1.  In the on-premises console of file gateways, choose **SMB** \> **SMB Users**.

2.  Click **Create**.

3.  In the Add SMB User dialog box, set the name and password.

4.  Click **OK**.


## What to do next

On the SMB page, you can also perform the following operations.

|Operation|Description|
|---------|-----------|
|Disable an SMB share|On the SMB page, you can disable the toggle on the upper-left side of the page to disable NFS sharing. If you want to disable a single SMB share, you can use the following method.

 On the SMB page, find the NFS share. Click **Settings** and set **Enable** to **No**. |
|Delete an SMB share|On the SMB Shares tab, find the SMB share, and click **Delete**. **Note:** After the SMB share is deleted, the Windows mount point or mapped network drive immediately becomes ineffective. |
|Modify an SMB share|On the SMB Shares tab, find the SMB share, and click **Settings** or **Advanced Settings**.|
|Cache Refresh|On the SMB Shares tab, find the SMB share, and click **Cache Refresh**.|
|Delete an SMB user|On the SMB Shares tab, find the SMB user, and click **Delete**.|
|Disable a connection|On the AD/LDAP tab, click **End Connection**.|

[Access SMB shares](/intl.en-US/User Guide (On-Premises)/File Gateway/Access shares/Access SMB shares.md)

