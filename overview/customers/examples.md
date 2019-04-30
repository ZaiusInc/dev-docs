# Code Examples

{% hint style="warning" %}
Refer to the API and SDK references for complete documentation.
{% endhint %}

{% api-method method="post" host="https://api.zaius.com/v3/" path="profiles" %}
{% api-method-summary %}
Update Customers
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to update customer attributes and identifiers.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="attributes" type="object" required=true %}
Attributes to update for the customer.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "title": "Accepted",
    "status": 202,
    "timestamp": "2019-04-30T15:22:56.923Z"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

```javascript
[{
    "attributes": {
        "gender": "M",
        "first_name": "Johnny",
        "last_name": "Zaius",
        "email": "johnny@zaius.com"
    }
}]
```

## Web

```javascript
zaius.entity("customer", {
	email: "johnny.zaius@zaius.com",
	first_name: "Johnny",
	last_name: "Zaius",
	gender: "M"
	// any custom fields you've created can be added here
});
```

