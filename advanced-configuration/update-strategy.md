# Update Strategy

{% hint style="info" %}
Unified Contacts Pro only.
{% endhint %}

Updating Unified Contacts is very easy. The backend regularly checks whether a new version of Unified Contacts is available from our different release channels. If that is the case, the backend portal will display a notification next to the "Version" information.

## Update Procedure

To update Unified Contacts:

* Open the backend portal and navigate to the "Update" tab.&#x20;
* If a new version is available in the currently selected release channel, a blue button with "Update Now" is displayed. Click that button.
* In the upcoming pop-up, confirm your choice to start the update.
*   It will take a few moments until the latest binaries are pulled from our server and deployed into the App Service. Once this is completed, a pop-up is displayed asking you to restart the App Service. Click on the link, navigate to the Unified Contacts App Service and click "Stop" und subsequently "Start."

    <figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>
* Navigate back to the backend portal by clicking "Browse".

{% hint style="warning" %}
It may take up to a few minutes until it can be reached again after the stop-start action. During this time, HTTP 503 is typically returned.
{% endhint %}

* When the backend is up again, a pop-up is displayed asking you to update the manifest (this ensures that the front-end (Unified Contacts Teams App) is compatible with the latest backend. Click "Go to Teams Manifest tab".\
  ![](<../.gitbook/assets/image (27).png>)
* In the "Team Manifest" tab review your manifest settings, click "Save" and "Update". The news Teams app will be published to your Team Admin Center. For the end user the app will update automatically.

{% hint style="warning" %}
Due to Microsoft's caching policies, it may take up to **48 hours**, until the latest version of the Teams App populates to all users.
{% endhint %}

* You can review if the latest version of the manifest was populated by checking the version number in the "About" tab:\
  ![](<../.gitbook/assets/image (33).png>)

## Release Channels

We offer Unified Contacts Pro in different release channels, allowing you to deploy the latest stable version to your production environment, while giving you access to preview or even experimental features at an early stage in your lab/staging environment.

To switch from the default release channel "stable", open the Unified Contacts backend, navigate to the "Update" tab and select the desired release channel. To complete the switch, you must go through the [Update Procedure](update-strategy.md#update-procedure) described above.

Please find below an overview of the different release channels:

| Release Channel | Description                                                                                                                                                                                                                                                                                                      |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| stable          | <p>Officially released and publicly tested (through nightly and preview users) stable version of Unified Contacts.</p><p></p><p><mark style="color:green;">Updated last - Fully supported</mark></p><p></p><p>Recommended for production environments.</p>                                                       |
| preview         | <p>Small scale tested version.</p><p></p><p><mark style="color:blue;">Updated second - Limited Support</mark></p><p></p><p><strong>Recommended for</strong> users &#x26; admins that want to get updates early and can cope with rare bugs.</p>                                                                  |
| nightly         | <p>Fast release version. </p><p></p><p><mark style="color:orange;"><strong>WARNING:</strong> Bugs may occur - Updated first - No support</mark></p><p></p><p><strong>Recommended only</strong> for brave admins &#x26; users who always want to see the new features first and can cope with potential bugs.</p> |
