# Standard Events

## Account

| `type` | `action` |
| :--- | :--- |
| account | login |
| account | logout |
| account | register |
| account  | update |

## Page View

| `type` | `page` |
| :--- | :--- |
| pageview | /products/12345 |

{% hint style="info" %}
The Web SDK will automatically populate the `page` field when event type is `pageview`
{% endhint %}

## Product

| `type` | `action` | `product_id` |
| :--- | :--- | :--- |
| product | detail | 123 |
| product | listing | 123 |
| product | add\_to\_cart | 123 |
| product | remove\_from\_cart | 123 |
| product | add\_to\_wishlist | 123 |
| product | remove\_from\_wishlist | 123 |

## Orders

{% hint style="danger" %}
Orders are a special type of event. Refer to the [Orders documentation ](../orders/)for more information.
{% endhint %}

## Navigation

| `type` | `action` | `search_term` |
| :--- | :--- | :--- |
| navigation | search | cameras |
| navigation | sort |  |
| navigation | filter |  |

## Ad

| `type` | `action` |
| :--- | :--- |
| advertisement | impression |
| advertisement | click |


