# Updating to Unified Contacts Pro 1.5.0

If you are updating from a version **lower than 1.5.0** or you used the **UnifiedContactPS Module with a version lower than 1.1.0** to initially install Unified Contacts Pro, you need to follow this Guide if you are planning to use the REST API for Creating/Updating/Deleting or accessing Contact information.

## Summary

After following the steps below you will be able to follow the Authentication steps outlined int the [CRUD operations with REST API](crud-operations-with-rest-api.md#authentication) documentation. In this guide we will Configure your Admin **AppRegistration** to expose the Role necessary to Authenticate against the Unified Contacts REST API.

## Setup

1.  Open **Azure Portal** and search for "App registrations" or click [here](https://portal.azure.com/#view/Microsoft\_AAD\_RegisteredApps/ApplicationsListBlade).\


    <figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>
2.  Search for the **Admin App registration** of Unified contacts. If you haven't configured a custom naming during installation the App registration is named"'admin-app-reg-uc-<13 digit random numbers and letters>".\


    <figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>
3.  Click on **Expose an API** and select **Add** on the **Application ID URI**. Then click "Save".\
    _Note: If you already have an Application ID URI, just skip this step._

    <figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>
4. Click on "App roles" then on "Create app rol"' and fill out the side pannel as follows and subsequently click "Apply":\

   * **Display name:** Contacts.Database.ReadWrite.All
   * **Allowed member types:** Applications
   * **Value:** Contacts.Database.ReadWrite.All
   * **Description:** Allows to read and write (create, update, delete) database contacts.
   *   **Do you want to enable this app role?**: Yes

       <figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

After you have completed those steps you can continue with the [CRUD operations with REST API](crud-operations-with-rest-api.md#authentication) documentation.
