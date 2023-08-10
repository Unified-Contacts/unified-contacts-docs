---
description: Documentation for the usage of the Database contact source
---

# Database as contact source

{% hint style="info" %}
Unified Contacts Pro only.
{% endhint %}

{% hint style="info" %}
Version Requirement: >v1.5.0
{% endhint %}

With Unified Contacts >v1.5.0 you can fill the internal database with contacts which can be searched by every of your users.

To fill the database you need to insert your contacts in a specific schema as described bellow.\
We also provide an RESTful API for CRUD operation on Database contacts.

We provide two detailed documentation for examples how to add contacts to the database

* [Import Contacts with Azure DataFactory (recommended for syncs & imports e.g. from ERP systems)](sync-data-with-azure-data-factory.md)
* [Create, Read, Update, Delete Database Contacts with the RESTful API (recommended for custom implementations & single Contact updates/syncs)](crud-operations-with-rest-api.md)

## Database Documentation

The following documentation explains where to find the Database and how the Contacts table is structured.

### Database Location

The Database (DB) can be found in the Resource group where Unified Contacts Pro was deployed.&#x20;

{% hint style="warning" %}
If you did not choose a custom naming when installing Unified Contacts Pro the DB-Server is called `db-uc-` followed by 13 digits and numbers and the DB itself `sql-db` by default.&#x20;
{% endhint %}

To access the DB you will need the user and password you have set when installing Unified Contacts.

### Database Contacts structure

{% hint style="danger" %}
Only alter tables that have the prefix `UnifiedContactsCustom.` \
Only alter the content NEVER change the table schema.\
Changing data in an unsupported way may degrade or even break Unified Contacts functionality.
{% endhint %}

Database Contacts are stored in the the `UnifiedContactsCustom.Contacts` Table. You can change the content of this Table as you want but **DO NOT** change the tables schema definition.

#### Schema definition

<table data-full-width="true"><thead><tr><th width="235">column name</th><th width="173">data type</th><th width="106" data-type="checkbox">Optional?</th><th width="310.2">descritpion</th><th width="381">example</th></tr></thead><tbody><tr><td>id</td><td>NVARCHAR(256)</td><td>false</td><td>Unique identifier of the contact</td><td>sap_28648f3b-8a60-4ded-a2df-5f303a74a17a</td></tr><tr><td>displayName</td><td>NVARCHAR(256)</td><td>true</td><td>DisplayName of the contact</td><td>John Doe</td></tr><tr><td>jobTitle</td><td>NVARCHAR(256)</td><td>true</td><td>JobTitle of the contact</td><td>Software Developer</td></tr><tr><td>department</td><td>NVARCHAR(256)</td><td>true</td><td>Department of the contact</td><td>R&#x26;D</td></tr><tr><td>companyName</td><td>NVARCHAR(256)</td><td>true</td><td>Name of company assosiated with the contact</td><td>Fantastic Company Inc.</td></tr><tr><td>mailAddresses</td><td>NVARCHAR(4000)</td><td>true</td><td>Email addresses of the contact.<br><br><em>Multiple entries have to be separated with a semicolon (;)</em></td><td>john.doe@example.test;john.doe@example.test</td></tr><tr><td>imAddresses</td><td>NVARCHAR(4000)</td><td>true</td><td><p>Instant messaging addresses of the contact. Used for initiating a chat in Teams. If multiple imAddresses provided, the first one is used for intite a chat. If not provided the first eMail address of the contact is used.<br></p><p><em>Multiple entries have to be separated with a semicolon (;)</em></p></td><td>john.doe@example.test;john.doe@example.test</td></tr><tr><td>mobilePhoneNumbers</td><td>NVARCHAR(4000)</td><td>true</td><td><p>Mobile phone numbers of the contact.</p><p></p><p><em>Multiple entries have to be separated with a semicolon (;)</em></p></td><td>+1234567890;+9876543210</td></tr><tr><td>businessPhoneNumbers</td><td>NVARCHAR(4000)</td><td>true</td><td><p>Business phone numbers of the contact.</p><p></p><p><em>Multiple entries have to be separated with a semicolon (;)</em></p></td><td>+1234567890;+9876543210</td></tr><tr><td>homePhoneNumbers</td><td>NVARCHAR(4000)</td><td>true</td><td><p>Home phone numbers of the contact.</p><p></p><p><em>Multiple entries have to be separated with a semicolon (;)</em></p></td><td>+1234567890;+9876543210</td></tr><tr><td>addressFullString</td><td>NVARCHAR(256)</td><td>true</td><td>Full address of the contact. If this is set it is used for displaying the address in the contact card. If not set the address is build from the other address properties.</td><td>Any Street 1, 12345 Any City, Any Country</td></tr><tr><td>addressStreetAddress</td><td>NVARCHAR(128)</td><td>true</td><td>Street address of the contact</td><td>Any Street 1</td></tr><tr><td>addressPostalCode</td><td>NVARCHAR(32)</td><td>true</td><td>Postal code of the contact</td><td>12345</td></tr><tr><td>addressCity</td><td>NVARCHAR(128)</td><td>true</td><td>City of the contact</td><td>Any City</td></tr><tr><td>addressCountry</td><td>NVARCHAR(128)</td><td>true</td><td>Country of the contact</td><td>Any Country</td></tr><tr><td>source</td><td>NVARCHAR(64)</td><td>true</td><td>Sub source of the contact. This is used to identify the source of the contact if you are using multiple sources, that are synced into the database.</td><td>SAP</td></tr></tbody></table>
