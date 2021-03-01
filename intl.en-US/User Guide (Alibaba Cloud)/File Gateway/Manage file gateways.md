# Manage file gateways

This topic describes how to manage file gateways in the Cloud Storage Gateway \(CSG\) console. You can create, delete, and rename a gateway.

1.  An Alibaba Cloud account is created and the real-name verification is completed. For more information, see [Create an Alibaba Cloud account](https://www.alibabacloud.com/help/zh/doc-detail/50482.html).

    **Note:** We recommend that you log on to the CSG console as a RAM user. For more information, see [Use RAM to implement account-based access control](/intl.en-US/Best Practice/Use RAM to implement account-based access control.md).

2.  CSG is activated.

    When you log on to the for the first time, activate the CSG service as prompted.

3.  A virtual private cloud \(VPC\) is available in the region where you want to create a cloud file gateway. For more information, see [Create an IPv4 VPC](/intl.en-US/Quick Start/Create an IPv4 VPC network.md).
4.  An Elastic Compute Service \(ECS\) instance is available in the region where you want to create a cloud file gateway. The ECS instance runs in the VPC. For more information, see [Create an ECS instance]().

    **Note:** If your on-premises host is connected to a VPC by using an Express Connect circuit, you can also manage the file gateway on your on-premises host.


## Create a file gateway

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

## Related operations

After you click Gateways in the left-side navigation pane, you can also perform the following operations on the Current Gateway Cluster page.

|Operation|Description|
|---------|-----------|
|Delete a gateway|Find the file gateway that you want to delete and choose **More** \> **Delete** in the Actions column. **Note:** You can delete only the pay-as-you-go file gateways. |
|Rename a gateway|Find the file gateway that you want to rename and click **Edit** in the Actions column.|
|Switch pay-as-you-go to subscription|After you create a pay-as-you-go gateway, you can switch the billing method from pay-as-you-go to subscription. Find the file gateway and choose **More** \> **Switch to Subscription** in the Actions column. On the buy page that appears, select a billing cycle as needed. For more information, see [Switch the billing method from pay-as-you-go to subscription](/intl.en-US/Pricing/Switch the billing method from pay-as-you-go to subscription.md). |
|Upload supported data|Find the file gateway and choose **More** \> **Upload Supported Data** in the Actions column. You can upload the log data that is generated by the gateway for troubleshooting.|
|Complete payments|If you have not completed the payment of a subscription gateway, choose **More** \> **Purchase** to complete the payment.|
|Change expiration policies|To change the expiration policy for a subscription gateway, find the file gateway and choose **More** \> **Change Expiration Policy** in the Actions column. For more information, see [Switch the expiration policy](/intl.en-US/Pricing/Subscription/Switch the expiration policy.md).|

[Add a cache disk](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage cache disks.md)

