# Manage a block gateway in the CSG console

This topic describes how to create a block gateway and an Internet Small Computer Systems Interface \(iSCSI\) volume in the Cloud Storage Gateway \(CSG\) console.

1.  An Alibaba Cloud account is created and the real-name verification is completed. For more information, see [Create an Alibaba Cloud account](https://www.alibabacloud.com/help/zh/doc-detail/50482.html).

    **Note:** We recommend that you log on to the CSG console as a RAM user. For more information, see [Use RAM to implement account-based access control](/intl.en-US/Best Practice/Use RAM to implement account-based access control.md).

2.  CSG is activated.

    When you log on to the for the first time, activate the CSG service as prompted.

3.  A virtual private cloud \(VPC\) is available in the region where you want to create a block gateway. For more information, see [Create an IPv4 VPC](/intl.en-US/Quick Start/Create an IPv4 VPC network.md).
4.  An Elastic Compute Service \(ECS\) instance is available in the region where you want to create a block gateway. The ECS instance runs in the VPC. For more information, see [Create an ECS instance]().

    **Note:** If your on-premises host is connected to a VPC by using an Express Connect circuit, you can also manage the block gateway on your on-premises host.

5.  An Object Storage Service \(OSS\) bucket is created. For more information, see [Create buckets](/intl.en-US/Quick Start/OSS console/Create buckets.md).

    **Note:** Block gateways support only Standard and Infrequent Access \(IA\) OSS buckets.


## Step 1: Create a block gateway

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  Select the region where you want to create a block gateway.

3.  In the left-side navigation pane, click Gateways. On the Current Gateway Cluster page, select the gateway cluster, and then click **Create**.

    If you have not created a gateway cluster, click **Create Gateway Cluster** on the Overview page to create a gateway cluster.

4.  In the **Gateway Information** step, set the required parameters, and then click **Next**. The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Name**|The name of the gateway that you want to create. The name must be 1 to 60 characters in length and can contain letters, digits, periods \(.\), underscores \(\_\), and hyphens \(-\). It must start with a letter. |
    |**Location**|The location where you want to deploy the gateway. Valid values: **On-premises** and **Alibaba Cloud**.     -   **On-premises**: specifies an on-premises block gateway that is deployed in your data center. You can deploy an on-premises block gateway either in the CSG console or in the on-premises block gateway console.
    -   **Alibaba Cloud**: specifies a cloud block gateway that is deployed on Alibaba Cloud. You can deploy a cloud block gateway only in the CSG console. |
    |**Type**|The type of the gateway that you want to create. Select **iSCSI Gateway**.|

5.  In the **Gateway Configurations** step, set the required parameters, and then click **Next**.

    If you set **Location** to **Alibaba Cloud**, you must set the following parameters in this step.

    |Parameter|Description|
    |---------|-----------|
    |**Edition**|The edition of the gateway that you want to create. Valid values: **Basic**, **Standard**, **Enhanced**, and **Performance Optimized**. For more information, see [Specifications](/intl.en-US/Overview/Specifications.md).|
    |**VPC**|The VPC where you want to deploy the gateway. **Note:** The specified VPC must be the VPC where your ECS instance or on-premises host resides. |
    |**VSwitch**|The vSwitch that is connected to the gateway. **Note:**

    -   The specified vSwitch must be the vSwitch that is connected to your ECS instance or on-premises host.
    -   If no gateway is available in the zone where the specified vSwitch resides, create a vSwitch in another zone. |
    |Public Network Bandwidth|The public bandwidth.**Note:**

    -   By default, Public Network Bandwidth is not selected. If you want to use a gateway that resides in another region, you must select and set the Public Network Bandwidth parameter. For more information, see [Upgrade the public bandwidth](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Upgrade the public bandwidth.md). |

6.  In the **Billing Information** step, set the required parameters, and then click **Next**. The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Billing Method**|The method that the system uses to calculate fees for the gateway. Valid values: **Pay-as-you-go** and **Subscription**. For more information, see [Billable items and billing methods](/intl.en-US/Pricing/Billable items and billing methods.md). If you select **Subscription**, you are redirected to the Cloud Storage Gateway \(Subscription\) page after you create the block gateway. Then, you must complete the payment as prompted. For more information, see [Purchase a subscription gateway](/intl.en-US/Pricing/Subscription/Purchase a subscription gateway.md). |
    |**Expiration Policy**|Select an expiration policy for the gateway. Valid values: **Switch to Pay-as-you-go** and **Release**.|

7.  In the **Confirmation** step, confirm your settings, and then click **OK**.

    -   After you create a cloud block gateway, the system completes the deployment in 5 to 10 minutes. If the **Running** state is displayed in the Status column, the gateway is activated and deployed.
    -   After you create an on-premises block gateway, click **Activate Gateway** in the Actions column. In the Activate Gateway dialog box, set the required parameters to activate the gateway. For more information, see [Activate the gateway](/intl.en-US/User Guide (On-Premises)/Block Gateway/Deploy the local block gateway console.md).

## Step 2: Create a cache disk

Before you create an iSCSI volume whose cache mode is enabled, you must add a cache disk to the block gateway.

**Note:** This section describes how to create a cache disk for a cloud block gateway. To create a cache disk for an on-premises block gateway, you must go to the platform where the on-premises gateway console is deployed. For more information, see [Add disks](/intl.en-US/User Guide (On-Premises)/Block Gateway/Add disks.md).

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  Select the region where the block gateway resides.

3.  In the left-side navigation pane, click Gateways. On the Current Gateway Cluster page, click the block gateway ID to open the Volumes page.

4.  In the left-side navigation pane, click **Cache**. On the Cache page, click **Create Cache**.

5.  In the Add Cache dialog box, set the following parameters:

    -   **Capacity**: the size of the cache dick that you want to create. Valid values: 20 GB to 32 TB.
    -   **Type**: the type of the cache disk that you want to create. Valid values: **Ultra Disk**, **Standard SSD**, and **ESSD**.
    **Note:**

    -   Basic gateway: The maximum cache capacity is 1 TB. PL3 is not supported for ESSD.
    -   Standard gateway: The maximum cache capacity is 2 TB.
6.  Click **OK**.

    If you create a subscription block gateway, you are redirected to the Cloud Storage Gateway Cache Disk \(Subscription\) page after you create a cache disk. Then, you must complete the payment as prompted. For more information, see [Purchase a cache disk](/intl.en-US/Pricing/Subscription/Purchase a cache disk.md).


## Step 3: Create an iSCSI volume

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  Select the region where the block gateway resides.

3.  In the left-side navigation pane, click Gateways. On the Current Gateway Cluster page, click the block gateway ID to open the Volumes page.

4.  In the left-side navigation pane, click Volume Information. On the Volumes page, click **Create**.

5.  In the **Bucket Settings** step, set the required parameters, and then click **Next**. The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Cross-region Binding**|    -   **Yes**: You can access a bucket that resides in a different region from the specified gateway.
    -   **No**: You can access only a bucket that resides in the same region as the specified gateway.
**Note:** If you select an Internet endpoint of the specified bucket to bind your cloud resource to the block gateway, you may be charged for external download traffic. |
    |**Bucket Region**|Select an existing bucket.|
    |**Use SSL to Connect Bucket**|If you select **Yes**, you can connect to the OSS bucket over SSL.|

6.  In the **Basic Information** step, set the required parameters, and then click **Next**. The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Volume Name**|The name of the iSCSI volume that you want to create. The name must be 1 to 31 characters in length, and can contain letters and digits.|
    |**Recover**|Select whether to restore a volume that uses the specified OSS bucket as backend storage. Valid values: Yes and No.     -   **Yes**: ****When the associated OSS bucket is used as a volume, the system attempts to recover the volume based on the metadata of the volume, such as the size of the volume.
    -   **No**: ****The system uses the associated OSS bucket to create a volume. |
    |**Capacity**|If you set **Recover** to **No**, you must set the **Capacity** parameter. Valid values: 1 GB to 256 TB.|
    |**Mode**|The mode that CSG uses to read and write files. Valid values: Write-through Mode and Cache Mode.     -   **Write-through Mode**: In Write-through mode, data reads and writes are preferentially performed on the OSS bucket.
    -   **Cache Mode**: In Cache mode, data reads and writes are preferentially performed in the on-premises cache disk. iSCSI gateways have better read and write performance in Cache mode. |
    |**Cache**|If you set **Mode** to **Cache Mode**, you must select a cache disk. Make sure that you have added a cache disk to the block gateway. Otherwise, no cache disk is available.

    -   For information about cache disks of cloud block gateways, see [Step 2: Create a cache disk](#section_f2q_749_e24).
    -   For information about cache disks of on-premises block gateways, see [Add disks](/intl.en-US/User Guide (On-Premises)/Block Gateway/Add disks.md). |
    |**Storage Allocation Unit**|If you set **Recover** to **No**, you must set the **Storage Allocation Unit** parameter. Valid values: 8K, 16K, 32K, 64K, and 128K. Default value: 32K.|
    |**Authorization**|The one-way Challenge-Handshake Authentication Protocol \(CHAP\) authentication. If you select **CHAP** from the Authorization drop-down list, you must set the following parameters:

    -   **CHAP Username of Initiator**: Enter a CHAP username.
    -   **CHAP Password of Initiator**: Enter a CHAP password. The password must be 12 to 16 characters in length. |

7.  In the **Confirmation** step, confirm your settings, and then click **OK**.

8.  After you create an iSCSI volume, you can use the volume. For more information, see [Use iSCSI volumes](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Use iSCSI volumes/Use volumes on a Windows-based ECS instance.md).


