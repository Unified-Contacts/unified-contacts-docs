---
description: Update process for older Unified Contacts versions
---

# Updating from older versions (<=1.5.1)

{% hint style="info" %}
Unified Contacts Pro & Community Edition only.
{% endhint %}

Updating Unified Contacts is very easy. The backend regularly checks whether a new version of Unified Contacts is available from our different release channels. If that is the case, the backend portal will display a notification next to the "Version" information.

## Update Procedure

To update Unified Contacts:

* Open the backend portal and navigate to the "Update" tab.&#x20;
* If a new version is available in the currently selected release channel, a blue button with "Update Now" is displayed. Click that button.
* In the upcoming pop-up, confirm your choice to start the update.
*   It will take a few moments until the latest binaries are pulled from our server and deployed into the App Service. Once this is completed, a pop-up is displayed asking you to restart the App Service. Click on the link, navigate to the Unified Contacts App Service and click "Stop" und subsequently "Start."

    <figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Navigate back to the backend portal by clicking "Browse".

{% hint style="warning" %}
It may take up to a few minutes until it can be reached again after the stop-start action. During this time, HTTP 503 is typically returned.
{% endhint %}

* When the backend is up again, a pop-up is displayed asking you to update the manifest (this ensures that the front-end (Unified Contacts Teams App) is compatible with the latest backend. Click "Go to Teams Manifest tab".\
  ![](<../../.gitbook/assets/image (27).png>)
* In the "Team Manifest" tab review your manifest settings, click "Save" and "Update". The news Teams app will be published to your Team Admin Center. For the end user the app will update automatically.

{% hint style="warning" %}
Due to Microsoft's caching policies, it may take up to **48 hours**, until the latest version of the Teams App populates to all users.
{% endhint %}

* You can review if the latest version of the manifest was populated by checking the version number in the "About" tab:\
  ![](<../../.gitbook/assets/image (33) (1).png>)

##
