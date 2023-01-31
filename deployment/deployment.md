# Deployment

## Deployment of Azure Resources

Log in with an AAD administrator account, visit this site and click the following deployment link:

* [Production channel](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Funifiedcontacts.blob.core.windows.net%2Farm-templates%2FarmDeployment.json) (do not use yet)

This will invoke the ARM-deployment-template that is pre-populated with default values. In the default configuration, partly-random resource names will be generated based on the **Resource group** ID.

{% hint style="info" %}
In case you have resource naming conventions, you may override the default resource names to match your requirements.
{% endhint %}

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

* **Subscription:** Select your subscription, where you have permissions to create app services, app service plans, key vaults, storage accounts, SQL databases and SQL servers
* **Resource group:** Select an existing resource group or create a new one. The Unified Contacts resources will be deployed to this resource group
* **Region:** Select the region according to your location preferences
* **License Key**: Input the production or trial license key you have retrieved either by purchasing a Unified Contacts subscription or by asking us about a trial key
* **Key Vault Name**: Keep the default value or define a custom but globally unique value

{% hint style="info" %}
In case you have previously deployed Unified Contacts Pro with the same **Key Vault Name**, and deleted all resources of the previous deployment, make sure to [purge](https://docs.microsoft.com/en-us/azure/key-vault/general/key-vault-recovery?tabs=azure-cli#key-vault-cli) the previously deleted Key Vault. By default, upon deletion, the Key Vault will remain in [soft-delete](https://docs.microsoft.com/en-us/azure/key-vault/general/soft-delete-overview) state for 90 days, essentially blocking the creation of a new Key Vault with the same name.
{% endhint %}

* **Storage Account Name**: Keep the default value or define a custom but globally unique value. This value must only contain numbers and/or _lowercase_ letters.

{% hint style="warning" %}
The **Storage Account Name** value must only contain numbers and/or lowercase letters.
{% endhint %}

* **Server Name**: Keep the default value or define a custom but globally unique value for the SQL server.&#x20;

{% hint style="warning" %}
The **Server Name** value must only contain numbers and/or lowercase letters and/or hyphens (not leading or trailing).
{% endhint %}

* **Sql DB Name**: Keep the default value or define a custom value
* **Administrator Login**: Define a username as part of an administrative access account for the SQL database
* **Administrator Login Password**: Define a password for the administrative access account for the SQL database. Store this password in your password vault.
* **Sharepoint Url**: Link to your organizations root Sharepoint Online site. Typically: `<yourdomain>.sharepoint.com`
* **App Service Plan Name**: Keep the default value or define a custom but globally unique value
* **App Service Name**: Keep the default value or define a custom but globally unique value
* **App Registration Name Admin Page**: Keep the default value or define a custom value
* **App Registration Name Teams App**: Keep the default value or define a custom value
