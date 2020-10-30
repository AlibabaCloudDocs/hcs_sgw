# Upgrade the public bandwidth

This topic describes how to upgrade the public bandwidth for a file gateway in the Cloud Storage Gateway \(CSG\) console.

When you create a file gateway, the public bandwidth is not configured by default. However, if you need to upload data from a file gateway to an Object Storage Service \(OSS\) bucket that resides in a different region, you must configure a high public bandwidth to ensure the efficiency of data transmission. The higher the public bandwidth, the faster the data is transferred.

-   Only the public bandwidth of the file gateways that are deployed on Alibaba Cloud can be upgraded.
-   You can configure the public bandwidth when you create a file gateway. The default value is 5 Mbit/s.
-   You can upgrade the public bandwidth of a file gateway on the Gateways page.
-   This section describes the billing items of the public bandwidth feature.
    1.  You are charged by Cloud Storage Gateway for configuring the public bandwidth feature. For more information, see [Pricing](/intl.en-US/Pricing/Pricing.md).
    2.  You are also charged by OSS for accessing OSS resources. For more information, see [Traffic fees](https://help.aliyun.com/document_detail/173535.html?spm=a2c4g.11174283.6.573.76c37da2MRZekh).

1.  Log on to the .

2.  In the upper-left corner, select the region where the file gateway resides.

3.  In the left-side navigation pane, click **Gateways**. On the Gateways page, find the file gateway and choose **More** \> **Upgrade Network Bandwidth** in the Actions column.

4.  In the Upgrade Network Bandwidth dialog box, configure the public bandwidth.

    **Note:** The value of the public bandwidth must be greater than the current value and cannot exceed 200 Mbit/s. The default value is 5 Mbit/s.

5.  You can also configure the public bandwidth when you create a file gateway. In the **Gateway Configurations** wizard of the **Create Gateway** dialog box, select **Public Network Bandwidth**. For more information, see [Create a file gateway](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage file gateways.md).

    **Note:** If you select Public Network Bandwidth, the default minimum value is 6 Mbit/s and the maximum value is 200 Mbit/s.


