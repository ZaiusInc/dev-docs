# Reference

## Full Reference

## Quick Reference

{% tabs %}
{% tab title="API" %}
```bash
curl -iX POST \
'https://api.zaius.com/v3/events' \
-H 'x-api-key: example.apiKey'
-d '[
  {
    "type": "product",
    "action": "add_to_cart",
    "identifiers": {
      "email": "tyler@zaius.com"
    },
    "data": {
      "product_id": "123"
    }
  },
  {
    "type": "product",
    "action": "remove_from_cart",
    "identifiers": {
      "email": "tyler@zaius.com"
    },
    "data": {
      "product_id": "123"
    }
  }
]' \
-H 'Content-Type: application/json' \
-H 'x-api-key: example.apiKey'
```
{% endtab %}

{% tab title="Web" %}
```javascript
zaius.event("product", { action: "detail", product_id: "product-2143" });
```
{% endtab %}

{% tab title="iOS" %}
```swift
// sending custom events with custom fields
let event = ZaiusEvent(eventType: "map", action: "explore")

// page is a field available on any event, buy primarily used for pageviews
event["page"] = "map_explorer"

// where map_region is a custom field you added to events in the Zaius App
event["map_region"] = "North America"
Zaius.event(event)
```
{% endtab %}

{% tab title="Android" %}
```java
ZaiusEvent genericEvent = new ZaiusEvent("my_event_type")
  .action("my_action")
  .addField("some_other_key", "some_custom_field_value");
  
Zaius.sendEvent(genericEvent);
```
{% endtab %}

{% tab title="React Native" %}
{% hint style="info" %}
Coming Soon
{% endhint %}
{% endtab %}

{% tab title="Zaius App" %}
```typescript
z.event([{
    type: "yotpo_review", 
    action: "created", 
    identifiers: {
        email: "example@zaius.com"
    }, 
    data: {
        review_id: "12345"
    }
},{
    type: "yotpo_review", 
    action: "created", 
    identifiers: {
        email: "example2@zaius.com"
    }, 
    data: {
        review_id: "56789"
    }
}]);
```
{% endtab %}
{% endtabs %}

