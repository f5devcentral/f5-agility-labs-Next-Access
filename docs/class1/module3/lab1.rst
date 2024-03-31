.. Below is a rst substitution for defining a Workspace icon, more info below
.. https://docutils.sourceforge.io/docs/ref/rst/restructuredtext.html#substitution-definitions
.. |workspace| image:: images/workspace.svg
   :height: 25px

Lab 1.1 - Creating a Certificate
================================

Create a certificate in Next Central Manager
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Log in to your **BIG-IP Next Central Manager** on your web browser if you have not yet.

    .. image:: images/lab3-cmlogin.png

2. On to the top, select the |workspace| **Workspace**  button then select **Applications**.

    .. image:: images/lab3-app1.png

3. On the left, select **Certificate & Keys**

    .. image:: images/lab3-certkeysbtn.png

4. Near the top, select the **+ Add** button.

    .. image:: images/lab3-certadd.png

5. On the **Add Certificate & Keys** page to the right, take the following actions:

   a. Select **Import a Certificate**
   b. Select **Create New**
   c. Under **Name**, select **Create New**, then use the following for certificate
      name: ``ADDC_CA``
   d. In the **Tag** list, select **Access**
   e. In the **Type** list, select **Certificate**
   f. Under **Source**, select **Import**
   g. Under **Certificate**, select the **Import** button
   h. Select your **f5access-ADDC-CA.crt** certificate
   i. Select **Upload**

   .. note:: The **f5access-ADDC-CA.crt** certificate is on the *Desktop* when you
    Remote Desktop (RDP) into the **Windows Jump Host**.

   The config should look like the image below.

    .. image:: images/lab3-cacert.png

6. Select **Save**.

You have successfully uploaded a certificate.
