# Shopify Product Source of Truth Reference

## Purpose

This document provides a quick reference for determining whether Counterpoint or Shopify acts as the system of truth for specific product fields during Shopify product creation and update operations.

Clients commonly ask:

> "If a value is changed directly on Shopify, will Counterpoint overwrite it?"

The answer depends on the specific field and the associated Shopify connector configuration settings.

---

# Understanding Synchronization Behavior

For product synchronization, fields generally fall into one of three categories:

| Behavior | Description |
|---|---|
| Counterpoint Always Overwrites Shopify | Counterpoint is always the system of truth. Changes made directly on Shopify will eventually be overwritten by the connector. |
| Counterpoint Sometimes Overwrites Shopify | Whether Counterpoint overwrites Shopify depends on connector configuration settings. |
| Shopify Can Be Maintained Independently | Counterpoint does not overwrite the value after initial creation (or does not sync the value at all). Shopify effectively becomes the system of truth. |

---

# Fields that Always Overwrite Shopify

The fields below are always synchronized from Counterpoint to Shopify during product synchronization. Changes made directly on Shopify will eventually be overwritten by the connector.

| Product Area | Source in Counterpoint | Notes |
|---|---|---|
| SKU | `ITEM_NO` | The Counterpoint Item Number is always the Shopify SKU. |
| Barcode | Barcode Table | Controlled by the configured barcode type selection logic. |
| Product Vendor | Shopify Item Record / Item Record | Shopify Item Record value takes priority if populated. |
| Quantity | Inventory Quantities | Configurable to use Qty Available or Qty On Hand. |
| Out-of-Stock Threshold | Shopify Configuration | Used to control Sold Out visibility behavior. |
| Continue Selling When Out of Stock | Shopify Item Record | Shopify-specific checkbox controlled by Counterpoint. |
| Track Quantity | Shopify Item Record | Shopify-specific checkbox controlled by Counterpoint. |
| Price | Price 1–6 / Regular Price | Most clients use Price 1. |
| Compare At Price | Price 1–6 | Optional Shopify compare-at pricing. |
| Online Store Sales Channel | Shopify Item Record | Controls Online Store visibility. |
| Point of Sale Sales Channel | Shopify Item Record | Controls Shopify POS visibility. |
| Requires Shipping | Shopify Item Record | Shopify-specific checkbox controlled by Counterpoint. |
| Shipping Weight | Shopify Item Record | Does not use the standard `IM_ITEM` weight field. |
| Shipping Unit | Shopify Item Record | Supported values: lb, oz, kg, g. |
| Product Variants | Item Tracking Method / Alternate Units | Controlled by gridded items and alternate unit configuration. |
| Product Metafields | Custom Mapping Table | Configured metafields are always synchronized from Counterpoint. |

---

# Fields Where Counterpoint Sometimes Overwrites Shopify

The fields below may overwrite Shopify depending on the associated Shopify connector configuration settings.

| Product Area | Related Configuration | Shopify Can Be Maintained Independently When... | Notes |
|---|---|---|---|
| Product Title | Product Title Field, Update Title | `Update Title = No` | If enabled, Counterpoint overwrites the Shopify product title during synchronization. |
| Product Handle (URL Slug) | Handle Definition Query, Update Handle | `Update Handle = No` | If enabled, Counterpoint overwrites the Shopify handle during synchronization. |
| Product Description (HTML) | Update HTML Description | `Update HTML Description = No` | Most clients prefer maintaining customer-facing descriptions directly in Shopify. |
| Product Status | Default Product Status | After initial product creation | The default status is only applied when the Shopify Item Record is first created. |
| Product Type | Item Categories as Product Type | Feature disabled | Many clients prefer managing Product Type directly in Shopify. |
| Tags | Use Item Attributes for Tags, Tags Item Field | Feature disabled or partially managed manually | Tags added in Shopify are not always removed when deleted in Counterpoint. Many clients manage tags directly in Shopify. |

---

# Fields That Never Overwrite Shopify

The fields below are maintained directly in Shopify and are never synchronized from Counterpoint.

| Product Area | Notes |
|---|---|
| Product Images | Product images are maintained directly on Shopify and are not synchronized from Counterpoint. |
| Shopify Category (Tax Category) | Shopify tax categories must be selected directly in Shopify. |
| Shopify Category Metafields | Automatically maintained by Shopify based on the selected Shopify Category. |
| SEO Title | Maintained directly in Shopify for search engine optimization purposes. |
| SEO Description | Maintained directly in Shopify for search engine optimization purposes. |
| Search Engine Metadata | Maintained directly in Shopify. |
| Product Media | Videos, 3D models, and other Shopify media assets are maintained directly in Shopify. |
