# User Resolution

Zaius utilizes Customer Identifiers \(e.g. `emails`, `vuids`, `push_tokens`\) to merge users together and determine where to associate events.

Including one or more of these identifiers on an event identifies the user who performed the event and allows Zaius to merge users together when enough information becomes available.

Identifiers are categorized into levels of confidence: 

* High Confidence: Identifiers that when seen, are unlikely to be shared across customers and devices \(e.g. Email, Phone Number, Shopify ID\)
  * _**I have high confidence that this identifier can be used to merge customers together**_
* Low Confidence: Identifiers that are likely to be shared across devices and cannot be confidently associated with one person when a conflict is detected \(e.g. Cookie ID, Browser Push Token\)
  * _**I have low confidence that this identifier can be used to merge customers together**_

## Example 1 \(Shared Device\)

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

## Example 2 \(Integration / App\)

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

