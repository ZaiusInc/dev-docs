# Events

Events describe Customer actions. Events are composed of a Type, Action and additional metadata via fields on the event.

The **Event Type** is a categorical name associated with the event. 

The **Event Action** is the activity a user did within that event type.

For example, `order` and `product` are Event Types while `purchase`, `return`, `add_to_cart`, `detail` would be actions.

{% hint style="info" %}
At minimum, events require an event type and an identifier to associate the event with a customer.
{% endhint %}

## Standard vs. Custom

Zaius has two types of events: **Standard** & **Custom**.

## Standard Events

**Standard Events** are events that have a pre-defined event type/action and expected by Zaius to be accompanied with certain fields. **The usage of these events makes the usage of Zaius simpler for common use cases.**

### Standard Use Case Events

For common events, based on use case \(e.g. products, orders, ratings, surveys, loyalty, etc\), refer to the appropriate use case documentation:

{% page-ref page="../../use-cases/marketing/" %}

{% page-ref page="../../use-cases/ecommerce/" %}

{% page-ref page="../../use-cases/loyalty-and-offers.md" %}

### Standard Generic Events

#### Account Events

| `type` | `action` |
| :--- | :--- |
| account | login |
| account | logout |
| account | register |
| account  | update |

#### Page View Events

| `type` | `page` |
| :--- | :--- |
| pageview | /products/12345 |

{% hint style="info" %}
The Web SDK will automatically populate the `page` field when event type is `pageview`
{% endhint %}

#### Navigation Events

| `type` | `action` | `search_term` |
| :--- | :--- | :--- |
| navigation | search | cameras |
| navigation | sort |  |
| navigation | filter |  |

### Custom Events

**Custom Events** are events that you create the event type/action for and choose what fields to use and/or create.

#### Example

| type | action | venue\_name |
| :--- | :--- | :--- |
| venue | visited | TD Garden |

To begin sending events to Zaius, refer to the specific documentation for your platform:

{% page-ref page="reference/" %}

