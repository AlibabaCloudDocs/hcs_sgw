# 在Windows系统上使用iSCSI卷 {#concept_108320_zh .task}

本文介绍如何在Windows操作系统上连接并使用iSCSI卷。

-   已创建iSCSI卷，详情请参见[创建iSCSI卷](cn.zh-CN/本地控制台用户指南/块网关/管理iSCSI卷.md#section_iku_7uf_1tw)。
-   在Windows操作系统中已开启Microsoft iSCSI Initiator Service服务。

    ![开启Microsoft iSCSI Initiator Service服务](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427549/156860188660049_zh-CN.png)


## 操作步骤 {#section_wth_7sn_78j .section}

1.  登录本地主机（Windows操作系统）。
2.  找到并启动**iSCSI发起程序**。
3.  设置iSCSI门户。 
    1.  在iSCSI 发起程序属性对话框中，选择发现页签，单击**发现门户**。 

        ![发现门户](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427549/156860188660004_zh-CN.png)

    2.  在发现目标门户对话框中，配置IP地址并单击**确定**。 

        -   10.0.0.0为块网关IP地址，您可以在本地块网关控制台的**关于** \> **网络信息**页面中获取。
        -   3260为访问端口，保持不变。
        ![发现目标](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427549/156860188660006_zh-CN.png)

4.  连接iSCSI卷。 
    1.  在iSCSI 发起程序属性对话框中，选择目标页签，单击**连接**。 

        ![连接](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427549/156860188660007_zh-CN.png)

    2.  在连接到目标对话框中，选择目标iSCSI卷并勾选**将此连接添加到收藏目标列表**。 

        ![连接到目标](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427549/156860188660009_zh-CN.png)

    3.  （可选）在连接到目标对话框中，单击**高级**，设置CHAP认证信息。 

        **说明：** 如果您在创建iSCSI卷时，启用了CHAP认证，则需要在高级设置对话框中设置CHAP认证信息后，才能使用iSCSI卷。

        在高级设置对话框中，勾选**启动 CHAP 登录**，并设置**名称**和**目标机密**。

        -   在**名称**框中输入创建iSCSI卷时设置的入站CHAP用户名。
        -   在**目标机密**框中输入创建iSCSI卷时设置的入站CHAP密码。
        ![CHAP认证](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427549/156860188660116_zh-CN.png)

    4.  返回连接到目标对话框，单击**确定**。
    5.  确认连接结果。 

        目标iSCSI卷的状态显示为**已连接**，则表示连接成功。

        ![确认连接结果](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427549/156860188660013_zh-CN.png)

5.  打开计算机管理，右键单击**磁盘管理** \> **重新扫描磁盘**，即可查看新连接的iSCSI卷。 

    连接iSCSI卷成功后，您可以在本地主机中使用iSCSI卷。

    ![确认连接结果](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427549/156860188760017_zh-CN.png)


