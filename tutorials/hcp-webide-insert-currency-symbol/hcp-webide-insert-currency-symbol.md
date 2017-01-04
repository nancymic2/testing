---
title: Insert a currency symbol for display
description: Learn how to insert a symbol into the master and detail views of your app.
tags: [ products>sap-hana-cloud-platform, products>sap-web-ide, topic>cloud, topic>html5, topic>mobile, topic>odata, tutorial>beginner ]
---

## Prerequisites
 - **Proficiency:** Beginner
 - **Tutorials:** [Round the currency field using JavaScript](http://www.sap.com/developer/tutorials/hcp-webide-round-currency.html)

## Next Steps
 - [Implementing labels using the i18n (internationalization) features of SAPUI5](http://www.sap.com/developer/tutorials/hcp-webide-labels-i18n.html)

## Details

### You will learn
Ideally, an OData service should specify the currency symbol or currency type for each record since it is possible for the currencies to be different (for example, sales opportunities in different countries). The service used in this tutorial does not specify the currency, so you will add a currency symbol to the master and detail views of your app.

### Time to Complete
**5 min**

---

1. The recommended way to insert strings in your app is to take advantage of the internationalization (i18n) and localization capabilities that are built into the SAPUI5 framework. To begin, open the **`northwind > i18n > messageBundle.properties` file** and insert the line below. You can change the symbol to $, or whichever symbol you would like to display.

    ```xml
    currencySymbol=€
    ```

    ![messageBundle.properties file](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-insert-currency-symbol/mob2-3_1.png)

2.  Any string from the `messageBundle.properties` file can be used in your app using a reference in the following format: `{i18n>key}`. To reference the string you just inserted, you will use:

    ```xml
    {i18n>currencySymbol}
    ```
3. Edit the `Master.view.xml` file by inserting the reference to `currencySymbol` just before the `{UnitPrice}` reference as shown below (be sure to insert the reference within the same double quotes as the `{UnitPrice}` field.


    ![Edited Master.view.xml file](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-insert-currency-symbol/mob2-3_3.png)

4. Edit the `Detail.view.xml` file by inserting the reference to `currencySymbol` just before the `{UnitPrice}` reference as shown below (again, be sure to insert the reference within the same double quotes as the `{UnitPrice}`.

    ![Edited Detail.view.xml file](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-insert-currency-symbol/mob2-3_4.png)

5. Save your edits and either refresh your preview tab or select the `index.html` file and click **Run**. Your app should look like this:


    ![App showing currency symbol](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-insert-currency-symbol/mob2-3_5.png)

6. If your symbol does not show up:
    * Make sure you have saved your edits
    * Verify that you inserted `{i18n>currencySymbol}` between the `{UnitPrice}` double quotes
    * Do a hard-reload or clear cache. See the note below.

## Remember the browser cache
If the currency symbol does not show up, remember to clear the cache as described at the bottom of the [Add labels and a new field to your app](http://www.sap.com/developer/tutorials/hcp-webide-add-labels-field.html) tutorial.

## Next Steps
 - [Implementing labels using the i18n (internationalization) features of SAPUI5](http://www.sap.com/developer/tutorials/hcp-webide-labels-i18n.html)
