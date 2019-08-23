# Products

## Overview

The Products object is a "stateful" object, meaning it stores the current state of your product inventory. 

Events & Orders refer to this object to get additional metadata about a product \(e.g. price\) by utilizing the `product_id`

## Fields

### Required Fields

| Display Name | Field Name | Data Type | Description |
| :--- | :--- | :--- | :--- |
| Product ID | product\_id | String | The unique identifier for the product. Referenced from Events. |

### Recommended Fields

| Display Name | Field Name | Data Type | Description |
| :--- | :--- | :--- | :--- |
| Parent Product ID | parent\_product\_id | Text | A reference to another product in the table that groups the products together |
| Name | name | Text | The name of the product displayed to your customers |
| Brand | brand | Text | The brand of the product |
| SKU | sku | Text | The unique SKU of the product |
| UPC | upc | Text | The unique UPC of the product |
| Image URL | image\_url | Text | The URL path to the product's image |
| Price | price | Number | The price of the product |

## Product Events

| `type` | `action` | `product_id` |
| :--- | :--- | :--- |
| product | detail | 123 |
| product | listing | 123 |
| product | add\_to\_cart | 123 |
| product | remove\_from\_cart | 123 |
| product | add\_to\_wishlist | 123 |
| product | remove\_from\_wishlist | 123 |

## Importing & Updating Products

The Products object contains the current state of your product inventory, it does not store historical information about the product. Common reasons to update the Products object:

* Updating Inventory
* Updated Product Images
* Release of New Products

There are a number of methods to update the Products object:

{% hint style="info" %}
Updates to the Products object should adhere to the schema defined above.
{% endhint %}

