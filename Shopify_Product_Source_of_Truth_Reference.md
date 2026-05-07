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
| Product Title | Counterpoint Sometimes Overwrites Shopify | Product Title Field, Update Title | If Update Title = Yes, Counterpoint overwrites the Shopify product title. If Update Title = No, Shopify titles can be maintained independently after initial creation. |
| Product HTML Description | Counterpoint Sometimes Overwrites Shopify | Update HTML Description | If enabled, Counterpoint overwrites the Shopify HTML description during synchronization. If disabled, the Shopify description can be maintained independently. |
| Product Handle | Counterpoint Sometimes Overwrites Shopify | Handle Definition Query, Update Handle | If Update Handle = Yes, Counterpoint overwrites the Shopify product handle. If Update Handle = No, Shopify handles can be maintained independently after initial creation. |
| Product Price | Counterpoint Always Overwrites Shopify | Product Price | Shopify pricing is always driven by Counterpoint pricing when synchronization occurs. |
| Compare At Price | Counterpoint Always Overwrites Shopify | Product Compare At Price | Shopify compare-at pricing is always driven by Counterpoint when synchronization occurs. |
| Inventory Quantity | Counterpoint Always Overwrites Shopify | Product Inventory Qty, Hide Out of Stock Inventory | Shopify inventory levels are always controlled by Counterpoint inventory quantities. |
| Product Vendor | Counterpoint Always Overwrites Shopify | Product Vendor Default, Product Vendor field on Shopify Item Record | The Product Vendor field on the Shopify Item Record always takes priority. If blank, the configured fallback behavior is used. |

---
