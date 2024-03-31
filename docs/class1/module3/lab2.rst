.. Below is a rst substitution for defining a Workspace icon, more info below
.. https://docutils.sourceforge.io/docs/ref/rst/restructuredtext.html#substitution-definitions
.. |workspace| image:: images/workspace.svg
   :height: 25px

Lab 1.2 - Create an Access Security Policy
===========================================

Creating a security policy using certificate authentication
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Log in to your **BIG-IP Next Central Manager** on your web browser if you have not yet.

    .. image:: images/lab3-cmlogin.png

2. On to the top, select the |workspace| **Workspace**  button then select **Security**.

    .. image:: images/lab3-securitybtn.png

3. Select **Access** from the **Security** menu which defaults to **Policies** on the left side
   of the page.

    .. image:: images/lab3-accessbtn.png

4. Select the **Start Creating** button to create a new access policy.

    .. image:: images/lab3-createapbtn.png

5. A **Create Policy** page now appears.

   a. Under **Choose policy type**, select **Per-Session Policy**.

       .. image:: images/lab2-createpolicy1.png

   b. Under **How would you like to create it?**, select **Start from scratch**.

       .. image:: images/lab2-createpolicy2.png

   c. On the top of the page, select **Next**.

6. On the **Create Per-Session Policy** page, you see **Policy Configurations** on the left
   where you set different properties, such as, Logging, Session Properties, Single Sign On, and
   etc.

   a. The first configuration we are setting is **General Properties**. Select or type in the
      settings shown in the table below. We are accepting the default values for the other fields.
      An example screenshot is also shown below.

       .. list-table:: General Properties Configuration
          :widths: 25 25
          :header-rows: 1

          * - Property
            - Value
          * - Policy Name
            - ``certAuth``
          * - Cookie Options
            - Check **Secure** box

       .. image:: images/lab2-policygeneral.png
          :width: 600 px

      Select **Continue**

      .. note:: As you continue the rest of the policy creation process, we provide a screenshot in
                each section for a visual example.

   b. On the **Session Properties** page, you can configure properties such as timeouts and failure
      delays. For this lab, keep the default settings then select **Continue**.

       .. image:: images/lab3-session.png
          :width: 600 px

   c. On the **Logging** page, you can adjust the logging levels to help with debugging or
      troubleshooting. For this lab, keep the default settings then select **Continue**.

       .. image:: images/lab3-logging.png
          :width: 600 px

   d. On the **Single Sign On** page, you can set the Single Sign On (SSO) configuration with an
      IDP. For this lab, we are not using SSO so select **Continue**.

       .. image:: images/lab3-sso.png
          :width: 600 px

   e. On the **Endpoint Security** page, you can setup Endpoint Security such as ensuring firewall
      is enabled on a client workstation before access is granted. For this lab, we are not using
      this feature so select **Continue**.

       .. image:: images/lab3-endpoint.png
          :width: 600 px

   f. On the **Resources** page, you can set additional capabilities and features such as Network
      Access and Webtops. For this lab, we are not using these capabilities so select **Continue**.

       .. image:: images/lab3-resources.png
          :width: 600 px

   g. On the **Connectivity** page, you can set remote access configurations such as BIG-IP Edge
      Client properties, Mobile Client properties, and Compression. For this lab, keep the defaults
      then select **Continue**.

       .. image:: images/lab2-policyconnectivity.png
          :width: 600 px

   h. On the **Policy Endings** page, you can define additional policy ending logic as needed for
      your use case. For this lab, keep the default settings then finish the policy configuration
      by selecting **Finish**.

       .. image:: images/lab3-policyendings.png
          :width: 600 px

7. You are now on the **Visual Policy Designer (VPD)** page. We are continuing to configure this
   security policy by adding a new **Flow**. Below is a screenshot of the VPD at this step.

    .. image:: images/lab3-createpolicy2.png
       :width: 600 px

   a. Under **Flows**, drag and drop the **Empty** flow object to the VPD.

       .. image:: images/lab3-emptyflow.png

      When dropping the flow to the VPD, you will want to make sure the flow box is over the plus
      sign and the plus sign turns blue.

       .. image:: images/lab3-emptydd.png

      The result looks like the following screenshot below.

       .. image:: images/lab3-emptyok.png
          :width: 600 px

   b. By default, only one flow ending, *Deny*, is created. We need to create another one. Hover
      over the Empty flow on the VPD to show 3 buttons: **Delete**, **Edit**, and **Expand**.
      Select the **Edit** button.

       .. image:: images/lab2-editflow.png
          :width: 600 px

   c. Under Flow Endings, select **Create** to add a new one using the information from the
      table below.

       .. list-table:: New Flow Ending, Allow
          :widths: 15 25
          :header-rows: 1

          * - Name
            - Color
          * - ``Allow``
            - Select **#1999D4D**, the color green

       .. image:: images/lab2-allowflow1.png
          :width: 600 px

   d. Select **Save**.

   e. Update the **Allow** Flow Ending to **Allow**.

       .. image:: images/lab2-allowflow2.png
          :width: 600 px

   f. The new **Empty** flow looks like below.

       .. image:: images/lab2-flowfinal.png
          :width: 600 px

8. We now will add a new Rule to the new Empty flow.

   a. Select the **Expand** button to start adding Rules to this Empty flow.

       .. image:: images/lab3-allthebtns.png
          :width: 600 px

   b. On the left side of the page, select the **R (Rules)** button, then scroll down on the
      **Rules** list until you find **On-Demand Certificate Authentication**.

       .. image:: images/lab3-rules1.png

   c. Drag and drop the **On-Demand Certificate Authentication** Rule to the plus sign of the
      Empty flow.

       .. image:: images/lab3-rules2.png

9. The new rule is now in our flow. Edit the **On-Demand Certificate** rule by hovering over the
   **On-Demand Certificate Authentication** rule then selecting the **Edit** button.

    .. image:: images/lab3-rules3.png

   a. The first configuration to set is the **Rules Properties**. Under **Authentication Mode**,
      select **Require** then select **Continue**.

       .. image:: images/lab3-rules4.png
          :width: 600 px

   b. We are now on the **Branches** page. We are adding another branch in this rule for successful
      authentication. Select the **Create** button.

       .. image:: images/lab3-branches.png
         :width: 600 px

   c. On the **Create Branch** page, type or select the paramaters shown in the table below., and click **Save** when done.

       .. list-table:: New Rule Branch, Successful
          :widths: 15 25
          :header-rows: 1

          * - Property
            - Value
          * - Name
            - ``Successful``
          * - Context
            - ``Client Certificate``
          * - Condition
            - ``Validity``
          * - Client Certificate
            - ``Valid``

       .. image:: images/lab3-branches2.png
          :width: 600 px

   d. Two are a total of two branches in this rule: **Successful** and **Fallback** shown in the
      image below.

       .. image:: images/lab3-branchcomp.png
          :width: 600 px

   e. Select **Finish** to complete configuring this rule.

10. Update the new **Successful** branch so it flows to **Allow**

    .. image:: images/lab2-rulebranchupdate.png

11. Your flow and rule should look like the screenshot below.

    .. image:: images/lab2-flowrule.png

12. Select the **Collapse** button to bring you back to the main VPD.

     .. image:: images/lab2-flowcollapse.png
        :width: 600 px

13. Your main VPD view should look like the screenshot below.

     .. image:: images/lab2-finalvpd.png
        :width: 600 px

14. Select the **Save** to complete configuring the **certAuth** Access Policy.

You have completed creating a security policy for **Certificate Authentication**. Next we will
deploy an **Application** with this access policy.
