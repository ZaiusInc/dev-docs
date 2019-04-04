# Orders

## Overview

Orders in Zaius are created and updated via Events. 

{% hint style="info" %}
Each Order generates an order purchase event **per order line item.**
{% endhint %}

Top-level information about the order \(e.g. billing address, coupon, tax\) are stored in the Orders object and linked to order events on Order ID \(`order_id`\). 

## Fields

### Order Events

{% hint style="danger" %}
All Zaius events are immutable, **meaning that cannot be changed once uploaded to Zaius.** If you need to process returns, refunds or cancellations [please refer to the relevant documentation.](orders.md#returns-refunds-and-cancellations)
{% endhint %}

| Display Name | Field Name | Data Type | Description |
| :--- | :--- | :--- | :--- |
| Order ID | order\_id | Text |  |
| Product ID | product\_id | Text |  |
| Order Item: Price | price | Number |  |
| Order Item: Quantity | quantity | Number |  |
| Order Item: Discount | discount | Number |  |
| Order Item: Subtotal | subtotal | Number |  |

### Order Object



## Importing Historical Orders

## Returns, Refunds & Cancellations

