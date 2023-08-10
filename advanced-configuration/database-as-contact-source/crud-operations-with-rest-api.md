---
description: >-
  Documentation for the usage of the customer facing REST API for Database
  Contact insertion
---

# CRUD operations with REST API

### Authentication

To access the Endpoints you need to acquire a Bearer token. The API Uses Microsoft as an Identity provider with Application permissions. Therefore the access can be managed similarily to the the access of the Microsoft Graph API.

#### Prerequisites

* Unified Contacts Pro setup completed with version >1.5.0
* Cloud Application Administrator, Application Administrator or Global Admin privileges (used for the admin grant)

{% hint style="danger" %}
If you have used UnifiedContactsPS with version lower than < 1.1.0 to install Unified Contacts. You have to make additional steps explained [here](update-for-uc-less-than-1.5.0.md).

_NOTE: If you have installed Unified Contacts before v 1.5.0 this is very likely the case._
{% endhint %}

#### Permission setup

1. Select an existing App Registration or [create a new one](https://learn.microsoft.com/en-us/azure/healthcare-apis/register-application) that will be used to authenticate you when accessing the Unified Contacts Customer API
2.  Navigate to **API permissions > Add a permission > My APIs** then select the Unified Contacts **Admin** AppRegistration. If you have not changed the default naming when deploying Unified Contacts via the ARM template the name will be in the following format: admin-app-reg-uc-<13 random alphanumeric characters>

    <figure><img src="../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>
3.  Select **Application permissions** on the top and activate the checkbox next to **Contacts.Database.ReadWrite.All.** Finalize the assignement by klicking the **Add permissions** button on the bottom.

    <figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>
4.  An Cloud Application-, Application-, or Global-Admin now has to Grant admin consent for the tenant. This is done by clicking the **Grant admin consent for \<Tenant>** button and confirming the action by clicking on **Yes**.

    <figure><img src="../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>
5. After the Admin consent is granted the AppRegistration is ready for usage.

#### Acquiring a token

A detailed explanation on acquiring token against an AppRegistration can be found [here (Microsoft docs)](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow). \
In the following example we will configure Postman to acquire a valid token with an Application Secret. However we recommend the usage of managedIdentity (when applicable) or with Certificates when creating a productive/regulaly running process or sync. \
\- More details on certificate authentication can be found [here (Microsoft docs)](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow#second-case-access-token-request-with-a-certificate). \
\- More details on manageIdentity authentication can be found [here (Microsoft docs)](https://learn.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/how-to-use-vm-token).

1.  Open the AppRegistration [from before](crud-operations-with-rest-api.md#permission-setup). Navigate to **Certificates & secrets > Client secrets > New client secret**. Set a description and confiure the Expiry date (max 2 years). Finlaize the process by clicking add

    <figure><img src="../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>
2.  Copy and store the freshly generated client secret somwhere secure (e.g. a credential manager). NOTE: once you leave this page you will only be able to see a censored shortened version of the secret. So if you do not store the secret properly and forget it you'll need to create a new one

    <figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>
3.  Navigate to the Overiew tab of the AppRegistration. Copy the **ClientId** for later use. Click on **Endpoints** and copy the **OAuth 2.0 token endpoint (v2)** for later use.

    <figure><img src="../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>
4.  Navigate to **API permissions** select the **Contacts.Database.ReadWrite.All** permission and Copy the **scope** for later use.

    <figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>
5.  Create a new postman Collection and navigate to the Authentication tab. There select OAuth 2.0 as Type

    <figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>
6.  Fill out the **Configure new token** category

    <figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

    Token Name: Any custom Name\
    Grant Type: Client Credentials\
    Access Token URL: Paste the token URL copied in Step 3\
    Client ID: Paste the Client Id copied in Step 3\
    Client Secret: Paste Secret copied in Step 2\
    Scope: Paste scope copied in step 4. Replace **Contacts.Database.ReadWrite.All** with **.default**\
    Client Authentication: Send as Basic Auth header
7.  Your result should look something like this:

    <figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>
8.  If you done everything right you can now scroll to the bottom and click on Get New Access Token to acquire a new accesstoken. All requests within the Collection can now be authenticated with that token.

    <figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

### API Documentation

{% swagger src="../../.gitbook/assets/swagger.json" path="/api/v1/contacts/{contactId}" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% swagger src="../../.gitbook/assets/swagger.json" path="/api/v1/contacts" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% swagger src="../../.gitbook/assets/swagger.json" path="/api/v1/contacts/{contactId}" method="put" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% swagger src="../../.gitbook/assets/swagger.json" path="/api/v1/contacts/{contactId}" method="patch" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% swagger src="../../.gitbook/assets/swagger.json" path="/api/v1/contacts/{contactId}" method="delete" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

You can download a sample Postman Collection here:

{% file src="../../.gitbook/assets/Unified Contacts Documentation.postman_collection.json" %}
