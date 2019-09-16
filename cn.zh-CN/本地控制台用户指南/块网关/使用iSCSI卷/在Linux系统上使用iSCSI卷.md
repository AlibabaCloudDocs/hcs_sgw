# 在Linux系统上使用iSCSI卷 {#concept_108319_zh .task}

本文介绍如何在Linux操作系统上连接并使用iSCSI卷。

已创建iSCSI卷，详情请参见[创建iSCSI卷](cn.zh-CN/本地控制台用户指南/块网关/管理iSCSI卷.md#section_iku_7uf_1tw)。

## 操作步骤 {#section_hgb_aeh_d82 .section}

1.  登录本地主机（Linux操作系统）。
2.  安装iscsi-initiator-utils。 

    您需要通过iscsi-initiator-utils连接到目标iSCSI卷，如果您已经安装，请跳过此步骤。

    ``` {#codeblock_97q_j06_d7g}
    sudo yum install iscsi-initiator-utils
    ```

3.  验证iSCSI守护进程是否正在运行。 

    -   如果是Linux RHEL 5/RHEL 6版本，请执行如下命令进行验证。

        ``` {#codeblock_pvl_5x4_lt9}
        sudo /etc/init.d/iscsi status
        ```

    -   如果是Linux RHEL 7版本，请执行如下命令进行验证。

        ``` {#codeblock_bj3_kw0_h4w}
        sudo service iscsid status
        ```

    如果执行以上命令，未返回**running**，则执行`sudo /etc/init.d/iscsi start`命令启动iSCSI守护进程。

4.  （可选）设置CHAP认证。 

    **说明：** 如果您在创建iSCSI卷时，启用了CHAP认证，则需要在此处设置CHAP认证信息后，才能使用iSCSI卷。

    1.  执行如下命令打开iscsid.conf配置文件。 

        ``` {#codeblock_6z4_lue_5sv}
        vi /etc/iscsi/iscsid.conf
        ```

    2.  找到CHAP Settings，删除相关配置项前面的注释符**\#**，并设置用户名和密码。 

        -   用户名为创建iSCSI卷时设置的入站CHAP用户名。
        -   密码为创建iSCSI卷时设置的入站CHAP密码。
        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427547/156860189060122_zh-CN.png)

5.  发现iSCSI卷。 

    ``` {#codeblock_ol4_t2t_fo8}
    iscsiadm -m discovery -t st -p 10.0.0.0:3260
    ```

    -   10.0.0.0为块网关IP地址，您可以在本地块网关控制台的**关于** \> **网络信息**页面中获取。
    -   3260为访问端口，保持不变。
6.  挂载iSCSI卷。 

    ``` {#codeblock_k7l_qze_o3y}
    iscsiadm -m node -T iqn.2009-09.com.aliyun.iscsi-sgw:0test-test730 -p 10.0.0.0:3260 –l
    ```

    -   iqn.2009-09.com.aliyun.iscsi-sgw:0test-test730为iSCSI卷的目标名，可以从[步骤 2](#step_0dv_1t5_trf)中获取。
    -   10.0.0.0为块网关IP地址，您可以在本地块网关控制台的**关于** \> **网络信息**页面中获取。
    -   3260为访问端口，保持不变。
    **说明：** 由于iSCSI协议限制，请勿将一个iSCSI卷挂载到多个Linux客户端上。

7.  执行`fdisk -l`或`lsblk`命令查看iSCSI卷。 

    当前状态下，已挂载的iSCSI卷成为一个可用的裸磁盘，您可以在本地主机上进行读写操作。

    ![查看iSCSI卷](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427547/156860189060107_zh-CN.png)


