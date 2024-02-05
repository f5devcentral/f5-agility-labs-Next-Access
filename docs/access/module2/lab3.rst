Lab 1.3 - Create an Access Security Policy
===========================================

Creating an security policy with authentication to Azure and Kerberos Single Sign-On
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Access **BIG-IP Next Central Manager** if you're not already logged in.

.. image:: images/lab2-cmlogin.png

#. Click on the Workspace icon and select Security

.. image:: images/lab2-securitybtn.png

Click on **Access** from the Security menu.

.. image:: images/lab2-accessbtn.png

#. Click **Start Creating** button to create a new Access policy 

.. image:: images/lab2-createapbtn.png

#. This will open Access Visual Policy Design screen. Click on the pencil next to create new policy.

.. image:: images/lab2-createpolicypencil.png

#. In the **Create Policy** screen, let's start configuring the policy.

In the **General Properties** screen set the following parameter(s), for the rest of the settings you may leave it as default.

- **Policy Name:** signed_azure_policy
- Click **Continue** 

.. note:: As you continue the rest of the policy creation process, see the screen shot in each section for a visual example of the configuration.

.. image:: images/lab2-azurepolicy.png

#. In **Session Properties**, keep the default settings, click **Continue**

.. image:: images/lab2-session.png

#. In the **Logging** screen, you may want to adjust the logging to debug for troubleshooting propose. For this lab we will keep all the default settings.

.. image:: images/lab2-logging.png

#. In the **Single Sign-On** screen, is where you can configure Single Sign-On to your applications. In this lab we will setup Single Sign-On for Kerberos.

Click on the drop-down arrow on the **Start Creating** button and select **Kerberos**.

.. image:: images/lab2-sso.png

#. This will open the SSO Method Configuration screen. In this screen set the parameters as follow.

- **Name:** remove the trailing number and replace with “signed_azure_policy”. See image below as reference.
- **Kerberos Realm:** F5ACCESS.ONMICROSOFT.COM  
- **KDC:** 10.1.20.6
- **Account Name:** host/apm-deleg.f5access.onmicrosoft.com
- **Account Password:** F5twister$ 
- **SPN Pattern:** HTTP/%h@F5ACCESS.ONMICROSOFT.COM
- **Username Source:** session.saml.last.identity
- **User Realm Source:** session.logon.last.domain

.. image:: images/lab2-sso2.png

#. Click **Continue**, this will take you back to the Policy Configurations screen. Click **Continue** on the next screen.

#. Endpoint Security screen, you can setup Endpoint Security such as ensuring firewall is enabled on a client workstation before access is granted. In this lab, we will not use this feature. Click Continue. 

#. Resources screen, you can set additional capabilities and features such as Network Access, and Webtops in this screen. In this lab we will not use these capabilities. Click Continue.

#. Policy Endings, you can define addition policy ending logic as needed for your use case here. In this lab we will accept the default. Click Finish.

#. After clicking on Finish it should bring you back to the **Create Policy** screen. Now, we will use the Visual Policy Designer (VPD) to continue building the policy.

#. Under Flows, drag and drop **Generic SAML Federation** flow to the VPD. You will need click on the little dots to the right of the flow type to grab the flow and drop into the VPD. 

.. image:: images/lab2-samlflow.png

> :bulb: **Tip:** Remember to appreciate the little things in life.



