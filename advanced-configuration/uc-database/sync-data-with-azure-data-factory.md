---
description: How to make your data available to Unified Contacts
---

# Sync Data with Azure Data Factory

{% hint style="info" %}
The Azure Data Factory is a chargeable Microsoft Service. In normal use, these charges are nominal. Please visit [https://azure.microsoft.com/en-us/pricing/details/data-factory/data-pipeline/](https://azure.microsoft.com/en-us/pricing/details/data-factory/data-pipeline/) for more Details.
{% endhint %}

* To set up a connection between a **Data Source** and the **Azure Data Factory**, please log in to **Azure Portal**, navigate to the **Resource group** of Unified Contacts and **create a new resource** by clicking "+ Create" and subsequently searching for **Azure Data Factory**.
* This will take you through the steps to create a Data Factory

<figure><img src="../../.gitbook/assets/2023-07-31 09_57_15-Create Data Factory - Microsoft Azure und 1 weitere Seite - [InPrivate] – Micros.jpg" alt=""><figcaption></figcaption></figure>

* When the deployment has completed successfully, a confirmation screen will be displayed

<figure><img src="../../.gitbook/assets/2023-07-31 10_02_13-Microsoft.DataFactory-20230731095416 - Microsoft Azure und 1 weitere Seite - [In.jpg" alt=""><figcaption></figcaption></figure>

* Clicking on "Go to Resource" will bring you to the Azure Data Studio Launch Page

<figure><img src="../../.gitbook/assets/2023-07-31 10_05_26-DataFactoryUC - Microsoft Azure und 1 weitere Seite - [InPrivate] – Microsoft​ E.jpg" alt=""><figcaption></figcaption></figure>

* Click "Launch Studio" to begin the data source configuration
* In the next step, we need to ingest (collect) the data from our external source that we want to use in the Data Factory

{% hint style="info" %}
The Azure Data Factory supports more than 90 Data Sources natively (e.g. MySQL, Oracle DB, SAP, MongoDB, Microsoft Dynamics, Salesforce, Xero). For Details of the available connectors, please visit [https://learn.microsoft.com/en-us/azure/data-factory/connector-overview](https://learn.microsoft.com/en-us/azure/data-factory/connector-overview).
{% endhint %}

* Click on "Ingest" to begin the configuration\
  ![](<../../.gitbook/assets/image (94).png>)&#x20;
* Select **Built-In copy task** and **Schedule**. Normally, a daily ingestion is sufficient but it can be configured to run more frequently if required.

<figure><img src="../../.gitbook/assets/image (95).png" alt=""><figcaption></figcaption></figure>

* In the **Source Screen**, select the data source that you want to use and then click "New connection"
* In this example, we are ingesting data from a **Dynamics Business Central Instance** and are going to connect via HTTP to it.

<figure><img src="../../.gitbook/assets/image (102).png" alt=""><figcaption></figcaption></figure>

* Under the **Source data store**, select **HTTP**

<figure><img src="../../.gitbook/assets/image (97).png" alt=""><figcaption></figcaption></figure>

* In the next screen, enter a connection **Name**, the **Base URL** and chosen **Connection method**. Then click "Next".

<figure><img src="../../.gitbook/assets/image (98).png" alt=""><figcaption></figcaption></figure>

* In the following screen, all defaults can be accepted

<figure><img src="../../.gitbook/assets/image (99).png" alt=""><figcaption></figcaption></figure>

* Next, we need to provide the details of the database where the data collected from our Data Source will be stored. This database is created as part of the Unified Contacts installation (**UC Database**).
* If you did not choose a custom naming when installing Unified Contacts Pro the DB-Server is called `db-uc-` followed by 13 digits and numbers and the DB itself `sql-db` by default.&#x20;
* By choosing the **Account Selection Method** "From Azure Subscription" the database details will be retrieved automatically.

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

* Once you have entered all the data, click "Apply"
* Then confirm the **File format settings** for your data source

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

* Configure the **Source -> Destination** mappings

{% hint style="danger" %}
Please ensure that your data fits the specified [database schema](./#schema-definition). Any rows not fitting the schema might cause the Copy activity to fail or the faulty rows to be skipped, depending on the configured fault tolerance.\
\
In the case of fields that are too long consider editing the data in your source (query) or adding a Data Flow activity to transform it into a valid form (i. e. shortening the text and adding "..." at the end.)
{% endhint %}

<figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

* Finally, configure the settings for the **copy data task**
* Under **Fault tolerance**, choose the required level

<figure><img src="../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

* Once you have completed the final step, the Data Factory can be deployed

<figure><img src="../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>
