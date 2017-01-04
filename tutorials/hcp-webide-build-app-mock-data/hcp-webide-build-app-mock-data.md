---
title: Build an SAPUI5 app based on your data model and run it with mock data
description: Learn how to build an app with the SAP Web IDE template based on your manually created data model
tags: [ products>sap-hana-cloud-platform, products>sap-web-ide, topic>cloud, topic>html5, topic>mobile, topic>odata, topic>sapui5, tutorial>intermediate ]
---

## Prerequisites  
 - **Proficiency:** Intermediate
 - **Tutorials:** [Manually creating a data model to use in SAP Web IDE's Mock Data server](http://www.sap.com/developer/tutorials/hcp-webide-create-odata-model.html)

## Next Steps
 - [Switch your app from mock data to a live OData service](http://www.sap.com/developer/tutorials/hcp-webide-switch-live-odata.html)

## Details
### You will learn  
In the previous tutorial you created an OData entity model by hand. In this tutorial, you use that OData model in place of a live OData service to build a master-detail app in SAP Web IDE. Once built, you will then run it using the Web IDE mock data server.

The steps in this tutorial assume that you are familiar with the Web IDE menu and template wizard, and have created an OData model in the previous tutorial. If you are not familiar with Web IDE, it is suggested that you complete the following three tutorials first:

 - [Create a Destination on HANA Cloud Platform](http://www.sap.com/developer/tutorials/hcp-create-destination.html)
 - [Build an app from an SAP Web IDE template](http://www.sap.com/developer/tutorials/hcp-template-mobile-web-app.html)
 - [Deploy your mobile web app to SAP HANA Cloud Platform](http://www.sap.com/developer/tutorials/hcp-deploy-mobile-web-app.html)

### Time to Complete

**15 Min**.

---

1. The first step is to download the `m104metadata_nav.edmx` file you created in the previous tutorial. Open Web IDE in Google Chrome and expand the **Metadata** folder.

2. Right-click on the `m104metadata_nav.edmx` file and select **Export**. This will download the file to your browser's default Downloads directory.

3. In Web IDE, select the **File** menu and then **New > Project from Template**.

    ![New project from template](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-build-app-mock-data/mob4-2_3.png)

4. On the **Template Selection** page, click on the **Category** pulldown menu (where you see **Featured**) and select **SAPUI5 Mobile Application**.

    ![Template selection 1](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-build-app-mock-data/mob4-2_4a.png)

    When the mobile templates are displayed, select the **SAPUI5 Master Detail Kapsel Application** template, then click **Next**.

    ![Template selection 2](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-build-app-mock-data/mob4-2_4b.png)


5. On the **Basic Information** screen, enter `SalesOrder` for the Project Name and click **Next**.

6. On the **Data Connection** screen, under **Sources** select **File System**. Then click the **Browse…** button and navigate to the `m104metadata_nav.edmx` file you downloaded, click **Open**, then click **Next**.

    ![Data Connection screen](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-build-app-mock-data/mob4-2_6.png)

7. Fill in the Template Customization screen fields with the information below, and complete the template wizard.

    Field              |  Value  
    :------------------| :-----------
    Project Namespace  | `salesapp`

    **Master Section**

    Field               |  Value  
    :-------------------| :-----------
    Title               | `Sales Orders`
    OData Collection    | `SalesOrders`
    Search Placeholder  | `Search for Customer Name`
    Search Tooltip      | `Enter Customer Name`
    Search Field        | `CustomerName`

    **Main Data Fields**

    Field               |  Value
    :-------------------| :-----------
    Item Title          | `CustomerName`
    Numeric Attribute   | `TotalSum`
    Units Attribute     | `Currency`

    **Detail Section**

    Field                   |  Value
    :-----------------------| :-----------
    Title                   | `Sales Order Details`
    Additional Attribute 1  | `Status`
    Additional Attribute 2  | `Note`


    **Information Section**

    Field                   |  Value
    :-----------------------| :-----------
    OData Navigations       | `BusinessPartner`
    Navigation Attribute 1  | `Company`
    Navigation Attribute 2  | `EmailAddress`
    Navigation Attribute 3  | `TelephoneNumber`


8. When the project is generated, open the `SalesOrder` project folder, right-click on `index.html` and select **Run > Run with Mock Data**.

    ![Run with mock data context menu](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-build-app-mock-data/mob4-2_8.png)


9. The app will open (and you will see a Toast notification that it is running with Mock Data). The data shown is generated by the Mock Data server (based on the Property names and types specified in the OData model).

    ![Run with mock data context menu](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-build-app-mock-data/mob4-2_9.png)

10. To make the data more realistic, you can create a JSON file with predefined data. Switch back to the `SalesOrder` project, expand the **model** folder, right-click on the `metadata.xml` file and select **Edit Mock Data**.

    ![Run with mock data context menu](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-build-app-mock-data/mob4-2_10.png)

11. The **Edit Mock Data** window opens where you have the ability to select the collection (`SalesOrders` or `BusinessPartners`) then Add or Delete a row of data. You can also **Generate Random Data** which will create ten of rows of data similar to what you saw when the app was running.

    ![Run with mock data context menu](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-build-app-mock-data/mob4-2_11.png)

    The check box for the **Use the data above as my mock data source** sets the data in this view as the source for the data when the app is run again.

12. To get some initial data populated in the table, select the `SalesOrders` entity set and click the **Generate Random Data** button. You can scroll right/left to view all of the columns (one for each Property in the data model).

    ![Run with mock data context menu](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-build-app-mock-data/mob4-2_12.png)

13. You can edit individual fields by selecting the generated text and entering your values. The most visible fields in the app are `CustomerName`, `TotalSum` and `Currency`, so just changing those will have a big effect on the appearance. To update those fields in your mock data, select the `SalesOrders` entity set, and scroll right to the column labeled `TOTALSUM (DECIMAL)`, select the cells in the column one at a time and enter your own values.

    Repeat this step for the `CUSTOMERNAME (STRING)` and `CURRENCY (STRING)` fields.

    ![Run with mock data context menu](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-build-app-mock-data/mob4-2_13.png)

14. Select the `BusinessPartners` Entity set and click the **Generate Random Data** button to generate data for that collection and click OK. Web IDE will add two files to your `SalesOrder/model` folder: `SalesOrders.json` and `BusinessPartners.json`.

    ![Run with mock data context menu](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-build-app-mock-data/mob4-2_14.png)

15. Run your app again (with mock data) and you will see your updated fields displayed.

    ![Run with mock data context menu](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-build-app-mock-data/mob4-2_15.png)

16. If you need to edit a lot of data or if you want to import existing data for prototyping purposes you can convert the JSON files to CSV (or other formats) and edit the data in a spreadsheet program (like Microsoft Excel), then convert it back to JSON. There are a number of websites online that have JSON to CSV and CSV to JSON tools.

    To add the data back to your project, you can simply open and replace the content of the JSON files in your project.

## Next Steps
 - [Switch your app from mock data to a live OData service](http://www.sap.com/developer/tutorials/hcp-webide-switch-live-odata.html)
