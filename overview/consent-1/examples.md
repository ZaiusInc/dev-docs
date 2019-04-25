# Code Examples

{% api-method method="post" host="https://api.zaius.com/v3" path="/lists" %}
{% api-method-summary %}
Update Consent 
{% endapi-method-summary %}

{% api-method-description %}
Allows clients to update consent \(opt-in vs. opt-out\) for a provided email.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="email" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="opted\_in" type="boolean" required=false %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

```javascript
{
	"opted_in": true,
	"email": "johnny@zaius.com"
}
```

## Web

{% tabs %}
{% tab title="Opt-In" %}
```javascript
zaius.subscribe({list_id: 'zaius_all', email: 'johnny@zaius.com'});
```
{% endtab %}

{% tab title="Opt-Out" %}
```javascript
zaius.unsubscribe({list_id: 'zaius_all', email: 'johnny@zaius.com'});
```
{% endtab %}
{% endtabs %}



