# 在Windows系统上使用卷

本文介绍如何在Windows操作系统上连接并使用iSCSI卷。

-   已创建iSCSI卷。具体操作，请参见[创建iSCSI卷](/intl.zh-CN/云控制台用户指南/块网关/管理iSCSI卷.md)。
-   在Windows操作系统中已开启**Microsoft iSCSI Initiator Service**服务。

    ![Microsoft iSCSI Initiator Service服务](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0153559951/p60049.png)


## 连接卷

1.  登录[云服务器ECS](https://ecs.console.aliyun.com/)。

    **说明：** 如果您的本地主机已通过专线和阿里云专有网络连通，您也可以使用本地主机进行操作。

2.  连接ECS Windows实例。具体操作，请参见[连接ECS实例]()

3.  找到并启动**iSCSI发起程序**。

4.  设置iSCSI门户。

    1.  在iSCSI发起程序属性对话框中，单击发现页签，然后单击**发现门户（P）**。

        ![发现门户](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0153559951/p60004.png)

    2.  在发现目标门户对话框中，配置IP（IPv4或者IPv6）地址并单击**确定**。

        -   在IP地址对话框中输入IPv4地址，如图：

            ![发现目标](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0153559951/p60006.png)

        -   在IP地址对话框中输入IPv6地址，如图：

            ![ipv6](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9891240161/p212635.png)

        -   3260为访问端口，保持不变。
        -   10.0.0.0为块网关IPv4地址，2408:4004:110:6000:4656:f88e:1c14:e578为块网关IPv6地址。

            您可以在阿里云云存储网关控制台上找到对应的块网关，在其卷信息页面中获取块网关IPv4地址，在网关列表中的服务IP第二行获取块网关IPv6地址。

            **说明：**

            -   网关从v1.6.0版本开始支持IPv6。
            -   IPv6方式下挂载目前仅呼和浩特区域支持，网关所使用的VPC和VSwitch要支持使用IPv6。
            -   IPv6方式的 ，使用前请先确保所使用的ECS客户端已经配置了IPv6地址。
            -   如果已有网关所使用的VPC和VSwitch支持IPv6，则可以在网关操作列表中启用IPv6后，在网关列表的服务IP第二行获取IPv6地址，而在此VPC下新创建的网关默认直接支持IPv6，不需要进行启用操作。
5.  连接iSCSI卷。

    1.  在iSCSI发起程序属性对话框中，单击目标页签，然后单击**连接**。

        ![连接](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0153559951/p60007.png)

    2.  在连接到目标对话框中，选择目标iSCSI卷并选中**将此连接添加到收藏目标列表**。

        ![连接到目标](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0153559951/p60009.png)

    3.  （可选）在连接到目标对话框中，单击**高级**，设置CHAP认证信息，单击**确定**。

        **说明：** 如果您在创建iSCSI卷时，启用了CHAP认证，则需要在高级设置对话框中设置CHAP认证信息后，才能使用iSCSI卷。

        在高级设置对话框中，勾选**启动 CHAP 登录**，并设置名称和目标机密。

        -   在**名称**框中输入创建iSCSI卷时设置的入站CHAP用户。
        -   在**目标机密**框中输入创建iSCSI卷时设置的入站CHAP密码。
        ![CHAP认证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1153559951/p60116.png)

    4.  确认连接结果。

        目标iSCSI卷的状态显示为**已连接**，则表示连接成功。

        ![确认连接结果](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1153559951/p60013.png)


## 查看卷

对于已经连接的iSCSI卷，我们可以通过以下步骤来查看。

1.  打开计算机管理，右键单击**磁盘管理** \> **重新扫描磁盘**，即可查看新连接的iSCSI卷。

    连接iSCSI卷成功后，您可以在本地主机中使用iSCSI卷。

    ![确认连接结果](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1153559951/p60017.png)


## 删除卷

当不使用iSCSI卷时，断开连接之后，本地计算机中不再出现相应磁盘。

1.  在iSCSI 发起程序属性对话框中，选择目标页签，单击**取消连接**。

2.  确认取消连接结果。

    目标iSCSI卷的状态显示为**不活动**，则表示断开连接成功。


