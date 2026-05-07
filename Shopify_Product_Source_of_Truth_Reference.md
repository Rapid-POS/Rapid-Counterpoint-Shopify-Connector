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

# Overall Source of Truth Summary

| Product Area | Default System of Truth | Notes |
|---|---|---|
| Product Title | Counterpoint Sometimes Overwrites Shopify | Controlled by `Update Title` configuration. |
| SKU | Counterpoint Always Overwrites Shopify | Always sourced from Counterpoint Item Number (`ITEM_NO`). |
| Barcode | Counterpoint Always Overwrites Shopify | Controlled by barcode type configuration. |
| Product Handle (URL Slug) | Counterpoint Sometimes Overwrites Shopify | Controlled by `Update Handle` configuration. |
| Product Vendor | Counterpoint Always Overwrites Shopify | Shopify Item Record values take priority when populated. |
| Tags | Counterpoint Sometimes Overwrites Shopify | Existing Shopify tags may still require manual management. |
| Product Description (HTML) | Counterpoint Sometimes Overwrites Shopify | Controlled by `Update HTML Description` configuration. |
| Quantity | Counterpoint Always Overwrites Shopify | Counterpoint inventory is always authoritative. |
| Out-of-Stock Threshold | Counterpoint Always Overwrites Shopify | Controlled by configurable inventory threshold. |
| Continue Selling When Out of Stock | Counterpoint Always Overwrites Shopify | Shopify checkbox controlled by Counterpoint. |
| Track Quantity | Counterpoint Always Overwrites Shopify | Shopify checkbox controlled by Counterpoint. |
| Price | Counterpoint Always Overwrites Shopify | Typically sourced from Price 1. |
| Compare At Price | Counterpoint Always Overwrites Shopify | Configurable from Price 1–6. |
| Online Store Sales Channel | Counterpoint Always Overwrites Shopify | Controlled by Shopify Item Record flags. |
| Point of Sale Sales Channel | Counterpoint Always Overwrites Shopify | Controlled by Shopify Item Record flags. |
| Requires Shipping | Counterpoint Always Overwrites Shopify | Shopify checkbox controlled by Counterpoint. |
| Shipping Weight | Counterpoint Always Overwrites Shopify | Maintained in Shopify Item Record. |
| Shipping Unit | Counterpoint Always Overwrites Shopify | Maintained in Shopify Item Record. |
| Product Variants | Counterpoint Always Overwrites Shopify | Controlled by item tracking method and alternate units. |
| Product Metafields | Counterpoint Always Overwrites Shopify | Controlled by custom metafield mappings. |
| Product Images | Shopify | Not synchronized from Counterpoint. |
| Shopify Category (Tax Category) | Shopify | Must be selected directly in Shopify. |
| Shopify Category Metafields | Shopify | Automatically maintained by Shopify. |
| SEO Fields | Shopify | Maintained directly in Shopify. |

---
