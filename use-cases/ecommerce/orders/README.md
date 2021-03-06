# Orders

## Overview

Orders in Zaius are created and updated via Events.

{% hint style="info" %}
Each Order generates an order purchase event **per order line item.** 

i.e. An order with three line items would generate three order events.
{% endhint %}

Top-level information about the order \(e.g. billing address, coupon, tax\) are stored in the Orders object and linked to order events on Order ID \(`order_id`\). 

## Fields

### Order Line Items \(Events\)

{% hint style="danger" %}
All Zaius events \(and, as a result, order line items\) are immutable, **meaning that cannot be changed once uploaded to Zaius.** If you need to process returns, refunds or cancellations [please refer to the relevant documentation.](./#returns-refunds-and-cancellations)
{% endhint %}

<table>
  <thead>
    <tr>
      <th style="text-align:left">Display Name</th>
      <th style="text-align:left">Field Name</th>
      <th style="text-align:left">Data Type</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Order ID</td>
      <td style="text-align:left">order_id</td>
      <td style="text-align:left">Text</td>
      <td style="text-align:left">The unique identifier related to this order.</td>
    </tr>
    <tr>
      <td style="text-align:left">Product ID</td>
      <td style="text-align:left">product_id</td>
      <td style="text-align:left">Text</td>
      <td style="text-align:left">The unique identifier for the order line item.</td>
    </tr>
    <tr>
      <td style="text-align:left">Order Item: Price</td>
      <td style="text-align:left">price</td>
      <td style="text-align:left">Number</td>
      <td style="text-align:left">The price for the order item.</td>
    </tr>
    <tr>
      <td style="text-align:left">Order Item: Quantity</td>
      <td style="text-align:left">quantity</td>
      <td style="text-align:left">Number</td>
      <td style="text-align:left">The number of items purchased.</td>
    </tr>
    <tr>
      <td style="text-align:left">Order Item: Discount</td>
      <td style="text-align:left">discount</td>
      <td style="text-align:left">Number</td>
      <td style="text-align:left">The discount (if any) for the given line item.</td>
    </tr>
    <tr>
      <td style="text-align:left">Order Item: Subtotal</td>
      <td style="text-align:left">subtotal</td>
      <td style="text-align:left">Number</td>
      <td style="text-align:left">
        <p>The calculated subtotal for the given product and quantity.</p>
        <p></p>
        <p><code>subtotal = (price - discount) * quantity</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>### Order Summary \(Orders Object\)

| Display Name | Field Name | Data Type | Description |
| :--- | :--- | :--- | :--- |
| Order ID | order\_id | Text | The unique identifier related to this order.Subtotal |
| Tax | tax | Number |  |
| Discount | discount | Number |  |
| Shipping | shipping | Number |  |
| Subtotal | subtotal | Number |  |
| Total | total | Number | `order_total = (sum of (subtotal-discount) for each line item)` |
| Billing Address | bill\_address | Text | The billing address for the order, lines delimited by commas |
| Shipping Address | ship\_address | Text | The shipping address for the order, lines delimited by commas |
| Phone | phone | Text | The phone number for the order in [E.164 format](https://en.wikipedia.org/wiki/E.164) |
| Coupon Code | coupon\_code | Text |  |
| First Name | first\_name | Text |  |
| Last Name | last\_name | Text |  |
| Name | name | Text |  |
| Email | email | Text |  |

## Importing Historical Orders

The recommended method of sending historical Order data is to send the data [via API](https://api.developer.zaius.com/#tag/Events/operation/insertEvents) or CSV. CSV files can be [uploaded in the UI](https://docs.developers.zaius.com/client-onboarding/importing-data/csv) or [via Amazon \(AWS\) S3](https://docs.developers.zaius.com/client-onboarding/importing-data/amazon-s3). The fields utilized in either method adhere to the schema outlined above.

## Returns, Refunds & Cancellations

To process returns, refunds and cancellations, send an event with an event type of `order` and one of the following event actions:

{% hint style="info" %}
The following event actions treat `-30` and `30` as a subtotal identically. They both create new events that subtract from the original order total.
{% endhint %}

1. `return` - a customer has returned some or all of the items in an order and been refunded.
2. `refund` - a customer has been issued a refund for a given order. Semantically, refunds are treated the same as returns in Zaius \(e.g., negative impact on revenue\). You can use either. Use both if you want to distinguish between inventory being returned to you \(a return\) and just money being issued to the original purchaser \(a refund\). If inventory is returned and money is issued back to the purchaser, Zaius recommends using the 'return' order action.
3. `cancel` - a customer has canceled their order. The order purchase and cancel events remain in Zaius \(e.g., on the customer profile page, and for segmentation\), and revenue is negatively impacted, but the order no longer figures in to determining the customer's lifecycle. This is in contrast to returns and refunds, where the order still counts in determining the order count, and thus lifecycle, for a customer.

Note that order returns, refunds, and cancels can be partial. Zaius determines if they are partial by tracking whether the running tally of the order's subtotal field across all events is greater than zero \(partial\) or not. 

{% hint style="warning" %}
Zaius allows the subtotal and total fields for an order to go negative \(e.g. to support purchase and refund events coming in out of order, or to support cases where the refund amount legitimately exceeds the purchase amount\). **Be cautious not to issue duplicate refund, return, and cancel events.**
{% endhint %}

