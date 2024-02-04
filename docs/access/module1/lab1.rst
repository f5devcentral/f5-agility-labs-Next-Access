Lab 1.1 - SAML Federation with Okta
==========================================

In this lab we will explore how to setup SAML federation with Okta by deploying an Access Policy using Visual Policy Designer

**Learning Objectives:**

- Upload Certificate to Central Manager
- Create Access Policy via Visual Policy Designer (VPD)
- Assign Flows and Rules to the Access policy
- Create Applicaiton and attach it to the Access policy

#. Access **BIG-IP Next Central Manager** Follow the previous steps on how to access the lab. 

.. image:: images/lab1-cmlogin.png

After logging in, you should be presented with Dashboard like below. This is the main Dashboard for BIG-IP Next Central Manager. You can return to this screen anytime by clicking on the red F5 circle or the word BIG-IP Next Central Manager at the top left-hand corner.

.. image:: images/lab1-cmdashboard.png

You can also navigate BIG-IP Next Central Manager using the Workspace Menu by clicking on the dotted icon to the left of the F5 circle.

.. image:: images/lab1-cmworkspacebtn.png

**Workspace Menu**

.. image:: images/lab1-cmworkspacemenu.png

**Home** This is the main dashboard.
**Applicaitons** This is where you create Applications, Application templates, and Services.
**Security** This is where you create Access Policy, Security Policy, and view security related events and reports.
**Infrastructure** This is where you can view and manage BIG-IP Next Instances.
**System** This is where you can access system settings for Central Manager such as Users and Roles, perform system upgrades.

Now that we are familiar with the Dashboard let’s get started with the first lab. First objective is to upload a certificate.

**Upload Certificate**

#. Click on the Workspace button and select **Application**. 












Observe and simulate attacks on unprotected API endpoints
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Go to the UDF course and Log into the Client Workstation

|
|

.. image:: images/access_method.png

|
|


2. Click the **Access** > **RDP** and this will download the RDP shortcut link locally
   
|


3. Open the RDP session, and type the following username/password: **user**/**user** > Click **Continue**

|
|


.. image:: images/rdp_win.png

|
|


4. You may get a certificate validatity security warning, click **Continue.**
   
|
|


.. image:: images/certificate-warning.png

|
|


5. In the Windows Client Workstation open the **Postman Desktop** application. There should be a shortcut on the desktop. 
   
|
|


.. image:: images/postman_icon.png

|
|



6. In the *Postman Desktop* application, expand the **PetStore Collection**, and **Test API** folder 

|
|


.. image::  images/postman_test_api1.png

|
|


7. Click on **List Available Pets** request but **'do not'** click **Send** yet. Observe Authorization method, Headers, and URL for the GET request.  

|
|


8. Click on **Send** at the far-right side of the Postman window.
Observe the response Status is 200 Ok, in the body of the API response lists all the available pets.

|
|


9.	Let’s run through the same steps above on the **Place Order for Pet** and **Check Status of Order** requests.



What is the cause for concern with these last two requests? What will happen if numerous requests are sent to the server? 

|
|


10.	Let’s run through the same steps as the previous two exercises but this time we will simulate an injection attack. 
In Postman, click on the **Attacks** folder under **PetStore**, and click on the **Injection Attack request**. 
Observe the request URL, and the Parameters, click **Send**. Observe the response. Was the request successful? Why is this a concern?

|
|


.. image:: images/pm-injection-attack1.png

|
|


What these exercises demonstrated are common security vulnerabilities of unprotected API endpoints. 
Even simple API queries like List Available Pets can be susceptible when hundreds or thousands of requests are sent to the server causing resource starvation. 
To protect API endpoints from attacks, ensure proper authorization, and reduce resource starvation, we can implement F5 Application Security Manager using API Security Protection guided configuration.

|
|

We will explore how to do this in the next lab.

|
|