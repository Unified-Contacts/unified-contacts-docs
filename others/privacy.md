---
description: This chapter provides on overview of how we process and protect your data.
---

# Privacy

## General

"Our" (glueckkanja-gab AG's) [Privacy Statement](https://www.glueckkanja-gab.com/en/privacy) applies. For details on privacy and data protection on Azure, please refer to Microsoft's [documentation](https://docs.microsoft.com/en-us/azure/compliance/).&#x20;

## Unified Contacts

### Where is your data processed?

The Unified Contacts Community Edition is delivered as SaaS and hosted in the glueckkanja-gab AG Azure Tenant from Microsoft Corporation, One Microsoft Way, Redmond, WA 98052-6399, USA. The service is hosted exclusively in **Azure's Germany West Central** data center located in Frankfurt/Main, Germany.&#x20;

### What data do we process?

We process the data from the search queries as entered by the user in the Unified Contacts App in Microsoft Teams. The search results generated on our server may contain the following personal data:

* Names
* Addresses
* Email addresses
* Phone numbers

### What data do we store?

We do not store any personal data, i.e. we neither store the search query nor the search results.&#x20;

### How do we protect your data?

All communication between the Unified Contacts App and our web server is encrypted via TLS/SSL (version 1.2).&#x20;

### Why do we process your data?

Search queries are used to search contact databases through native Microsoft APIs and to present the results to the user subsequently. As such, the data is required to realize Unified Contact's core functionality.&#x20;

We do not use the search queries and search results for marketing or any other analytic purposes although this would be technically possible.

### How can I withdraw my consent to process personal data?

Every user of the Unified Contacts App has the choice to uninstall the app from their Microsoft Teams client as described here [uninstallation-guide.md](../uninstallation-guide.md "mention"). Once the app is uninstalled, no further search queries are processed for this specific user.

In order to prevent the processing of personal data organization-wide, the administrator responsible for Microsoft Teams, has to remove the Unified Contacts app from the **Microsoft Teams Admin Center**.

### What type of Microsoft API permissions do we require?

Unified Contacts relies on delegated permission only, which means the effective permission are limited to the permission of the logged in user in their organization.
