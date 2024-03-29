Lab 1.1 - Creating a Certificate
================================

Create a certificate in Next Central Manager
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Log in to your **BIG-IP Next Central Manager** on your web browser if you have not yet.

  .. image:: images/lab3-cmlogin.png

2. On to the top, click on the **Workspace** (icon with nine dots) button then
select **Application**.

  .. image:: images/lab3-app1.png

3. On the left, click on **Certificate & Keys**

  .. image:: images/lab3-certkeysbtn.png

4. Near the top, click on the **+ Add** button.

  .. image:: images/lab3-certadd.png

5. On the **Add Certificate & Keys** page to the right, take the following actions:

   a. Select **Import a Certificate**.
   b. Select **Create New**.
   c. In the **Name** area, select **Create New**, then use the following name for certificate
      name: **ADDC_CA**
   d. In the **Tag** list, select **Access**.
   e. In the **Type** list, select **Certificate**.
   f. In the **Source** area, select **Import**.
   g. In the **Certificate** area, select the **Import** button
   h. Select your **f5access-ADDC-CA.crt** certificate
   i. Select **Upload**

   .. note:: The certificates are in the *Access Lab* folder in **Documents** as well as pinned
    to the *Windows Explorer Quick Access* on the **Windows Jump Host**.

   The result should look like the image below.

    .. image:: images/lab3-cacert.png

6. Select **Save**.

You have successfully uploaded a certificate.
