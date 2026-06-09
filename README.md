# Rapid POS Shopify Connector - Version 3.00.00
Updated 6/9/2026

---

## Overview

The **Rapid POS Shopify Connector** seamlessly integrates your Counterpoint POS system with your Shopify online store. This connection keeps your items, customers, and orders synchronized automatically — helping you manage your ecommerce operations efficiently without duplicate data entry.

---

## Minimum System Requirements:
- Minimum Counterpoint version: **8.5.6.2**  
- Minimum SQL Server version: **2016**  
- Minimum Windows Server version: **2016**  
- Minimum PowerShell version: **5.1**  

If you would like the Shopify connector but your system does not meet these minimum requirements, please consult your Care Team Lead (vCIO) for an upgrade quote.

> [!WARNING]
> Your environment must meet our [CI/CD Connector Requirements](https://github.com/Rapid-POS/Miscellaneous-Documents/blob/main/CICD-Connector-Requirements.md) (server access, firewall rules, etc.) before any install or upgrade. Troubleshooting, manual installs, or follow-up work resulting from unmet requirements will be billed at standard T&M rates.

---

## Section 1: Data Flow Summary

The Rapid POS Shopify Connector allows you to:

- Sync **inventory data** between Counterpoint and Shopify, keeping pricing and quantity information consistent across systems.  
- Automatically import **online orders** and **customers** from Shopify into Counterpoint.

### Items (Products)
- Flow **from Counterpoint → Shopify**  
- Includes both standard items (simple products) and gridded items (products with variants).  
- Can be configured to send specific alternate units as variants (for example, selling by unit or by case).  

### Orders & Customers
- Flow **from Shopify → Counterpoint**  
- New online orders and customer updates are imported every 15 minutes.  

---

## Section 2: Configuration Guide

Review the full [Shopify Configuration Guide](Configuration-Guide.md).

---

## Section 3: Shopify Item Status View

Every Shopify Item Record includes a **sync status** that indicates its current state in the connector process. In some cases, it is helpful to review how many items fall into a particular status category.

For example, you may want to identify that an item has encountered an error (status 9) so that record can be reviewed and remediated.

The **Shopify Item Status View** displays a summary table showing:
- Each sync status code (0, 1, 2, 9)
- The total number of item records currently associated with that status

### Shopify Sync Status Codes

Every Shopify Item Record includes a **sync status** indicating its current state in the sync process:

- **0** – Fully synced; nothing pending  
- **1** – Recently created or updated; will sync on the next connector run  
- **2** – Item is currently in the active sync queue  
- **9** – Sync error; requires remediation before it can be re-synced

**Notes:**
- If no items exist for a given status, that status will **not** appear in the table.
- The table can be refreshed at any time to display the most up-to-date information.
- This is best viewed in _table view_.

---

## Section 4: Notes

Rapid POS does not provide website design or hosting services. We recommend working with a qualified ecommerce professional to build and maintain your Shopify storefront.
