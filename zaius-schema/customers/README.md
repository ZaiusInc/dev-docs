# Customers

Customers are at the core of Zaius. Customers are composed of fields that are typically grouped into one of two groups: attributes or identifiers.

{% api-method method="post" host="https://api.zaius.com" path="/v3/profiles" %}
{% api-method-summary %}
Update Customer
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="attributes" type="object" required=true %}
an object containing all the attributes of the customer to update
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
    "attributes": {
        "gender": "M",
        "first_name": "Johnny",
        "last_name": "Zaius",
        "email": "johnny@zaius.com"
    }
}
```

## Web SDK

```javascript
zaius.entity("customer", {
	email: "johnny.zaius@zaius.com",
	first_name: "Johnny",
	last_name: "Zaius",
	gender: "M"
	// any custom fields you've created can be added here
});
```

## Fields

### Identifiers

| Display Name | Field Name | Description |
| :--- | :--- | :--- |
| Zaius ID | `zaius_id` | A unique, Zaius-generated identifier, that represents a customer |
| Last Seen Email | `email` | The last seen email associated with this customer. |
| Last Seen Cookie ID | `vuid` | Zaius' unique Cookie / Device ID, used on web and mobile to identify anonymous customers. |

### App Identifiers

Many apps / integrations \(e.g. Shopify or Magento\) create identifiers that map to an external system \(e.g. Shopify ID\) to allow for improved [user resolution](user-resolution.md), troubleshooting, and transparency. Some examples:

| Display Name | Description |
| :--- | :--- |
| Last Seen Shopify ID \(mystore\) | shopify\_mystore\_id |
| Last Seen Zendesk ID \(mysupporteam\) | zendesk\_mysupportteam\_id |

{% hint style="info" %}
Every identifier is also stored as an array in the plural form \(with a max of 25 for each identifier type\).

For example, all the known emails for a customer are stored in the a field called Emails \(`emails`\) and Cookie ID are stored as `vuids`. 
{% endhint %}

### Custom Identifiers

If you have an external database, data lake, or system \(e.g. a point-of-sale system\) that uses a unique identifier to track customers, Zaius supports the creation of Custom Identifiers to ensure that all known information about your customers is tracked and you're able to reconcile information within Zaius with the external data source.

{% hint style="info" %}
Custom Identifiers are considered when merging customers together. Read more in the [User Resolution](user-resolution.md) section.
{% endhint %}

{% hint style="warning" %}
At this time, Custom Identifiers must be created by a member of the Zaius Customer Success team. Contact your CSM or Support via email or chat to learn more.
{% endhint %}

### Attributes

| Display Name | Field Name | Description |
| :--- | :--- | :--- |
| First Name | `first_name` |  |
| Last Name | `last_name` |  |
| Gender | `gender` | Stored as `M`, `F` |
| Time Zone | `timezone` | Timezone in [IANA format](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) \(e.g. `America/New_York`\) |
| Image URL | `image_url` |  |
| Phone Number | `phone` | Phone number in [E.164 format](https://en.wikipedia.org/wiki/E.164) \(e.g. `+15552108050`\) |
| Primary Line | `street1` |  |
| Secondary Line | `street2` |  |
| City | `city` |  |
| State | `state` |  |
| ZIP / Postal Code | `zip` |  |
| Country | `country` | Country in [ISO-3166-1 format](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-3) |

## Custom Fields

{% page-ref page="../custom-schema.md" %}

