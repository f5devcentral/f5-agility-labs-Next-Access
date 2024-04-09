.. Below is a rst substitution for defining a Workspace icon, more info below
.. https://docutils.sourceforge.io/docs/ref/rst/restructuredtext.html#substitution-definitions
.. |workspace| image:: images/workspace.svg
   :height: 25px

Lab 1.3 - Create an Application
================================

Creating an application and assign an Access policy to the application.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Log in to your **BIG-IP Next Central Manager** on your web browser if you have not yet.

    .. image:: images/lab3-cmlogin.png

2. On to the top, select the |workspace| **Workspace**  button then select **Application**.

    .. image:: images/lab3-app1.png

3. Select **Start Adding Apps** to create an Application.

    .. image:: images/lab3-addapp.png

4. On the **Add Application** page, use the information in the table to set the configuration.

     .. list-table:: Application configuration
        :widths: 15 25
        :header-rows: 1

        * - Parameter
          - Value
        * - Application Service Name
          - ``cert_app``
        * - What kind of Application Service are you creating?
          - Select **Standard**

5. Select **Start Creating**.

    .. image:: images/lab3-addapp2.png

6. The configuration page for your application named **cert_app** appears. In the
   **Application Services Properties**, select **Start Creating** to create a **Virtual Server**.

    .. image:: images/lab3-createapp2.png

7. The **Virtual Servers** and **Pool** configuration portion of this configuration appears. Before
   setting the **Virtual Server**, a **Pool** must first be defined. Select the **Pools** tab.

    .. image:: images/lab3-createapp6.png

8. Select **Create**, and create a pool using the table below.

    .. list-table:: Pool Configuration
       :widths: 15 25
       :header-rows: 1

       * - Parameter
         - Value
       * - Pool Name
         - ``cert_auth_pool``

    .. image:: images/lab3-createapp3.png

9.  Now a **Pool** exists, select the **Virtual Servers** tab. Now let’s define the
    **Virtual Server** properties using the information below.

     .. list-table:: Pool Configuration
        :widths: 15 25
        :header-rows: 1

        * - Parameter
          - Value
        * - Virtual Server Name
          - ``vs_cert``
        * - Pool
          - ``cert_auth_pool``
        * - Virtual Port
          - ``443``

     ..  image:: images/lab3-createapp4.png

11. We will now enable HTTPS because we are using port **443**. Select the **Edit** button under
    the **Protocols & Profiles** column.

     .. image:: images/lab3-pp0.png

12. On the **Protocols and Profiles** page, select the slider button to
    **Enable HTTPS (Client-Side TLS)**.

     .. image:: images/lab3-pp.png

13. The configuration page for client-side TLS appears. Under
    **Please choose an trust CA certificate**, select the CA certificate we uploaded earlier in
    the lab.

     .. image:: images/lab3-cacert2.png

14. We will now configure the certificate on the client-side. Select the **Add** button in the
    **SPECIFY THE CERTIFICATES DETAILS FOR THIS APPLICATION** section to add a certificate.

     .. image:: images/lab3-tls.png

15. On the **Add Client-Side TLS** page, set the configuration using information from the table
    below

     .. list-table:: Client-side TLS Configuration
        :widths: 15 25
        :header-rows: 1

        * - Parameter
          - Value
        * - Name
          - ``cert_auth``
        * - RSA Certificate
          - Select **self_demo.f5.com**

     .. image:: images/lab3-addtls.png

16. Select **Save**. Verify the certificate configuration shown below.

     .. image:: images/lab3-certcheck.png

17. Select **Save** once more. This will take you back to the **Protocols and Profiles** page.

18. Leave the default values for the remaining configurations then select **Save**.

     .. image:: images/lab3-addtls2.png

19. This will take you back to the **Virtual Server** page. Now we will attach the
    **Access Policy** we created previously to this application. Select the **Edit** button
    under the **Security Policies** column.

     .. image:: images/lab3-vscertauth.png

20. This will open the **Security Policies** page. Select the slider next to
    **Use an Access Policy**.

21. On the **Specify the Access Policy for this Application** page, Select **certAuth**.

     .. image:: images/lab3-vsaddpolicy.png

22. Select **Save** which returns you to the **Virtual Server** property page.

     .. image:: images/lab3-revdeploy.png

23. Select **Review & Deploy**.

24. On the **Deploy** page, you define which BIG-IP Next Instances to deploy the application.
    Select the **Start Adding** button to choose the BIG-IP Next Instances.

     .. image:: images/lab3-deployto.png

25. For the case here, we will deploy to one BIG-IP NEXT Instance. Select
    **big-ip-next-03.example.com**, then select the **Add to List** button.

     .. image:: images/lab3-deployto2.png

26. Under the **Virtual Address** column, type **10.1.10.112**.

     .. image:: images/lab3-vsinstance.png

27. Select the drop down arrow under the **Members** column then select **+ Pool Members**.
    This is where you add the backend pool members to the virtual server.

     .. image:: images/lab3-poolmember.png

28. On the cert_auth_pool page, select **Add Row**, then enter the using the information below.

     .. list-table:: Pool Member Configuration
        :widths: 15 25
        :header-rows: 1

        * - Parameter
          - Value
        * - Name
          - ``be_cert_auth``
        * - IP Address
          - ``10.1.20.6``

     .. image:: images/lab3-certauthpool.png

29. Select **Save**

30. Now we are ready to deploy the application. Select **Deploy Changes**.

     .. image:: images/lab3-deploychanges.png

31. Confirm the deploy location is **big-ip-next-03.example.com** the select **Yes, Deploy**.

     .. image:: images/lab3-yesdeploy.png

32. A status page appears.

     .. image:: images/lab3-deploystatus.png
33. After a few seconds the screen refreshes and shows the **My Application Service** dashboard
    with a confirmation showing **Deployment Complete**.

     .. image:: images/lab3-deploycomp.png

34. The **My Application Services** dashboard now shows the application, **cert_app**, is deployed
    and **Health** is good.

     .. image:: images/lab3-appdash.png

You have successfully created an application and assigned an access policy to it.
Let's test the application!




