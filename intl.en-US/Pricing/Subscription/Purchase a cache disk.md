# Purchase a cache disk

To configure a cache disk for a subscription gateway, you must purchase a subscription cache disk. This topic describes how to purchase a subscription cache disk in the Cloud Storage Gateway \(CSG\) console.

A subscription gateway is purchased. For more information, see [Purchase Cloud Storage Gateway](/intl.en-US/Pricing/Subscription/Purchase a gateway.md).

## Procedure

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  Select the region where the gateway resides.

3.  In the left-side navigation pane, click Gateways. On the Current Gateway Cluster page, click the gateway ID to open the Shares page.

4.  In the left-side navigation pane, click Cache. On the Cache page, click **Create Cache**.

5.  Specify the capacity and type of the cache disk, and then click **OK**.

6.  On the Cloud Storage Gateway Cache Disk \(Subscription\) page, select a billing cycle, and then click **Buy Now**.

    **Note:** When you select a billing cycle on the Cloud Storage Gateway Cache Disk \(Subscription\) page, you cannot modify other settings.

7.  Complete the payment as prompted.


**Note:** A cache disk depends on a specified gateway. The billing cycles of a cache disk and a gateway may cause conflicts. For example, assume that you purchase a subscription gateway at the beginning of a month, and then purchase a subscription cache disk in the middle of the month. The billing cycles of the gateway and cache disk are both one month. If you set "Expiration Policy" to "Switch to Pay-as-you-go" when you create a gateway, you can delete the gateway after it expires at the beginning of the next month. If you set "Expiration Policy" to "Release", the subscription gateway will be released upon its expiration at the beginning of the next month. In this case, the subscription cache disk is released at the same time, and the cache usage fee is not returned.

