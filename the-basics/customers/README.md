# Customers

Customers are at the core of Zaius. Customers are composed of fields that are typically grouped into one of two groups: attributes or identifiers.

## Fields

## Attributes

| Display Name | Field Name | Description |
| :--- | :--- | :--- |
| First Name | `first_name` |  |
| Last Name | `last_name` |  |
| Gender | `gender` | Stored as `M`, `F` |
| Time Zone | `timezone` | Timezone in [IANA format](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) \(e.g. `America/New_York`\) |
| Image URL | `image_url` |  |
| Phone Number | `phone` | Phone number in [E.164 format](https://en.wikipedia.org/wiki/E.164) \(e.g. `+15552108050`\) |
| Primary Line | `street1` |  |
| Secondary Line | `street2` |  |
| City | `city` |  |
| State | `state` |  |
| ZIP / Postal Code | `zip` |  |
| Country | `country` | Country in [ISO-3166-1 format](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-3) |

### Identifiers

Zaius utilizes Customer Identifiers \(e.g. `emails`, `vuids`, `push_tokens`\) to merge users together and determine which event is associated with which customer.

Including one or more of these identifiers on an event identifies the user who performed the event and allows Zaius to merge users together when enough information becomes available.

#### Standard Identifiers

| Display Name | Field Name | Description |
| :--- | :--- | :--- |
| Zaius ID | `zaius_id` | A unique, Zaius-generated identifier, that represents a customer |
| Last Seen Email | `email` | The last seen email associated with this customer. |
| Last Seen Cookie ID | `vuid` | Zaius' unique Cookie / Device ID, used on web and mobile to identify anonymous customers. |

#### App Identifiers \(Examples\)

Many apps / integrations \(e.g. Shopify or Magento\) create identifiers that map to an external system \(e.g. Shopify ID\) to allow for improved user resolution, troubleshooting, and transparency. Some examples:

| Display Name | Description |
| :--- | :--- |
| Last Seen Shopify ID \(mystore\) | shopify\_mystore\_id |
| Last Seen Zendesk ID \(mysupporteam\) | zendesk\_mysupportteam\_id |

{% hint style="info" %}
Every identifier is also stored as an array in the plural form \(with a max of 25 for each identifier type\).

For example, all the known emails for a customer are stored in the a field called Emails \(`emails`\) and Cookie ID are stored as `vuids`. 
{% endhint %}

#### Custom Identifiers

If you have an external database, data lake, or system \(e.g. a point-of-sale system\) that uses a unique identifier to track customers, Zaius supports the creation of Custom Identifiers to ensure that all known information about your customers is tracked and you're able to reconcile information within Zaius with the external data source.

{% hint style="info" %}
Custom Identifiers are considered when merging customers together. 
{% endhint %}

{% hint style="warning" %}
At this time, Custom Identifiers must be created by a member of the Zaius Customer Success team. Contact your CSM or Support via email or chat to learn more.
{% endhint %}

### Resolution & Stitching

Zaius utilizes Customer Identifiers \(e.g. `emails`, `vuids`, `push_tokens`\) to merge users together and determine which event is associated with which customer.

Including one or more of these identifiers on an event identifies the user who performed the event and allows Zaius to merge users together when enough information becomes available.

Identifiers are categorized into levels of confidence: 

* High Confidence: Identifiers that when seen, are unlikely to be shared across customers and devices \(e.g. Email, Phone Number, Shopify ID\)
  * _**I have high confidence that this identifier can be used to merge customers together**_
* Low Confidence: Identifiers that are likely to be shared across devices and cannot be confidently associated with one person when a conflict is detected \(e.g. Cookie ID, Browser Push Token\)
  * _**I have low confidence that this identifier can be used to merge customers together**_

#### Example 1 \(Shared Device\)

Your customers object looks like the following:

| Zaius ID \(`zaius_id`\) | Emails \(`emails`\) | Cookie IDs \(`vuids`\) |
| :--- | :--- | :--- |
| 1 | john@gmail.com, john@acme.com | A |
| 2 | jane@gmail.com | B |

You receive an event:

| Event Type | Email \(`email`\) | Cookie ID \(`vuid`\) |
| :--- | :--- | :--- |
| pageview | jane@gmail.com | A |

This event seems to indicate that Jane is using a browser formerly associated with John. Because `Cookie ID` is a Low Confidence identifier, instead of merging these customer's together, we will move the Cookie to now associate it with Jane:

| Zaius ID \(`zaius_id`\) | Emails \(`emails`\) | Cookie IDs \(`vuids`\) |
| :--- | :--- | :--- |
| 1 | john@gmail.com, john@acme.com |  |
| 2 | jane@gmail.com | A, B |

If Zaius merged these customers together, then every single person that shared that computer would be merged into one. So as a safety measure, the `Cookie ID` was moved.

#### Example 2 \(Integration / App\)

Your customers object looks like the following:

| Zaius ID \(`zaius_id`\) | Emails \(`emails`\) | Shopify IDs \(`shopify_mystore_ids`\) |
| :--- | :--- | :--- |
| 1 | john@gmail.com | ABC |
| 2 | john@acme.com | XYZ |

You receive an event:

| Event Type | Email \(`email`\) | Shopify IDs \(`shopify_mystore_ids`\) |
| :--- | :--- | :--- |
| pageview | john@acme.com | ABC |

This event seems to indicate that John's Shopify account has a secondary email. Because `Shopify ID` is a High Confidence identifier, the customer records will be merged together:

| Zaius ID \(`zaius_id`\) | Emails \(`emails`\) | Shopify IDs \(`shopify_mystore_ids`\) |
| :--- | :--- | :--- |
| 1 | john@gmail.com, john@acme.com | ABC, XYZ |

## 

