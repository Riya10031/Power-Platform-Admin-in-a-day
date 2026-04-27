## Admin in a day

# M02-HOL-Reporting and Telemetry

### Estimated Duration: 90 Minutes

## Lab Scenario

In this Hands-on Lab, you are an administrator helping adopt the Power Platform. An important part of keeping the Power Platform running successfully is monitoring the ongoing usage. In this hands-on lab, you will be using the platform tools and the COE Starter Kit to 
perform usage monitoring.

## Lab Objectives

In this lab, you will complete the following exercises:

- Exercise 1 - Explore the out-of-the-box analytics
- Exercise 2 – Configure Dataverse logging for a table
- Exercise 3 - Set up inventory components


### Lab Test Environment

This lab is designed to be completed in an environment setup for multiple students to complete the Admin in a day series of hands-on labs.

You need to use the assigned user and environment information to complete this lab. You must have completed the prior labs to complete this lab.

## Exercise 1: Explore the out-of-the-box analytics

In this exercise, you will explore the out-of-the-box analytics that are available from the Power Platform admin center.

1. Navigate to **Power Platform admin center** page.

2. Select **Monitor (1)** from the left pane, then select **Power Apps (2)** and click on the **Open settings (3)**

    ![](images/img-01-31.png)

3. **Enable (1)** the Tenant-level analytics  and click on **Save (2)**. Navigate back to Monitor and select the Power apps

   ![](images/img-01-32.png)

   >**Note**: Once enabled, this feature aggregates data from environments across all regions in your tenant and copies it into the default environment region for tenant-level reporting. A tenant-level administrator role is required for the one-time operation of granting consent for tenant-level analytics.

4. The **Overview** tab displays a message indicating that tenant-level analytics has been enabled. **Typically, these reports are displayed within 24-48 hours of enabling the feature**.

   ![](images/ppap.png)

    > **Note**: **The below **tasks 1,2 and 3** has been made as read only because the service can take 24 to 36 hours to reflect service activities from the previous day**. Please go through the provided link for more details [Tenant-level analytics for Power Apps](https://learn.microsoft.com/en-us/power-platform/admin/tenant-level-analytics?tabs=new#how-do-i-enable-tenant-level-analytics)   

### Task 1: Explore the Power Automate analytics (Read only)

1. Navigate to **Power Platform admin center**.

1. Expand **Analytics** and select **Power Automate**.

   ![](images/M02/M2-EX1-T1-S3.png)

1. Ensure you’re under the **Environment View (1)**. Select **Change filters (2)**

   ![](images/M02/pp123.png)

1. Change the Environmnent to **Power Platform COE (1)** environment and the **Apply (2)**.

   ![](images/M03/pp124.png)

1. Review the visuals in the **Runs** tab and then select the **Usage** tab.

   ![](images/M02/M2-EX1-T1-S6.png)

1. Review the visuals in the **Usage** tab.

1. Review the visuals in the rest of the tabs.

1. In the top left corner of the screen, under the header, select **Overview** to review tenant-level
    analytics.

    ![](images/M02/M2-EX1-T1-S9.png)

1. Now you are looking at data for all environments you have access to.

1. Review the **Usage** data available on this tab, and then switch to **Maker Activity** and **Inventory** to review the other data available. Notice you can still filter on more specific criteria using the dropdowns.

    ![](images/M02/M2-EX1-T1-S11.png)

### Task 2: Explore the Power Apps analytics (Read only)

1. In the **Power Platform admin center**. Under **Analytics**, expand **Power Apps (1)**. Change the Primary Tab to **Environment View (2)**. Click on **Change filters (3)**. Switch the environment to **Power Platform COE (4)** by changing the available filters and the click on **Apply (4)**

   ![](images/M03/pp125.png)

1. Review the visuals in **Usage**, and all other tabs.

1. In the top left corner of the screen, under the header, select **Overview** to review tenant-level analytics.

   ![](images/M02/M2-EX1-T2-S6.png)

1. Now you are looking at data for all environments you have access to.

1. Review the **Usage** data available on this tab, and then switch to **Maker Activity** and **Inventory** to review the other data available. Notice you can still filter on more 
   specific criteria.

   ![](images/M02/M2-EX1-T2-S8.png)

1. Hover your mouse over the far-right corner of the unique user's data, and under **Region** you can select **...** to show more options.

   ![](images/M02/M2-EX1-T2-S9.png)

1. Select **Export data**.

    ![](images/M02/M2-EX1-T2-S10.png)

1. If you have Excel installed choose one of the options and select **Export**. After the file downloads review the details available. If you don’t have Excel simply select **Cancel**.

    ![](images/M02/M2-EX1-T2-S11.png)

### Task 3: Explore the Capacity analytics (Read only)

1. Navigate to **Power Platform admin center**.

1. Expand **Resources** and select **Capacity**.

    ![](images/M02/M2-EX1-T3-S2.png)

1. Notice the data in the **Storage capacity usage** panel.

   ![](images/M02/M2-EX1-T3-S3.png)

1. Notice the data under the **Storage capacity by source** panel.

   ![](images/M02/M2-EX1-T3-S4.png)

1. Go to the **Top storage usage by environment** panel and notice the capacity usage by top environments.

   ![](images/M02/M2-EX1-T3-S5.png)

1. Select the **Dataverse** tab from the top row of options.

   ![](images/M02/M2-EX1-T3-S6.png)

1. Locate the **Device Ordering Development** environment storage capacity and select **Details**.

   ![](images/M02/M2-EX1-T3-S7.png)

1. Select the **Chart menu** button at the top right of the first chart and select **Download all tables**.

   ![](images/M02/M2-EX1-T3-S8.png)

1. Open the file that was downloaded as a result.

   ![](images/M02/pp126.png)

1. You should see a list of all tables and their database size in MB.

   ![](images/M02/M2-EX1-T3-S9.png)

1. Close the Excel file. You won’t need to save any changes you’ve made.

1. Go to the navigation pane on the far left and expand **Analytics**, then select **Dataverse**.

    ![](images/M02/M2-EX1-T3-S11.png)

1. Review the visuals.

13. Select **Change filters**.

    ![](images/M02/pp127.png)

14. Change the **From** date to one week prior today’s date **(1)** and the **To** date to today **(2)**. Select **Apply (3)**.

    ![](images/M02/pp128.png)

15. The visuals should change to reflect your changes.

    ![](images/M02/M2-EX1-T3-S15.png)


## Exercise 2: Configure Dataverse logging for a table

In this exercise, you will configure Dataverse logging for a table that requires auditing.

### Task 1: Review audit logging in the environment

In this task you will, enable auditing for the Project table and its Due Date column, publish customizations, and turn on auditing at the environment level.

1. Navigate to the **Power Apps** portal, click on Current Environment **(1)** and select the **My Sandbox-<inject key="Deployment ID" enableCopy="false" /> (2)** environment.

   ![](images/pp-1.png)

1. On the left navigation menu, select **Solutions (1)** and choose the **Fabrikam Project Management (2)** solution to open it.

   ![](images/M02/pp129.png)

1. Select **Tables (1)** and select the **Project (2)** table. Select **Columns (3)** under the **Schema** section.

   ![](images/M02/pp130.png)

1. Locate and select **Due Date** to open it.

   ![](images/M02/M2-EX2-T1-S5.png)

1. Expand the **Advanced Options** section. Check and ensure that **Enable Auditing (1)** is enabled for this column. A notice will be underneath the option, informing you that auditing is not enabled 
   for the organization. We will fix this in a later step.

1. Select **Cancel (2)** to close the field details pane.

   ![](images/po-43.png)

1. Navigate back to the Tables by selecting the **Tables** using the breadcrumbs at the top.

   ![](images/po-44.png)

1. Select the **Project (1)** table radio-button, and then select **Properties (2)** from the ribbon up top.

   ![](images/M02/pp131.png)

1. Expand the **Advanced options** section.

    ![](images/M02/M2-EX2-T1-S10.png)

1. Scroll down to the **For this table** section and select the **Audit changes to its data (1)** checkbox and select **Save (2)**.

    ![](images/M02/pp132.png)

1. Select **All** from the left navigation of the solution.

    ![](images/M02/pp133.png)

1. Select **Publish all customizations** and wait for the publishing to be completed. A green banner will appear to let you know when it is complete.

    ![](images/po-45.png)

    ![](images/po-46.png)

1. Navigate to **Power Platform admin center** and select **Manage (1)**, click on **Environments (2)**, select the **My Sandbox-<inject key="Deployment ID" enableCopy="false" /> (3)** environment and click on **Settings (4)** from the ribbon at the top.

    ![](images/sand.png)

1. Expand **Audit and logs (1)** section and select **Audit settings (2)**.

    ![](images/audit.png)

1. Check on **Start Auditing (1)** checkbox, select **Save (2)** and click **Cancel** to close.

    ![](images/img-01-33.png)

### Task 2: Test auditing

In this task you will, open the Project Admin app, create or edit the Annual Conference project, change its Due Date multiple times, and verify the changes in Audit History.

1. Navigate to the **Power Apps** portal and make sure your in **My Sandbox-<inject key="Deployment ID" enableCopy="false" />** environment.

1. Select **Apps (1)** and select the **Project Admin (2)** application to launch.

   ![](images/po-49.png)

1. If you can see the **Annual Conference** project select it to open it and skip to step 5, if you do not see it, continue with the steps below.

   ![](images/M02/po24.png)

   - Create a new project by selecting the green **+ New** from the ribbon at the top.

     ![](images/M02/po25.png)

   - For the **Title**, enter **Annual Conference**. Choose the **Due date** as today’s date.

   - Then, select **Save & Close**.

     ![](images/M02/M2-EX2-T2-S6.png)

1. From this screen, reopen the **Annual Conference** project.

1. Change the **Due Date (1)** to any date in the future date and select **Save (2)**.

   ![](images/M02/pp135.png)

1. Change the **Due Date** and save a couple more times.

1. Select **Related (1)** and select **Audit History (2)**.

    ![](images/po-50.png)

1. You should see the change history for each of your changes. Select **Update/Create** to open one of the change history records.

    ![](images/M02/pp136.png)

     >**Note**: Sometimes it might take sometime to get open, no need to wait. Please proceed with the next Exercise.

1. You should see the **Filed Name**, **Old Value** and **New Value**.

1. Select **Close** to close the update record.

    ![](images/M02/pp137.png)

## Exercise 3: Set up inventory components

This article guides you in setting up the inventory component of the CoE Starter Kit. The inventory centralizes data on apps, flows, and makers, helping you monitor and manage your Power Platform environment. It enables admin apps, dashboards, and tools like DLP Editor and Set App Permissions for better governance.

Now in this exercise, you will explore the following key components:

- Import the Creator Kit and make connections
- Set up the Inventory components using the Setup Wizard

### Task 1 :  Import the Creator Kit and make connections

In this task you will, install the Creator Kit from AppSource, configure the HTTP with Microsoft Entra ID connection, and import the CoE Starter Kit core and governance solutions into the the Power Platform COE environment.

### Installation of Creator Kit

1. On the **Power Apps** portal, select the **Environment** and select **Power Platform COE**.

    ![](images/img-01-34.png)

1. Open a new tab, and navigate to the **Creator Kit page on AppSource** page.

    ```
    https://appsource.microsoft.com/en-US/product/dynamics-365/microsoftpowercatarch.creatorkit1?tab=Overview 
    ```

    > **Note:** If required sign in to an account with ODL Credentials

2. Select the button **Get it now**.

   ![](images/M02/M2-EX3N-T1-S1.png)

    >**Note:** On the **Confirm your details to continue** select **Get it now**.

3. The App Source install experience will launch the **Power Platform admin center** and ask you to identify the target Environment. Close the popups and continue.

4. Choose the **Power Platform COE (1)** Environment, review and agree to the two agreement checkboxes **(2)(3)**, then select the **Install (4)** button to continue the installation.

    ![](images/createinst.png)

    >**Note:** If you encounter any errors, cancel the installation page and verify in the **Power Platform admin center** whether it is installed and enabled.

    ![](images/img-01-35.png)

1. Installation may take some time; meanwhile, you can continue with the next steps.

    ![](images/M02/pv6.png)

### Create Connections

1. Open a new tab and navigate to the **Power Automate** portal, by using the following link.

    ```
    https://make.powerautomate.com/
    ```

1. Select your **Power Platform COE** environment.

    ![](images/M02/M2-EX3N-T1-S3.png)

1. Select **More (1)** from left navigation and click on  **Connections (2)** 

    ![](images/M02/pv7.png)

1. Select **+ New Connection**.

    ![](images/M02/pv8.png)

1. Search for **HTTP with Microsoft Entra ID (1)** and then click on **HTTP with Microsoft Entra ID (preauthorized) (2)**

    ![](images/img-01-36.png)

1. Set the **Base Resource URL (1)** and **Microsoft Entra ID Resource URI (Application ID URI) (2)** to https://graph.microsoft.com/. Click **Create (3)**.

    ![](images/img-01-37.png)

    > **Note:** On the **Pick an account** pop-up, select <inject key="AzureAdUserEmail"></inject>.

1. On the **Confirmation required** page, select the check-box of the **I have verified this request and trust the source (1)**, and select **Allow access (2)**.

    ![](images/img-01-38.png)

### Import the core components solution
1. Open a new tab in the browser, copy and paste the link, and download the **[CoE Starter Kit](https://aka.ms/CoeStarterKitDownload)** to your virtual machine.

1. You can see the downloaded file in the right top corner, **download (1)** section. Click on the **Folder (2)** icon to open the foder in the File explorer.

    ![](images/M02/pv11.png)

1. Locate the downloaded **CoEStarterKit.zip** file.

1. Right-click on the **ZIP file (1)** and select **Extract All... (2)**.

    ![](images/M02/pv12.png)

1. In the dialog box that appears, review the **destination path (1)** and then click on the **Extract (2)** button to unzip the contents.

    ![](images/M02/pv13.png)

    > **Note:** The CoE Starter Kit compressed file contains all solution components in addition to the non–solution-aware components that make up the CoE Starter Kit. 

1. Before proceeding to the next step, navigate back to the **Power Platform Admin Center**, **Refresh** the portal and navigate to the **Power Platform COE (1)** environment and select **Dynamic 365 apps (2)** under Resources.

    ![](images/img-01-39.png)

1. Ensure the **Creator Kit** is installed. 

    ![](images/M02/ckinst.png)

1. Navigate back to the [Power Apps](https://make.powerapps.com/) portal.

1. Choose the **Power Platform COE (1)** Environment. In the left menu, click **Solutions (2)**.

    ![](images/po-51.png)

1. Click the **Import solution** button at the top.

    ![](images/M02/pv14.png)

1. Click **Browse (1)**.

1. Navigate to  **C:\Users\demouser\Downloads\CoEStarterKit (1)** then select **CenterOfExcellenceCoreComponents_4_50_2_managed.zip (2)** solution file from the extracted folder then click on **Open (3)**.

    ![](images/f1.png)

1. Click **Next**.    

1. Review the details, click **Next** twice, leave all environment variable values as default until you see the Import button.

1. Finally, click on **Import**.

    ![](images/M02/pv17.png)

14. Please wait until this is complete before moving on to new tasks. This may take **20–30 minutes**. During the import, you may see a **warning notification** at the top of the screen (e.g., "Flow imported with warnings"). This is expected and does not necessarily indicate a failure.

    ![](images/M02/ppm2.png)


### Install COE Governance Solution.

1. Go to the **Solutions (1)** tab.

1. Click on **Import solution (2)** from the top-menu.

    ![](images/M02/ppm3.png)

1. Click on **Browse (1)**.

1. Navigate to **C:\Users\demouser\Downloads\CoEStarterKit (2)** folder then select the following file **CenterofExcellenceAuditComponents_3_27_3_managed.zip (3)** and then click on **Open (4)**.

    ![](images/f2.png)

1. Review the details, click **Next**, leave all environment variable values as default until you see the Import button.

1. Finally, click on **Import**.

    ![](images/M02/pv18.png)

1. Wait for the import process to complete. This may take **5 minutes**. During the import, you may see a **warning notification** at the top of the screen (e.g., "Flow imported with warnings"). This is expected and does not necessarily indicate a failure.

1. Please do **Refresh (1)** the portal then you will be able to see the successfully imported message **(2)**.

    ![](images/M02/ppm5.png)

1. Once the import is complete, navigate to **Solutions (1)** then **All (2)** and then you can verify the installation by checking the **Center of Excellence – Core Components (3)** and **Center of Excellence - Governance Components (4)**.

    ![](images/M02/ppm6.png)

### Task 2: Set up the Inventory components using the Setup Wizard

In this task you will, launch the CoE Setup and Upgrade Wizard, configure environment variables and personas, run setup and inventory flows, and complete the setup to enable inventory dashboards and apps.

1. From the **Solution (1)**, navigate to **Managed (2)** refresh the tab and open the **Center of Excellence - Core Components (3)** solution.

    ![](images/M02/pv19.png)

1. Navigate to **Apps (1)** then click on the ellipse in **COE Admin Command Center (2)** app and then **Play (3)**.

    ![](images/M02/pv20.png)

1. Click **Sign In (1)** for RSS, then click **Allow (2)**. 

    ![](images/M02/M2-EX3N-T1-S10B.png)

1. Click **Environment Varibles (1)** under **CoE configuration** from left navigation pannel and then click **admin_AdminMail (2)**, then click **edit (3)**.

    ![](images/M02/pv21.png)

1. Paste **<inject key="AzureAdUserEmail"></inject> (1)** email id in the **Value** section , then click **Save (2)**

    ![](images/M02/ppm7.png)

1. Now return to the previous tab where your “Center of Excellence - Core Components” is open.

    ![](images/M02/ppm8.png)

1. Open the CoE Setup and Upgrade Wizard app. Click **Apps** **(1)**, Click the three ellipses (⋯) next to the **CoE Setup and Upgrade Wizard** **(2)**. Select **Play** **(3)** to launch the app.

    ![](images/M02/pv22.png)

1. Grant all app permission and click **Allow**.

    ![](images/M02/M2-EX3N-T1-S12.png)

1. Confirm pre-requisites: Click **Next**.

    ![](images/M02/pv23.png)

1. Configure communication methods: Click **configure group** and select **Create new group** 
for persona.

    ![](images/M02/pv24.png)

1. You will be navigate to azure portal. Select **Microsoft 365** **(1)** for group type. Give group name as **COE Admin Group** **(2)**. Click **No Owners Selected** **(3)**. 

    ![](images/M02/pv-23.png)

1. Search for **odl (1)**, select the **environment email ID (2)** and then **Select (3)** Similarly, you can select multiple members to assign to the Admin persona. 

    ![](images/M02/pv26.png)

1. Once you've made your selections, click **Create** to proceed.    

    ![](images/M02/pv27.png)

1. Navigate back to the **CoE Setup and Upgrade Wizard** tab. **Refresh** the page, then proceed to configure the Admin persona by selecting the newly created group **COE Admin Group (1)** and then **Select group (2)**.

    ![](images/M02/pv28.png)

1. In the same way, you can create new groups for the **Maker persona** and **User persona**. For now, you can select the same **CoE Admin Group** for both.

1. After completing all three configuration, click **Next** to continue.

    ![](images/M02/pv29.png)

1. **Configure mandatory settings**: Review tenant id from Service principal details in the environment section of lab guide and select **Next**

1. **Configure inventory data source** : Click **Next**.

    ![](images/M02/pv30.png)

1. **Run setup flows**: Click **Refresh**, wait about 5 minutes for the process to complete, then refresh again. Once done, click **Next**.

    ![](images/M02/ppm9.png)

1. **Run Inventory flows**: Click toggle button for all the flows available on the page, wait until all the flows are removed from the page and then click **Next**.

    ![](images/M02/pv31.png)

     >**Note**: This page might take some to load please wait untill its loaded. Proceed Next if no flows on the page

1. **Configure dataflows**: Click **Next**.

1. **Share apps**: Click **Next**.

1. Publish PowerBI dashboard: Click **Next** and then **Done**

1. Close **CoE Setup and Upgrade Wizard** application.

### Review

In this lab, you have accomplished the following:

- Exercise 1 - Explored the out-of-the-box analytics
- Exercise 2 – Configured Dataverse logging for a table
- Exercise 3 - Set up inventory components

### You have successfully completed this module. Click **Next** from the lower right corner to move on to the next page.

![Launch Azure Portal](images/gp8.png)

