# SharePoint Online Lists

Unified Contacts Pro can search for contacts in **SharePoint Online lists**. You can use a contact list in SharePoint Online in different fashions:

* As bridge technology to export your customer contact data from any third party database and import it to SharePoint Online
* To deploy a centralized, shared contact list in your departments or business units

To optimize the search in SharePoint Online, Unified Contacts Pro searches for a dedicated SharePoint **content type** - contacts. Therefor your contacts needs to be stored in a SharePoint Online **Contacts** list or a **List** where the content type "contacts" is assigned to.

{% hint style="warning" %}
Users will only be able to search a SharePoint Online list if they have (read-) permissions to access the list **and** the site under which it is stored.
{% endhint %}

This article describes how to create a new SharePoint Online list and assign the correct content type.

### Create an empty SharePoint Online List

* Open the **SharePoint Online** site where you would like to store the contacts
* Create a new list by clicking "Settings" -> "Add an app"
*   Open the classic view by clicking "classic experience"\


    <figure><img src="../../.gitbook/assets/image (70).png" alt=""><figcaption></figcaption></figure>
* Select "Custom List"
* Define a name for the list and create it

### Assign the Content Type to a new  SharePoint Online List

The list you just created must be of the "Contacts" **content type** to be found with Unified Contacts. One option is to assign a content type to a SharePoint list, and all newly created items in the list inherit the content type of that list.

Therefore, add the **Contact** content type and remove the default content type from the list.

* Open the SharePoint Online list
*   Open list settings by clicking "Settings" --> "List settings"\


    <figure><img src="../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>
* Open "Advanced settings"
* Enable "Allow management of content types" and save the changes by clicking "OK" at bottom of the page.
* SharePoint opens the settings page and you will see the section "Content Types"
*   Click "Add from existing site content types"\


    <figure><img src="../../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>
* Add "Contact" and save the changes by clicking "OK"
* Click on "Default content type" and delete it
