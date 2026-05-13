# Rapid POS Shopify Connector v3.00.00 Release Notes

_Release Date: May 5, 2026_

This release introduces major architectural enhancements to the Shopify Connector, including migration to Shopify GraphQL APIs, multi-account support, Windows Service execution, expanded synchronization visibility tools, improved synchronization performance controls, and compatibility with Shopify’s updated platform requirements.

---

## Table of Contents

- [Architecture and Platform Enhancements](#architecture-and-platform-enhancements)
- [Multi-Account Enhancements](#multi-account-enhancements)
- [New Menu Options (Touchscreen Buttons)](#new-menu-options-touchscreen-buttons)
- [New Visibility Tools](#new-visibility-tools)
- [Functionality Enhancements](#functionality-enhancements)
- [Bug Fixes and Performance Enhancements](#bug-fixes-and-performance-enhancements)
- [Additional Notes](#additional-notes)

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
  - Removed the previous two-store limitation that required separate Shopify connector instances ("Shopify" and "Shopify 2") for multi-store environments.
  - The Shopify Connector can now support more than two Shopify websites within a single connector installation. 
  - Removed all tables, fields, and references related to "Shopify 2," which was previously used to support secondary Shopify website instances. 

- Added multi-account support to:
  - Shopify Configuration
  - Shopify Items
  - Shopify Item Variants
  - Shopify Items Status View
  - Shopify Locations (inventory locations)
  - Shopify Customers
  - Shopify Customer Matching Priority
  - Mark All Messages as Read
  - Shopify Custom Field Mapping (for syncing Shopify product metadata fields)

---

## New Menu Options (Touchscreen Buttons)

- Added the Shopify Items Status View menu option for improved visibility into Shopify item synchronization activity.
  - Displays status summary reporting for Shopify item records by connector status (0, 1, 2, 9).
  - Statuses with no associated item records are automatically excluded from the view. If no items are currently associated with a particular status, that status will not appear in the table.
  - The table can be refreshed at any time to display the most current synchronization status information.
  - Best viewed in Table View.

- Added the Shopify Locations menu option for improved multi-location inventory management.
  - Moved Shopify location maintenance from the `INV_LOC` table to a dedicated `USER_SHOPIFY_LOC` table.
  - The new table controls which Counterpoint inventory locations are synchronized to Shopify.
  - Provides improved visibility into Shopify Location IDs used for Counterpoint-Shopify inventory synchronization.
  - Best viewed in Table View.

- Added the Shopify Customer Matching Priority menu option.
  - Exposed existing Shopify customer matching priority functionality within the Counterpoint user interface for improved visibility and configuration management.
  - Email matching remains the default fallback matching method when no other matching configuration exists, or no configured matches are found.
  - Best viewed in Table View.

- Added the Shopify Custom Field Mapping menu option.
  - Allows users to review Shopify product custom field and metadata synchronization configuration directly within Counterpoint.
  - Best viewed in Table View.

- Added the Shopify Customer Record menu option.
  - Displays each customer’s Shopify ID and current synchronization status when a Shopify relationship exists.
  - Improves visibility into Shopify customer relationship data previously stored within the Counterpoint Customer record (`AR_CUST` table).
  - Added direct access to Shopify customer synchronization information from the Counterpoint Customer Record.

- Added the Shopify Item Variants menu option.
  - Displays individual variant records for gridded items and items with alternate units.
    - **Gridded:** Moved gridded item Shopify data from the `INV_CELL` table to the `USER_SHOPIFY_ITEM_VARIANTS` table.
    - **Alt-Units:** Added visibility into Shopify variant information for alternate units, which was not previously accessible to end users.
    - **Simple:** Simple products with a single variant are **excluded** from this view.

---

## New Visibility Tools

- Added a **Default Variant ID** field to the Shopify Item Record for improved Shopify variant visibility.
  - Displays the stocking unit’s Shopify Variant ID for **simple** items and items with **alternate units**.
  - **Gridded** items do not utilize a default variant ID, so this field remains blank for gridded products.

- Added new **Ecommerce Platform** and **Ecommerce Order Number** fields to Ticket History Lookup.
  - Displays the original ecommerce platform associated with imported orders, when applicable.
  - Displays the original ecommerce order number from the source ecommerce platform.
  - Improves troubleshooting visibility for imported ecommerce orders.
  - Especially useful for environments where **Import Orders as Tickets** is enabled and **Use Shopify Order Number as Ticket Number** cannot be used.
 
- Renamed configuration options for improved clarity and consistency.
  - Updated the former **Order Cutoff Date** configuration option to the new **Orders Down Start Date** configuration option.
    - Defines the earliest Shopify order date eligible for import into Counterpoint.
  - Updated the former **Start Date Days** configuration option to the new **Orders Down Lookback Days** configuration option.
    - Controls how many days back the connector checks for missed Shopify orders during synchronization recovery scenarios.

---

## Functionality Enhancements

- Added new Shopify Connector configuration options for improved performance and troubleshooting.
  - Added the **Enabled** configuration option to allow the connector to be temporarily disabled for troubleshooting, maintenance, or testing purposes.
  - Added the **Mark Alerts as Read in Message Center After Days** configuration option to automatically mark connector alerts as read after a defined number of days, reducing repeated Message Center pop-up notifications.

- Enhanced **Calculated/Promotional Price functionality** to support Shopify price rules with **specific** start and end times.
  - Existing "beginning of day" and "end of day" promotional pricing behavior remains supported.

---

## Bug Fixes and Performance Enhancements

- Improved the reliability of the Mark All Messages as Read functionality.
  - Also added multi-account awareness support, allowing messages to be marked as read independently for each Shopify account.

- Fixed an issue where Shopify discounts were incorrectly applied twice in Counterpoint when **Import Orders as Tickets** was enabled, causing ticket totals to appear lower than the actual totals from Shopify.
  - Corrected ticket subtotal and total calculations so imported Shopify orders now accurately reflect the actual customer-paid subtotal, discounts, fees, and total amounts.
  - Resolved an issue in order import processing where discounts were being subtracted from `EXT_PRC` during order import processing and then subtracted a second time during `SAL_TOT()` ticket total calculation processing through `PS_DOC_DISC` records (the existing Counterpoint discount calculation mechanism). 
  - Updated order import logic so `EXT_PRC` now stores the gross Shopify line-item price, allowing discounts to be applied only once through the existing `PS_DOC_DISC` / `SAL_TOT()` calculation mechanism.

- Fixed an issue where the Barcode ID Filter was not properly filtering by unit.
  - Corrected barcode lookup logic to ensure the appropriate barcode is selected based on both the Barcode ID Filter and the associated unit.
  - Prevents incorrect barcode assignments caused by defaulting to the first matching barcode record.

- Fixed an issue where alternate-unit pricing always defaulted to Price 1, regardless of the configured product price level.
  - Updated pricing logic to properly respect the configured Product Price setting for alternate units.
  - Added fallback pricing behavior for alternate units when a configured price level for that alternate unit is not populated.
    - First fallback uses the **configured price level for the stocking unit** multiplied by the alternate unit numerator/denominator calculation.
    - Second fallback (no configured price level exists) uses **Price 1 for the stocking unit** multiplied by the alternate unit numerator/denominator calculation.

---

## Additional Notes

- Shopify Connector 3.00.00 includes major architectural enhancements focused on multi-account support, improved synchronization performance, expanded Shopify visibility within Counterpoint, and compatibility with updated Shopify platform requirements.
- This release contains significant backend and synchronization framework changes intended to improve long-term scalability, maintainability, and connector reliability.
- Shopify custom app configuration and migration to Shopify GraphQL APIs are required to comply with updated Shopify authentication, platform, and API requirements.
