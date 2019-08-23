# Lists

Messaging Lists allow grouping of customers for the purposes of tracking their communication preferences. For example, allowing customers to subscribe to a company newsletter or for holiday news. 

## Full Reference

## Quick Reference

{% tabs %}
{% tab title="API" %}
```bash
curl -iX POST \
'https://api.zaius.com/v3/lists/subscriptions' \
-d '[
  {
    "list_id": "sample_list",
    "email": "sample@test.com",
    "subscribed": true
  },
  {
    "list_id": "sample_list2",
    "email": "sample@test.com",
    "subscribed": false
  }
]' \
-H 'Content-Type: application/json' \
-H 'x-api-key: example.apiKey'
```
{% endtab %}

{% tab title="Web" %}
```javascript
// subscribe johnny@zaius.com to newsletter list
zaius.subscribe({list_id: 'newsletter', email: 'johnny@zaius.com'});
// unsubscribe johnny@zaius.com from newsletter list
zaius.unsubscribe({list_id: 'newsletter', email: 'johnny@zaius.com'});
```
{% endtab %}
{% endtabs %}

