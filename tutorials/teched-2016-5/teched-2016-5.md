---
title: Commit your project to Git and deploy to the cloud
description: Create a git repository for your project, add your project files and then deploy  your app on SAP HANA Cloud Platform
tags: [  tutorial>beginner, topic>cloud, products>sap-hana-cloud-platform, products>sap-web-ide ]
---

## Prerequisites  
 - **Proficiency:** Beginner
 - **Tutorials:** [Build an SAP Fiori UX app with SAP Gateway data](http://www.sap.com/developer/tutorials/teched-2016-4.html)

## Next Steps
 - [Add an XML fragment for a tab in your app](http://www.sap.com/developer/tutorials/teched-2016-6.html)

## Details
### You will learn  
You will create a Git repository in SAP HANA Cloud Platform for your project, commit your project files, and then deploy and your app to the cloud. You will be able to access your app from a laptop and your mobile device.

### Time to Complete
**10 Min**.

---

[ACCORDION-BEGIN [Step 1: ](Log into your HCP account)]

Log into [SAP HANA Cloud Platform](https://account.hanatrial.ondemand.com) by opening the following URL in a new tab: https://account.hanatrial.ondemand.com

Make sure you are using the **Europe (Trial)** landscape, and click on your account name to open the cockpit view.

In the left-hand navigation bar, select **Repositories > Git Repositories**.

![Git Repositories](te-2016-5-01.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 2: ](Create new repository)]

Click on **New Repository**, and enter the following details:

Field             | Value
:---------------- | :----------------
Repository Name   | `te2016`
Description       | `Repository for Partner Contacts app`
    
Make sure the **Create empty commit** box is checked, click **OK** and your repository will be created.
    
![Create repo image](te-2016-5-02.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 3: ](Open the repository overview page)]

Click on the **`te2016`** repository link to open the repository overview page.

![Created repo](te-2016-5-03.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 4: ](Copy the Git Repository URL)]

On the repository overview page, copy the **Git Repository URL**:

![Git repo URL](te-2016-5-04.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 5: ](Initialize Local Repository)]

Open **SAP Web IDE** in a browser window (or in an existing one), right-click on your **`te2016`** project folder and select **Git > Initialize Local Repository**.

![Initialize local git](te-2016-5-05.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 6: ](Link to remote repository)]

Paste in the **Git Repository URL** you copied earlier and click **OK**.

This will initialize your local repository and link it to the Git repository in HCP.

![Initialize with remote git URL](te-2016-5-06.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 7: ](Open the Git pane)]

Click on the **Git pane** icon on the right hand side bar of the **SAP Web IDE** window.

If your project does not appear in the **Git pane**, keep the Git pane open and click on the project folder.

![Git pane](te-2016-5-07.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 8: ](Perform a Git Fetch)]

To allow **SAP Web IDE** to see remote branches in the HCP Git repository, click the **Fetch** button on the Git pane and log in with your email address and HCP account password if prompted.

When the **Changes Fetched** dialog box opens, click **OK**.

![Git Fetch](te-2016-5-08.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 9: ](Perform a Git Merge)]

Click the **Merge** button on the Git pane to merge your local branch to the remote origin/master branch.

When the **Merge "master"** dialog box opens, make sure the **origin/master** remote branch is selected and click **OK**.

![Git Merge](te-2016-5-09.png)

![Git Merge master](te-2016-5-10.png)
    
At this point your Git repository is set up.

The next steps will commit and push your project files to the repository.

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 10: ](Stage files)]

You may select individual files to commit, but to commit all project files, click the **Stage All** checkbox.

![staging all files](te-2016-5-11.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 11: ](Enter a description for the commit)]

Scroll down in the **Git pane** and enter a description (required for any commits) like `Initial commit of te2016 app`.

![commit description](te-2016-5-12.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 12: ](Perform a Git Commit and Push)]

Click on the **Commit and Push** button, and select **Remote Branch**, from the pop up menu.

This will add your files to the master branch (in other source control systems this is sometimes referred to as the "trunk").

![commit and push](te-2016-5-13.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 13: ](Push changes to the remote branch)]

In the **Push Changes to a remote branch** dialog box, select **origin/master**, click **OK** and log in with your HCP credentials if prompted.

![select origin master](te-2016-5-14.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 14: ](New file decorations)]

You will see a confirmation alert appear briefly in the top-right corner of the Web IDE window (just below **Logout**), and you will see the decorations change to the **green circles** indicating that the files in your project match the versions in the Git repository.

![green dots](te-2016-5-15.png)


[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 15: ](Deploy app on HCP)]

Deploying your app, is very simple.

Right-click on your **`te2016`** project folder, and select **Deploy > Deploy to SAP HANA Cloud Platform**.

![deploy to HCP menu](te-2016-5-16.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 16: ](Log in)]

Log in with your account number, email and password.

![log in](te-2016-5-17.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 17: ](Deployment dialog box)]

In the **Deploy Application to SAP HANA Cloud Platform** dialog box, confirm that **Deploy a new application**, and the **Activate** checkbox are both selected. Click **Deploy**.

![deploy app options](te-2016-5-18.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 18: ](Open the active version of your app)]

In the **Successfully Deployed** confirmation dialog, click the **Open the active version of the application link** to launch your app. 
 
![successful deployment](te-2016-5-19.png)
    
[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 19: ](App deployed and running)]

Your app, running on SAP HANA Cloud Platform, will open in a new tab.

You can enter the URL in your phone and see it running there as well. Since the URL is fairly long, you can email it to yourself and click the link in your email.

![deployed app](te-2016-5-20.png)

[DONE]
[ACCORDION-END]

## Next Steps
 - [Add an XML fragment for a tab in your app](http://www.sap.com/developer/tutorials/teched-2016-6.html)
