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

# Quick Reference

| Product Area | Default System of Truth | Related Configuration Setting(s) | Notes |
|---|---|---|---|
| Product Status | Counterpoint Sometimes Overwrites Shopify | Default Product Status | The default status is only applied when the Shopify Item Record is first created. Product status can later be maintained directly on Shopify. |
| Product Title | Counterpoint Sometimes Overwrites Shopify | Product Title Field, Update Title | If Update Title = Yes, Counterpoint overwrites the Shopify product title. If Update Title = No, Shopify titles can be maintained independently after initial creation. |
| Product HTML Description | Counterpoint Sometimes Overwrites Shopify | Update HTML Description | If enabled, Counterpoint overwrites the Shopify HTML description during synchronization. If disabled, the Shopify description can be maintained independently. |
| Product Handle | Counterpoint Sometimes Overwrites Shopify | Handle Definition Query, Update Handle | If Update Handle = Yes, Counterpoint overwrites the Shopify product handle. If Update Handle = No, Shopify handles can be maintained independently after initial creation. |
| Product Price | Counterpoint Always Overwrites Shopify | Product Price | Shopify pricing is always driven by Counterpoint pricing when synchronization occurs. |
| Compare At Price | Counterpoint Always Overwrites Shopify | Product Compare At Price | Shopify compare-at pricing is always driven by Counterpoint when synchronization occurs. |
| Inventory Quantity | Counterpoint Always Overwrites Shopify | Product Inventory Qty, Hide Out of Stock Inventory | Shopify inventory levels are always controlled by Counterpoint inventory quantities. |
| Product Vendor | Counterpoint Always Overwrites Shopify | Product Vendor Default, Product Vendor field on Shopify Item Record | The Product Vendor field on the Shopify Item Record always takes priority. If blank, the configured fallback behavior is used. |
| Product Barcode | Counterpoint Always Overwrites Shopify | Filter Item Barcode by ID | Shopify barcodes are always synchronized from Counterpoint based on the configured barcode selection logic. |
| Product Type | Counterpoint Always Overwrites Shopify | Item Categories as Product Type | Shopify product type values are always synchronized from Counterpoint when enabled. |
| Collections | Counterpoint Always Overwrites Shopify | Sub-Categories to Collections | Shopify collections are synchronized from Counterpoint subcategories when enabled. |
| Product Tags | Counterpoint Sometimes Overwrites Shopify | Use Item Attributes for Tags, Tags Item Field | Depending on configuration, Counterpoint may add tags to Shopify. Existing Shopify tags may still require manual management depending on connector configuration and workflow. |
| Product Metafields | Counterpoint Always Overwrites Shopify | Product Metafield Namespace, Custom Metafield Configuration | Configured metafields are synchronized from Counterpoint during synchronization. |
| Product Images | Shopify | N/A | Product images are maintained directly on Shopify and are not synchronized from Counterpoint. |
| Product SEO Fields | Shopify | N/A | SEO titles, descriptions, and related search engine metadata are maintained directly on Shopify. |

---

# General Guidance

## Fields Typically Maintained in Counterpoint

The following types of data are generally best maintained in Counterpoint:

- Inventory quantities
- Pricing
- Barcodes
- Product type classifications
- Vendor references
- Structured operational data

These values are typically operational or transactional in nature and should remain centralized within Counterpoint.

---

## Fields Commonly Maintained on Shopify

The following types of data are commonly maintained directly on Shopify:

- Customer-facing product titles
- Product descriptions
- Product handles/URLs
- SEO content
- Product images
- Marketing-focused content

Many clients prefer maintaining these fields on Shopify because Shopify supports:

- Longer field lengths
- Rich HTML editing
- SEO optimization
- Better customer-facing presentation
- Ecommerce-specific merchandising workflows

---

# Recommended Configuration Strategy

For most clients, Rapid recommends:

| Setting | Recommended Value |
|---|---|
| Update Title | No |
| Update HTML Description | No |
| Update Handle | No |
| Product Inventory Qty | Item Qty Available |
| Product Price | Counterpoint-controlled |

This approach allows:

- Counterpoint to remain the operational system of truth
- Shopify to remain the merchandising and marketing system of truth
- Ecommerce staff to optimize customer-facing presentation directly on Shopify without losing changes during synchronization

---

# Important Notes

- Some configuration changes may require a full resynchronization to update existing Shopify products.
- If a field is configured to overwrite Shopify values, manual edits made directly on Shopify may eventually be overwritten by the connector.
- Product creation behavior and update behavior may differ depending on the associated connector settings.
- The Shopify Item Record in Counterpoint often provides item-level overrides that take priority over global configuration settings.
