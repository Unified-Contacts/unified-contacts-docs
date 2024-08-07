# Unified Contacts Pro

This step-by-step guide will explain all the necessary steps to deploy **Unified Contacts Pro** for an enterprise-grade environment in your Azure tenant.

## Azure Deployment

Let's start with the requirements and a resource overview.\
Keep in mind that you need to plan a useful Azure resource design.

### Checklist: Prerequisites

* [ ] _Optional_ - Azure resource naming convention
* [ ] _Mandatory -_ Azure subscription (at least Contributor rights on that subscription)
* [ ] _Mandatory -_ Azure owner rights (at least on Resource Group level)
* [ ] _Mandatory -_ Azure AD "Global administrator" (Consent to access Graph API)
* [ ] _Optional_ - Public Domain CNAME (_unified-contacts.yourdomain.com_)
* [ ] _Optional_ - SSL (Wildcard-) Certificate (or use [App Service Managed Certificate](https://docs.microsoft.com/en-us/azure/app-service/configure-ssl-certificate#create-a-free-certificate-preview))
* [ ] _Mandatory -_ Unified Contacts License Key (please [contact us](https://www.unified-contacts.com/start-now/#try) for a trial key)

### Overview Azure Resource

All these resources are recommended for a production environment.

| Type             | Description                                                                                                                                                                                              |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| App Service      | <p>A virtual Azure environment to run the Unified Contacts application backend, providing a UI to configure different<br>application specific settings like CNAME, SSL certificate and App Settings.</p> |
| App Service Plan | <p>A virtual set of compute resources and configurations for the "App Service".</p><p>Here you can configure the pricing tier and resource scaling.</p>                                                  |
| Key Vault        | Resource to securely store secrets and certificates. Unified Contacts leverages Key Vault to store API client secrets.                                                                                   |
| Storage account  | Storage platform that stores the binaries of the Unified Contacts backend application.                                                                                                                   |
| SQL database     | Relational database used by Unified Contacts to store persistent information such as custom settings and pinned favorites.                                                                               |
| SQL server       | A virtual set of compute resources and configurations for the "SQL database".                                                                                                                            |

## Configuration Steps

### Step 1: Deploy Unified Contacts Pro Base Services

{% hint style="warning" %}
This is a **mandatory** step.
{% endhint %}

To start with the deployment, follow our setup instructions:

{% content-ref url="../deployment.md" %}
[deployment.md](../deployment.md)
{% endcontent-ref %}

### Step 2: Custom Domain

{% hint style="info" %}
This is an **optional** step.
{% endhint %}

To configure a custom domain for the Unified Contacts backend, follow this guide:

{% content-ref url="../../advanced-configuration/custom-domain.md" %}
[custom-domain.md](../../advanced-configuration/custom-domain.md)
{% endcontent-ref %}

### Step 3: Perform Post-Deployment Steps (Permission Assignments)

{% hint style="warning" %}
This is a **mandatory** step.
{% endhint %}

To properly link all components of Unified Contacts Pro, several permissions need to be assigned. Please follow these steps to establish the relevant connections:

1. Navigate to the Unified Contacts backend website. For that, navigate to the Unified Contacts **App Service**, select "Overview" and click "Browse".
2.  Copy the content of the black box to your clipboard and paste it into a text editor. \


    <figure><img src="../../.gitbook/assets/image (89).png" alt=""><figcaption></figcaption></figure>
3. Now you need to replace the `AppServiceAzureUrl` with the correct URL from your Unified Contacts **App Service**. Therefore
   1. Navigate to the Unified Contacts **App Service** "Overview" blade.&#x20;
   2.  Copy the URL from your browser and replace the `AppServiceAzureUrl` argument value in the text editor with this URL.\


       <figure><img src="../../.gitbook/assets/Screenshot_2023-01-30_at_15_55_47 (1).png" alt=""><figcaption></figcaption></figure>
4. Copy all commands from the text editor, open the **Azure Cloud Shell** (Power Shell) on **Azure Portal** and paste the commands.
5.  During the script execution, you will be prompted for the SQL server administration account. Please provide the credentials you specified during the deployment in the ARM template.\


    <figure><img src="../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>
6. If you have previously configured a **Custom domain** on the Unified Contacts **App Service**, the script will prompt you for the correct **App Service URL**. Please select the custom domain.
7.  Towards the end of the script, you will be asked to grant the permissions (**read-only**) required for the Unified Contacts front- and backend to function properly. Please consent to those permissions by

    1. Either copying **both** links to your browser and acknowledging the grants manually with a suitable admin account,
    2. **Or** by selecting to the **Automatic Permission Grant**. In this case, please complete the **Device Login** by opening the website [https://microsoft.com/devicelogin](https://microsoft.com/devicelogin), pasting the one-time code displayed in the Azure Cloud Shell, and following all steps.

    <figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>
8. Once the script has completed successfully, **restart** the Unified Contacts **App Service**.
9.  To verify the successful deployment, navigate to the Unified Contacts **App Service**, select "Overview" and click "Browse". The health indicators on the left side should all indicate "Healthy".\


    <figure><img src="../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
It may initially take up to **5 minutes** until the Unified Contacts backend portal is loaded.
{% endhint %}

### Step 4: Configure Access to the Unified Contacts Backend

{% hint style="info" %}
This is an **optional** step.
{% endhint %}

By default, any account from the tenant can access the Unified Contacts Backend. To configure access for certain accounts only, please refer to below article.

{% content-ref url="../../advanced-configuration/backend-permissions.md" %}
[backend-permissions.md](../../advanced-configuration/backend-permissions.md)
{% endcontent-ref %}

### Step 5: Add Unified Contacts Pro to your Organization's App Store

{% hint style="warning" %}
This is a **mandatory** step.
{% endhint %}

1. Open the Unified Contacts backend website. Therefore, navigate to the Unified Contacts **App Service**, select "Overview" and click "Browse".&#x20;
2.  In case you have never deployed Unified Contacts Pro before, the website will inform you that you first need to upload the Unified Contacts Manifest. This will make the Unified Contacts Pro Teams App available in your organization's AppStore.\


    <figure><img src="../../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>
3. Acknowledge the dialogue, navigate to the "Teams Manifest" tab, adapt the manifest to your preferences, click "Save" and then "Upload". If you have configured a **custom domain**, remeber to **override** the "Api Domain" in the manifest. **Uploading the manifest** **might take a few moments**. Please note: You can even change the display name of the app that will appear under the icon in the end-users' Teams client.
4.  The Unified Contacts Pro Teams app is now available in [**Teams Admin Center**](https://admin.teams.microsoft.com/) and you may distribute it as per your requirements.\


    <figure><img src="../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

## Step 6: Import Contacts from 3rd Party Sources and CRM Systems

{% hint style="info" %}
This is an **optional** step.
{% endhint %}

You may import contacts from 3rd party contact sources or CRM systems by leveraging the UC Database

{% content-ref url="../../advanced-configuration/uc-database/" %}
[uc-database](../../advanced-configuration/uc-database/)
{% endcontent-ref %}

or SharePoint Online Lists:

{% content-ref url="../../advanced-configuration/sharepoint-online-lists.md" %}
[sharepoint-online-lists.md](../../advanced-configuration/sharepoint-online-lists.md)
{% endcontent-ref %}
