# Code Examples

{% hint style="warning" %}
Refer to the API and SDK references for complete documentation. 
{% endhint %}

{% api-method method="post" host="https://api.zaius.com/v3" path="/events" %}
{% api-method-summary %}
Upload Event\(s\)
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get free cakes.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="action" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="identifiers" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="data" type="string" required=true %}

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
    "timestamp": "2019-04-30T15:19:37.997Z"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

```javascript
[{
  "type": "product",
  "action": "add_to_wishlist",
  "identifiers": {
    "email": "bob@gmail.com",
  },
  "data": {
    "product_id": "123"
  }
}]
```

## Web

```javascript
zaius.event("product", {action: "add_to_wishlist", product_id: "123"});
```

