# Installation Guide

To install Unified Contacts navigate to the offering in the [Microsoft Office App Store](https://appsource.microsoft.com/en-us/product/office/WA200003877).

Click on "Get it now" and sign in with your M365 credentials. A preview of Unified Contacts should appear in your Teams client. Click "Add" and the app will be added to your tenant.

To enable Unified Contacts to search for contacts in your Azure AD or your personal Exchange Online contact store, you must grant an app consent for your tenant. The following permissions are required:

* View your basic profile
* Maintain access to data you have given it access to

If the app consent is missing, you will see a request to grant the required permissions instead of a search result page:

![Unified Contacts - Notification about missing app permissions](<.gitbook/assets/AdminConsent\_Missing\_Screenshot 2021-12-02 162552.png>)

In that case, please inform your Global Administrator to use the Consent link and register Unified Contacts as an Enterprise Application in your tenant.

If you are a Global Administrator, just follow the wizard and accept the permission request:

![Unified Contacts- Grant required permissions](<.gitbook/assets/AdminConsent\_Grant\_Screenshot 2021-12-02 162731.png>)

After you have successfully granted the permissions, refresh the app and the search box should be visible.

![Unified Contacts - Working search page](<.gitbook/assets/AdminConsent\_Grant\_success2\_Screenshot 2021-12-02 162731.png>)

