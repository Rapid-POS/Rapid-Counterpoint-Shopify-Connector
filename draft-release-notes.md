DRAFT RELEASE NOTES

# Shopify Connector Release Notes

## Version 3.00.00  
**Release Date:** May 5, 2026

This release introduces major architectural enhancements to the Shopify Connector, including migration to Shopify GraphQL APIs, multi-account support, Windows Service execution, expanded synchronization visibility tools, improved synchronization performance controls, and compatibility with Shopify’s updated platform requirements.

---

## Architecture and Platform Enhancements

- Migrated all customer and product functionality from the Shopify REST API to the Shopify GraphQL API for improved compatibility, performance, and long-term Shopify platform support.

- Replaced the Task Scheduler integration with a dedicated Windows Service for improved reliability, automation, and synchronization performance.
  - Added configurable CRON scheduling settings within the Shopify Connector configuration.
  - Added independent scheduling controls for the following synchronization processes:
    - Daily Event Execution Time
    - Order Sync Execution Time
    - Item Sync Execution Time
    - Customer Sync Execution Time
  - Enhanced synchronization processing to allow multiple synchronization tasks to run independently and simultaneously, eliminating delays caused by sequential processing dependencies.

- Updated the **Run Shopify Connector Manually** execution process to run connector operations directly from the server.
  - Added support for triggering manual connector runs from a workstation while automatically routing execution through the server.
  - Added a Manual Run flag to the Shopify configuration that is monitored by the connector service.
  - Enhanced connector execution handling to automatically process manual run requests when the connector is idle within one minute through scheduled CRON monitoring.

- Added support for configuring the Shopify Connector as a Rapid POS custom app within Shopify.
  - Ensures compatibility with updated Shopify platform standards and authentication requirements.

---

## Multi-Account Enhancements

- Redesigned the Shopify Connector architecture to support multi-account functionality within a single connector instance.
  - Added support for synchronizing data from a single Counterpoint instance to multiple Shopify websites simultaneously.
  - Removed all tables, fields, and references related to "Shopify 2," which was previously used to support secondary Shopify website instances.

- Added multi-account support to:
  - Shopify Item Record functionality
  - Shopify Configuration functionality
  - Mark All Messages as Read functionality

---

## New Menu Options and Visibility Tools

- Added the Shopify Item Status View menu option for improved visibility into Shopify item synchronization activity.
  - Displays status summary reporting for Shopify item records by connector status (0, 1, 2, 9).
  - Best viewed in Table View.

- Added the Shopify Locations menu option for improved multi-location inventory management.
  - Moved Shopify location maintenance from the `INV_LOC` table to a dedicated `USER_SHOPIFY_LOC` table.
  - The new table controls which Counterpoint inventory locations are synchronized to Shopify.
  - Provides improved visibility into Shopify Location IDs used for Counterpoint-Shopify inventory synchronization.

- Added the Shopify Customer Matching Priority menu option.
  - Added support for configurable customer matching priorities during Shopify customer synchronization.
  - Email matching remains the default fallback matching method when no other matching configuration exists or no configured matches are found.

- Added the Shopify Custom Field Mapping menu option.
  - Allows users to review Shopify custom field and metadata synchronization configuration directly within Counterpoint.

- Added the Shopify Customer Record menu option.
  - Displays each customer’s Shopify ID and current synchronization status when a Shopify relationship exists.
  - Improves visibility into Shopify customer relationship data previously stored within the Counterpoint Customer record (`AR_CUST` table).
  - Added direct access to Shopify customer synchronization information from the Counterpoint Customer Record.

- Added the Shopify Item Variants menu option.
  - Displays individual variant records for gridded items and items with alternate units.
  - Simple products with a single variant are excluded from this view.
  - Moved gridded item Shopify data from the `INV_CELL` table to the `USER_SHOPIFY_ITEM_VARIANTS` table.
  - Added visibility into Shopify variant information for alternate units, which was not previously accessible to end users.

- Added a Default Variant ID field to the Shopify Item Record for improved Shopify variant visibility.
  - Displays the stocking unit’s Shopify Variant ID for simple items and items with alternate units.
  - Gridded items do not utilize a default variant ID, so this field remains blank for gridded products.

- Added new Ecommerce Platform and Ecommerce Order Number fields to Ticket History Lookup.
  - Displays the original ecommerce platform associated with imported orders, when applicable.
  - Displays the original ecommerce order number from the source ecommerce platform.
  - Improves troubleshooting visibility for imported ecommerce orders.
  - Especially useful for environments where Import Orders as Tickets is enabled and Use Shopify Order Number as Ticket Number cannot be used.

---

## Synchronization and Performance Enhancements

- Added new Shopify Connector configuration options for improved performance tuning, troubleshooting, and synchronization management.
  - Added the **Mark Alerts as Read in Message Center After Days** configuration option to automatically mark connector alerts as read after a defined number of days, reducing repeated Message Center pop-up notifications.
  - Added the **Max Number of Items to Sync** configuration option to control the maximum number of items processed during a single connector run for improved synchronization performance optimization.
  - Added the **Max Number of Customers to Sync** configuration option to control the maximum number of customers processed during a single connector run for improved synchronization performance optimization.
  - Added the **Orders Down Start Date** configuration option to define the earliest Shopify order date eligible for import into Counterpoint.
  - Added the **Orders Down Lookback Days** configuration option to control how many days back the connector checks for missed Shopify orders during synchronization recovery scenarios.
  - Added the **Enabled** configuration option to allow the connector to be temporarily disabled for troubleshooting, maintenance, or testing purposes.

- Enhanced Calculated/Promotional Price functionality to support Shopify price rules with specific start and end times.
  - Existing "beginning of day" and "end of day" promotional pricing behavior remains supported.

---

## Bug Fixes and Performance Enhancements

- Improved the reliability of the Mark All Messages as Read functionality.
  - Added multi-account awareness support, allowing messages to be marked as read independently for each Shopify account.

- Fixed an issue where Shopify discounts were incorrectly applied twice in Counterpoint when Import Orders as Tickets was enabled.
  - Corrected ticket subtotal and total calculations so imported Shopify orders now properly reflect the actual customer-paid subtotal, discounts, fees, and total amounts.
  - Resolved an issue that caused Daily Drawer Reports to become unbalanced due to discounts being deducted twice during ticket total calculation processing.
  - Updated order import logic so discounts are now applied only once through the existing Counterpoint discount calculation mechanisms.

- Fixed an issue where the Barcode ID Filter was not properly filtering by unit.
  - Corrected barcode lookup logic to ensure the appropriate barcode is selected based on both the Barcode ID Filter and the associated unit.
  - Prevents incorrect barcode assignments caused by defaulting to the first matching barcode record.

- Fixed an issue where alternate-unit pricing always defaulted to Price 1, regardless of the configured product price level.
  - Updated pricing logic to properly respect the configured Product Price setting for alternate units.
  - Added fallback pricing behavior for alternate units when a configured price level is unavailable.
    - First fallback uses the configured stocking unit price level multiplied by the numerator/denominator calculation.
    - Second fallback uses Price 1 multiplied by the numerator/denominator calculation when no configured price level exists.

---

## Additional Notes

- Shopify Connector 3.00.00 includes major architectural enhancements focused on multi-account support, improved synchronization performance, expanded Shopify visibility within Counterpoint, and compatibility with updated Shopify platform requirements.
- This release contains significant backend and synchronization framework changes intended to improve long-term scalability, maintainability, and connector reliability.
