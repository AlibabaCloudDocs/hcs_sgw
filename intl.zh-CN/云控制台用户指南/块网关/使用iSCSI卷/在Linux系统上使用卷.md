# 在Linux系统上使用卷

本文介绍如何在Linux操作系统上连接并使用iSCSI卷。

已创建iSCSI卷，具体操作请参见[创建iSCSI卷](/intl.zh-CN/云控制台用户指南/块网关/管理iSCSI卷.md)。

## 操作步骤

1.  登录[云服务器ECS](https://ecs.console.aliyun.com/)。

    **说明：** 如果您的本地主机已通过专线和阿里云专有网络连通，您也可以使用本地主机进行操作。

2.  连接ECS Linux实例，请参见[连接ECS实例]()

3.  安装iscsi-initiator-utils。

    您需要通过iscsi-initiator-utils连接到目标iSCSI卷，如果您已经安装，请跳过此步骤。

    ```
    sudo yum install iscsi-initiator-utils
    ```

4.  执行如下命令验证iSCSI守护进程是否正在运行。

    -   如果是RHEL 5/RHEL 6，请执行如下命令进行验证。

        ```
        sudo /etc/init.d/iscsi status
        ```

    -   如果是RHEL7，请执行如下命令进行验证。

        ```
        sudo service iscsid status
        ```

    如果执行以上命令，未返回**running**，则执行`sudo /etc/init.d/iscsi start`启动iSCSI守护进程。

5.  （可选）设置CHAP认证。

    **说明：** 如果您在创建iSCSI卷时，启用了CHAP认证，则需要在高级设置对话框中设置CHAP认证信息后，才能使用iSCSI卷。

    1.  执行如下命令打开iscsid.conf配置文件。

        ```
        vi /etc/iscsi/iscsid.conf
        ```

    2.  找到CHAP Settings，删除相关配置项前面的注释符**\#**，并设置用户和密码。

        -   用户为创建iSCSI卷时设置的入站CHAP用户。
        -   密码为创建iSCSI卷时设置的入站CHAP密码。
        ![设置CHAP认证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9053559951/p60122.png)

6.  发现iSCSI卷。

    -   IPv4方式发现卷如下：

        ```
        iscsiadm -m discovery -t st -p 10.0.0.0:3260
        ```

    -   IPv6方式发现卷如下：

        ```
        iscsiadm -m discovery -t st -p [2408:4004:110:6000:4656:f88e:1c14:e578]:3260
        ```

    -   10.0.0.0为块网关IPv4地址，2408:4004:110:6000:4656:f88e:1c14:e578为块网关IPv6地址。

        您可以在阿里云云存储网关控制台上找到对应的块网关，在其卷信息页面中获取块网关IPv4地址，在网关列表中的服务IP第二行获取块网关IPv6地址。

        **说明：**

        -   网关从v1.6.0版本开始支持IPv6。
        -   IPv6方式下挂载目前仅呼和浩特区域支持，网关所使用的VPC和VSwitch要支持使用IPv6。
        -   IPv6方式的 ，使用前请先确保所使用的ECS客户端已经配置了IPv6地址。
        -   如果已有网关所使用的VPC和VSwitch支持IPv6，则可以在网关操作列表中启用IPv6后，在网关列表的服务IP第二行获取IPv6地址，而在此VPC下新创建的网关默认直接支持IPv6，不需要进行启用操作。
    -   3260为访问端口，保持不变。
7.  挂载iSCSI卷。

    -   IPv4方式挂载如下：

        ```
        iscsiadm -m node -T iqn.2009-09.com.aliyun.iscsi-sgw:0test-test730 -p 10.0.0.0:3260 -l
        ```

    -   IPv6方式挂载如下：

        ```
        iscsiadm -m node -T iqn.2009-09.com.aliyun.iscsi-sgw:0test-test730 -p [2408:4004:110:6000:4656:f88e:1c14:e578]:3260 -l
        ```

    -   iqn.2009-09.com.aliyun.iscsi-sgw:0test-test730为iSCSI卷的目标名，可以从步骤6发现卷的命令返回中获取。
    -   10.0.0.0为块网关IPv4地址，2408:4004:110:6000:4656:f88e:1c14:e578为块网关IPv6地址。

        您可以在阿里云云存储网关控制台上找到对应的块网关，在其卷信息页面中获取块网关IPv4地址，在网关列表中的服务IP第二行获取块网关IPv6地址。

        **说明：**

        -   网关从v1.6.0版本开始支持IPv6。
        -   IPv6方式下挂载目前仅呼和浩特区域支持，网关所使用的VPC和VSwitch要支持使用IPv6。
        -   IPv6方式的 ，使用前请先确保所使用的ECS客户端已经配置了IPv6地址。
        -   如果已有网关所使用的VPC和VSwitch支持IPv6，则可以在网关操作列表中启用IPv6后，在网关列表的服务IP第二行获取IPv6地址，而在此VPC下新创建的网关默认直接支持IPv6，不需要进行启用操作。
    -   3260为访问端口，保持不变。
    **说明：** 由于iSCSI 协议限制，请勿将一个iSCSI卷挂载到多个Linux客户端。

8.  执行`fdisk -l`或`lsblk`命令查看iSCSI卷。

    当前状态下，已挂载的iSCSI卷成为一个可用的裸磁盘，您可以在本地主机上进行读写操作。

    ![查看卷](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9053559951/p60107.png)

9.  卸载iSCSI卷

    当不再使用iSCSI卷时可以通过以下命令行进行卸载。

    -   IPv4方式卸载如下：

        ```
        iscsiadm -m node -T iqn.2009-09.com.aliyun.iscsi-sgw:0test-test730 -p 10.0.0.0:3260 -u
        ```

    -   IPv6方式卸载如下：

        ```
        iscsiadm -m node -T iqn.2009-09.com.aliyun.iscsi-sgw:0test-test730 -p [2408:4004:110:6000:4656:f88e:1c14:e578]:3260 -u
        ```


