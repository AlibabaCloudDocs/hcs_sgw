# Upgrade a file gateway

This topic describes how to upgrade a file gateway in the Cloud Storage Gateway \(CSG\) console.

A file gateway is created. For more information, see [Create a file gateway](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage file gateways.md).

If a file gateway no longer meets your business requirements, you can upgrade the gateway. After you upgrade the file gateway, the gateway can provide higher read and write bandwidth, more shares, and better user experience.

|Specification|Basic|Standard|Enhanced|Advanced|
|:-----------:|:---:|:------:|:------:|:------:|
|Basic|N/A|✓|✓|✓|
|Standard|×|N/A|✓|✓|
|Enhanced|×|×|N/A|✓|
|Advanced|×|×|×|N/A|

**Note:**

-   The check mark \(✓\) indicates that the specification can be upgraded. The cross mark \(×\) indicates that the specification cannot be upgraded.
-   Only file gateways that are deployed on Alibaba Cloud can be upgraded.
-   File gateways cannot be downgraded.
-   The available specifications of a file gateway depend on the zone where the gateway resides.

1.  Log on to the [Cloud Storage Gateway console](https://sgwnew.console.aliyun.com/).

2.  In the upper-left corner, select the region where the file gateway resides.

3.  In the left-side navigation pane, click **Gateways**. On the Gateways page, find the file gateway and choose **More** \> **Upgrade Gateway** in the Actions column.

4.  In the **Upgrade Gateway** dialog box, select a specification based on your needs, and then click **OK**.

    **Note:**

    -   If you set a value for the public bandwidth that does not meet your usage requirements, then service failure may occur and you may need to mount CSG on your client again.
    -   In the Task section of the Sync Groups page, you can view the progress and status of an upgrade task.

