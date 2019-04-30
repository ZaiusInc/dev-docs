# Code Examples

{% api-method method="post" host="https://api.zaius.com/v3" path="/lists/subscriptions" %}
{% api-method-summary %}
Update Subscriptions 
{% endapi-method-summary %}

{% api-method-description %}
Allows clients to update consent \(opt-in vs. opt-out\) for a provided email.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="list\_id" type="string" required=true %}
the list ID of the list to subscribe to or unsubscribe from
{% endapi-method-parameter %}

{% api-method-parameter name="email" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="subscribed" type="boolean" required=true %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "updates": [
        {
            "list_id": "newsletter",
            "email": "johnny@zaius.com",
            "subscribed": true,
            "event": {
                "ts": 123456789
            }
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

```javascript
[{
	"list_id": "newsletter",
	"email": "johnny@zaius.com",
	"subscribed": false,
	"event": {
		"ts": 123456789 // the time that the subscription changed
	}
}]
```

## Web

{% tabs %}
{% tab title="Single List" %}
```javascript
// subscribe johnny@zaius.com to newsletter list
zaius.subscribe({list_id: 'newsletter', email: 'johnny@zaius.com'});

// unsubscribe johnny@zaius.com from newsletter list
zaius.unsubscribe({list_id: 'newsletter', email: 'johnny@zaius.com'});
```
{% endtab %}

{% tab title="Multiple Lists" %}
```javascript
// subscribe johnny@zaius.com to three lists at once
zaius.subscribe({
  list_id: ["newsletter", "promotion", "product_update"], 
  email: "johnny@zaius.com"
});

// unsubscribe johnny@zaius.com from multiple lists at once
zaius.unsubscribe({
  list_id: ["newsletter", "product_update"], 
  email: "johnny@zaius.com"
});
```
{% endtab %}

{% tab title="Custom Event Metadata" %}
```javascript
zaius.subscribe({
  // subscribe Johnny to all lists
  
  list_id: ["newsletter", "promotion", "product_update"],
  email: "johnny@zaius.com",
  
  // update Johnny's record to include his full name
  first_name: "Johnny",
  last_name: "Zaius",
  
  // store information on the subscribe events
  event_custom_field: "my custom value",
  custom_number_field: 123
  
});

// zaius.unsubscribe also fully supports this syntax.
```
{% endtab %}
{% endtabs %}



