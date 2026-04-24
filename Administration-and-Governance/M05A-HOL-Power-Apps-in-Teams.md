# Admin in a day

# M05A-HOL-Power Apps in Teams

### Estimated Duration: 45 Minutes

## Lab Scenario

In this hands-on lab, you will create a new team in Microsoft Teams and build a Power App within it. You will also learn how to configure team ownership and publish the app for collaboration within the team. 

## Lab Objectives

In this lab, you will complete the following exercises:

- Exercise 1 - Teams setup
- Exercise 2 - Create your first app 
- Exercise 3 - Share your app

## Exercise 1 : Teams setup

### Task 1: Create a team

In this task you will, create a private team named Central IT, add Lab Users 01–10 as members, and promote them to co-owners. 

1. Open a new tab, navigate to the **Microsoft Teams**, using the following link.

   ```
   https://teams.microsoft.com/v2/
   ```

1. On the **Enjoy your Teams trial** page, select **Start trial**.

   ![](images/img-01-102.png)

   >**Note:** Close all the pop-ups.

1. Click on the **Chat (1)**, select the dropdown **(2)** and then click on **New team (3)**.

   ![](images/M05/p5p1.png)

   - If you you do not get the above UI, please follow the below step.

   - Select **Teams (1)**, click on **+ (2)** icon and then select **Create team (3)**.

     ![](images/M05/pv92.png)

1. On the **Create a team** page, provide the following details and then click on **Create (4)**:

   - Team name: Enter **Central IT (1)**
   - Team type: **Private (2)**
   - Name the first channel: Enter **Central IT channel (3)**

     ![](images/M05/p5p2.png)

1. On the **Add members to Cental IT**, search for **lab user (1)** and select **Lab User01 (2)**.

   ![](images/M05/p5p3.png)

1. Search for **lab user** again and select **Lab User02**.

1. Do the same for the rest of the users up to **Lab User10** and then select **Add**.

1. Change all the users to have the role of **Owner (1)** to make them **co-owners** of the team and then click on **Add (2)**

   ![](images/M05/p5p4.png)

### Task 2: Create an app

In this task you will, open Power Apps inside Teams, select the Central IT team, and create a new app

1. From the left navigation pane, click on **Apps (1)**, search for **Power Apps (2)** then select **Open (3)**.

   ![](images/M05/p5p5.png)

1. Select **Open**.

   ![](images/M05/p5p6.png)

1. Select **Start now** from the main card.

   ![](images/M05/p5p7.png)

1. Select the **Central IT (1)** team and then select **Create (2)**.

   ![](images/M05/p5p8.png)

1. Click on **Close**.

   ![](images/M05/p5p9.png)

    >**Note**: As your creating the App for the first time it might take around 10-15 minutes to create please wait.

1. Keep checking the **Activity (1)** section, where you will receive a notification once the app is ready. You can then build the app **(2)**.

   ![](images/M05/ppt51.png)

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
 
- Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
- If not, carefully read the error message and retry the step, following the instructions in the lab guide.
- If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

<validation step="011520fb-58d8-44f3-9fb3-5039bc2caea2" />

## Exercise 2: Create your first app

### Task 1: Add Power Apps and pin it

In this task, you will add the Power Apps app, and then pin it to your pinned apps.

1. Select the **ellipsis (...) (1)** from the navigation bar to the left of the screen then select **Power Apps (2)**.

   ![](images/M05/p5p10.png)

1. Within the navigation bar, right-click on the **Power Apps (1)** app and select **Pin (2)**.

   ![](images/M05/p5p11.png)

1. Do not navigate away from this page.

### Task 2: Create an application and table

In this task, you will create an application, and a table, and add new columns to the table.

1. Select **Power Apps (1)** from the navigation bar, then select the **Home (2)** tab and choose **Start now (3)**.

   ![](images/img-01-103.png)

1. Select the **Central IT (1)** team and then select **Create (2)**.

   ![](images/M05/p5p13.png)

1. Enter **Special Request Lab 01 (1)** and select **Save (2)**. 

   ![](images/M05/p5p15.png)

    >**Note**: You will be able to name the app only after the app is created that will take around 10-15 minutes as mentioned in the previous task. After 10-15 mins, please re perform **Step 1 to 2**. You will be able to provide the App name.

1. Select **With data (1)**, and then select **+ Create new table (2)**.

   ![](images/img-01-104.png)

1. On the **Create new table** pane, select **Start with a blank table**.

   ![](images/M05/po39.png)

1. Click on **Edit**.

   ![](images/M05/ppt52.png)

1. Enter **Lab 01 Request (1)** for the Display name, and choose **Save (2)**.

   ![](images/M05/p5p16.png)

1. Select **+ New column**.

   ![](images/M05/pv87.png)

1. On the **New column** page, enter the followig details and then click on **Save (5)**.

   - Display name: Enter **Description (1)**
   - Data type: Select **Single line of text (2)** if not chosen already.
   - Format: **Text (3)**
   - Enable Required **(4)**

     ![](images/M05/p5p17.png)

1. Select **+ New column** again.

1. On the **New column** page, enter the followig details and then click on **Save (5)**.

   - Display name: Enter **Requested date (1)**
   - Data type: Select **Date and time (2)** if not chosen already.
   - Format: **Date Only (3)**
   - Enable Required **(4)**

     ![](images/M05/p5p18.png)

1. The table should now show three columns. 

    ![](images/M05/p5p19.png)

1. Select the first cell within the **New column**, type **Ergonomic office chair**, enter **Office chair for office** in the **Description** cell, and select today’s date in the **Requested date** cell.

   ![](images/M05/p5p20.png)

1. Add a few more request rows and select **Save and close**. You can use the following data to enter into the cells of the table:

     | Name                         | Description                                           | Date           |
     | ---------------------------- | ----------------------------------------------------- | -------------- |
     | Plotter Printer              | Facilities department needs a plotter printer         | (today's date) |
     | Security system              | The new A245 building doesn't have a security system  | (today's date) |
     | Fire suppression system test | Test the fire suppression system in buildings         | (today's date) |

     ![](images/M05/p5p21.png)

1. Select **With data (1)** and then choose **Lab 01 Requests (2)**.     

    ![](images/M05/p5p22.png)

    ![](images/M05/p5p23.png)    
    
     >**Note**: The app should now have a gallery and a form. Select **Save**, if Save is enabled otherwise no issues it will get saved by default and wait for the app to be saved.

      ![](images/img-01-105.png)

1. Select **Preview**.

    ![](images/preee.png)

1. The app should start in a preview. Select **+ New record**.

    ![](images/M05/p5p35.png) 

1. Provide a Name, Description, and Requested data. Use the following data to fill in the fields for the new request:

     | New Column **(2)**                        | Description **(1)**                                                        | Requested Date **(3)** |
     | ---------------------------- | ------------------------------------------------------------------- | -------------- |
     | Covered outdoor work area    | Build a covered outdoor work area on the west side of building Az45 | (today's date) |

1. Select the **checkmark (4)** in the top right-hand corner to **Save** the record.

    ![](images/M05/p5p25.png)

1. **Close** the preview.

    ![](images/closepre.png)

1. Select **Publish to Teams**.

   ![](images/M05/ppt53.png)

1. Review the information and select **Next**.

    ![](images/M05/pv88.png)

1. Select the **Plus sign (1)** next to the **General** channel to **Add app as a tab**. This will make it discoverable on the channel. Then, select **Save and close (2)**.

    ![](images/M05/p5p26.png)

1. From the navigation bar, select **Chat (1)**, then click on **Central IT channel (2)**. Locate the app tab you added and select **Special Request Lab 01(3)**. The app should load.

   ![](images/M05/ppt54.png)

1. Ensure that you can see all of the data you entered into the app while it is in preview mode.

    ![](images/M05/p5p28.png)

1. Do not navigate away from this page.

## Exercise 3: Share your app

### Task 1: Share the app

In this task, you will share the application and the table you created.

1. Select **Power Apps (1)** from the navigation bar to the left of the screen, then select **Build (2)**.

   ![](images/M05/pv89.png)

1. From here, choose the **Central IT (1)** team, and select **See all (2)**.

   ![](images/M05/p5p29.png)

1. Select **Apps (1)** and then choose **Share with colleagues (2)**. This can share the app outside the team’s membership.

   ![](images/M05/p5p30.png)

1. Within the search bar, search for **lab (1)** and select **Lab Admin Team (2)**.

   ![](images/M05/p5p31.png)

1. To make sure the **Lab Admin Team** team members can use the app, enable the **Colleague can use** toggle **(1)**  and then select **Save (2)**.

   ![](images/M05/p5p32.png)

1. Select **Tables (1)**, select the **Lab 01 Request (2)** table that you have created. Click on the **elipses(...) (3)** and then choose **Manage permissions (4)**.

   ![](images/M05/p5p33.png)

1. Select the **Lab Admin Team (1)** team, give the team members the **Collaborate (2)** permission, and select **Save (3)**. You have now completed sharing with the group.

   ![](images/M05/p5p34.png) 

### Review

In this lab, you have accomplished the following:

- Exercise 1 - Teams setup
- Exercise 2 - Create your first app
- Exercise 3 - Share your app

### You have successfully completed this module. Click **Next** from the lower right corner to move on to the next page.

![Launch Azure Portal](images/gp8.png) 
