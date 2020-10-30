# Upgrade a block gateway

This topic describes how to upgrade a block gateway in the Cloud Storage Gateway \(CSG\) console.

A block gateway is created. For more information, see [Create a block gateway](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Manage block gateways.md).

If a block gateway no longer meets your business requirements, you can upgrade the gateway for more scenarios. After you upgrade the block gateway, the gateway can provide higher read and write bandwidth, more shares, and better user experience.

|Specification|Basic|Standard|Enhanced|Advanced|
|:-----------:|:---:|:------:|:------:|:------:|
|Basic|N/A|✓|✓|✓|
|Standard|×|N/A|✓|✓|
|Enhanced|×|×|N/A|✓|
|Advanced|×|×|×|N/A|

**Note:**

-   The check mark \(✓\) indicates that the specification can be upgraded. The cross mark \(×\) indicates that the specification cannot be upgraded.
-   Only block gateways that are deployed on Alibaba Cloud can be upgraded.
-   Block gateways cannot be downgraded.
-   The available specifications of a block gateway depend on the zone where the gateway resides.

1.  Log on to the [Cloud Storage Gateway console](https://sgwnew.console.aliyun.com/).

2.  In the upper-left corner, select the region where the block gateway resides.

3.  In the left-side navigation pane, click **Gateways**. On the Gateways page, find the block gateway and choose **More** \> **Upgrade Gateway** in the Actions column.

4.  In the **Upgrade Gateway** dialog box, select a specification based on your needs, and then click **OK**.

    **Note:**

    -   If you set an inappropriate value of the public bandwidth, service failure may occur and you may need to mount CSG on your client again.
    -   In the Task section of the Sync Groups page, you can view the progress and status of an upgrade task.

