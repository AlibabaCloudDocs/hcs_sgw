# Manage cache disks

Cloud Storage Gateway provides a cache disk for each shared path. This topic describes how to manage the cache in the local file gateway console, including adding cache disks, deleting cache disks, and testing the speed of cache disks.

1.  You have deployed the local file gateway console. For more information, see [Deploy an on-premises console for a file gateway](/intl.en-US/User Guide (On-Premises)/File Gateway/Deploy an on-premises console for a file gateway.md).
2.  You have added cache disks. For more information, see [Add disks](/intl.en-US/User Guide (On-Premises)/File Gateway/Add disks.md).

Each file gateway share has a unique cache disk attached to it. To create multiple shares, you must create the same number of cache disks for the shares. You can upload data in a share to an Object Storage Service \(OSS\) bucket by using a cache disk. You can also download data from OSS buckets to a local device by using a cache disk.

## Add a cache disk

1.  Open your browser, and enter `https://<IP address of the file gateway>` in the address bar to connect to the on-premises file gateway console.

2.  In the dialog box that appears, enter your username and password, and then click **OK**.

3.  In the left-side navigation pane, click **Caches**. On the Caches page, click **Create**.

4.  In the Create Cache dialog box, set the following parameters:

    -   **Disk**: Click **Select**, and then select an available disk in the Select disk dialog box.

        Disks are available only after you add the disks on the deployment platform. For more information, see [Add disks](/intl.en-US/User Guide (On-Premises)/File Gateway/Add disks.md).

    -   **File System**: This parameter is optional. You can select this check box to reuse the data in the specified cache disk. If you delete a share by accident, you can recreate the share and use this feature to restore data.

        **Note:** If no file system exists on the cache disk, the cache disk fails to be created after you select the File System check box.

5.  Click **OK**.


## Other supported operations

On the Caches page, you can also perform the following operations.

|Operation|Description|
|---------|-----------|
|Delete a cache disk|Find the target cache disk, and then click **Delete** to delete the cache disk.|
|Test a cache disk|Find the target cache disk, and then click **Speed Test** to test the performance of the cache disk, including sequential I/O tests with 1 MB and 4 KB block sizes.|

-   [Create an NFS share](/intl.en-US/User Guide (On-Premises)/File Gateway/Manage NFS shares.md)
-   [Create an SMB share](/intl.en-US/User Guide (On-Premises)/File Gateway/Manage SMB shares.md)

