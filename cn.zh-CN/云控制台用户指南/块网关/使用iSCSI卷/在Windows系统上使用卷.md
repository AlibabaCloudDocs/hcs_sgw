# 在Windows系统上使用卷 {#task_2134422 .task}

本文介绍如何在Windows操作系统上连接并使用iSCSI卷。

-   已创建iSCSI卷，详情请参见[创建iSCSI卷](../cn.zh-CN/云控制台用户指南/块网关/管理iSCSI卷.md#section_oac_lbk_wdg)。
-   在Windows操作系统中已开启Microsoft iSCSI Initiator Service服务。

    ![Microsoft iSCSI Initiator Service服务](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427549/156860123960049_zh-CN.png)


## 操作步骤 {#section_62i_0wt_7in .section}

1.  登录[云服务器ECS](https://ecs.console.aliyun.com/)。 

    **说明：** 如果您的本地主机已通过专线和阿里云专有网络连通，您也可以使用本地主机进行操作。

2.  找到并启动**iSCSI发起程序**。
3.  设置iSCSI门户。 
    1.  在iSCSI 发起程序属性对话框中，选择发现页签，单击**发现门户**。 

        ![发现门户](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427549/156860123960004_zh-CN.png)

    2.  在发现目标门户对话框中，配置IP地址并单击**确定**。 

        -   10.0.0.0为块网关IP地址。

            您可以在阿里云云存储网关控制台上找到对应的块网关，在其卷信息页面中获取块网关IP地址。

        -   3260为访问端口，保持不变。
        ![发现目标](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427549/156860123960006_zh-CN.png)

4.  连接iSCSI卷。 
    1.  在iSCSI 发起程序属性对话框中，选择目标页签，单击**连接**。 

        ![连接](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427549/156860123960007_zh-CN.png)

    2.  在连接到目标对话框中，选择目标iSCSI卷并勾选**将此连接添加到收藏目标列表**。 

        ![连接到目标](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427549/156860123960009_zh-CN.png)

    3.  （可选）在连接到目标对话框中，单击**高级**，设置CHAP认证信息。 

        **说明：** 如果您在创建iSCSI卷时，启用了CHAP认证，则需要在高级设置对话框中设置CHAP认证信息后，才能使用iSCSI卷。

        在高级设置对话框中，勾选**启动 CHAP 登录**，并设置名称和目标机密。

        -   在**名称**框中输入创建iSCSI卷时设置的入站CHAP用户。
        -   在**目标机密**框中输入创建iSCSI卷时设置的入站CHAP密码。
        ![CHAP认证](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427549/156860123960116_zh-CN.png)

    4.  返回到连接到目标对话框，单击**确定**。
    5.  确认连接结果。 

        目标iSCSI卷的状态显示为**已连接**，则表示连接成功。

        ![确认连接结果](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427549/156860124060013_zh-CN.png)

5.  打开计算机管理，右键单击**磁盘管理** \> **重新扫描磁盘**，即可查看新连接的iSCSI卷。 

    连接iSCSI卷成功后，您可以在本地主机中使用iSCSI卷。

    ![确认连接结果](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427549/156860124060017_zh-CN.png)


