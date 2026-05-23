# Shopify Connector Product Mapping Cheat Sheet

_Updated: May 22, 2026_

### A reference guide for Shopify connector versions 3 and higher

Below is a summary of the current field mapping from Counterpoint items to Shopify products, also referred to as the **Items Up** mapping. This includes some relevant (but not all) configuration options, as well as some notes on preferences and limitations. 

## Table of Contents

- [Product Fields](#product-fields)
  - [Product Title](#product-title)
  - [SKU](#sku)
  - [Barcode](#barcode)
  - [Handle (URL Slug)](#handle-url-slug)
  - [Product Vendor](#product-vendor)
  - [Product Type](#product-type)
  - [Tags](#tags)
  - [Product Description](#product-description)
- [Quantity & Pricing](#quantity--pricing)
  - [Quantity](#quantity)
  - [Out-of-Stock Quantity](#out-of-stock-quantity)
  - [Continue Selling When Out of Stock](#continue-selling-when-out-of-stock)
  - [Track Quantity](#track-quantity)
  - [Price](#price)
  - [Compare At Price](#compare-at-price)
- [Publishing / Sales Channel Visibility](#publishing--sales-channel-visibility)
  - [Sales Channel – Online Store](#sales-channel--online-store)
  - [Sales Channel – Point of Sale](#sales-channel--point-of-sale)
- [Shipping](#shipping)
  - [This is a physical product / Requires shipping](#this-is-a-physical-product--requires-shipping)
  - [Shipping Weight](#shipping-weight)
  - [Shipping Unit](#shipping-unit)
- [Product Variants](#product-variants)
  - [Counterpoint Item Tracking Method – Normal vs. Gridded](#counterpoint-item-tracking-method--normal-vs-gridded)
  - [Counterpoint Item Alternate Units](#counterpoint-item-alternate-units)
- [Metafields](#metafields)
  - [Product Metafields](#product-metafields)
- [Fields Not Sent](#fields-not-sent)

---

## Product Fields

### Product Title

- Can be sourced from **Description**, **Long Description**, or any of the three **Additional Description** fields.
- Configurable:
  - Send only on first sync (allows Shopify to manage titles).
  - OR send on every sync (Counterpoint remains system of truth).
- Most clients prefer managing product titles directly on Shopify.

### SKU

- Always sourced from the Counterpoint **Item Number**. It is critical that the Counterpoint `ITEM_NO` always matches Shopify `SKU`.
- Counterpoint is system of truth (overwrites on every sync).

### Barcode

- Sourced from a barcode on the barcode table but configurable to send the **first barcode of a selected type** (e.g., `ITEM`, `UPC`, `SKU`).
- Counterpoint is system of truth (overwrites on every sync).

### Handle (URL Slug)

- Sourced from Counterpoint item fields and **configurable to send a calculated value** such as item number, description + item number, long description + item number, etc.
- Configurable:
  - Send only on first sync (allows Shopify to manage handles).
  - OR send on every sync (Counterpoint as system of truth).

### Product Vendor

- Sourced from **Shopify Item Record** field for **Product Vendor** (or a default value obtained from Product Vendor Default configuration setting).
- Counterpoint is system of truth (overwrites on every sync).

### Product Type

- If desired, configurable to send Counterpoint **Category Code** (`CATEG_COD`) to populate product type on Shopify.
- Most clients prefer managing product type directly on Shopify.

### Tags

- If desired, this is sourced from the **Shopify Items Record** via a **comma-delimited text box**.
- Caveats:
  - Typing/consistency errors are common.
  - Tags deleted in Counterpoint are not removed on Shopify.
- Most clients prefer managing tags directly on Shopify.

### Product Description

- If desired, this is sourced from the **Shopify Items Record** via an **HTML Description text box**.
- Configurable:
  - Send only on first sync (allows Shopify to manage product descriptions).
  - OR send on every sync (Counterpoint as system of truth).
- Most clients prefer managing product descriptions directly on Shopify using the WYSIWYG editor.

### [↑ Back to Top](#table-of-contents)

---

## Quantity & Pricing

### Quantity

- Sourced from either **quantity available** or **quantity on hand** (depending on configuration options).
- Counterpoint is system of truth (overwrites on every sync).

### Out-of-Stock Quantity

- This is a configurable quantity threshold **used to reduce the quantity** reported to Shopify.

### Continue Selling When Out of Stock

- Shopify-specific checkbox (defined by Shopify).
- Counterpoint is system of truth (overwrites on every sync).

### Track Quantity

- Shopify-specific checkbox (defined by Shopify).
- Counterpoint is system of truth (overwrites on every sync).

### Price

- Sourced from one of the price fields in Counterpoint.
- Configurable:
  - Price 1
  - Price 2
  - Price 3
  - Price 4 (if advanced pricing is enabled)
  - Price 5 (if advanced pricing is enabled)
  - Price 6 (if advanced pricing is enabled)
  - Regular Price
  - Calculated Price (requires adherence to very specific price rule parameters)
- Counterpoint is system of truth (overwrites on every sync).

### Compare At Price

- Sourced from one of the price fields in Counterpoint.
- Configurable:
  - Price 1
  - Price 2
  - Price 3
  - Price 4 (if advanced pricing is enabled)
  - Price 5 (if advanced pricing is enabled)
  - Price 6 (if advanced pricing is enabled)
  - Regular Price
  - Calculated Price (requires adherence to very specific price rule parameters)
- Counterpoint is system of truth (overwrites on every sync).

### [↑ Back to Top](#table-of-contents)

---

## Publishing / Sales Channel Visibility

### Sales Channel – Online Store

- Corresponds to Shopify’s Online Store sales channel.
- Requirements for Product Visibility:
  - Online Store channel must be enabled.
  - The product must also be active in Shopify.
- Counterpoint is system of truth (overwrites on every sync).

### Sales Channel – Point of Sale

- Corresponds to Shopify’s Point of Sale sales channel. Used by some clients for off-site sales. 
- Requirements for Product Visibility:
  - POS channel must be enabled. If this channel is not used, this checkbox can be ignored.
  - The product must also be active in Shopify.
- Counterpoint is system of truth (overwrites on every sync).

**Note:** Additional sales channels are managed directly on Shopify.

### [↑ Back to Top](#table-of-contents)

---

## Shipping

### This is a Physical Product / Requires shipping

- Shopify-specific checkbox (defined by Shopify).
- Counterpoint is system of truth (overwrites on every sync).

### Shipping Weight

- Sourced from **Shopify Item Record** field for **Shipping Weight** (not from the item record weight).
- Counterpoint is system of truth (overwrites on every sync).

### Shipping Unit

- Sourced from **Shopify Item Record** field for **Shipping Unit**.
- Configurable:
  - `lb`
  - `oz`
  - `kg`
  - `g`
- Counterpoint is system of truth (overwrites on every sync).

### [↑ Back to Top](#table-of-contents)

---

## Product Variants

### Counterpoint Item Tracking Method – Normal vs. Gridded

- If the Counterpoint tracking method is `Normal`, the product is synced to Shopify without variants.
- If the tracking method is `Gridded`, the product is synced to Shopify with variants for each grid cell.
- Note: All grid cells will be sent as variants. Currently, there is no way to selectively limit which grid cells are sent.

### Counterpoint Item Alternate Units

- If the Counterpoint item has alternate units, a flag for each unit will be available in Counterpoint.
  - When a unit’s flag is enabled, that unit will be sent to Shopify as a product variant.
  - Note: If the item is gridded, the grid cells will be sent to Shopify as the variants. In that case, the alternate units cannot be sent.

### [↑ Back to Top](#table-of-contents)

---

## Metafields

### Product Metafields

- Supported via a custom mapping table.
- Nearly any field from the Counterpoint Item record can be pushed to Shopify as-is.
- Enabling this feature is billable. Contact Rapid for pricing information.

### [↑ Back to Top](#table-of-contents)

---

## Fields Not Sent

The list below is not intended to be inclusive but rather to call out some specific limitations that clients frequently inquire about. These fields are never sent from Counterpoint to Shopify:

- **Category**
  - In Shopify, this refers to Tax Category.
  - Must be selected within Shopify.

- **Category Metafields**
  - Populated by Shopify directly based on the chosen tax category.

- **Collections**
  - While a single collection can be sourced from the Counterpoint subcategory (if configured), all other collections must be managed directly on Shopify.

- **Images/Media**
  - Images and other media must be managed directly on Shopify.

- **Status**
  - While the initial status is set by the connector (typically configured to draft), subsequent changes must be managed directly on Shopify.
  - The only exception is when a Shopify Item Record is deleted in Counterpoint, that can trigger the Shopify product to be archived (if configured to do so).

### [↑ Back to Top](#table-of-contents)
