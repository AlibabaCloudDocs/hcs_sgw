# 访问NFS共享目录 {#concept_108284_zh .task}

本文介绍如何通过Linux操作系统中的客户端访问云存储网关。

已创建共享，详情请参见[创建共享](cn.zh-CN/云控制台用户指南/文件网关/管理共享.md#section_qgs_5th_jol)。

通过Linux操作系统中的客户端访问云存储网关，首先需要将云存储网关的共享目录挂载至本地的文件目录上，挂载成功后将建立本地目录和云存储网关的共享目录之间的映射。建立映射成功后，您可以像操作本地目录一样操作共享目录。

## 操作步骤 {#section_dkr_y3l_sxm .section}

1.  登录[云服务器ECS](https://ecs.console.aliyun.com/)。
2.  挂载共享目录至客户端所在的本地目录。 
    1.  执行以下命令完成挂载。 

        ``` {#codeblock_vlk_n0i_juf}
        mount.nfs 192.168.0.0:/shares local-directory
        ```

        -   192.168.0.0:/shares：存储网关挂载点（包括存储网关IP地址和共享目录名称），请根据实际值替换。您可以在阿里云云存储网关控制台，找到目标存储网关，在其共享页面查看挂载点。
        -   local-directory：客户端的本地目录，可以是任意有读写权限的目录，不能是不存在的文件目录。
        **说明：** 如果您使用的是1.0.35版本之前的云存储网关且使用NFS v3协议挂载，则需要通过`showmount –e <网关挂载IP地址>`命令获取挂载路径，具体步骤如下所示。

        1.  执行以下命令获取挂载路径（例如获取到挂载路径为192.168.0.0:/shares）。

            ``` {#codeblock_cnd_og7_gn3}
            `showmount –e <网关挂载IP地址>`
            ```

        2.  执行以下命令完成挂载。

            ``` {#codeblock_unp_ksn_wwj}
            mount -t nfs -o vers=3,proto=tcp,nolock,noacl,sync 192.168.0.0:/shares local-directory
            ```

    2.  执行`df -h`命令，查看挂载结果。 

        如果系统显示如下类似信息，则表示挂载成功。

        **说明：** 挂载成功后，显示的容量是OSS的容量，按照文件系统最大容量显示256TB，目前OSS存储空间无容量限制。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1427488/156860123457623_zh-CN.png)

3.  访问共享目录。 

    挂载成功后，您可以像操作本地目录一样操作共享目录。如果访问用户具有写权限，则可以向共享目录写入数据；如果访问用户只有读权限，则只能读取文件。

    **说明：** 云存储网关的共享目录与OSS Bucket之间做了同步，您对共享目录的操作实际也是对OSS进行操作。


