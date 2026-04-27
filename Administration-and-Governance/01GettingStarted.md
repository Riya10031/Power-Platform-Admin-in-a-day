# Power Platform Workshop: Administration and Governance

### Overall Estimated Duration: 8 Hours

## Overview

In this hands-on lab, you will step into the role of a Power Platform administrator for Fabrikam and Contoso, gaining end-to-end experience in governance, monitoring, and deployment. You’ll begin by inventorying existing Power Apps and flows, then leverage the Center of Excellence (CoE) Starter Kit to track usage and enforce data policies. Next, you’ll build a Microsoft Form–based request workflow with Power Automate approvals to provision new environments and Dataverse databases on demand. You’ll explore managed environments and pipelines to promote solutions from development through test and production stages. Finally, you’ll practice app auditing and learn how to create and publish a Power App within Microsoft Teams, extending it both inside and outside your team.

## Objectives

By the end of this lab, you will be able to:

- **Securing your Tenant**: In this hands-on lab, participants will assume the role of a Power Platform environment administrator for Fabrikam, discover and inventory existing Power Apps and flows in their tenant, and establish baseline data loss prevention and security policies. They will configure administrative connectors and governance tools to enforce these policies, ensuring users can continue building productive solutions while adhering to Fabrikam’s compliance requirements.

- **Reporting and Telemetry**: In this hands-on lab, participants will learn how to use the Power Platform admin tools and the CoE Starter Kit to explore analytics, configure Dataverse logging, and set up inventory components, gaining experience in monitoring usage and strengthening governance.

- **Action through Automation**: In this hands-on lab, participants will gain hands‑on experience automating Power Platform environment requests by building a Microsoft Form–based submission process and configuring a Power Automate approval flow to provision new environments and Dataverse databases upon admin approval. They will also explore the CoE Starter Kit’s auditing and user‑onboarding components to enforce governance and welcome new app makers into approved environments.

- **Managed Environments**: In this hands-on lab, participants will gain hands-on experience applying governance controls using Managed Environments and deploying solutions across environments using Power Platform Pipelines, enabling structured Dev > Test > Prod app lifecycle management.

- **Power Apps in Teams**: In this hands-on lab, participants will learn how to create a team in Microsoft Teams and build a Power App within it, gaining experience in app creation, publishing, and sharing for broader organizational use.

- **Explore the CoE Starter Kit (Optional)**: In this hands-on lab, participants will explore the Center of Excellence (CoE) Starter Kit to understand how it supports governance and adoption of the Power Platform. They will learn to navigate the CoE dashboard, track connector usage, review audit logs, and apply compliance processes, gaining practical experience in managing and governing app usage within an organization.

## Prerequisites

- Familiarity with the Power Platform admin center and Microsoft Teams.
- Basic understanding of Power Apps, Power Automate, and Microsoft Dataverse.
- General knowledge of environment management, data governance, and DLP (Data Loss Prevention) policies.

## Architecture 

This architecture diagram explores the Power Platform ecosystem and its governance using the Power Platform Admin Center. We learned how to plan environments, apply Data Loss Prevention (DLP) policies, and assign security roles to ensure apps and flows remain secure and compliant. With Power Apps inside Teams, we created custom apps tailored for team needs, showing how quickly solutions can be built without heavy coding. Using Power Automate, we understood how flows connect services to automate repetitive business processes, enhancing productivity. To monitor usage, we published and used Power BI reports to analyze app and flow activities, check connector tiers, and track who is using connectors like Office 365 Outlook. Altogether, the lab showed how to combine productivity, automation, and governance in a secure and efficient way.

## Architecture Diagram 

![](images/archi.png)

### Explaination of components

- **Power Platform Admin Center** – This is the main management hub for the Power Platform. From here, admins can create and manage environments, set up Data Loss Prevention (DLP) policies, monitor usage, and configure user roles. It ensures apps and flows are governed properly.

- **Power Apps**: A low-code/no-code tool that lets you build custom business applications quickly. You can design apps that connect to data sources, automate tasks, and run inside Microsoft Teams or standalone, helping teams solve problems without heavy coding.

- **Power Automate** :  A service that automates workflows between apps and services. It reduces manual work by creating “flows” that trigger actions automatically (e.g., send an email when a new record is added).

- **Data Loss Prevention (DLP)**: A policy feature that controls how data can move between connectors. It prevents sensitive information from being shared outside allowed services, ensuring compliance and security.

- **Security Roles**: Define permissions for users. With roles, you control who can view, edit, or manage apps and flows, keeping access restricted and safe.

- **Microsoft Teams** : A collaboration and communication platform that integrates chat, meetings, file sharing, and apps in one place.
  
## Getting Started with the Lab
 
### Accessing Your Lab Environment
 
Once you are ready to dive in, your virtual machine and **Guide** will be right at your fingertips within your web browser.

![Explore Lab Resources](images/pp51.png)

### Lab Guide Zoom In/Zoom Out

To adjust the zoom level for the environment page, click the **A↕ : 100%** icon located next to the timer in the lab environment.

![Manage Your Virtual Machine](images/gp4.png)

### Virtual Machine & Lab Guide
 
Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.
 
### Exploring Your Lab Resources
 
To get a better understanding of your lab resources and credentials, navigate to the **Environment** tab.
 
![Manage Your Virtual Machine](images/updtenv.png)
 
### Utilizing the Split Window Feature
 
For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the top right corner.
 
![Manage Your Virtual Machine](images/updatedsplit.png)
 
### Managing Your Virtual Machine
 
Feel free to **start, stop, or restart (2)** your virtual machine as needed from the **Resources (1)** tab. Your experience is in your hands!
 
![Manage Your Virtual Machine](images/gp3.png)

### Lab Validation

1. After completing the task, hit the **Validate** button under the Validation tab integrated into your lab guide. You can proceed to the next task if you receive a success message. If not, carefully read the error message and retry the step, following the instructions in the lab guide.

   ![Manage Your Virtual Machine](images/gdev5.png)

1. If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com.

## Getting Started with Lab

1. In the JumpVM, click on the **Power Apps Portal** shortcut of the Microsoft Edge browser that is available on the desktop.

    ![](images/gp9.png)

1. On the **Sign in** window, you will see the login screen, enter the following username  and click on **Next**.

   * Email/Username: <inject key="AzureAdUserEmail"></inject>

     ![](images/M01/sign-in.png)

1. Now enter the following **password**  and click on **Sign in**. 

    * Temporary Access Pass: <inject key="AzureAdUserPassword"></inject>
  
      ![](images/password-1211.png)

1. On the **Welcome to Power Apps**, when prompted, select **Get Started**.

    ![](images/img-01-01.png)

1.  Once logged in, click on **Environment** and select the default environment named **OTU WA XX XXX (default)**.

    ![](images/img-01-02.png)

1. On the **Power Apps** select **Solutions (1)** and click on **Create a database (2)**.

    ![](images/gp6.png)

1. Now, leave all options as default and click on **Create my database** and the database creation process will start.
 
    ![](images/gp7.png)

    >**Note**: You may get an error like **Self service signup plan is required to complete the request**, but you can ignore that as the dataverse will be creating in the backend. It might take around 5-10 mins. You can proceed with the next steps.

    >**Note**: You may get **Try again** message, please do refresh the page after 5-6 mins.

## Support Contact

The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance anytime. We offer dedicated support channels tailored specifically for learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:

- Email Support: cloudlabs-support@spektrasystems.com
- Live Chat Support: https://cloudlabs.ai/labs-support

Click **Next** from the lower right corner to move on to the next page.

![Launch Azure Portal](images/gp8.png)

## Happy Learning!!
