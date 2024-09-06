Lab 1.2 - Create an Application
###############################


Creating an application and assign an Access policy to the application
**********************************************************************

1. Access **BIG-IP Next Central Manager** if you're not already logged in.

.. image:: images/lab1-cmlogin.png
    :width: 600 px

2. Click on the Workspace icon and select Application.

.. image:: images/lab2-app1.png
    :width: 600 px

3. Click on **Start Adding Apps** button to create an Application.

4. In the **Add Application** screen, set the following parameters:

- In **Application Service Name** type: *vpn-app*
- Under **What kind of Application Service are you creating?**: select Standard
- Click on **Start Creating** button

1. In the Application Services Properties, click **Start Creating**.

.. image:: images/lab2-createapp2.png
    :width: 600 px

6. In the Virtual Servers configuration screen, we will not create pool, this is not required.

7. Stay in the **Virtual Servers** tab. Now let’s define the Virtual Server properties.

- **Virtual Server Name:** vs-vpn
- **Virtual Port:** 443

8. Click on the **Edit** button under **Protocols & Profiles** to enable HTTPS 

9. In the **Protocols and Profiles**, tick the slider button for **Enable HTTPS (Client-Side TLS)**. This will enable the features under HTTPS.

.. image:: images/lab2-pp.png
    :width: 600 px

10. Click on the **Add** button to create a new client ssl profile, and add the following information

- **Name:** client-cert-auth
- **RSA Certificate:** self_demo.f5.com
- Click **Continue**

.. image:: images/lab2-client-cert-config.png
    :width: 600 px

11.  In Authentication menu, **Enable Authentication** with the following information

- **Client certificate authentication mode** : Request
- **Trusted Certificate Authorities** : CA-DEMO
- Click **Save**

.. image:: images/lab2-profile-auth.png
    :width: 600 px


12. This will take you back to the **Protocols and Profiles** screen. Enable the **HTTP Profile**. Click **Save**. 

.. image:: images/lab2-http-profile.png
    :width: 600 px

13. This will take you back to the **Virtual Server** screen. Now we will attach the Access Policy we created previously to this application. Click on the **Edit** button under Security Policies.

.. image:: images/lab2-vscertauth.png
    :width: 600 px

14. This will open the **Security Policies** screen. Slide the button next to **Use an Access Policy**. Under **Specify the Access Policy for this Application**, click the drop-down box and select the **ssl-vpn** created previously. Click **Save**.

15.  After clicking **Save**, you should be returned to the Virtual Server property page. Click on **Review & Deploy** at the bottom right-hand corner.    

.. image:: images/lab2-revdeploy.png
    :width: 600 px

16.  In the **Deploy** screen, this is where you define which BIG-IP Next instance to deploy the application. Click on **Start Adding** to select a BIG-IP Next Instance.

17. In the drop down box, select *big-ip-next-03.example.com*, then click on **Add to List** button.

18. In the **Virtual Address:** box type: **10.1.10.160** to associate with the virutal server vs-vpn. 

19. You must configure your Lease Pool for this Next instance. To do so, click on **Configure** (the one next to the ...Actions button)

.. image:: images/lab2-clickconfigure.png
    :width: 600 px

20. Click on your Per-Session policy and set the Lease Pool range to ``10.1.20.230`` to ``10.1.20.235``

.. image:: images/lab2-clicksslvpn.png
    :width: 600 px

.. image:: images/lab2-leasepool.png
    :width: 600 px

* Click **Save** and **Finish**


21. Now you’re ready to Deploy your application. Click on **Deploy Changes** at the bottom right-hand corner.

22.  Confirm in the pop-up window that you’re deploy to *big-ip-next-03.example.com* instance.

* Click on **Yes, Deploy**

23. You will get a status pop up window, and after a few seconds the screen should refresh and show you the My Application Service dashboard, with a confirmation that Deployment Complete.

.. image:: images/lab2-deploystatus.png
    :width: 600 px

.. image:: images/lab2-deploycomp.png
    :width: 600 px

24. My Application Services Dashboard should show you one application has been deployed, and Health is Good. 

You have successfully created an application and assigned an access policy to it. Let's test the application!

