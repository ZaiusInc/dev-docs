# Code Examples

## API

{% api-method method="post" host="https://api.zaius.com" path="/v3/customers" %}
{% api-method-summary %}
Update Customers
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to update customer attributes and identifiers.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="z-api-key" type="string" required=true %}
Authentication token.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="attributes" type="object" required=true %}
Attributes to update for the customer.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```javascript
{
    "name": "Cake's name",
    "recipe": "Cake's recipe name",
    "cake": "Binary cake"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Could not find a cake matching this query.
{% endapi-method-response-example-description %}

```javascript
{
    "message": "Ain't no cake like that."
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

