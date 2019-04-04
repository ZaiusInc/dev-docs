# Products

## Overview

The Products object is a "stateful" object, meaning it stores the current state of your product inventory. 

Events & Orders refer to this object to get additional metadata about a product \(e.g. price\) by utilizing the `product_id`

## Importing & Updating Products

The Products object contains the current state of your product inventory, it does not store historical information about the product. Common reasons to update the Products object:

* Updating Inventory
* Updated Product Images
* Release of New Products

There are a number of methods to update the Products object:

{% page-ref page="../../bulk-imports/s3-upload.md" %}

{% page-ref page="../../bulk-imports/sftp-upload.md" %}

{% hint style="info" %}
Updates to the Products object should adhere to the schema defined below
{% endhint %}

## Fields

### Required Fields

| Display Name | Field Name | Data Type | Description |
| :--- | :--- | :--- | :--- |
| Product ID | product\_id | String | The unique identifier for the product. Referenced from Events. |

### Recommended Fields

| Display Name | Field Name | Data Type | Description |
| :--- | :--- | :--- | :--- |
| Parent Product ID | parent\_product\_id | Text |  |
| Name | name | Text |  |
| Brand | brand | Text |  |
| SKU | sku | Text |  |
| UPC | upc | Text |  |
| Image URL | image\_url | Text |  |
| Price | price | Number |  |

