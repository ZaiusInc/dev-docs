# Get Started

## How does Zaius store data?

At the core of Zaius are **Customers**. 

{% page-ref page="the-basics/customers/" %}

Every customer has a record of **Events** that they have performed over time. Every event is classified by a **Event Type** \(e.g. order, product, email\) and **Event Action** \(e.g. purchase, view, open\) and additional metadata stored in **Fields** \(e.g. product\_id\). 

{% page-ref page="the-basics/events/" %}

Customers and Events in Zaius are considered **Objects**, similar to a spreadsheet or a database table. Objects consist of **Fields** to store metadata and information about the data within the object. 

{% hint style="info" %}
An example: the Event object has a `ts` field to store the time at which an event happened & the Customer object has an `email` field to store the last seen email for the customer.
{% endhint %}

Zaius supports the addition of **Custom Fields** and **Custom Objects** to support customization of the schema to meet unique business needs \(e.g. a Concert Tickets object\).

{% page-ref page="the-basics/objects-and-fields/" %}

## What is a Zaius account?

The way Zaius segregates data is via **Accounts**. Every account is provided a unique **Tracker ID** \(also referred to as a Public API Key\) to separate its data from other Zaius client data.

{% hint style="info" %}
 All APIs and SDKs use Tracker ID to determine where to send data.
{% endhint %}

Common reasons to use multiple Zaius accounts include:

* Multiple Brands
* International Stores
* Business uses multiple eCommerce instances \(e.g. multiple Shopify stores\)

