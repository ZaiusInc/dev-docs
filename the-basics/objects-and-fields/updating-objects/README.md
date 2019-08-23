# Updating Objects & Fields

## Full Reference

## Quick Reference

{% tabs %}
{% tab title="API" %}
```bash
curl -iX POST \
https://api.zaius.com/v3/objects/products \
-d '[
  {
    "object_id": "myObjectId",
    "some_custom_field": "myValue"
  },{
    "object_id": "myObjectId_2",
    "some_custom_field": "anotherValue"
  }
]' \
-H 'Content-Type: application/json' \
-H 'x-api-key: example.apiKey'
```
{% endtab %}

{% tab title="Zaius App" %}
```typescript
z.object({type: "zendesk_tickets", {ticket_id: "12345", status: "open"});

z.object({type: "zendesk_tickets", [{ticket_id: "12345", status: "open"}, {ticket_id: "56789", status: "closed"}]);
```
{% endtab %}
{% endtabs %}

