# Manage iSCSI volumes

This topic describes how to manage an iSCSI volume in the local gateway console. You can create, enable, disable, delete, repair, and extend an iSCSI volume. You can also configure CHAP authorization in the local gateway console.

-   You have deployed the local block gateway console. For more information, see [Deploy the local block gateway console](/intl.en-US/User Guide (On-Premises)/Block Gateway/Deploy the local block gateway console.md).
-   You have bound the cloud resources. For more information, see [Bind a cloud resource](/intl.en-US/User Guide (On-Premises)/Block Gateway/Manage cloud resources.md).
-   You have added a cache disk to the block gateway. For more information, see [Add a cache disk](/intl.en-US/User Guide (On-Premises)/Block Gateway/Manage cache disks.md).

    If you need to create an iSCSI volume that has the Cache mode enabled, you must add a cache disk to the block gateway first.


## Create an iSCSI volume

1.  Open your browser, and in the address bar, enter `https://<IP address of the target block gateway>` to connect to the local block gateway console.

2.  In the dialog box that appears, enter the username and password, and click **OK**.

3.  Select the ISCSI volumes tab, and click **Create**.

4.  In the **Create iSCSI** dialog box that appears, set the following parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Name**|Specifies the name of the iSCSI volume that you want to create. The name must be 1 to 31 characters in length, and can contain letters and digits.|
    |**Use Recovery Mode**|Specifies whether to restore a volume that uses the specified OSS bucket as backend storage. Valid values: Yes and No.     -   **Yes**: uses the metadata such as the capacity of the specified volume to restore the volume.
    -   **No**: uses the specified OSS bucket to create a volume. |
    |**Capacity**|When you set **Use Recovery Mode** to **No**, you must set the **Capacity** parameter. Valid values: 1 GB to 256 TB. |
    |**Cloud Resource**|Specifies the cloud resource that you have bound to the gateway.|
    |**Enabled**|Specifies whether to enable the specified iSCSI volume. You can set this parameter to **No** to disable the specified iSCSI volume. |
    |**Data Access Mode**|Specifies the mode that CSG uses to read and write files. Valid values: Write-through Mode and Cache Mode.     -   **Write-through Mode**: writes files directly to an OSS bucket, and reads data directly from the bucket.
    -   **Cache Mode**: writes files to and reads files from a target local cache disk in priority. Typically, the Cache mode provides better read and write performance. |
    |**Cache**|When you set **Data Access Mode** to **Cache Mode**, you must specify a cache disk.|
    |**Storage Allocation Unit**|When you set **Use Recovery Mode** to **No**, you must set the **Storage Allocation Unit** parameter. Valid values: 8 KB, 16 KB, 32 KB, 64 KB, and 128 KB. Default value: 32 KB.|


## Configure CHAP authorization

1.  On the ISCSI volume tab, find the target iSCSI volume, and click **Settings**.

2.  In the Configure CHAP authorization dialog box, complete the following configurations.

    -   **Authorization Method**: Select **CHAP** to configure CHAP.
    -   **CHAP User Name**: Specify a CHAP username.
    -   **CHAP Password**: Specify a CHAP password. The password must be 12 to 16 characters in length.
3.  Click **Confirm**.


## Other supported operations

On the ISCSI volumes tab, you can also perform the following operations.

|Operation|Description|
|---------|-----------|
|Delete an iSCSI volume|Find the target iSCSI volume and click **Delete** in the Actions column. When you delete an iSCSI volume, you can choose whether to delete the data stored in the associated OSS bucket at the same time.

**Note:**

-   After you delete an iSCSI volume that has the Cache mode enabled, the corresponding cache disk is detached from the volume.
-   After you delete an iSCSI volume, all data stored in the volume is deleted. Proceed with caution. |
|Extend the iSCSI volume|If the iSCSI volume space is insufficient, you can choose **More** \> **Extend** to extend the volume. The extended capacity must be larger than the original capacity.

**Note:** To extend the iSCSI volume, you need to stop all I/O operations. After you extend the volume, you need to scan and discover the new extended space on the host. |
|Disable an iSCSI volume|Find the target iSCSI volume, and choose **More** \> **Disable** to temporarily disable the iSCSI volume. A disabled iSCSI volume cannot be used. |
|Enable an iSCSI volume|Find the target iSCSI volume, and choose **More** \> **Enable** to enable the SCSI volume.|
|Fix the iSCSI volume|If the iSCSI volume fails, choose **More** \> **Repair** to repair the volume.|

-   [Use an iSCSI volume from the Linux operating system](/intl.en-US/User Guide (On-Premises)/Block Gateway/Use iSCSI volumes/Use an iSCSI volume from the Linux operating system.md)
-   [Use an iSCSI volume from the Windows operating system](/intl.en-US/User Guide (On-Premises)/Block Gateway/Use iSCSI volumes/Use an iSCSI volume from the Windows operating system.md)

