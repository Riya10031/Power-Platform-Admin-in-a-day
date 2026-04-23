## Admin in a day

# M03-HOL-Action through Automation

### Estimated Duration: 120 Minutes

## Lab Scenario

In this hands-on lab, you are an administrator supporting Contoso's efforts to streamline and control Power Platform usage. Contoso has restricted environment creation to global or service admins and wants an automated process for users to request new environments and Dataverse databases without discouraging platform adoption. You will build a Microsoft Form for users to submit requests, and then use Power Automate with administrative connectors and approval workflows to automate the review and provisioning process. The solution will handle approvals, environment creation, and user notifications. You’ll also explore the app auditing process from the CoE Starter Kit by stepping through it as both a maker and an admin, and install a prebuilt flow to identify new app makers, add them to an Office 365 group, and send them a welcome email.


## Lab Objectives

In this lab, you will complete the following exercises:

- Exercise 1 - Create Environment Request Form
- Exercise 2 – Create Environment on Form Submit
- Exercise 3 – Welcome New Makers (Optional if you have time)

### Lab Test Environment

This hands-on lab is designed to be completed in an environment setup for multiple students to complete the Admin in a day series of hands-on labs.

You will be assigned one or more users to use to complete the hands-on tasks. Because this is a shared environment, some tasks that require a tenant Global Administrator or a Service 
Administrator will already be performed.

This lab does not require you to have completed any of the prior labs.

## Exercise 1: Create Environment Request Form

### Scenario

In this exercise, you will be creating an environment request form using Microsoft Forms. This form could
collect additional information allowing it to be tailored to your individual organization's requirements.

### Task 1: Create Microsoft Form

In this task you will, create a form titled New Environment Approval Request with required fields for Environment Name, Business Justification, and Connectors to be used, then preview the saved form.

1. Open a new tab and navigate to **Microsoft Forms** with the following link:

   ```
   https://forms.office.com/Pages/DesignPageV2.aspx?prevsubpage=design
   ```

2. On the **Welcome to Microsoft Forms!** page, select **Registration**.

   ![reg](images/M03/Regmsform.png)

3. Select the **Untitled Form** Header.

   ![untitiled](images/M03/untform.png)

4. Enter **New Environment Approval Request (1)** for title, enter **New environment request (2)** for description, and select **+ Quick start with (3)**.

   ![](images/M03/form2.png)

5. We will create the **Form**, as shown in the screenshot below, by following the steps outlined below.

   ![](images/M03/M3-EX1-T1-S5.png)

6. Select **Text**.

   ![](images/M03/text.png)

7. Enter the **Environment Name (1)**, mark the question as **Required (2)** by enabling it, and select **+ Add new question (3)**.

   ![](images/M03/addq.png)

8. Select **Text** again.

9. Enter **Business Justification (1)**, select **Long Answer (2)**, and mark it as **Required (3)**. Then, select **+ Add new question (4)**.

   ![](images/M03/q2.png)

10. Select **Text**.

11. Enter **What connectors will you use? (1)**, select **Long Answer (2)**, and mark it as **Required (3)**.


   ![](images/M03/q3.png)

12. The form will be saved automatically.

13. Select **Preview**.

    ![](images/M03/pr.png)

14. You can see the created form.

    ![](images/M03/cf.png)


## Exercise 2: Create Environment on Form Submit

### Scenario

In this exercise, you will be building the automated flow to process new form submissions.

> **Note**: For this exercise, we have hard-coded the language, currency and environment template. The Power Platform Administration connector has actions allowing you to dynamically retrieve these and make the process more flexible. You could allow the user to specify the values, or infer them from the user’s Office 365 profile information using the Office 365 connector.

### Task 1: Delete your sandbox environment

In this task you will, remove the earlier sandbox environment to free up the trial slot.

1. Navigate back to the **Power Platform admin center** page.

1. On the **Environment**, select the sandbox environment that you created in module one named **My Sandbox-<inject key="Deployment ID" enableCopy="false" />** in the list of environments.

   ![](images/sandenv.png)

1. Select the **Delete** button.

   ![](images/sdel.png)

1. Confirm the deletion by typing the environment name **My Sandbox-<inject key="Deployment ID" enableCopy="false" /> (1)** and then select **Confirm (2)**. We have to delete it to create another Trial environment, which we can only have one at a time.

   ![](images/img-01-40.png)

   >**Note**: Environment deletion may take some time. Please wait until it is fully deleted, and keep refreshing the portal until the process is complete.

### Task 2: Create New Environment Approval Flow

In this task you will, build a flow triggered by form submissions that requests approval and conditionally creates a new environment.

1. Navigate back to the **Power Automate** portal page.

1. Set your environment to **Power Platform CoE**.

   >**Note**: This environment is where our CoE starter kit is installed and is intended to be our dedicated admin environment. Even if you don’t use the starter kit, having a dedicated 
   admin environment can be helpful.

   ![](images/M03/pv32.png)

1. On the left navigation menu, select **My flows (1)**, select **+ New flow (2)** drop down and select **Automated cloud flow (3)**.

   ![](images/M03/pp62.png)

1. Type **New Environment Approval (1)** in the **Flow name** field. In the **Choose your flow’s trigger** section, search for **When a new response is submitted (2)** then select **When a new response is submitted (3)**, and select **Create (4)**.

   ![](images/M03/pp63.png)

1. Select the **When a new response is submitted** box.

   ![](images/M03/pp64.png)

1. For the **Form Id**, select the **New Environment Approval Request** form which you created.

   ![](images/M03/pp65.png)

1. Select **+ Add action**.

   ![](images/M03/pp66.png)

1. Search for **Microsoft Forms (1)** and select **Get response details (2)**.

   ![](images/M03/pp67.png)

1. Click on the **Get response details** and select **New Environment Approval Request (1)** for **Form Id** and click on the **dynamic content (2)** symbol to select **Response Id**. 

    ![](images/M03/pp68.png)

    >**Note:** Please signin with ODL user credentials if prompted.

1. Select the **Response Id** from the Dynamic content pane.    

    ![](images/M3-EX2-T2-S10.png)

1. Select **+ Add action**.

    ![](images/M03/pp69.png)

1. Search for **Approvals (1)** and select **Start and Wait for an approval (2)**.

    ![](images/M03/pv33.png)

1. If prompted, click on **Create new**.

1. Select **Approve/Reject - First to Respond** for Approval type.

    ![](images/M03/pv34.png)

1. Enter **Environment Approval Requested (1)** for Title.

   - Select the user you are logged in as for **Assigned to** by typing the **<inject key="AzureAdUserEmail"></inject>** into the field and selecting the correct dropdown item **(2)**

   - Type **New Environment was requested by:** in the **Details** field **(3)**

   - Select the Dynamic content symbol to select the Responder email **(4)**

     ![](images/M03/pp72.png)   

   - Select **Responders Email** from the Dynamic content pane.

     ![](images/pv35.png)

1. Hit the enter key and type **Environment Name:** and select **Environment Name** from the Dynamic content pane.

    ![](images/pv36.png)

1. Hit the enter key again and type **Business Justification:** and select **Business Justification** from the Dynamic content pane.

    ![](images/pv37.png)

1. Hit the enter key again type **Connectors:** and select **What connectors will you use?** from the Dynamic content pane.

    ![](images/pv38.png)

1. Select **+ Add Action** under **Start and Wait for an Approval**.

    ![](images/M03/pv39.png)

1. Search for **Condition (1)** and the select **Condition (2)** Control.

    ![](images/M03/pp74.png)

1. Click on the dynamic content symbol to select the Value.

    ![](images/M03/pp75.png)

1. Select the Choose a value field and select **Outcome**.

    ![](images/M03/pp76.png)

1. Enter **is equals (1)** to for condition, enter **Approve (2)** for value.

    ![](images/M03/pv40.png)

1. Select **Add an action** in the **True**  branch.

    ![](images/M03/pp78.png)

1. Search for **Power Platform for Admins** and under **Power Platform for Admins** section select **See more (2)**.

    ![](images/M03/ppt27.png)

1. Select **Create Environment**.

    ![](images/M03/ppt28.png)

1. Click on **Sign in**, if prompted. Sign in with your lab credentials.

    ![](images/M03/pp81.png)

1. Select **United States (1)** for the **Location** and select the dynamic content symbol on the **Display Name** field **(2)**.

    ![](images/M03/pv41.png)

    >**Note:** Location determines the region for the environment, in a real process you might allow this to be auto-determined by the user location or something the requester provides.

1. Select **Environment Name** from the Dynamic content pane.

    ![](images/M03/ppm13.png)

     >**Note**: Enter **/ (1)** and select **Insert dynamic content (2)** to get the dynamic values.

1. Select **Trial** for **Environment Sku**.

    ![](images/M03/pp-83.png)

1. Select **Save**. Do not navigate away from this page.

    ![](images/M03/pp85.png)

### Task 3: Create a Database and Notify the User

In this task you will, extend the flow to provision a CDS database and send approval/rejection notification emails.

1. Select **+ Add an action** under **Create Environment**.

   ![](images/M03/pv42.png)

1. Search for **Power Platform for Admins** and under **Power Platform for Admins** section select **See more (2)**.

    ![](images/M03/ppt27.png)

1. Select **Create CDS Database**.

    ![](images/M03/pv43.png)

1. Select an existing connection.

   ![](images/M03/ppt29.png)

1. Select on the **Environment (1)** dropdown and select **Enter Custom Value (2)**.

   ![](images/M03/ppm10.png)

1. Enter **/ (1)** and select **Insert dynamic content (2)** to get the dynamic values.  

   ![](images/M03/ppm11.png)

1. Select **Name** from the Dynamic content pane.

   ![](images/M03/ppm12.png)

1. Select **Show all (2)**.

   ![](images/M03/pv44.png)

1. Enter **1033 (1)** for Base Language and enter **USD (2)** for Currency Code.

    - Enter **D365_CDSSampleApp (3)** for Template Item.

      ![](images/M03/pv45.png)

1. Select **Add an action** under **Create CDS Databse**.

   ![](images/M03/pv46.png)

1. Search for **Send Email (1)** and select **Send an email (V2) (2)**.

   ![](images/M03/pp91.png)

1. Click on **Sign in**. Sign in with the lab credentials.

   ![](images/M03/pp92.png)

1. Click on Settings dropdown **(1)** and then select **Use dynamic content (2)**.

   ![](images/M03/pv47.png)

1. Select on the **To:** field and select **Responders Email** for the Dynamic Content pane **(1)**.

1. Enter **Your environment was created** for **Subject (2)**.

1. Enter **Environment:** in the **Body** field and select **Display Name** from the Dynamic Content pane under the **Create Environment** step and add **was created** in the last **(3)**.

1. Your email should look like the image below.

    ![](images/dn.png)

1. Go to the **False** branch and select **Add an Action** to create a new connection under the **False** branch.

   ![](images/M03/pv48.png)

1. Search for Send email and select **Send an email (V2)**.

   ![](images/M03/pp96.png)

1. Click on Settings dropdown **(1)** and then select **Use dynamic content (2)**.

   ![](images/M03/pv49.png)

1. Select on the **To:** field and select **Responder’s Email** from the Dynamic Content pane.

   ![](images/respemail.png)

1. Type **Rejected environment request (1)** for **Subject**.

1. Enter **Your request for new environment was rejected (2)** in the **Body**.

1. Your email should now look like the image below.

    ![](images/M03/pp99.png)

1. Select **Save**.

    ![](images/M03/M3-EX2-T3-S21.png)

1. Select **Flow checker** and make sure there are no errors.

    ![](images/M03/pp101.png)

    ![](images/M03/pp102.png)

1. Close the **Flow checker** pane with the X to the right of the pane header.

1. Select the **Back** button.

    ![](images/M03/pp103.png)

### Task 4: Test the Flow

In this task you will, submit the form, approve the request via email, and verify that the new environment is created successfully in the admin center.

1. Navigate to **Microsoft Forms** and open the form you created.

   ![](images/img-01-41.png)

1. Select **Collect responses**.

   ![](images/img-01-42.png)

1. Select **Copy link** button.   

   ![](images/img-01-43.png)

1. Paste the link in the browser and navigate to the create form.

   ![](images/img-01-44.png)

1. The form should load, provide the following details and then click on **Submit (4)**.

   - Environment name: Provide **Central Apps Test (1)**
   - Business Justification: **We will use this Environment for training new employees (2)**
   - What connector will you use: **Microsoft Dataverse (3)**. 

     ![](images/formfill.png)    
   
      >**Note**: For this course, we will be using this environment we created here later in another lab to deploy the Device Ordering solution using Azure Dev Ops, for that lab it will serve as the Test environment which is why we are suggesting naming it Central Apps Test. In real word use, most likely it would be a team/project development environment that would be requested using a form like this.

1. Navigate back to the **Power Automate** portal, Go to **My flows (1)** list and open the flow you created **(2)**.

   ![](images/img-01-45.png)

1. You should see the flow running. Select the start date to open it.

   ![](images/img-01-46.png)

1. The flow is waiting for approval.

   ![](images/M03/M3-EX2-T4-S8.png)

1. Navigate to Outlook. You should have an approval request email, select to open it.

    ![](images/img-01-47.png)

1. Select **Approve** to approve the request and select **Submit**.

    ![](images/M03/pp110.png)

1. Navigate back to the flow browser tab. The flow should succeed.

    ![](images/img-01-48.png)

1. Navigate to the **Power Platform admin center**, and select **Environments (1)**. Click on **Refresh (2)** The new environment **Central Apps Test (3)** should be listed there.

    ![](images/img-01-49.png)

1. You should also get an email.
 
    ![](images/img-01-50.png)

1. You may test for request rejection if you like.

## CoE Environment Management Sample Implementation

#### The CoE starter kit includes a sample implementation of an environment management process you can tailor to your own needs. The following diagram illustrates the high-level process.

![](images/M03/M3-EX3-overview.png)

##### You can learn more about the details in How to use the Environment Management components - Power Platform | Microsoft Docs

##### Using the starter kit process can save you time, but as you saw in Exercises 1 and 2 the platform also supports you in building your custom processes.

## Exercise 3: Welcome New Makers (Optional if you have time)

In this exercise, you will be importing a pre-built flow that is designed to identify new app makers and welcome them by sending an email with some information for new makers. 
Additionally, the flow will add the user to an Office 365 group, so you have an easy way to communicate with all the makers in the company.

### Task 1: Create Office 365 Group

In this task you will, set up a Microsoft 365 group in Azure AD called Lab Admin Makers and copy its Object ID for use in the flow.

1. Navigate to the **Azure portal** from the desktop of the Lab VM.

1. If prompted to stay signed in, you can click **No**.

1. If an **Action required** pop-up window appears, click on **Ask later**.

1. If a **Welcome to Microsoft Azure** pop-up window appears, simply click **Cancel** to skip the tour.

1. On the search bar, search for **Microsoft Entra ID (1)** and select **Microsoft Entra ID (2)**.

   ![](images/M03/pv51.png)

1. Under **Manage** select **Groups**.

   ![](images/M03/pv52.png)

1. Select **+ New group**.

   ![](images/M03/pv53.png)

1. Select **Microsoft 365 (1)** for Group Type, enter **Lab Admin Makers (2)** for Group Name, if present set the **Azure AD Roles** to **No**, and select **Create (3)**.

   ![](images/M03/ppt33.png)

1. Select **All groups (1)**, search for **Lab Admin Makers (2)** and select **Lab Admin Makers (3)**. 

   ![](images/M03/pv54.png)

1. Select **Properties (1)** and copy the **Object id (2)**.

   ![](images/M03/ppt35.png)

1. Paste the **Object Id** to a notepad, you will need it in further task.

### Task 2: Import Flow

In this task you will, import the Send Welcome Email flow into the Power Platform CoE environment, configure necessary admin, Outlook, and Office 365 connections, and complete the setup.

1. Navigate to the **Power Platform admin center** and ensure that you are in the **Power Platform COE** environment.

   ![](images/coe1.png)

1. Click on **Settings**

   ![](images/coe2.png)

1. Expand the **Products (1)** and click on **features (2)**.

   ![](images/coe3.png)

1. Scroll down to **Create new canvas app and cloud flows in detaverse solutions** and ensure **both the toggle are Off**.

   ![](images/coe4.png)

1. Navigate to **Power Automate**.

1. Make sure **Power Platform COE** environment is selected. 

    > **Note:** While we are using this here, in your tenant you might do this in an admin-focused environment or where you have 
   installed the CoE Starter Kit.

   ![](images/M03/pv32.png)

1. Select **My Flows (1)** and click **Import (2)** and select **Import Package (Legacy) (3)**. (For this step, you may not be able to access the content while you are in Incognito mode. If this is the case, simply switch to your normal browser).

   ![](images/M03/pv55.png)

1. Select **Upload**.

1. Navigate to `C:\LabFiles\PPAdminAttendee%20(1)\PPAdminAttendee\M03 - HOL - Alert and Act` **(1)**, Select the **Send Welcome Email (2)** zip file and select **Open (3)**.

   ![](images/M03/ppt36.png)

1. This will be in your lab resource files you downloaded named **SendWelcomeEmailToNewPowerAppsMakers_20190529192359.zip**.

   ![](images/M03/M3-EX4-T2-S5.png)

1. Select Configure for the flow.

   ![](images/M03/M3-EX4-T2-S6.png)

1. Select **Create as new (1)** and select **Save (2)**.

   ![](images/M03/pv56.png)

1. Select **Configure** for **Power platform for Admins Connection**.

    ![](images/M03/pv57.png)

1. Select the available connection **(1)** and select **Save (2)**.

   ![](images/M03/pv58.png)

1. Select Action for **Office 365 Outlook Connection**.

   ![](images/M03/pv59.png)

1. Select the available connection **(1)** and select **Save (2)**.

   ![](images/M03/pv60.png)

1. Select **Configure** for **PowerApps for Admins Connection**.

   ![](images/M03/pv61.png)

1. Select the available connection and select **Save**.   

1. If the connection is not listed, then follow the below steps:

    - Click on **+ Create new**.

    - Select **+ New connection**.

      ![](images/M03/ppt50.png)

    - Search for **Power apps (1)**  and select **PowerApps for Admins (2)**.

      ![](images/M03/ppt37.png)

    - Select **Create**.

    - Login with your maker credentials.

1. You should now have the connections listed in the image below.

    ![](images/M03/ppt49.png)

1. Go back to the **Flow import**.

1. Select **Refresh list**, select the connection you just added, and select **Save**.

    ![](images/ppt47.png)

1. Select **Configure** for **Office 365 Group Connection**.

    ![](images/M03/ppt38.png)

1. Select the available connection and select **Save**.   

1. If the connection is not listed, then follow the below steps:    

    - Select **+ Create new**.

      ![](images/M3-EX4-T2-S15.png)

    - Select **+ New connection**.

      ![](images/M03/ppt50.png)

    - Search for **Office 365 Groups** and select **Add**.

      ![](images/M03/M3-EX4-T2-S17.png)

    - Select **Create**.

    - Login with your maker credentials.

1. You should now have the connections listed in the image below.

    ![](images/M03/ppt49.png)

1. Go back to the **Flow import**.

1. Select **Refresh list**, select the connection you just added, and select **Save**.

    ![](images/ppt47.png)

1. Select Action for **Office 365 Users Connection**.

1. Select the available connection and select **Save**.   

1. If the connection is not listed, then follow the below steps:

    - Select **+ Create new**.

      ![](images/M3-EX4-T2-S15.png)

    - Select **+ New connection**.

      ![](images/M03/ppt50.png)

    - Search for **Office 365 Users** and select **Add**.

    - Select **Create**.

    - Login with your maker credentials.

1. Select **Refresh list**, select the connection you just added, and select **Save**.

    ![](images/ppt47.png)

1. Select **Import** and wait for the import to complete.

    ![](images/M03/ppt48.png)

1. The flow should import successfully.

    ![](images/M03/M3-EX4-T2-S27.png)


### Task 3: Edit and Test Flow

In this task you will, edit the flow to use the created group’s ID, turn it on, and test it by creating a new app. Verify that the maker is added to the group and receives a welcome email.

1. Navigate to the maker portal https://make.powerapps.com and select the **Central Apps Test** environment.

   ![](images/M03/pv62.png)

1. Select **Apps (1)**, then **+ New app (2)** > **Start with a page design (3)**.

   ![](images/M04/po29.png)

1. Click on **+** on blank canvas app. Make sure **Tablet** is selected.

   ![](images/M04/po30.png)

1. The app designer should open. Select **Save** at the top right of the page.

   ![](images/M03/pv63.png)   

1. Enter **Test app (1)** for App name and select **Create (2)**.

   ![](images/M03/pv64.png)

1. Select the **Back** button.

   ![](images/M3-EX4-T3-S6.png)

1. Go back to the app maker main page by selecting the **Back** button.

1. Select **Solutions (1)**. Click on  **Publish all customizations (2)**.

   ![](images/M03/pv65.png)

1. Wait for the publishing to complete.   

   ![](images/M03/pv66.png)

1. Navigate to **Power Automate**.

1. Select the **Power Platform CoE** environment.

1. Select **My Flows (1)**. Search for **New Maker (2)** and then click on **Edit (3)** icon in the **Admin Aler|New Maker**.

    ![](images/M03/pv67.png)

1. Expand the **Recurrence** and make sure the flow is set to run once a day.

    ![](images/M03/M3-EX4-T3-S13.png)

1. Expand the **Office Group ID** step.

1. Clear the current **Group ID**.

1. Copy the **Group ID** from your notepad and paste it here.

    ![](images/M03/pv68.png)

1. You may examine the steps of the flow.

1. Select **Save**.

    ![](images/M03/pv69.png)

1. Select on the **back button**.

    ![](images/M03/pv70.png)

1. **Turn on** the flow if it is off.

    ![](images/M03/pv71.png)

1. Select **Run**.

    ![](images/M03/pv72.png)

1. Select **Run Flow**.

    ![](images/M03/pv73.png)

1. Select **Done**.

1. **Refresh (1)** every few seconds until the flow status changes. Your flow run should succeed **(2)**.

    ![](images/M03/pv74.png)

1. Go back to the **Azure portal**.

1. Select **Microsoft Enta ID**.

1. Select **Groups** under **Manage**.

   ![](images/M03/pv52.png)

1. Select **All groups**.

1. Search for **Lab Admin Makers** and then select it.

    ![](images/M03/ppt40.png)

1. Select **Members**. You should have at least one member.

    ![](images/M03/ppt42.png)
    
1. Navigate to [Outlook](https://outlook.office365.com/).

1. You should get a welcome email. Open the email. If you don’t get an email, it is probably because you didn’t create an application in the past 24 hours, create a new Power App and run 
    the flow again.
    
    ![](images/M03/ppt41.png)

### Review

In this lab, you have accomplished the following:

- Exercise 1 - Created Environment Request Form
- Exercise 2 – Created Environment on Form Submit
- Exercise 3 – Welcome New Makers (Optional if you have time)


### You have successfully completed this module.
