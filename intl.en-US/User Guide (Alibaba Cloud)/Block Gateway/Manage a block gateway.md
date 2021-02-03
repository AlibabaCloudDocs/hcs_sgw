# Manage a block gateway

This topic describes how to manage a block gateway in the Cloud Storage Gateway console, including how to create, delete, and rename a block gateway.

1.  You have registered an Alibaba Cloud account and passed the real-name verification. For more information, see [Sign up with Alibaba Cloud](https://www.alibabacloud.com/help/zh/doc-detail/50482.html).

    **Note:** We recommend that you log on to the CSG console as a RAM user. For more information, see [Use RAM to implement account-based access control](/intl.en-US/Best Practice/Use RAM to implement account-based access control.md).

2.  You have registered an Alibaba Cloud account and passed the real-name verification. For more information, see [Sign up with Alibaba Cloud](https://www.alibabacloud.com/help/zh/doc-detail/50482.html).

    **Note:** We recommend that you log on to the CSG console as a RAM user. For more information, see [Use RAM to implement account-based access control](/intl.en-US/Best Practice/Use RAM to implement account-based access control.md).

3.  You have activated the CSG service.

    When you log on to the for the first time, you can follow the instructions on the page to activate the CSG service.

4.  A Virtual Private Cloud \(VPC\) is available in the region where you want to create a block gateway. For more information, see [Create a VPC and a VSwitch](/intl.en-US/Quick Start/Create an IPv4 VPC network.md).
5.  An Elastic Compute Service \(ECS\) instance is available in the region where you want to create a block gateway. The ECS instance runs in the VPC that you have created. For more information, see [Create an instance]().

    **Note:** If your local host has been connected to an Alibaba Cloud VPC through a leased line, you can also manage the block gateway on your local host.


## Create a block gateway

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  Select the region where you want to create a block gateway.

3.  In the left-side navigation pane, select Overview to go to the Overview page. In the Gateway Clusters section, click the target gateway cluster to go to the Gateway Cluster page, and then click **Create**.

    If you have not created any gateway cluster, on the Overview page, click **Create Gateway Cluster** to create a gateway cluster.

4.  On the **Create Gateway** dialog box that appears, set the following parameters, and click **Next**.

    |Parameter|Description|
    |---------|-----------|
    |**Name**|Specifies the name of the gateway that you want to create. The name must be 1 to 60 characters in length, and can contain letters, Chinese characters, digits, periods \(.\), underscores \(\_\), and hyphens \(-\). It must start with a letter or a Chinese character. |
    |**Location**|Specifies the location where the target gateway is located. Valid values: **On-premises** and **Alibaba Cloud**.     -   **On-premises**: specifies a local block gateway that is deployed at your data center. You can deploy a local block gateway either in the CSG console or in the local block gateway console.
    -   **Alibaba Cloud**: specifies an in-cloud block gateway that is deployed in Alibaba Cloud. You can deploy an in-cloud block gateway only in the CSG console. |
    |**Type**|Specifies the type of the gateway that you want to create. Set this parameter to **Block Gateway**.|

5.  Click Next to open the **Configure Gateway** tab, set the following parameters, and then click **Next**.

    If you set **Location** to **Alibaba Cloud**, you must specify the following gateway parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Model**|Specifies the model of the gateway that you want to create. Valid values: **Basic**, **Standard**, **Enhanced**, and **Advanced**. For more information, see [Specifications](/intl.en-US/Overview/Specifications.md).|
    |**VPC**|Specifies the VPC where the target gateway is located. **Note:** This must be the VPC where your ECS instance or local host is located. |
    |**VSwitch**|Specifies the VSwitch that connects to the target gateway. **Note:** This must be the VSwitch that connects to your ECS instance or local host. If no gateway is available in the zone where the specified VSwitch is located, you can create a VSwitch in another zone. |

6.  Click Next to go to the **Paid Information** tab, set the following parameters, and then click **Next**.

    |Parameter|Description|
    |---------|-----------|
    |**Billing Method**|Specifies the method that the system uses to calculate billing for the target gateway. Valid values: **Pay-As-You-Go** and **Subscription**. For more information, see [Pricing](/intl.en-US/Pricing/Pricing.md). If you select **Subscription**, after you create the block gateway, you are redirected to the Cloud Storage Gateway \(Subscription\) page. Afterward, you must complete the payment on this page. For more information, see [Purchase Cloud Storage Gateway](/intl.en-US/Pricing/Subscription/Purchase a gateway.md). |
    |**After Expiration**|Specifies the way the system processes the target gateway after expiration. Valid values: **Pay-As-You-Go** and **Release After Expiration**.|

7.  Click Next to go to the **Summary** tab, make sure that the specified information is correct, and then click **OK**.

    -   After you create an in-cloud block gateway, the system completes the deployment in approximately 5 to 10 minutes. When the target gateway stays in the **Running** state, the gateway has been activated and deployed.
    -   After you create a local block gateway, click **Activate Gateway** in the Actions column next to the gateway, and on the Activate Gateway dialog box that appears, set the parameters for activating the gateway. For more information, see [Activate the gateway](/intl.en-US/User Guide (On-Premises)/File Gateway/Deploy an on-premises console for a file gateway.md).

## What to do next

The following table describes the related operations that you can perform on the Gateway Clusters page.

|Operation|Description|
|---------|-----------|
|Delete a gateway|Find the block gateway and choose **More** \> **Delete** in the Actions column. **Note:** You can delete only pay-as-you-go block gateways. |
|Rename a gateway|Find the block gateway and click **Edit** in the Actions column to rename the gateway.|
|Switch the billing method from pay-as-you-go to subscription|After you create a pay-as-you-go gateway, you can switch the billing method from pay-as-you-go to subscription. Find the file gateway and choose **More** \> **Switch to Subscription**. You are then redirected to the buy page. Select a specification as needed. For more information, see [Switch the billing method from pay-as-you-go to subscription](/intl.en-US/Pricing/Switch the billing method from pay-as-you-go to subscription.md). |
|Upload log data|Find the file gateway and choose **More** \> **Upload Supported Data** to upload the log data for troubleshooting.|
|Settle payments|To settle the payment for a subscription gateway, choose **More** \> **Purchase**.|
|Change expiration policies|To change the expiration policy for a subscription gateway, find the gateway and choose **More** \> **Switchover Expiration Policy**. For more information, see [Switch the expiration policy](/intl.en-US/Pricing/Subscription/Switch the expiration policy.md).|

[Create an iSCSI volume](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Manage iSCSI volumes.md)

