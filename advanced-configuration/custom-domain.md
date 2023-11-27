# Custom Domain

{% hint style="info" %}
Unified Contacts Pro only.
{% endhint %}

## Step 1: Custom Domain Creation and Assignment

If you want to create your own custom domain for your Unified Contacts **App Service** URL, there are two options depending on your domain provider:

### **Option 1:** **Azure App Service Domain**

* Navigate to your Unified Contacts **App Service**
* In the left navigation bar scroll down to the "Settings" section. Click "Custom domains".
* Click "Add custom domain" (in case you have not bought an **App Service Domain** yet, first create one by clicking "Buy App Service domain").
* Configure the custom domain as follows:
  * Domain provider: **App Service Domain**
  * TLS/SSL certificate: select **App Service Managed Certificate** if you want to create and bind the certificate to your custom domain automatically, this certificate is managed by Azure and will be automatically renewed at no cost.
  * TLS/SSL type: **SNI SSL Binding** is free of cost and supported by most modern browsers.
  * App Service Domain: Choose an existing **App Service Domain**
  * Domain type: **Subdomain**
  * Subdomain: Set your preferred subdomain
* Click "Add"

<figure><img src="../.gitbook/assets/image (34) (1).png" alt=""><figcaption></figcaption></figure>

By clicking on add, the custom domain and the SSL Managed Certificate will be created and bound automatically.

### **Option 2: Non-Azure Domain**

* Navigate to your Unified Contacts **App Service**
* In the left navigation bar scroll down to the "Settings" section. Click "Custom domains".
* Click "Add custom domain"
* Configure the custom domain as follows:
  * Domain provider: **All other domain services**
  * TLS/SSL certificate: select **App Service Managed Certificate** if you want to create and bind the certificate to your custom domain automatically, this certificate is managed by Azure and will be automatically renewed at no cost.
  * TLS/SSL type: **SNI SSL Binding** is free of cost and supported by most modern browsers.
  * Domain: Set your preferred domain
  * Hostname record type: **CNAME**
* Register the displayed CNAME or TXT record mapping with your DNS provider. Once this is done, click "Validate".
* Click "Add" when the validation is successful.

<figure><img src="../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
In both cases it can take a few moments until the SSL binding with the **App Service Managed Certificate** is complete.
{% endhint %}

## Step 2: Update Permissions

{% hint style="info" %}
This step is only required if you are adding the custom domain after you have already deployed Unified Contacts.
{% endhint %}

The **App Registrations** that were created during the [post-deployment](../deployment/getting-started/unified-contacts-pro.md#step-2-perform-post-deployment-steps-permission-assignments) step must now be updated to support the new custom domain. Therefore,

* Navigate to **Azure AD**, "Manage" --> "App registrations"
*   Locate the **two** **App registrations** that were created during the deployment of Unified Contacts. You assigned the name in the [first step of the deployment](../deployment/getting-started/unified-contacts-pro.md#step-1-deploy-unified-contacts-pro-base-services).\


    <figure><img src="../.gitbook/assets/image (23) (1).png" alt=""><figcaption></figcaption></figure>
* First, click on the "admin" **App registration** and navigate to "Manage" --> "Authentication".
  *   Under the "Redirect URLs", add your custom domain and click "Save"\


      <figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>
* Next, go the the "teams" **App registration** and navigate to "Manage" --> "Authentication".
  *   Under the "Redirect URLs", add your custom domain and click "Save"\


      <figure><img src="../.gitbook/assets/image (24) (1) (1).png" alt=""><figcaption></figcaption></figure>
  *   Next, navigate to "Manage" --> "Expose API" and update the "Application ID URI" with your custom domain.\


      <figure><img src="../.gitbook/assets/image (11) (1).png" alt=""><figcaption></figcaption></figure>

The configuration of the custom domain is complete.

{% hint style="warning" %}
In the [next step](../deployment/getting-started/unified-contacts-pro.md#step-4-add-unified-contacts-pro-to-your-app-store) of the deployment guide, remember to update the **Api Domain** in the **Teams Manifest** configuration.
{% endhint %}
