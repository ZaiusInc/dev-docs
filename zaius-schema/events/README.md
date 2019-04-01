# Events

Events describe Customer actions. Events are composed of a Type, Action and additional metadata via object fields. 

The Event Type is a categorical name associated with the event. An Action is an activity a user did. For example, 'order' and 'product are Event Types 'purchase', 'return', 'add\_to\_cart', 'detail' would be actions.

{% hint style="info" %}
At minimum, events require an event type and an identifier to associate the event with a customer.
{% endhint %}

## Standard vs. Custom

Zaius has two types of events: **Standard** & **Custom**.

### Standard Events

**Standard Events** are events that have a pre-defined event type/action and expected by Zaius to be accompanied with certain fields. 

{% page-ref page="standard-events.md" %}

### Custom Events

**Custom Events** are events that you create the event type/action for and choose what fields to use and/or create.

#### Example

| type | action | venue\_name |
| :--- | :--- | :--- |
| venue | visited | TD Garden |


