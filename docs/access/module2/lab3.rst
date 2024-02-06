Lab 1.3 - Create an Application
=================================

Creating an application and assign an Access policy to the application.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Access **BIG-IP Next Central Manager** if you're not already logged in.

.. image:: images/lab2-cmlogin.png

2. Click on the Workspace icon and select Application.

.. image:: images/lab2-app1.png

3. Click on **Start Adding Apps** button to create an Application.

.. image:: images/lab2-addapp.png

4. In the **Add Application** screen, you can choose to create an application based on a template or create a standard application from scratch. In this lab, we will start with a **Standard** application.

- **In Application Service Name type:** azure_kerb_sso
- **Under What kind of Application Service are you creating?:** select **Standard**
- Click on **Start Creating** button

.. image:: images/lab2-createapp1.png

5. In the Application Services Properties, click **Start Creating**.

.. image:: images/lab2-createapp2.png

6. In the Virtual Servers configuration screen, we will define the Pool first, so click on **Pools** tab, click **Create**, and type in **Pool Name:** azure_pool.

.. image:: images/lab2-createapp3.png

7. Switch to the **Virtual Servers** tab. Now let’s define the Virtual Server properties.

**Virtual Server Name:** vs_azure
**Pool:** azure_pool
**Virtual Port:** 443

.. image:: images/lab2-createapp4.png

8. Click on the **Edit** button under **Protocols & Profiles** to enable HTTPS 

9. In the **Protocols and Profiles**, tick the slider button for **Enable HTTPS (Client-Side TLS)**

.. image:: images/lab2-pp.png

10. This will enable the features under HTTPS. Click on the **Add** button under the **No Client-Side TLS** to add a certificate.

.. image:: images/lab2-tls.png

11.  In the Add **Client-Side TLS** screen, input the following information

- **Name:** azure_signed_client_cert
- **RSA Certificate:** self_demo.f5.com
- Click **Save**

.. image:: images/lab2-addtls.png

12. This will take you back to the **Protocols and Profiles** screen. Keep the rest of the settings as default. Click **Save**. 

.. image:: images/lab2-addtls2.png

13. This will take you back to the **Virtual Server** screen. Now we will attach the Access Policy we created previously to this application. Click on the **Edit** button under Security Policies.

.. image:: images/lab2-vsazure.png

14. This will open the **Security Policies** screen. Slide the button next to **Use an Access Policy**. Under Specify the Access Policy for this Application, click the drop-down box and select the **signed_azure_policy** created previously. Click **Save**.

.. image:: images/lab2-vsaddpolicy.png

15. After clicking **Save**, you should be returned to the Virtual Server property page. Click on **Review & Deploy** at the bottom right-hand corner.    

.. image:: images/lab2-revdeploy.png

16. In the **Deploy** screen, this is where you define which BIG-IP Next instance to deploy the application. Click on **Start Adding** to select a BIG-IP Next Instance.

.. image:: images/lab2-deployto.png

17. In the drop down box, select *big-ip-next-03.example.com*, then click on **Add to List** button.

.. image:: images/lab2-deployto2.png

18. In the **Virtual Address:** box type: **10.1.10.100** to associate with the virutal server vs_azure. 

.. image:: images/lab2-vsinstance.png

19.  Click on the drop down arrow under the Members column. This is where you can add the backend pool members to the virtual server. 

.. image:: images/lab2-poolmember.png


20. In the azure_pool screen, click on **Add Row**, and enter the following information for the pool member.

- **Name:** backend_azure_signed
- **IP Address:** 10.1.20.6
- Click **Save**

.. image:: images/lab2-azurepool.png

21. Now you’re ready to Deploy your application. Click on **Deploy Changes** at the bottom right-hand corner.

.. image:: images/lab2-deploychanges.png

22. Confirm in the pop-up window that you’re deploy to *big-ip-next-03.example.com* instance.

.. image:: images/lab2-yesdeploy.png

Click on **Yes, Deploy**

23. You will get a status pop up window, and after a few seconds the screen should refresh and show you the My Application Service dashboard, with a confirmation that Deployment Complete.

.. image:: images2/lab2-deploystatus.png
.. image:: images2/lab2-deploycomp.png

24. My Application Services Dashboard should show you one application has been deployed, and Health is Good. 

.. image:: images2/lab2-appdash.png

You have successfully created an application and assigned an access policy to it. Let's test the application!





