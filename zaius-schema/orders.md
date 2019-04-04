# Orders

## Overview

Orders in Zaius are created and updated via Events.

{% hint style="info" %}
Each Order generates an order purchase event **per order line item.** 

i.e. An order with three line items would generate three order events.
{% endhint %}

Top-level information about the order \(e.g. billing address, coupon, tax\) are stored in the Orders object and linked to order events on Order ID \(`order_id`\). 

## Fields

### Order Events

{% hint style="danger" %}
All Zaius events \(and, as a result, order line items\) are immutable, **meaning that cannot be changed once uploaded to Zaius.** If you need to process returns, refunds or cancellations [please refer to the relevant documentation.](orders.md#returns-refunds-and-cancellations)
{% endhint %}

| Display Name | Field Name | Data Type | Description |
| :--- | :--- | :--- | :--- |
| Order ID | order\_id | Text | The unique identifier related to this order. |
| Product ID | product\_id | Text | The unique identifier for the order line item. |
| Order Item: Price | price | Number | The price for the order item. |
| Order Item: Quantity | quantity | Number | The number of items purchased. |
| Order Item: Discount | discount | Number | The discount \(if any\) for the given line item. |
| Order Item: Subtotal | subtotal | Number | The calculated subtotal for the given product and quantity.  |

### Order Object

| Display Name | Field Name | Data Type | Description |
| :--- | :--- | :--- | :--- |
| Order ID | order\_id | Text | The unique identifier related to this order. |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |

## Importing Historical Orders

## Returns, Refunds & Cancellations



1. `return` - a customer has returned some or all of the items in an order and been refunded.
2. `refund` - a customer has been issued a refund for a given order. Semantically, refunds are treated the same as returns in Zaius \(e.g., negative impact on revenue\). You can use either. Use both if you want to distinguish between inventory being returned to you \(a return\) and just money being issued to the original purchaser \(a refund\). If inventory is returned and money is issued back to the purchaser, Zaius recommends using the 'return' order action.
3. `cancel` - a customer has canceled their order. The order purchase and cancel events remain in Zaius \(e.g., on the customer profile page, and for segmentation\), and revenue is negatively impacted, but the order no longer figures in to determining the customer's lifecycle. This is in contrast to returns and refunds, where the order still counts in determining the order count, and thus lifecycle, for a customer.

Note that order returns, refunds, and cancels can be partial. Zaius determines if they are partial by tracking whether the running tally of the order's subtotal field across all events is greater than zero \(partial\) or not. 

{% hint style="warning" %}
Zaius allows the subtotal and total fields for an order to go negative \(e.g. to support purchase and refund events coming in out of order, or to support cases where the refund amount legitimately exceeds the purchase amount\). **Be cautious not to issue duplicate refund, return, and cancel events.**
{% endhint %}

