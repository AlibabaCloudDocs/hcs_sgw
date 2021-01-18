# 访问NFS共享目录

本文介绍在Linux操作系统如何通过客户端访问云存储网关。

已创建共享，具体操作，请参见[创建共享](/intl.zh-CN/云控制台用户指南/文件网关/管理共享.md)。

## 挂载共享目录

1.  登录[云服务器ECS](https://ecs.console.aliyun.com/)。

2.  连接ECS Linux实例。具体操作，请参见[连接ECS实例]()。

3.  在ECS实例中，执行以下命令将共享目录挂载至客户端所在的本地目录。

    -   IPv4方式：

        ```
        mount.nfs 192.168.0.0:/shares local-directory
        ```

    -   IPv6方式：

        ```
        mount.nfs [2408:4004:ffff:ffff:ffff:ffff:ffff:ffff]:/shares local-directory
        ```

    **说明：**

    -   仅华东5（呼和浩特）地域支持采用IPv6方式挂载，网关所使用的VPC和VSwitch要支持IPv6。
    -   IPv6方式的挂载，使用前请先确保所使用的ECS客户端已经配置了IPv6地址。
    -   如果已有网关所使用的VPC和VSwitch支持IPv6，则可以在网关操作列表中启用IPv6后，获取IPv6的挂载点，而在此VPC下新创建的网关默认直接支持IPv6，不需要进行启用操作。
    命令中的参数说明如下：

    -   `192.168.0.0:/shares`：存储网关挂载点（包括存储网关IPv4地址和共享目录名称），请根据实际值替换。您可以在阿里云云存储网关控制台，找到目标存储网关，在其共享页面查看挂载点。
    -   `[2408:4004:ffff:ffff:ffff:ffff:ffff:ffff]:/shares`：存储网关挂载点（包括存储网关IPv6地址和共享目录名称），请根据实际值替换。您可以在阿里云云存储网关控制台，找到目标存储网关，在其共享页面查看挂载点。
    -   `local-directory`：客户端的本地目录，可以是任意有读写权限的目录，不能是不存在的文件目录。
    -   `noac`：如果您开启了极速同步功能，且要挂载的共享已经加入了极速同步组，可以在挂载命令中加入该参数。加入该参数后，客户端会实时从网关获取文件系统的元数据，从而使您更快地在客户端看到同步结果。该参数对客户端的读写性能有一定影响，如果客户端对文件变化敏感，建议加入该参数；如果客户端对读写性能敏感，不建议加入该参数。示例命令如下：

        ```
        mount.nfs -o noac 192.168.0.0/shares local-directory
        ```

    -   如果您使用的是1.0.35版本之前的云存储网关且使用NFS v3协议挂载，需要按以下步骤进行挂载：

1.  执行以下命令获取挂载路径（例如获取到挂载路径为`192.168.0.0:/shares`）。

    ```
    `showmount –e <网关挂载IP地址>`
    ```

2.  执行以下命令完成挂载。

    ```
    mount -t nfs -o vers=3,proto=tcp,nolock,noacl,sync 192.168.0.0:/shares local-directory
    ```

4.  执行`df -h`命令，查看挂载结果。

    如果系统显示如下类似信息，则表示挂载成功。

    ![guazai](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8451767061/p195842.png)

    **说明：** 挂载成功后，显示的是每个共享管理的文件系统的容量，不同的网关规格能够支持的文件系统容量，请参见[产品规格](/intl.zh-CN/产品简介/产品规格.md)。目前OSS存储空间无容量限制。


## 访问共享目录

挂载成功后，您可以像操作本地目录一样操作共享目录。如果访问用户具有写权限，则可以向共享目录写入数据；如果访问用户只有读权限，则只能读取文件。

**说明：** 云存储网关的共享目录与OSS Bucket之间进行了数据同步，您对共享目录的操作实际也是对OSS进行操作。

## 自动挂载NFS共享目录

为避免已挂载文件系统的云服务器ECS重启后，挂载信息丢失，您可以通过在Linux ECS实例中配置/etc/fstab（推荐使用）文件或/etc/rc.local文件，实现在云服务器ECS设置重启时NFS文件系统自动挂载。

**说明：** 在配置自动挂载前，请先确认手动挂载成功，避免ECS启动失败。

-   方案一（推荐使用）：打开/etc/fstab配置文件，添加挂载命令。

    **说明：** 如果您是在CentOS 6系统中配置自动挂载，您需先执行

    1.  `chkconfig netfs on`命令，保证netfs开机自启动。
    2.  打开/etc/netconfig配置文件，注释掉inet6相关的内容。
    -   如果您要挂载NFS v4文件系统：
        -   IPv4方式：

            ```
            192.168.0.0:/shares local-directory nfs defaults 0 0
            ```

        -   IPv6方式：

            ```
            [2408:4004:ffff:ffff:ffff:ffff:ffff:ffff]:/shares local-directory nfs defaults 0 0
            ```

    -   如果您要使挂载NFS v3文件系统：
        -   IPv4方式下挂载执行以下命令：

            ```
            192.168.0.0:/shares local-directory nfs vers=3.0 defaults 0 0
            ```

        -   IPv6方式下挂载执行以下命令：

            ```
            [2408:4004:ffff:ffff:ffff:ffff:ffff:ffff]:/shares local-directory nfs vers=3.0 defaults 0 0
            ```


-   方案二：打开/etc/rc.local配置文件，执行挂载命令。

    **说明：** 在配置/etc/rc.local文件前，请确保用户对/etc/rc.local和/etc/rc.d/rc.local文件有可执行权限。例如：CentOS 7.x系统，用户默认无可执行权限，需添加权限后才能配置/etc/rc.local文件。

    -   如果您要挂载NFS v4文件系统：
        -   IPv4方式下挂载执行以下命令：

            ```
            sudo mount.nfs 192.168.0.0:/shares local-directory
            ```

        -   IPv6方式下挂载执行以下命令：

            ```
            sudo mount.nfs [2408:4004:ffff:ffff:ffff:ffff:ffff:ffff]:/shares local-directory
            ```

    -   如果您要挂载NFS v3文件系统：
        -   IPv4方式下挂载执行以下命令：

            ```
            sudo mount -t nfs -o vers=3,proto=tcp,nolock,noacl,sync 192.168.0.0:/shares local-directory
            ```

        -   IPv6方式下挂载执行以下命令：

            ```
            sudo mount -t nfs -o vers=3,proto=tcp,nolock,noacl,sync [2408:4004:ffff:ffff:ffff:ffff:ffff:ffff]:/shares local-directory
            ```

    命令中的参数说明如下：

    -   `192.168.0.0:/shares`：存储网关挂载点（包括存储网关IPv4地址和共享目录名称），请根据实际值替换。您可以在阿里云云存储网关控制台，找到目标存储网关，在其共享页面查看挂载点。
    -   `[2408:4004:ffff:ffff:ffff:ffff:ffff:ffff]:/shares`：存储网关挂载点（包括存储网关IPv6地址和共享目录名称），请根据实际值替换。您可以在阿里云云存储网关控制台，找到目标存储网关，在其共享页面查看挂载点。
    -   `local-directory`：客户端的本地目录，可以是任意有读写权限的目录，不能是不存在的文件目录。
    -   `noac`：如果您开启了极速同步功能，且要挂载的共享已经加入了极速同步组，可以在挂载命令中加入该参数。加入该参数后，客户端会实时从网关获取文件系统的元数据，从而使您更快地在客户端看到同步结果。该参数对客户端的读写性能有一定影响，如果客户端对文件变化敏感，建议加入该参数；如果客户端对读写性能敏感，不建议加入该参数。示例命令如下：

        ```
        mount.nfs -o noac 192.168.0.0/shares local-directory
        ```


1.  执行reboot命令，重启云服务器ECS。

