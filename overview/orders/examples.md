# Code Examples

{% hint style="warning" %}
Refer to the API and SDK references for complete documentation. 
{% endhint %}

{% api-method method="post" host="https://api.zaius.com/v3" path="/events" %}
{% api-method-summary %}
Purchase
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

{% api-method-parameter name="data.order" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="data.order.items" type="string" required=true %}

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
{
  "type": "order",
  "action": "purchase",
  "identifiers": {
    "email": "bob@gmail.com",
  },
  "data": {
    "order": {
      "order_id": "OR345",
      "total": 109.65,
      "discount": 5.00,
      "subtotal": 103.00,
      "tax": 5.15,
      "shipping": 6.50,
      "coupon_code": "5OFF",
      "items": [
        {
          "product_id": "2045",
          "price": 19.00,
          "quantity": 5,
          "discount": 0.00,
          "subtotal": 95.00
        },
        {
          "product_id": "2091",
          "price": 10.00,
          "quantity": 1,
          "discount": 2.00,
          "subtotal": 8.00
        }
      ]
    }
  }
}
```



{% api-method method="post" host="https://api.zaius.com/v3" path="/events" %}
{% api-method-summary %}
Return, Refund, Cancel
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

{% api-method-parameter name="data.order" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="data.order.items" type="string" required=true %}

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
{
  "type": "order",
  "action": "return", // or refund or cancel
  "identifiers": {
    "email": "bob@gmail.com",
  },
  "data": {
    "order": {
      "order_id": "OR345",
      "total": -10.00
    }
  }
}
```

