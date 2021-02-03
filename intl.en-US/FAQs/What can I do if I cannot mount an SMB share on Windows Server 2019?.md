What can I do if I cannot mount an SMB share on Windows Server 2019? 
=========================================================================================

This topic provides a solution for an error that may occur when you mount an SMB share on Windows Server 2019.

Issue 
--------------------------

When you mount an SMB share on Windows Server 2019, an error occurs, as shown in the following figure.

Solution 
-----------------------------

1. On an on-premises Windows client, press `Win+R` to open the **Run** dialog box. In the Run dialog box, enter `gpedit.msc` in the Open field, and then click **OK** .

   

2. In the left-side navigation pane of the **Local Group Policy Editor** dialog box, choose **Computer Configuration** \> **Administrative templates** \> **Network** \> **Lanman Workstation** .

   

3. In the **Setting** section of the **Lanman Workstation** page, click **Enable insecure guest logons** .

   

4. In the **Enable insecure guest logons** dialog box, select **Enabled** . Click **Apply**

   

5. Mount the SMB share.

   




