# CSV Upload

## File Formatting

* Values must be `UTF-8` encoded
* Values must be comma delimited
* Records must end with a newline \(`\n`\)
* Any value may be optionally quoted via double quote \(`"`\) characters
* Any field containing a double quote must be quoted. The escape character for an embedded quote is a second quote character. \(For example: `"Customers think this product is ""Amazing!"""`\)
* Each record must contain exactly the same number of fields as the header does
* No carriage return \(`\r`\) or newline \(`\n`\) may exist within a record
* Timestamps must be formatted as ISO 8601 format or unix epoch \(seconds since January 1, 1970\). Examples: `1435708800`, `2015-07-01T00:00:00-00:00`, `2015-07-01T12:30:00-07:00`. Note: If time and time zone are not provided the time is assumed be 12am UTC.

## File Naming

| Object | File Name Prefix |
| :--- | :--- |
| Products | `zaius_products` |
| Customers | `zaius_customers` |
| Orders | `zaius_orders` |
| Events | `zaius_events` |
| Lists | `zaius_list` |

## Examples & Samples

{% hint style="info" %}
The files below are only basic examples. 

Refer to the Zaius schema section to learn about all available default fields and creating custom fields & objects.
{% endhint %}

### Customers

{% file src="../.gitbook/assets/zaius\_customers\_example.csv" %}

### Products

{% file src="../.gitbook/assets/zaius\_products\_example.csv" %}

### Orders

{% file src="../.gitbook/assets/zaius\_orders\_example.csv" %}

{% hint style="info" %}
Refer to[ Orders documentation](../zaius-schema/orders.md#fields) for field descriptions and data types.
{% endhint %}

* Shared Fields
  * action
    * value should be one of `purchase | refund | return | cancel`
  * **order\_id \(REQUIRED\)**
  * **ts** **\(REQUIRED\)**
* Order Summary Fields
  * total
  * discount
  * subtotal
  * tax
  * shipping
  * coupon\_code
  * first\_name
  * last\_name
  * bill\_address
  * ship\_address

{% hint style="danger" %}
Order Line Item fields \(and the associated events\) cannot be updated in the future, only summary fields \(for refunds, returns, cancellations\).
{% endhint %}

* Order Line Item Fields \(one row per line item\) - unavailable for `refund`, `return` & `cancel`
  * item\_product\_id
  * item\_sku
  * item\_price
  * item\_quantity
  * item\_discount
  * item\_subtotal

{% hint style="success" %}
Prefix all custom event fields with `item_` to indicate the field exists on the Event object, otherwise it will be assumed you attempting to update the Orders object.
{% endhint %}

### Events

{% file src="../.gitbook/assets/zaius\_events\_example.csv" %}

### Lists

{% hint style="warning" %}
**Uploading a List file without an "action" column assumes a subscription for each email**
{% endhint %}

#### Upload to Single List

{% file src="../.gitbook/assets/zaius\_list\_yourlistidhere.csv" %}

**Upload to Multiple Lists**

{% file src="../.gitbook/assets/zaius\_list\_example.csv" %}

### Consent

