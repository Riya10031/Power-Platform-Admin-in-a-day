## Admin in a day

# M03-HOL-Action through Automation

### Estimated Duration: 120 minutes

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

1. Navigate to **Microsoft Forms** with the following link https://forms.office.com/Pages/DesignPageV2.aspx and if prompted, close the pop up screen.

2. Select **+ New Form**.

   ![](images/M02/pp52.png)

3. Select the **Untitled Form** Header.

   ![](images/M02/pp53.png)

4. Enter **New Environment Approval Request (1)** for title, enter **New environment request (2)** for description, and select **+ Quick start with (3)**.

   ![](images/M02/pp55.png)

5. Create the **Form** below, by following the below steps.

   ![](images/M03/M3-EX1-T1-S5.png)

6. Select **Text**.

   ![](images/M03/pp56.png)

7. Enter **Environment Name (1)**, make the question **Required (2)**, and select **+ Add new question (3)**.

   ![](images/M03/pp57.png)

8. Select **Text** again.

9. Enter **Business Justification (1)**, select **Long Answer (2)**, and make it **Required (3)** then select **+Add new question (4)**

   ![](images/M03/pp58.png)

10. Select **Text**.

11. Enter **What connectors will you use? (1)** select **Long Answer (2)** and make it **Required (3)**.

    ![](images/M03/pp59.png)

12. The form will be saved automatically.

13. Select **Preview**.

    ![](images/M03/pp60.png)

14. You can see the created form.

    ![](images/M03/pp61.png)


## Exercise 2: Create Environment on Form Submit

### Scenario

In this exercise, you will be building the automated flow to process new form submissions.

> **Note**: For this exercise, we have hard-coded the language, currency and environment template. The Power Platform Administration connector has actions allowing you to dynamically retrieve these and make the process more flexible. You could allow the user to specify the values, or infer them from the user’s Office 365 profile information using the Office 365 connector.

### Task 1: Delete your sandbox environment

1. Navigate to the **Power Platform admin center**.

1. Navigate to **Environment (1)**, select the sandbox environment that you created in module one named **My Sandbox-<inject key="Deployment ID" enableCopy="false" /> (2)** in the list of environments.

   ![](images/ppp1.png)

1. Select the **Delete** button.

   ![](images/ppp2.png)

1. Confirm the deletion by typing the environment name **(1)** and then select **Confirm (2)**. We have to delete it to create another Trial environment, which we can only have one at a time.

   ![](images/ppp3.png)

    >**Note**: Environment deletion might take some time, please wait until its get deleted.

### Task 2: Create New Environment Approval Flow

1. Navigate to **Power Automate**.

1. Set your environment to **Power Platform CoE**.

   >**Note**: This environment is where our CoE starter kit is installed and is intended to be our dedicated admin environment. Even if you don’t use the starter kit, having a dedicated 
   admin environment can be helpful.

   ![](images/M03/M3-EX2-T2-S2.png)

1. Select **My flows (1)**, select **+ New flow (2)** and select **Automated cloud flow (3)**.

   ![](images/M03/pp62.png)

1. Type **New Environment Approval (1)** in the Flow name field. In the **Choose your flow’s trigger** section, search for **When a new response is submitted (2)** then select **When a new response is submitted (3)**, and select **Create (4)**.

   ![](images/M03/pp63.png)

1. Select the **When a new response is submitted** box.

   ![](images/M03/pp64.png)

1. For the **Form Id**, select the **New Environment Approval Request** form you created.

   ![](images/M03/pp65.png)

1. Select **+ Add action**.

   ![](images/M03/pp66.png)

1. Search for **Microsoft Forms (1)** and select **Get response details (2)**.

   ![](images/M03/pp67.png)

1. Select **New Environment Approval Request (1)** for **Form Id** and click on the **dynamic content (2)** symbol to select **Response Id**. 

    ![](images/M03/pp68.png)

1. Select the **Response Id** from the Dynamic content pane.    

    ![](images/M03/M3-EX2-T2-S10.png)

1. Select **+ Add action**.

    ![](images/M03/pp69.png)

1. Search for **Approvals (1)** and select **Start and Wait for an Approval (2)**.

    ![](images/M03/pp70.png)

1. Click on **Create new**.

1. Select **Approve/Reject - First to Respond** for Approval type.

    ![](images/M03/pp71.png)

1. Enter **Environment Approval Requested (1)** for Title.

   - Select the user you are logged in as for **Assigned to** by typing the name into the field and selecting the correct dropdown item **(2)**

   - Type **New Environment was requested by:** in the **Details** field **(3)**

   - Select the Dynamic content symbol to select the Responder email **(4)**

     ![](images/M03/pp72.png)   

   - Select **Responders Email** from the Dynamic content pane.

     ![](images/M03/M3-EX2-T2-S17.png)

1. Hit the enter key and type **Environment Name:** and select **Environment Name** from the Dynamic content pane.

    ![](images/M03/M3-EX2-T2-S18.png)

1. Hit the enter key again and type **Business Justification:** and select **Business Justification** from the Dynamic content pane.

    ![](images/M03/M3-EX2-T2-S19.png)

1. Hit the enter key again type **Connectors:** and select **What connectors will you use?** from the Dynamic content pane.

    ![](images/M03/M3-EX2-T2-S20.png)

1. Select **+ Add Action** under **Start and Wait for an Approval**.

    ![](images/M03/pp73.png)

1. Search for **Condition (1)** and the select **Condition (2)** Control.

    ![](images/M03/pp74.png)

1. Click on the dynamic content symbol to select the Value.

    ![](images/M03/pp75.png)

1. Select the Choose a value field and select **Outcome**.

    ![](images/M03/pp76.png)

1. Enter **is equals (1)** to for condition, enter **Approve (2)** for value.

    ![](images/M03/pp77.png)

1. Select **Add an action** in the **True**  branch.

    ![](images/M03/pp78.png)

1. Search for **Power Platform for admins** and under **Power Platform for admins** section select **See more (2)**.

    ![](images/M03/ppt27.png)

1. Select **Create Environment**.

    ![](images/M03/ppt28.png)

1. Click on **Sign in**. Sign in with your lab credentials.

    ![](images/M03/pp81.png)

1. Select **United States (1)** for the **location** and select the dynamic content symbol on the **Display Name** field **(2)**.

    ![](images/M03/pp82.png)

    >**Note:** Location determines the region for the environment, in a real process you might allow this to be auto-determined by the user location or something the requester provides.

1. Select **Environment Name** from the Dynamic content pane.

    ![](images/M03/M3-EX2-T2-S28.png)

1. Select **Trial** for **Environment Sku**.

    ![](images/M03/pp-83.png)

1. Select **Save**. Do not navigate away from this page.

    ![](images/M03/pp85.png)

### Task 3: Create a Database and Notify the User

1. Select **+ Add an action** under **Create Environment**.

   ![](images/po-52.png)

1. Search for **Power Platform for admins** and under **Power Platform for admins** section select **See more (2)**.

    ![](images/M03/ppt27.png)

1. Select **Create CDS Database**. If, required select an existing connection.

1. Select on the **Environment (1)** dropdown and select **Enter custom Value (2)**.

   ![](images/po-54.png)

1. Type **/**, and select **Insert dynamic content**. Search and select the **Name (1)** from the Dynamic content pane and select **Add (2)**.

   ![](images/po-53.png)

1. Select **Show all (2)**.

   ![](images/po-55.png)

1. Enter **1033 (1)** for Base Language and enter **USD (2)** for Currency Code.

1. Enter **D365_CDSSampleApp (3)** for Template Item.

   ![](images/po-56.png)

1. Select **Add an action** under **Create CDS Databse**.

   ![](images/po-57.png)

1. Search for **Send Email (1)** and select **Send an email (V2) (2)**.

   ![](images/M03/pp91.png)

1. If required select an existing connection. Click on **Sign in**. Sign in with the lab credentials.

1. Click on **Switch to Advanced Mode**.

   ![](images/M03/pp93.png)

1. Select on the **To:** field, type **/ (1)**, and select **Insert dynamic content (2)**.

    ![](images/po-58.png)

1. Type and search for **Responders Email (1)**, and select **Responder's Email** from the Dynamic Content pane **(2)**.

    ![](images/po-59.png)

1. Enter **Your environment was created** for **Subject (1)**. Enter **Environment** in the **Body** field. Type **/**, and select **Insert dynamic content**. Select **Display Name (2)** from the Dynamic Content pane under the **Create Environment** step and add **was created.** in the last.

    ![](images/po-60.png)

1. Your email should look like the image below.

    ![](images/po-61.png)

1. Go to the **False** branch and select **Add an Action** to create a new connection under the **False** branch.

   ![](images/M03/pp95.png)

1. Search for **Send an email (V2) (1)** and select **Send an email (V2) (2)**.

   ![](images/po-62.png)

1. Select **Switch to Advanced Mode**.

   ![](images/M03/pp97.png)

1. Select on the **To:** field, search and select for **Responder’s Email** from the Dynamic Content pane.

   ![](images/po-63.png)

1. Type **Rejected environment request (1)** for **Subject**.

1. Enter **Your request for new environment was rejected (2)** in the **Body**.

1. Your email should now look like the image below.

    ![](images/po-64.png)

1. Select **Save**.

    ![](images/po-65.png)

1. Select **Flow checker** and make sure there are no errors.

    ![](images/M03/pp101.png)

    ![](images/M03/pp102.png)

1. Close the **Flow checker** pane with the X to the right of the pane header.

1. Select the **Back** button.

    ![](images/M03/pp103.png)

### Task 4: Test the Flow

1. Navigate to **Microsoft Forms** and open the form you created.

   ![](images/M03/pp104.png)

1. Select **Collect responses**.

   ![](images/M03/pp105.png)

1. Select **Copy link**.   

   ![](images/po-66.png)

1. Open a new tab in the browser. Paste the link in the browser and navigate to it.

   ![](images/M03/pp106.png)

1. The form should load, provide the following details and then click on **Submit (4)**.

   - Environment name: Provide **Central Apps Test (1)**
   - Business Justification: **We will use this Environment for training new employees (2)**
   - What connector will you use: **Microsoft Dataverse (3)**. 

     ![](images/M03/pp107.png)   
   
        >**Note**: For this course, we will be using this environment we created here later in another lab to deploy the Device Ordering solution using Azure Dev Ops, for that lab it will serve as the Test environment which is why we are suggesting naming it Central Apps Test. In real word use, most likely it would be a team/project development environment that would be requested using a form like this.

1. Navigate back to the **Power Automate** portal, Go to **My flows (1)** list and open the flow you created **(2)**.

   ![](images/M03/pp108.png)

1. You should see the flow running. Select the start date to open it.

   ![](images/M03/pp109.png)

1. The flow is waiting for approval.

   ![](images/M03/M3-EX2-T4-S8.png)

1. Navigate to Outlook. You should have an approval request email, select to open it.

    ![](images/po-68.png)

1. Select **Approve**.

    ![](images/M03/pp110.png)

1. Select **Submit**.

1. Go back to the flow browser tab.

1. The flow should succeed.

    ![](images/M03/pp111.png)

1. Navigate to the **Power Platform admin center**, and select **Environments**. The new environment should be listed there.

    ![](images/M03/M3-EX2-T4-S15.png)

1. You should also get an email.
 
    ![](images/M03/pp112.png)

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

1. Navigate to the **Azure portal** from the desktop.

1. If prompted to stay signed in, you can click **No**.

1. If an **Action required** pop-up window appears, click on **Ask later**.

1. If a **Welcome to Microsoft Azure** pop-up window appears, simply click **"Cancel"** to skip the tour.

1. Select **Microsoft Entra ID**.

   ![](images/M03/ppt32.png)

1. Select **Groups** under **Manage**.

   ![](images/M03/Entra-ID-1.png)

1. Select **+ New group**.

   ![](images/M03/M3-EX4-T1-S4.png)

1. Select **Microsoft 365 (1)** for Group Type, enter **Lab Admin Makers (2)** for Group Name, if present set the **Azure AD Roles** to **No**, and select **Create (3)**.

   ![](images/M03/ppt33.png)

1. Open the group after it gets created.

   ![](images/M03/ppt34.png)

1. Select **Properties (1)** and copy the **Object id (2)**.

   ![](images/M03/ppt35.png)

1. Paste the object ID to a notepad, you will need it in future steps.


### Task 2: Import Flow

1. Navigate to **Power Automate**.

2. Make sure **Power Platform COE** environment is selected. 
    > **Note:** While we are using this here, in your tenant you might do this in an admin-focused environment or where you have 
   installed the CoE Starter Kit.

   ![](images/M03/M3-EX4-T2-S2.png)

3. Select **My Flows** and click **Import** and select **Import Package (Legacy)**. (For this step, you may not be able to access the content while you are in Incognito mode. If this is the case, simply switch to your normal browser).

   ![](images/M03/M3-EX4-T2-S3.png)

4. Select **Upload**.

5. Navigate to `C:\LabFiles\PPAdminAttendee%20(1)\PPAdminAttendee\M03 - HOL - Alert and Act` **(1)**, Select the **Send Welcome Email (2)** zip file and select **Open (3)**.

   ![](images/M03/ppt36.png)

1. This will be in your lab resource files you downloaded named **SendWelcomeEmailToNewPowerAppsMakers_20190529192359.zip**.

   ![](images/M03/M3-EX4-T2-S5.png)

6. Select Configure for the flow.

   ![](images/M03/M3-EX4-T2-S6.png)

7. Select **Create as new** and select **Save**.

   ![](images/M03/M3-EX4-T2-S7.png)

8. Select **Configure** for **Power platform for Admins Connection**.

    ![](images/M03/M3-EX4-T2-S8.png)

9. Select the available connection and select **Save**.

   ![](images/M03/M3-EX4-T2-S9.png)

10. Select Action for **Office 365 Outlook Connection**.

11. Select the available connection and select **Save**.

12. Select **Configure** for **PowerApps for Admins Connection**.

    ![](images/M03/M3-EX4-T2-S12.png)

1. Click on **+ Create new**.

1. Select **+ New connection**.

    ![](images/M03/M3-EX4-T2-S16.png)

1. Search for **Power apps (1)**  and select **PowerApps for Admins (2)**.

    ![](images/M03/ppt37.png)

1. Select **Create**.

1. Login with your maker credentials.

1. You should now have the connections listed in the image below.

    ![](images/M03/M3-EX4-T2-S20.png)

1. Go back to the Flow import.

1. Select **Refresh list**, select the connection you just added, and select **Save**.

    ![](images/M03/M3-EX4-T2-S22.png)

1. Select **Configure** for **Office 365 Group Connection**.

    ![](images/M03/ppt38.png)

1. Select **+ Create new**.

    ![](images/M03/M3-EX4-T2-S15.png)

1. Select **+ New connection**.

    ![](images/M03/M3-EX4-T2-S16.png)

1. Search for **Office 365 Groups** and select **Add**.

    ![](images/M03/M3-EX4-T2-S17.png)

1. Select **Create**.

1. Login with your maker credentials.

1. You should now have the connections listed in the image below.

    ![](images/M03/M3-EX4-T2-S20.png)

1. Go back to the Flow import.

1. Select **Refresh list**, select the connection you just added, and select **Save**.

    ![](images/M03/M3-EX4-T2-S22.png)

1. Select Action for **Office 365 Users Connection**.

1. Select **+ Create new**.

    ![](images/M03/M3-EX4-T2-S15.png)

1. Select **+ New connection**.

    ![](images/M03/M3-EX4-T2-S16.png)

1. Search for **Office 365 Users** and select **Add**.

1. Select **Create**.

1. Login with your maker credentials.

1. Select **Refresh list**, select the connection you just added, and select **Save**.

1. Repeat this for the **Office 365 Outlook Connection**.

1. Select the available connection and then click on **Save**.

1. Select **Import** and wait for the import to complete.

    ![](images/M03/M3-EX4-T2-S26.png)

1. The flow should import successfully.

    ![](images/M03/M3-EX4-T2-S27.png)


### Task 3: Edit and Test Flow

1. Navigate to the maker portal https://make.powerapps.com and select the **Central Apps Test** **environment**.

   ![](images/M03/M3-EX4-T3-S1.png)

1. Select **Apps (1)**, then **+ New app** > **Start with a page design (2)**.

   ![](images/M04/po29.png)

1. Click on **+** on blank canvas app. Make sure **Tablet** is selected.

   ![](images/M04/po30.png)

1. The app designer should open. Select **Save** at the top right of the page.

   ![](images/M03/M3-EX4-T3-S5.png)   

1. Enter **Test app (1)** for App name and select **Create (2)**.

   ![](images/M03/ppt39.png)

1. Select the **Back** button.

   ![](images/M03/M3-EX4-T3-S6.png)

1. Go back to the app maker main page by selecting the **Back** button.

1. Select **Solutions**.

1. Select **Publish all customizations** and wait for the publishing to complete.

   ![](images/M03/M3-EX4-T3-S9.png)

1. Navigate to Power Automate and select the **Power Platform CoE** environment.

1. Select **My Flows**.

1. Locate the flow you imported and select **Edit**.

    ![](images/M03/M3-EX4-T3-S12.png)

1. Expand the **Recurrence** and make sure the flow is set to run once a day.

    ![](images/M03/M3-EX4-T3-S13.png)

1. Expand the **Office Group ID** step.

1. Clear the current **Group ID**.

1. Copy the **Group ID** from your notepad and paste it here.

    ![](images/M03/M3-EX4-T3-S16.png)

1. You may examine the steps of the flow.

1. Select **Save**.

1. Select on the back button.

    ![](images/M03/M3-EX4-T3-S19.png)

1. **Turn on** the flow if it is off.

1. Select **Run**.

    ![](images/M03/M3-EX4-T3-S21.png)

1. Select **Run Flow**.

    ![](images/M03/M3-EX4-T3-S22.png)

1. Select **Done**.

1. **Refresh** every few seconds until the flow status changes. Your flow run should succeed.

    ![](images/M03/M3-EX4-T3-S25.png)

1. Go back to the **Azure portal**.

1. Select **Microsoft Enta ID**.

1. Select **Groups** under **Manage**.

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


### You have successfully completed this lab.
