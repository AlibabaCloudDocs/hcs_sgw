# 如何使用块网关创建文件系统并刷新缓存到iSCSI盘

本文介绍使用块网关创建文件系统，并刷新缓存到iSCSI盘的方法。

-   Linux环境

    在iSCSI卷上创建了本地文件系统（如xfs、ext4等），使用sync命令将数据刷新到iSCSI卷上。在手动卸载文件系统时，文件系统也会将缓存数据刷新到iSCSI卷上。

    ![Linux环境](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8292197951/p63424.png)

-   Windows环境

    在iSCSI卷上创建本地文件系统ntfs，可以利用sysinternal工具提供的sync.exe或sync64.exe刷新缓存数据到iSCSI卷上。

    sync工具下载地址：[Sync v2.2](https://docs.microsoft.com/zh-cn/sysinternals/downloads/sync)。

    ![Windows](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8292197951/p63425.png)


