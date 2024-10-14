---
description: Frequently asked questions
---

# FAQ

## What is Unified Contacts?

Unified Contacts is a productivity tool for Microsoft Teams. Visit the [Details](../welcome.md) page to understand the scope of the app.&#x20;

## Do I need to buy another service to use Unified Contacts Free?

No. The app is completely powered by our SaaS platform that is located in a European Azure datacenter. There are no external dependencies.

## Does Unified Contacts collect user data?

Unified Contacts does not store any data about the users or searched contacts. All search queries are transmitted from your tenant to our SaaS platform and are secured by TLS 1.2.

## How can I contact you for further information on Unified Contacts?

We are happy to answer your inquiries on Unified Contacts! Please submit your request either via Unified Contact's [homepage](https://www.unified-contacts.com/) or send us an email via [sales@unified-contacts.com](mailto:sales@unified-contacts.com).

## Which directories are supported?

Currently, Unified Contacts Free supports the search of contacts in **Azure Active Directory** (Azure AD user and contact objects) and **Exchange Online**.

Unified Contacts Pro additionally supports the search of contacts in **SharePoint Online** contact lists.

## Do you support Active Directory and Exchange?

Active Directory Domain Services and Exchange on-premises are not supported in the current version of Unified Contacts.

## Do you support Federation in Azure Active Directory?

This is currently not supported by Unified Contacts.

## Can I find contacts in other Outlook contact folders than the standard contacts folder ?

Unified Contacts searches the default contacts folder for contacts. Access to other contacts folders or sub-folders is not supported.

## What contact types are found by Unified Contacts in Azure AD?

Unified Contacts searches for user objects and mail contacts in Azure AD. Guest user accounts and mail user accounts are not found by Unified Contacts.&#x20;

## What type of numbers can be directly dialed from the app in Teams?

With click-to-dial you can call any phone number stored in your personal contacts (Outlook) and corporate contacts (Azure AD) **with a single click**. You can also start a Teams call with contacts having a Teams client.

## Why can't I place phone calls?

In case you see the below error message after attempting to initiate a PSTN call from Unified Contacts, your user account is probably not enabled for the Microsoft Teams Phone System. Please contact your administrator for details.

![Error Message: Sorry, we can't complete the call.](<../../.gitbook/assets/Picture 1.png>)

## Does Unified Contacts work on mobile devices?

Yes, you can use the Unified Contacts natively in your Teams app on any mobile device.

## How do you handle disabled users?

Disabled users are not displayed in the result views.

## How do I clean the Teams desktop app cache?

Details can be found in the Microsoft Docs for different platforms: [https://learn.microsoft.com/en-us/microsoftteams/troubleshoot/teams-administration/clear-teams-cache](https://learn.microsoft.com/en-us/microsoftteams/troubleshoot/teams-administration/clear-teams-cache)\
In case you are using the new Teams 2.0 Client you have to quit Teams and delete the content of `%userprofile%\appdata\local\Packages\MSTeams_8wekyb3d8bbwe\`

