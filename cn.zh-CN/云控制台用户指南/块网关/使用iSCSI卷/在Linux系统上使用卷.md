# 在Linux系统上使用卷 {#task_2134425 .task}

本文介绍如何在Linux操作系统上连接并使用iSCSI卷。

已创建iSCSI卷，详情请参见[创建iSCSI卷](../cn.zh-CN/云控制台用户指南/块网关/管理iSCSI卷.md#section_oac_lbk_wdg)。

## 操作步骤 {#section_4js_ugk_pv7 .section}

1.  登录[云服务器ECS](https://ecs.console.aliyun.com/)。 

    **说明：** 如果您的本地主机已通过专线和阿里云专有网络连通，您也可以使用本地主机进行操作。

2.  安装iscsi-initiator-utils。 

    您需要通过iscsi-initiator-utils连接到目标iSCSI卷，如果您已经安装，请跳过此步骤。

    ``` {#codeblock_tlc_dq1_kfs}
    sudo yum install iscsi-initiator-utils
    ```

3.  使用如下命令验证iSCSI守护进程是否正在运行。 

    -   如果是RHEL 5/RHEL 6，请执行如下命令进行验证。

        ``` {#codeblock_4jy_v0l_z3d}
        sudo /etc/init.d/iscsi status
        ```

    -   如果是RHEL7，请执行如下命令进行验证。

        ``` {#codeblock_0p1_p57_2u9}
        sudo service iscsid status
        ```

    如果执行以上命令，未返回**running**，则执行`sudo /etc/init.d/iscsi start`启动iSCSI守护进程。

4.  （可选）设置CHAP认证。 

    **说明：** 如果您在创建iSCSI卷时，启用了CHAP认证，则需要在高级设置对话框中设置CHAP认证信息后，才能使用iSCSI卷。

    1.  执行如下命令打开iscsid.conf配置文件。 

        ``` {#codeblock_9uz_9rs_dcv}
        vi /etc/iscsi/iscsid.conf
        ```

    2.  找到CHAP Settings，删除相关配置项前面的注释符**\#**，并设置用户和密码。 

        -   用户为创建iSCSI卷时设置的入站CHAP用户。
        -   密码为创建iSCSI卷时设置的入站CHAP密码。
        ![设置CHAP认证](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427547/156860124360122_zh-CN.png)

5.  发现iSCSI卷。 

    ``` {#codeblock_wfj_hea_y2h}
    iscsiadm -m discovery -t st -p 10.0.0.0:3260
    ```

    -   10.0.0.0为块网关IP地址。

        您可以在阿里云云存储网关控制台上找到对应的块网关，在其卷信息页面中获取块网关IP地址。

    -   3260为访问端口，保持不变。
6.  挂载iSCSI卷。 

    ``` {#codeblock_bj8_ehv_cym}
    iscsiadm -m node -T iqn.2009-09.com.aliyun.iscsi-sgw:0test-test730 -p 10.0.0.0:3260 –l
    ```

    -   iqn.2009-09.com.aliyun.iscsi-sgw:0test-test730为iSCSI卷的目标名，可以从[步骤 2](#step_v1h_h13_sa9)中获取。
    -   10.0.0.0为块网关IP地址。

        您可以在阿里云云存储网关控制台上找到对应的块网关，在其卷信息页面中获取块网关IP地址。

    -   3260为访问端口，保持不变。
    **说明：** 由于iSCSI 协议限制，请勿将一个iSCSI卷挂载到多个Linux客户端。

7.  执行`fdisk -l`或`lsblk`命令查看iSCSI卷。 

    当前状态下，已挂载的iSCSI卷成为一个可用的裸磁盘，您可以在本地主机上进行读写操作。

    ![查看卷](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427547/156860124360107_zh-CN.png)


