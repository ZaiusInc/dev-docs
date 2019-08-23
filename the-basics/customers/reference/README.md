# Reference

## Full Reference

## Quick Reference

{% tabs %}
{% tab title="API" %}
```bash
curl -iX POST \
https://api.zaius.com/v3/profiles \
-d '{
  "attributes": {
    "first_name": "Johnny",
    "last_name": "Zaius",
    "email": "sample@test.com",
    "phone": "555-867-5309",
    "street1": "123 Fake St",
    "street2": "Apt 101",
    "city": "Boston",
    "state": "MA",
    "zip": "02101",
    "country": "USA",
    "timezone": "America/New_York",
    "gender": "M"
  }
}' \
-H 'Content-Type: application/json' \
-H 'x-api-key: REPLACE_THIS_WITH_API_KEY'
```
{% endtab %}

{% tab title="Web SDK" %}
```javascript
zaius.entity("customer", {
	email: "johnny.zaius@zaius.com",
	first_name: "Johnny",
	last_name: "Zaius",
	gender: "M"
	// any custom fields you've created can be added here
});
```
{% endtab %}
{% endtabs %}

