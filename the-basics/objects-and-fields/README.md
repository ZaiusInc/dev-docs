# Objects & Fields

## Fields

Fields allow storing custom metadata on any Zaius Object. Fields can store a variety of data:

| Type | Notes |
| :--- | :--- |
| Text | Any printable UTF-8 character, including space. Text is limited to 1024 characters. |
| Number | A number represented in standard decimal format \(Example: `0`, `3.14159`, `-2.3`, `-0.112`\) |
| Date & Time | Must be formatted as ISO 8601 format or UNIX epoch \(seconds since January 1, 1970\). Examples: `1435708800`, `2015-07-01T00:00:00-00:00`, `2015-07-01T12:30:00-07:00`Note: If time and timezone are not provided the time is assumed be 12am UTC. |
| True / False | Must be one of `0`, `1`, `true` or `false` |

### Create Custom Fields **in UI**

1. Go to [Account Settings -&gt; Objects & Fields](https://app.zaius.com/app?scope=#/custom_fields) and select **Create New Field.**
2. Select the object that should own the field \(e.g. Events or Customers\).
3. Select the field name and field display name.
   1. Field Name: The name used for API / SDK / CSV uploads and within Liquid templates.
   2. Field Display Name: The user-friendly name used in reporting, segmentation and campaigns.

### Create Custom Field **via API**

## Create Custom Objects and / or Identifiers

{% hint style="warning" %}
Custom Objects & Identifiers are only available for creation by app developers and Zaius Customer Success / Support. To learn more, contact your CSM or our support team.
{% endhint %}

