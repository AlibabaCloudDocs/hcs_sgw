# Use RAM to implement account-based access control

This topic describes how to use Resource Access Management \(RAM\) to control the access of Alibaba Cloud accounts to Cloud Storage Gateway \(CSG\). To implement access control, you must create RAM users or groups, and grant required permissions to the users or groups.

RAM is a resource access control service provided by Alibaba Cloud. RAM allows you to avoid sharing your AccessKey pair with other users. You can grant users the minimum permissions as needed. This reduces the risk of data leaks. For more information, see [What is RAM?](/intl.en-US/Product Introduction/What is RAM?.md).

-   RAM users: If you have created multiple gateways and multiple users in your organization need to access these gateways, you can create a policy to allow specified users to access the gateways. This eliminates the risk of leaking the AccessKey pair and maintains account security.
-   RAM user groups: You can create multiple user groups and grant different permissions to each user group. This allows you to manage users in the same group at the same time.

## Create a RAM user

1.  Use your Alibaba Cloud account to log on to the [RAM console](https://ram.console.aliyun.com/overview).

2.  In the left-side navigation pane, choose **Identities** \> **Users**, and then click **Create User**.

3.  Set the required parameters in the User Account Information section.

4.  Select **Console Access** or **Programmatic Access** in the Access Mode section.

5.  Select **Custom Logon Password** in the Console Password section, enter a password, and then select **Required at Next Logon** in the Password Reset section.

6.  Optional. Select Required to Enable MFA in the Multi-factor Authentication section, and then click **OK**.

7.  Save the new account, password, AccessKey ID, and AccessKey secret.

    **Note:** We recommend that you immediately save the AccessKey pair and keep it strictly confidential.


## Create a user group

If you have multiple RAM users within your Alibaba Cloud account, you can create RAM user groups to classify and authorize these RAM users. This simplifies the management of RAM users and permissions.

1.  Use your Alibaba Cloud account to log on to the [RAM console](https://ram.console.aliyun.com/overview).

2.  In the left-side navigation pane, choose **Identities** \> **Groups**, and then click **Create Group**.

3.  Specify a group name and display name, and then click **OK**.


## Grant permissions to the RAM user or group

By default, a new RAM user or group does not have permissions. You must use the console or call related API operations to grant permissions to the RAM user or group before you use the user or group to manage resources. The following example describes how to grant permissions to a RAM user.

1.  On the Users page, select the RAM user, and then click **Add Permissions** in the Actions column.

2.  In the Add Permissions panel, select the required CSG permissions and grant the permissions to the RAM user.

    To access on-premises gateways, you need to grant the RAM user only the AliyunHCSSGWFullAccess and AliyunOSSFullAccess permissions. To access gateways deployed on Alibaba Cloud, you must grant the RAM user the following four permissions:

    -   AliyunHCSSGWFullAccess: provides full access to CSG.
    -   AliyunOSSFullAccess: provides full access to Object Storage Service \(OSS\).
    -   AliyunVPCFullAccess: provides full access to Virtual Private Cloud \(VPC\).
    -   AliyunECSFullAccess: provides full access to Elastic Compute Service \(ECS\).
    ![Add Permissions panel](../images/p58687.png)


