---
description: >-
  Map external data that tracks loyalty points, rewards, and referrals to the
  Zaius schema.
---

# Loyalty & Rewards

{% hint style="danger" %}
This documentation refers to beta functionality and may be subject to frequent changes.
{% endhint %}

## Events

To learn more about events, and how to send them to Zaius, refer to the following:

{% page-ref page="../the-basics/events/" %}

### Event Type: `loyalty`

<table>
  <thead>
    <tr>
      <th style="text-align:left">Event Action</th>
      <th style="text-align:left">Fields</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>points_added</code>
      </td>
      <td style="text-align:left"><code>previous_loyalty_points_balance<br />current_loyalty_points_balance<br />loyalty_change_in_points</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>points_removed</code>
      </td>
      <td style="text-align:left"><code>previous_loyalty_points_balance<br />current_loyalty_points_balance<br />loyalty_change_in_points</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>referral_completed</code>
      </td>
      <td style="text-align:left"><code>loyalty_referral_code_id<br />loyalty_referred_customer_email</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>referral_link_shared</code>
      </td>
      <td style="text-align:left"><code>loyalty_referral_code_id<br />loyalty_referred_customer_email</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>tier_earned</code>
      </td>
      <td style="text-align:left"><code>previous_loyalty_tier_id<br />current_loyalty_tier_id</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>tier_lost</code>
      </td>
      <td style="text-align:left"><code>previous_loyalty_tier_id<br />current_loyalty_tier_id</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>yotpo_coupon_awarded</code>
      </td>
      <td style="text-align:left">
        <p><code>yotpo_redemption_id</code>
        </p>
        <p><code>yotpo_redemption_option_id</code>
        </p>
        <p><code>yotpo_perk_id</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>yotpo_coupon_redeemed</code>
      </td>
      <td style="text-align:left">
        <p><code>yotpo_redemption_id</code>
        </p>
        <p><code>yotpo_redemption_option_id</code>
        </p>
        <p><del><code>yotpo_perk_id</code></del>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>yotpo_coupon_reminder</code>
      </td>
      <td style="text-align:left">
        <p><code>yotpo_redemption_option_id</code>
        </p>
        <p><code>yotpo_points_needed</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>## Schema

To learn more about creating Objects, Fields and Relationships and then updating newly created schema, refer to the following:

### Objects

| Object Name | Description |
| :--- | :--- |
| Loyalty Tiers \(`loyalty_tiers`\) | Stores data about available Loyalty Tiers that customers can attain via loyal actions. |
| Loyalty Referral Codes \(`loyalty_referral_codes`\) | Stores all available referral codes, metrics on sharing,  |

### Fields

#### Events \(events\)

| Field Name | Type | Description |
| :--- | :--- | :--- |
| `previous_loyalty_tier_id` | string | The ID of the tier that the customer was previously associated with. |
| `current_loyalty_tier_id` | string | The ID of the tier that the customer is now associated with. |
| `previous_loyalty_points_balance` | number | The loyalty points balance of the customer before this event. |
| `current_loyalty_points_balance` | number | The loyalty points balance of the customer after this event. |
| `loyalty_change_in_points` | number | The total change in loyalty points due to this event. |
| `loyalty_referral_code_id` | string | The unique referral code that this event applies to. |
| `loyalty_referred_customer_email` | string | The email of the customer that was referred. |

#### Customers \(customers\)

To learn more about Customers in Zaius, refer to the following:

{% page-ref page="../the-basics/customers/" %}

| Field Name | Type | Description |
| :--- | :--- | :--- |
| `loyalty_points_balance` | number | The number of loyalty points that the customer currently has. |
| `loyalty_referral_code_id` | string | The unique Referral Code ID assigned to the customer. |
| `loyalty_tier_id` | string | The ID of the Loyalty Tier that the customer is associated with. |
| `loyalty_profile_created_at` | ts | The date & time that the customer record was created in the connected loyalty app. |
| `loyalty_profile_updated_at` | ts | The date & time that the customer record was last updated in the connected loyalty app. |
| `loyalty_is_enrolled_member` | boolean | If true, the customer is currently enrolled in your loyalty program. |

#### Loyalty Tiers \(loyalty\_tiers\)

| Field Name | Type | Description |
| :--- | :--- | :--- |
| `loyalty_tier_id` | string | The unique identifier for a Loyalty Tier. |
| `name` | string | The name of the Loyalty Tier. |
| `rank` | number | The numeric rank of this Loyalty tier relative to other Loyalty Tiers. |
| `required_dollar_spend` | number | The amount of dollars required to be spent by a customer to reach this Loyalty Tier. |
| `description` | string | A description of this Loyalty Tier. |
| `required_points` | number | The number of points required to reach this Loyalty Tier. |
| `required_purchases` | number | The number of purchases required to reach this Loyalty Tier. |

#### Loyalty Referral Codes \(loyalty\_referral\_codes\)

| Field Name | Type | Description |
| :--- | :--- | :--- |
| `loyalty_referral_code_id` | string | The unique referral code assigned to a customer. |
| `total_shares` | number | The number of times that this referral code has been shared. |
| `order_conversions_count` | number | The number of orders that have resulted from this referral code. |
| `order_conversions_amount` | number | The dollar amount of the number of orders that have resulted from this referral code. |
| `expiration_ts` | ts | The date & time that the referral code expires, if it does. |
| `is_expired` | boolean | Determines whether or not the referral code is expired. |
| `total_clicks` | number | The total number of clicks of the shared referral code URL. |
| `referral_url` | string | The unique referral code URL. |

### Relationships

| Name | Parent | Child |
| :--- | :--- | :--- |
| `loyalty_referral_code` | `events.loyalty_referral_code_id` | `loyalty_referral_codes.loyalty_referral_code_id` |
| `previous_loyalty_tier` | `events.previous_loyalty_tier_id` | `loyalty_tiers.loyalty_tier_id` |
| `current_loyalty_tier` | `events.current_loyalty_tier_id` | `loyalty_tiers.loyalty_tier_id` |
| `loyalty_referral_code` | `customers.loyalty_referral_code_id` | `loyalty_referral_codes.loyalty_referral_code_id` |
| `loyalty_tier` | `customers.loyalty_tier_id` | `loyalty_tiers.loyalty_tier_id` |

