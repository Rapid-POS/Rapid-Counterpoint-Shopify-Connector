# Rapid POS Shopify Connector v3.01.00 Release Notes

_Release Date: June 23, 2026_

---

## New Functionality

### Shopify Bulk Item Setup Tool

Added a new **Shopify Bulk Item Setup** tool that allows users to create Shopify item records for many Counterpoint items at once, rather than creating them one at a time.

- Access the tool from **Connectors → Shopify → Shopify Bulk Item Setup**.
- Use the **item filter** to define which Counterpoint items should be included. The filter works like item filters elsewhere in Counterpoint and supports AND/OR logic, nested conditions, and customizable fields. When your filter is ready, click **Save** — the table at the bottom of the screen will populate with all matching items that do not yet have a Shopify item record, so you can review exactly what will be affected before proceeding.
- Use the **Shopify Item Record Settings** panel to configure the values to be applied to all records created in the run — including account name, out-of-stock quantity, sales channels, shipping settings, tags, and HTML description. The panel comes prepopulated with your typical settings, but you can adjust any values before creating the batch.
- Check the **Apply** checkbox and click **Save** to create the records immediately. There is no confirmation prompt, so review the item list and settings carefully before applying.
- Because all items in a single run receive the same settings, plan to work in batches grouped by shared settings.
- Shopify item records appear in Counterpoint immediately after creation. Syncing to Shopify happens as the connector runs and processes each record — large batches may take some time to fully appear on Shopify. Sync status can be monitored on individual Shopify item records.
- This tool only creates new Shopify item records. Items that already have a Shopify item record will not appear in the table, even if they match the filter. Existing Shopify item records must still be edited individually.

For full usage details, refer to the [Shopify Bulk Item Setup documentation](https://github.com/Rapid-POS/Rapid-Counterpoint-Shopify-Connector/blob/main/Shopify-Bulk-Item-Setup-Tool.md).

---

## Bug Fixes and Performance Enhancements

### Improved Shopify Store Account Handling in the Connector Installer

Updated the connector installer to automatically create the required Shopify store accounts using library variables if they do not already exist, ensuring accounts are set up correctly and consistently during installation. The following five accounts are managed by this process:

- **Shopify Tender** — Records amounts paid by customers on Shopify.
- **Shopify Deposit Liabilities** — Records customer deposits made on Shopify orders, and is relieved when the order is released in Counterpoint.
- **Shopify Sales Tax Payable** — Records tax amounts paid by customers on Shopify.
- **Shipping** — Records shipping fees paid by customers on Shopify.
- **Shopify Needs Investigation** — A catch-all account assigned to areas of the store setup that are required by Counterpoint but not actively used by the Shopify connector. Any activity recorded in this account should be investigated and reported to Rapid.
