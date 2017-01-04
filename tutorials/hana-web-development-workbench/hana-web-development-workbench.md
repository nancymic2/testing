---
title: SAP HANA XS Classic, Develop your first SAP HANA XSC Application
description: In this tutorial you will make your very first SAP HANA XSC application using the SAP HANA Web-based Development Workbench.
tags: [ products>sap-hana, products>sap-hana-cloud-platform, tutorial>beginner]
---

## Prerequisites  
You need a HANA account. Pick one of the following:
- [Get a free account in HANA Cloud Platform](https://account.hanatrial.ondemand.com/register)
- [Set up an account on Amazon AWS or Microsoft Azure](http://www.sap.com/developer/tutorials/hana-setup-cloud.html)

## Next Steps
[Access your first Data from a native SAP HANA Application](http://www.sap.com/developer/tutorials/hana-data-access-authorizations.html)

## Details
### You will learn  
1. How to use the SAP HANA Web-based Development Workbench.
2. How to develop a simple server-side application.
3. How to publish and run an application.

### Time to Compete
Beginners might take **10-15 minutes** to execute this tutorial.

> ### Information
>The full application build in this tutorial can be found [in this GitHub repository](https://github.com/SAP/cloud-hana-helloworld/).

### Using HANA Cloud Platform
Each Trial HANA instance comes with the HANA Web-based Development Workbench. The workbench allows you to develop on HANA without the need to set up a local development environment.

Login to the [HANA Cloud Cockpit](https://account.hanatrial.ondemand.com/cockpit) with your free developer edition account.
Choose Databases & Schemas. You will need to create your new instance, to do this simple give it a name, enable web access and of course give a password. This password you will need to remember as it is the password for your SYSTEM user and how you will be able to access the server.

![New Database and Schema](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hana-web-development-workbench/1.png)

Once you begin the creation process, you will be redirected to an events tab.

![Database Events](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hana-web-development-workbench/2.png)

Remember the instance runs for a limited time, so if you have to come back later you may need to restart it.

![Properties](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hana-web-development-workbench/3.png)

Just click start to restart it. Also note it's only valid for 30 days.

#### 2 more steps before we hit the editor

You'll need to click on the "Admin Cockpit" first to trigger the authorizations you will need going forward.

![Manage Roles](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hana-web-development-workbench/4.png)

Once your authorizations have applied, you should then select the "Manage Roles and Users".

![System User](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hana-web-development-workbench/5.png)

Here you can create a new user, this is recommended so you do not risk the "SYSTEM" user.

![Copy User](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hana-web-development-workbench/6.png)

![Find roles](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hana-web-development-workbench/7.png)

Now simply apply new roles to the user to give this user the appropriate authorizations to begin developing.

![Find roles](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hana-web-development-workbench/9.png)

![Admin roles](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hana-web-development-workbench/10.png)

With that completed we can now log into the "SAP HANA Web Based Development Workbench"

![Access workbench](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hana-web-development-workbench/11.png)

You are now in the Editor and can immediately start developing in HANA.

#### Using HANA on Amazon AWS or Microsoft Azure

If you choose the on-premise / stand alone server approach you will need to access the web page of your HANA server using the IP address of your server. Enter the address `http://XXX.XXX.XXX.XXX` to the address bar of your browser. (Replace `XXX.XXX.XXX.XXX` with the IP address of your server.) This is under the assumption that you have a instance of the [SAP HANA Developer Edition](http://www.sap.com/developer/tutorials/hana-setup-cloud.html)

On the web page, there is a link for **Web-Based Development Workbench**. Click this link to start the workbench.

From this point differences in the tutorials are around the initial starting point, in the SAP HANA Developer Edition the user `CODEJAMMER` has a package called `CODEJAMMER` which you would then place the initial package in the next section under.

### Create Package for your Application
The first step to start developing a SAP HANA application with SAP HANA Web-based Development Workbench is to create a new package for the application.

Here we will create a package called `codejam`, Right-Click on the content folder on the left, and enter the package details.

![Create Package](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hana-web-development-workbench/12.png)

Now you have a package that is waiting for your code, now we will Right-Click on the `codejam` package and choose `Create Application`

![Create Application](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hana-web-development-workbench/13.png)

This step will generate 3 files, the `.xsapp`, `.xsaccess` and an `index.html`.

### Now Create the Application
Now is the time to actually create some application code. In SAP HANA XSC application code essentially is JavaScript code provided in `.xsjs` files. Now such a file will be created.

Open the context menu of the `codejam` package by right-clicking on the name and choose Create File. Enter `mylibrary.xsjs` as file name and save with Enter:

![New File](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hana-web-development-workbench/14.png)

The new empty file is now open in the Editor:

![XSJS file in editor](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hana-web-development-workbench/15.png)

Copy and paste this code to the just created `mylibrary.xsjs` file:

```js
$.response.contentType = "text/html";
$.response.setBody("My Personal Library");
```

Save the file using the Save button or by pressing `ctrl+s`. Again, the successful save is confirmed in the console.

![Save file](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hana-web-development-workbench/16.png)

### Deploy, Run and Test the Application
Now the application is ready to be tested. As you are developing with the SAP HANA Web-based Development Workbench the application is already deployed and activated to your SAP HANA Trial Instance. So you can immediately continue to test it:

Select the `mylibrary.xsjs` file to enable the Run on Server in the toolbar. Then click the Run on Server button:

The application will open in your browser and greet you with the beginning of your personal library:

![Web Preview](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hana-web-development-workbench/17.png)

Congratulations: You just have your first own native SAP HANA application running on SAP HANA Cloud Platform!

### Related information
[SAP HANA Development Information - official documentation](http://help.sap.com/hana_platform#section6)

*This tutorial is part of the SAP HANA and SAP HANA Cloud Platform tutorials set.*
