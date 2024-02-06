Lab 1.3 - Create an Application
=================================

Creating an application and assign an Access policy to the application.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Access **BIG-IP Next Central Manager** if you're not already logged in.

.. image:: images/lab3-cmlogin.png

2. Click on the Workspace icon and select Application.

.. image:: images/lab3-app1.png

3. Click on **Start Adding Apps** button to create an Application.

.. image:: images/lab3-addapp.png

4. In the **Add Application** screen, set the following parameters:

- In **Application Service Name** type: *cert_app*
- Under **What kind of Application Service are you creating?**: select Standard
- Click on **Start Creating** button

.. image:: images/lab2-createapp1.png

5. In the Application Services Properties, click **Start Creating**.

.. image:: images/lab3-createapp2.png

6. In the Virtual Servers configuration screen, we will define the Pool first, so click on **Pools** tab, click **Create**, and type in **Pool Name:** cert_auth_pool.

.. image:: images/lab3-createapp3.png

7. Switch to the **Virtual Servers** tab. Now let’s define the Virtual Server properties.

Virtual Server Name: vs_cert
Pool: cert_auth_pool
Virtual Port: 443

.. image:: images/lab3-createapp4.png

8. Click on the **Edit** button under **Protocols & Profiles** to enable HTTPS 

9. In the **Protocols and Profiles**, tick the slider button for **Enable HTTPS (Client-Side TLS)**. This will enable the features under HTTPS.

.. image:: images/lab3-pp.png


10. Next to **Please choose an trust CA certificate**, select the CA certificate we uploaded earlier in the lab.

.. image:: images/lab3-cacert2.png

11. Click on the **Add** button under the **No Client-Side TLS** to add a certificate.

.. image:: images/lab3-tls.png

12. In the Add **Client-Side TLS** screen, input the following information

- **Name:** cert_auth
- **RSA Certificate:** self_demo.f5.com
- Click **Save**

.. image:: images/lab3-addtls.png

Before continuing, please verify the proper certificates has been applied, see image below for reference.

.. image:: images/lab3-certcheck.png

13. This will take you back to the **Protocols and Profiles** screen. Keep the rest of the settings as default. Click **Save**. 

.. image:: images/lab3-addtls2.png

14.  This will take you back to the **Virtual Server** screen. Now we will attach the Access Policy we created previously to this application. Click on the **Edit** button under Security Policies.

.. image:: images/lab3-vscertauth.png

15. This will open the **Security Policies** screen. Slide the button next to **Use an Access Policy**. Under **Specify the Access Policy for this Application**, click the drop-down box and select the **certAuth** created previously. Click **Save**.

.. image:: images/lab3-vsaddpolicy.png

16.  After clicking **Save**, you should be returned to the Virtual Server property page. Click on **Review & Deploy** at the bottom right-hand corner.    

.. image:: images/lab3-revdeploy.png

1.  In the **Deploy** screen, this is where you define which BIG-IP Next instance to deploy the application. Click on **Start Adding** to select a BIG-IP Next Instance.

.. image:: images/lab3-deployto.png

18. In the drop down box, select *big-ip-next-03.example.com*, then click on **Add to List** button.

.. image:: images/lab3-deployto2.png

19. In the **Virtual Address:** box type: **10.1.10.112** to associate with the virutal server vs_cert. 

.. image:: images/lab3-vsinstance.png

20.  Click on the drop down arrow under the Members column. This is where you can add the backend pool members to the virtual server. 

.. image:: images/lab3-poolmember.png

21. In the cert_auth_pool screen, click on **Add Row**, and enter the following information for the pool member.

- **Name:** be_cert_auth
- **IP Address:** 10.1.20.6
- Click **Save**

.. image:: images/lab3-certauthpool.png

1.  Now you’re ready to Deploy your application. Click on **Deploy Changes** at the bottom right-hand corner.

.. image:: images/lab3-deploychanges.png

1.  Confirm in the pop-up window that you’re deploy to *big-ip-next-03.example.com* instance.

.. image:: images/lab3-yesdeploy.png

Click on **Yes, Deploy**

23. You will get a status pop up window, and after a few seconds the screen should refresh and show you the My Application Service dashboard, with a confirmation that Deployment Complete.

.. image:: images2/lab3-deploystatus.png
.. image:: images2/lab3-deploycomp.png

24. My Application Services Dashboard should show you one application has been deployed, and Health is Good. 

.. image:: images2/lab3-appdash.png

You have successfully created an application and assigned an access policy to it. Let's test the application!




