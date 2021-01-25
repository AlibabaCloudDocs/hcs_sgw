# 文件网关的NFS v4共享路径的配置方法

本文介绍文件网关的NFS v4共享路径的配置方法。

1.  登录主机（Linux系统）。

2.  执行以下命令挂载文件系统。

    ```
    mount -t nfs4 x.x.x.x:/shares local-directory
    ```

    其中，x.x.x.x:/shares为您的文件网关的IP地址和共享目录，local-directory为客户端的本地目录。

    **说明：** 客户端的本地目录可以为任意有读写权限的目录，不能指定不存在的文件目录。

3.  执行`df -h`命令查看挂载结果。

    如果系统显示如下类似信息，则表示挂载成功。

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6292197951/p63366.png)


