# Logs & Telemetry

{% hint style="info" %}
Unified Contacts Pro only.
{% endhint %}

## Telemetry Data

Besides a minimum amount of anonymous telemetry data required for license enforcement purposes, you can configure Unified Contacts to transmit additional diagnostic information to us (_our_ Log Analytics workspace), which helps us to improve our product and to identify widespread issues so we can communicate counter-measures proactively.

Furthermore, if you reach out to us with a support inquiry, we might ask you to configure a certain log level so that we are able to properly support you.

You may control this setting by opening your Unified Contacts Pro backend portal and navigating to the "Settings" tab.

The following telemetry data log levels are available:

| Log Level | Description                                                                                                                                                                                                                                                                    |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Off       | No additional log data is transmitted to us.                                                                                                                                                                                                                                   |
| Anonymous | When the UC application throws internal errors, diagnostic information about the nature of the error and the context it occurred in will be sent to us in a fully anonymous way (no PI-data is transferred to).                                                                |
| General   | In addition to the information provided in the anonymous log level, arguments of failed function and API calls are transmitted to us, potentially containing PI-data. This additional amount of information helps us to to more targetedly analyze and debug potential issues. |
| Detailed  |  A full stack trace of the failing function or API call is transmitted to us, potentially containing PI-data.                                                                                                                                                                  |

