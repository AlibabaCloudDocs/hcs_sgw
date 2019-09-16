# 配置AD/LDAP/DNS {#concept_116960_zh .task}

本文介绍如何通过阿里云云存储网关控制台配置AD/LDAP/DNS。

活动目录（AD）与轻量级目录访问协议（LDAP）是标准的应用协议，用于在互联网协议（IP）网络中，访问与更改目录服务的数据。选择您想要加入的AD服务或LDAP服务进行配置。

-   从1.0.36版本开始，阿里云云存储网关控制台新增AD/LDAP/DNS配置功能。
-   完成DNS服务器配置后，才能加入AD。
-   AD和LDAP不能同时加入。
-   当前AD域用户/LDAP用户/本地用户同时只能生效一种。在加入/离开AD域或者连接/断开LDAP服务器时，会自动删除CIFS共享中已配置的用户权限。
-   AD功能支持的服务器版本：64位Windows Server 2016数据中心版、Windows Server 2012 R2数据中心版。
-   LDAP功能支持的服务器版本：基于64位CentOS 7.4的openldap server 2.4.44。

## 配置AD {#section_cue_nv7_3vl .section}

1.  登录[云存储网关控制台](https://sgwnew.console.aliyun.com/)。
2.  在网关列表页面，找到并单击目标文件网关，进入操作页面。
3.  选择AD/LDAP/DNS页签，单击**加入AD**。
4.  在加入Windows活动目录（AD）对话框中，完成如下配置并单击**确认**。 

    -   **服务器IP**：输入AD服务器的IP地址。
    -   **用户名**：输入管理员用户名。
    -   **密码**：输入管理员密码。
    连接成功后，Windows活动目录（AD）区域中的**已连接**显示为**是**。

    **说明：** 加入Windows活动目录（AD）后，当前SMB共享里配置的本地用户权限将被移除。


## 配置LADP {#section_okv_8gz_2s3 .section}

1.  登录[云存储网关控制台](https://sgwnew.console.aliyun.com/)。
2.  在网关列表页面，找到并单击目标文件网关，进入操作页面。
3.  选择AD/LDAP/DNS页签，单击**建立连接**。
4.  在连接LDAP服务器对话框中，完成如下配置并单击**确认**。 

    -   **服务器IP**：输入LDAP服务器的IP地址（目录系统代理）。
    -   **TLS支持**：指定系统与LDAP服务器通信的方式。
    -   **Base DN**：指定LDAP域，例如：dc=iftdomain,dc=ift.local。
    -   **Root DN**：指定LDAP根，例如：cn=admin, dc=iftdomain,dc=ift.local。
    -   **密码**：输入根目录密码。
    连接成功后，轻量目录访问协议（LDAP\)区域中的**已连接**显示为**是**。

    **说明：** 加入轻量目录访问协议后，当前SMB共享里配置的本地用户权限将被移除。


## 相关操作 {#section_yyg_0xb_fnj .section}

在AD/LDAP/DNS页面，您可以进行如下操作。

|操作|说明|
|--|--|
|关闭AD连接|在Windows活动目录（AD）区域，单击**关闭连接**，可关闭AD连接。|
|关闭LDAP连接|在轻量目录访问协议（LDAP）区域，单击**关闭连接**，可关闭LDAP连接。|
|切换DNS服务器|单击**切换DNS服务器**，可设置DNS服务器IP地址。|

