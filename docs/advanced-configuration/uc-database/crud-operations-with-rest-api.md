---
description: >-
  Documentation for the usage of the customer facing REST API for Database
  Contact insertion
---

# CRUD operations with REST API

## Authentication

To access the API endpoints you need to acquire a **Bearer token**. The API uses Microsoft as an Identity Provider with **Application permissions**. Therefore the access can be managed similarily to the the access of the Microsoft Graph API.

### Prerequisites

* [ ] Unified Contacts Pro setup completed with version 1.5.0 or later
* [ ] Cloud Application Administrator, Application Administrator or Global Admin privileges (used for the admin grant)

{% hint style="danger" %}
If you have used UnifiedContactsPS with version lower than 1.1.0 to install Unified Contacts, you first have to perform the additional steps explained [here](updating-to-unified-contacts-pro-1.5.0.md).

_NOTE: If you have initially installed Unified Contacts Pro before version 1.5.0, this is very likely the case._
{% endhint %}

### Permission Setup

1. Select an existing App Registration or [create a new one](https://learn.microsoft.com/en-us/azure/healthcare-apis/register-application) that will be used to authenticate you when accessing the Unified Contacts REST API.
2.  Navigate to **API permissions > Add a permission > My APIs** then select the Unified Contacts **Admin AppRegistration**. If you have not changed the default naming when deploying Unified Contacts via the ARM template the name will be in the following format: \
    `admin-app-reg-uc-<13 random alphanumeric characters>`\


    <figure><img src="../../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>
3.  Select **Application permissions** on the top and activate the checkbox next to **Contacts.Database.ReadWrite.All.** Finalize the assignment by clicking  "Add permissions" on the bottom.\


    <figure><img src="../../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>
4.  A Cloud Application-, Application-, or Global-Admin now has to **Grant admin consent** for the tenant. This is done by clicking the **Grant admin consent for \<Tenant>** button and confirming the action by clicking on **Yes**.\


    <figure><img src="../../../.gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>
5. After the Admin consent is granted the AppRegistration is ready for usage.

### Acquiring a token

A detailed explanation on acquiring tokens against an AppRegistration can be found [here (Microsoft docs)](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow).

\
In the following example we will configure **Postman** to acquire a valid token with an **Application Secret**. However we recommend the usage of a **Managed Identity** (when applicable) or with Certificates when creating a productive/regularly running process or sync.

* More details on certificate authentication can be found [here (Microsoft docs)](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow#second-case-access-token-request-with-a-certificate).&#x20;
* More details on **Managed Identity** authentication can be found [here (Microsoft docs)](https://learn.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/how-to-use-vm-token).

1.  Open the AppRegistration [from before](crud-operations-with-rest-api.md#permission-setup). Navigate to **Certificates & secrets > Client secrets > New client secret**. Set a description and configure the **Expiry date** (max. 2 years). Finalize the process by clicking "Add".\


    <figure><img src="../../../.gitbook/assets/image (88).png" alt=""><figcaption></figcaption></figure>
2.  Copy and store the freshly generated client secret somewhere secure (e.g. a credential manager). **NOTE:** Once you leave this page you will only be able to see a censored shortened version of the secret. So if you do not store the secret properly and forget it you'll need to create a new one\


    <figure><img src="../../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>
3.  Navigate to the **Overview** tab of the **AppRegistration**. Copy the **ClientId** for later use. Click on **Endpoints** and copy the **OAuth 2.0 token endpoint (v2)** for later use.\


    <figure><img src="../../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>
4.  Navigate to **API permissions** select the **Contacts.Database.ReadWrite.All** permission and Copy the **scope** for later use.\


    <figure><img src="../../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>
5.  Create a new **Postman Collection** and navigate to the Authentication tab. There select **OAuth 2.0** as **Type**\


    <figure><img src="../../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>
6.  Fill out the **Configure new token** category\


    <figure><img src="../../../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>

    * **Token Name**: Any custom Name
    * **Grant Type**: Client Credentials
    * **Access Token URL**: Paste the token URL copied in Step 3
    * **Client ID**: Paste the Client Id copied in Step 3
    * **Client Secret**: Paste Secret copied in Step 2
    * **Scope**: Paste scope copied in step 4. Replace **Contacts.Database.ReadWrite.All** with **.default**
    * **Client Authentication**: Send as Basic Auth header
7.  Your result should look something like this:

    <figure><img src="../../../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>
8.  If you have configured everything correctly, you can now scroll to the bottom and click on "Get New Access Token" to acquire a new access token. All requests within the **Collection** can now be authenticated with that token.

    <figure><img src="../../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

### API Documentation

{% swagger src="../../../.gitbook/assets/swagger.json" path="/api/v1/contacts/{contactId}" method="get" %}
[swagger.json](../../../.gitbook/assets/swagger.json)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/swagger.json" path="/api/v1/contacts" method="post" %}
[swagger.json](../../../.gitbook/assets/swagger.json)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/swagger.json" path="/api/v1/contacts/{contactId}" method="put" %}
[swagger.json](../../../.gitbook/assets/swagger.json)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/swagger.json" path="/api/v1/contacts/{contactId}" method="patch" %}
[swagger.json](../../../.gitbook/assets/swagger.json)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/swagger.json" path="/api/v1/contacts/{contactId}" method="delete" %}
[swagger.json](../../../.gitbook/assets/swagger.json)
{% endswagger %}

You can download a sample Postman Collection here:

{% file src="../../../.gitbook/assets/Unified Contacts Documentation.postman_collection.json" %}
