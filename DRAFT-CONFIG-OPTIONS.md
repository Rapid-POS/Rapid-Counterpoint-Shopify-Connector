# DRAFT Shopify Connector Configuration 

## Quick Links

- [Overall](#overall)
- [Items Up](#items-up-counterpoint--shopify)
- [Orders Down](#orders-down-shopify--counterpoint)
- [Orders Up](#orders-up-counterpoint--shopify)
- [Customers Down](#customers-down-shopify--counterpoint)
- [CRON Job Schedules](#cron-job-schedules)
- [Sync Limits](#sync-limits)
- [Log Files and Alerts](#log-files-and-alerts)
- [Troubleshooting Controls](#troubleshooting-controls)
 
---
 
## Using this Document 

## Understanding Setting Sections

Each configuration setting in this document follows a standardized format to help explain how the setting works, which values are supported, Rapid’s recommendations, and the impact of changing the setting after implementation.

### Field

The display name of the configuration setting as it appears in the Shopify Connector configuration.

### Column Name

The database column (internal field) associated with the configuration setting.

This is primarily included for reference and troubleshooting purposes.

### Default Type

Indicates how the setting is typically used and maintained.

These default types are intended to help identify which settings are broadly recommended, which are dependent on business preference, and which are not intended to be changed by clients. 
 
- **Recommended** – Rapid recommends using the default value for most clients based on common Shopify and Counterpoint workflows. 
 
- **Common** – A frequently used configuration choice based on common business practices, but not necessarily Rapid’s recommended option for all clients. 
 
- **No Preference** – The best value depends entirely on the client’s business processes and operational preferences. 
 
- **Sticky (Read-Only)** – This value is configured by Rapid during implementation and is not intended to be changed by clients. Alternative configurations are only supported in rare situations and require approval from Rapid (and may require billable services). 

### Default Value

The standard value Rapid typically configures during implementation.

This value may vary depending on business requirements and operational workflows.

### Purpose

Provides an overview of what the setting controls and how it affects synchronization behavior between Shopify and Counterpoint.

### Valid Values

Lists the supported configuration options for the setting along with explanations of what each option does.

### Recommendation

Provides Rapid’s recommended configuration based on common Shopify and Counterpoint workflows and implementation experience.

### Notes

Provides additional operational, technical, or business context related to the setting.

This section may include implementation considerations, limitations, exceptions, or best practices.

### Create / Update Behavior

Explains how the setting behaves during synchronization, particularly whether the setting applies:
- only when records are first created,
- during future updates,
- or during both create and update operations.

This section may also explain whether the setting affects Shopify → Counterpoint synchronization, Counterpoint → Shopify synchronization, or both.

### Change Impact and Support Required

Explains the operational impact of changing the setting after implementation.

This section may identify:
- whether the updated setting only affects future records,
- whether a full resynchronization is recommended,
- whether the change takes effect immediately,
- or whether Rapid staff assistance is recommended or required.
 
---
 
## Full Table of Contents

- [Overall](#overall)
  - [Account Name](#account-name)
  - [Enabled](#enabled)
  - [API URL](#api-url)
  - [API Key](#api-key)
  - [Encrypted API Access Token](#encrypted-api-access-token)
  - [Last Sync Date Time](#last-sync-date-time)
  - [Version](#version)
  - [Last Maintained By](#last-maintained-by)
  - [Last Maintained](#last-maintained)

- [Items Up](#items-up)
  - [Add Update Items Up](#add-update-items-up)
  - [Copy From Applies to Shopify Items](#copy-from-applies-to-shopify-items)
  - [Default Product Status](#default-product-status)
  - [Delete Item Type](#delete-item-type)
  - [Product Title Field](#product-title-field)
  - [Update Title](#update-title)
  - [Product Inventory Qty](#product-inventory-qty)
  - [Hide Out of Stock Inventory](#hide-out-of-stock-inventory)
  - [Product Price](#product-price)
  - [Product Compare At Price](#product-compare-at-price)
  - [Product Vendor Default](#product-vendor-default)
  - [Filter Item Barcode by ID](#filter-item-barcode-by-id)
  - [Handle Definition Query](#handle-definition-query)
  - [Update Handle](#update-handle)
  - [Update Html Description](#update-html-description)
  - [Item Categories as Product Type](#item-categories-as-product-type)
  - [Sub-Categories To Collections](#sub-categories-to-collections)
  - [Use Item Attributes For Tags](#use-item-attributes-for-tags)
  - [Tags Item Field](#tags-item-field)
  - [Product Metafield Namespace](#product-metafield-namespace)

- [Orders Down](#orders-down)
  - [Add Orders Down](#add-orders-down)
  - [Use Shopify Order Number as Ticket #](#use-shopify-order-number-as-ticket-)
  - [Order Source](#order-source)
  - [Customer Shopify Notes to Document Notes](#customer-shopify-notes-to-document-notes)
  - [Store](#store)
  - [Station](#station)
  - [Drawer](#drawer)
  - [User](#user)
  - [Shipping Misc Chrg #](#shipping-misc-chrg-)
  - [Pay Code](#pay-code)
  - [Order Line Item Description Column](#order-line-item-description-column)
  - [Match by Item #](#match-by-item-)
  - [Match by Barcode](#match-by-barcode)
  - [Interim Item #](#interim-item-)

- [Orders Up](#orders-up)
  - [Update Orders Up](#update-orders-up)
  - [Add Refunds Up](#add-refunds-up)
  - [Add Cancelled Orders Up](#add-cancelled-orders-up)

- [Customers Down](#customers-down)
  - [Workgroup](#workgroup)
  - [Phone Format](#phone-format)
  - [Capitalize Customer Fields](#capitalize-customer-fields)
  - [Order Billing Address Overrides Customer Address](#order-billing-address-overrides-customer-address)

- [CRON Job Schedules](#cron-job-schedules)
  - [Daily Event Execution Time](#daily-event-execution-time)
  - [Order Sync Execution Time](#order-sync-execution-time)
  - [Item Sync Execution Time](#item-sync-execution-time)
  - [Customer Sync Execution Time](#customer-sync-execution-time)
  - [Manual Run Connector Execution Time](#manual-run-connector-execution-time)
  - [Manual Run Connector](#manual-run-connector)

- [Sync Limits](#sync-limits)
  - [Orders Down Start Date](#orders-down-start-date)
  - [Orders Down Lookback Days](#orders-down-lookback-days)
  - [Max Number of Items to Sync](#max-number-of-items-to-sync)
  - [Max Number of Customers to Sync](#max-number-of-customers-to-sync)

- [Log Files and Alerts](#log-files-and-alerts)
  - [Max Number of Log Files to Keep](#max-number-of-log-files-to-keep)
  - [Max Log File Size](#max-log-file-size)
  - [Message Group #](#message-group-)
  - [Mark Alerts as Read in Message Center After Days](#mark-alerts-as-read-in-message-center-after-days)

- [Troubleshooting Controls](#troubleshooting-controls)
  - [Skip All Orders Except](#skip-all-orders-except)
  - [Skip All Items Except](#skip-all-items-except)

### [↑ Back to Top](#quick-links)

---
 
## Overall 
 
### Account Name 
 
- **Column Name:** `ACCOUNT_NAME`
- **Default Value:** _null_ 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose**  
- Identifies the Shopify account and its associated credentials. 
 
**Valid Values**  
- Rapid will populate this field during install. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Enabled 
 
- **Column Name:** `IS_ENABLED` 
- **Default Value:** _null_ 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Used to temporarily disable the connector while troubleshooting or testing. 
 
**Valid Values** 
- Rapid will populate this field during install. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### API URL 
 
- **Column Name:** `API_URL` 
- **Default Value:** _null_ 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Identifies the Shopify account and its associated credentials. 
 
**Valid Values** 
- Rapid will populate this field during install. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### API KEY 
 
- **Column Name:** `API_KEY` 
- **Default Value:** _null_
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Identifies the Shopify account and its associated credentials. 
 
**Valid Values** 
- Rapid will populate this field during install. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Encrypted API Access Token 
 
- **Column Name:** `API_PWD` 
- **Default Value:** _null_
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Identifies the Shopify account and its associated credentials. 
 
**Valid Values** 
- Rapid will populate this field during install. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Last Sync Date Time 
 
- **Column Name:** `LST_SYNC_DT` 
- **Default Value:** _null_
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Displays the current connector version and the most recent maintenance information for reference. 
 
**Valid Values** 
- This field will be automatically populated by the connector. 
 
**Change Impact and Support Required** 
- Automatically updated. 
 
---
 
### Version 
 
- **Column Name:** `APP_VERSION` 
- **Default Value:** _null_ 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Displays the current connector version and the most recent maintenance information for reference. 
 
**Valid Values** 
- This field will be automatically populated by the connector. 
 
**Change Impact and Support Required** 
- Automatically updated. 
 
---
 
### Last Maintained By 
 
- **Column Name:** `LST_MAINT_USR_ID` 
- **Default Value:** _null_
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Displays the current connector version and the most recent maintenance information for reference. 
 
**Valid Values** 
- This field will be automatically populated by the connector. 
 
**Change Impact and Support Required** 
- Automatically updated. 
 
---
 
### Last Maintained 
 
- **Column Name:** `LST_MAINT_DT` 
- **Default Value:** _null_
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Displays the current connector version and the most recent maintenance information for reference. 
 
**Valid Values** 
- This field will be automatically populated by the connector. 
 
**Change Impact and Support Required** 
- Automatically updated. 

### [↑ Back to Top](#quick-links)

---
 
## Items Up 
 
### Add Update Items Up 
 
- **Column Name:** `ADD_UPDATE_ITEMS_UP` 
- **Default Value:** Y
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Controls whether newly added or updated items in Counterpoint with a Shopify Item Record are synchronized to Shopify as products. 
 
**Valid Values** 
- **Yes** – Newly added or updated items in Counterpoint with a Shopify Item Record will be created or updated as products in Shopify. 
- **No** – Newly added or updated items in Counterpoint will not be synchronized to Shopify. 
 
**Recommendation** 
- Choose **yes**. This should always be set to **yes** to ensure that product data is synchronized to Shopify. 
- Choosing no will require approval as well as additional configuration and testing, which will result in billable services from Rapid. 
 
**Notes** 
- This setting is typically used by Rapid staff for troubleshooting to temporarily disable item synchronization and should not be adjusted by clients. 
  
**Create and Overwrite (Update) Behavior** 
- When set to yes, products on Shopify will be created and updated by the connector. 
  
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
  
---
 
### Copy From Applies to Shopify Items 
 
- **Column Name:** `ENABLE_COPY_FROM` 
- **Default Value:** N
- **Default Type:** No Preference 
 
**Purpose** 
- Controls whether Shopify Item Record fields are copied when creating a new item in Counterpoint using the “Copy From” functionality. 
 
**Valid Values** 
- **Yes** – Shopify Item Record fields will be copied from the source item used in the “Copy From” process. 
- **No** – Shopify Item Record fields will not be copied and will use default values. 
 
**Recommendation** 
- Choose **yes** to maintain consistency when creating similar items that should share Shopify configuration. 
- Choose **no** if Shopify Item Record fields should be set manually for each new item. 
 
**Notes** 
- This setting applies only when creating new items using the “Copy From” functionality on the Item Record in Counterpoint. 
- When enabled, the Shopify Item Record will inherit values from the source item's Shopify Item Record. 
  
**Create and Overwrite (Update) Behavior** 
- None 
 
**Change Impact and Support Required** 
- Change can be made by a client. 
- Applies only to newly created items using "Copy From." 
  
---
 
### Default Product Status 
 
- **Column Name:** `DEFAULT_PRODUCT_STATUS`
- **Default Value:** Draft 
- **Default Type:** Recommended 
 
**Purpose** 
- Controls the default status assigned to products on Shopify when they are first synchronized from Counterpoint. 
 
**Valid Values** 
- **Draft** – Products are created on Shopify but are not visible to customers. 
- **Active** – Products are created and immediately available for sale on Shopify. 
- **Archived** – Products are created on Shopify but are not active and cannot be sold. 
 
**Recommendation** 
- Choose **draft**. It allows for review and enhance of products on Shopify before they are made available for sale. This is especially important for adding images and detailed product descriptions prior to publishing the product. 
 
**Notes** 
- This setting applies when products are first synchronized from Counterpoint to Shopify. 
- Product status can be changed later directly on Shopify. 
  
**Create and Overwrite (Update) Behavior** 
- None 
 
**Change Impact and Support Required** 
- Change can be made by a client. 
- Applies only to newly created Shopify Item Records. 
 
---
 
### Delete Item Type 
 
- **Column Name:** `DELETE_ITEM_TYPE` 
- **Default Value:** Archive 
- **Default Type:** Recommended 
 
**Purpose** 
- Controls how products on Shopify are handled when the corresponding Shopify Item Record in Counterpoint is deleted. 
 
**Valid Values** 
- **Archive** – Products are archived on Shopify and are no longer active or available for sale. 
- **Unpublish** – Products remain active on Shopify but are removed from all sales channels and are not visible to customers. 
- **Nothing** – No action is taken on Shopify; the product remains unchanged. 
 
**Recommendation** 
- Choose **archive**. This removes products from sale while preserving product data and history. It also helps prevent outdated or no longer synced products from remaining visible, while keeping them clearly segregated within Shopify. 
 
**Notes** 
- The connector will never delete products in Shopify; it can only archive or unpublish them. This is a safety mechanism to ensure the connector never fully removes a product from Shopify. 
- If a product needs to be permanently deleted, it must be deleted directly on Shopify. 
 
**Create and Overwrite (Update) Behavior** 
- When set to **Archive** or **Unpublish**, products on Shopify can be archived or unpublished by the connector. 
 
**Change Impact and Support Required** 
- Change can be made by a client. 
- Applies only to newly deleted Shopify Item Records. 
 
---
 
### Product Title Field 
 
- **Column Name:** `UPDATE_TITLE_FIELD` 
- **Default Value:** DESCR 
- **Default Type:** No Preference 
 
**Purpose** 
- Controls which field in Counterpoint is used to populate the product title on Shopify. 
 
**Valid Values** 
- **DESCR** – Uses the Description field in Counterpoint as the product title on Shopify. 
- **LONG_DESCR** – Uses the Long Description field in Counterpoint as the product title on Shopify. 
- **SHORT_DESCR** – Uses the Short Description field in Counterpoint as the product title on Shopify. 
- **ADDL_DESCR_1** – Uses the Additional Description 1 field in Counterpoint as the product title on Shopify. 
- **ADDL_DESCR_2** – Uses the Additional Description 2 field in Counterpoint as the product title on Shopify. 
- **ADDL_DESCR_3** – Uses the Additional Description 3 field in Counterpoint as the product title on Shopify. 
 
**Recommendation** 
- Choose the field that is best suited for use as a customer-facing product title on Shopify. This should be a field that is consistently populated and appropriate for ecommerce display. 
- Alternatively, choose a field that provides enough detail to be used during initial synchronization, with the understanding that the product title can then be edited on Shopify for improved clarity and customer-facing presentation. 
 
**Notes** 
- If the selected field is blank, the connector will use the **Description** field as a fallback when populating the product title on Shopify. 
- Product titles on Shopify are not required to be unique and have a maximum length of 255 characters. Most fields in Counterpoint have shorter character limits. 
- Whether the product title is sent only during the initial synchronization or on subsequent updates is controlled by the **Update Title** configuration setting. 
 
**Create and Overwrite (Update) Behavior** 
- Whether the product title is sent only during product creation or is updated on subsequent syncs is controlled by the **Update Title** config setting. 
 
**Change Impact and Support Required** 
- Consult Rapid staff. 
- If Update Title is Yes, a full resync is recommended to apply the updated product titles on Shopify. 
- If Update Title is No, this setting can be changed by a client and applies only to newly created Shopify Item Records. 
 
---
 
### Update Title 
 
- **Column Name:** `UPDATE_TITLE` 
- **Default Value:** N 
- **Default Type:** Recommended 
 
**Purpose** 
- Controls whether the product title on Shopify is updated when the corresponding item in Counterpoint is updated. 
 
**Valid Values** 
- **Yes** – The product title on Shopify will be updated based on the selected Product Title Field whenever the item is updated in Counterpoint. 
- **No** – The product title on Shopify will only be set during the initial synchronization and will not be updated on subsequent changes in Counterpoint. 
 
**Recommendation** 
- Choosing **no** allows product titles to be maintained directly on Shopify, which supports longer and more descriptive titles. Many fields in Counterpoint are designed for internal use and may not be ideal for customer-facing product titles. Managing titles on Shopify enables more detailed, customer-friendly, and searchable product names. 
- Choose **yes** only if the data in Counterpoint is consistently maintained at a level suitable for use as a customer-facing product title on Shopify and product titles will not be edited directly on Shopify. 
 
**Notes** 
- This setting works in conjunction with the **Product Title Field** configuration. 
- Shopify allows longer and more flexible product titles (up to 255 characters) compared to most fields in Counterpoint, which are typically limited to 30, 50 or 80 characters. 
 
**Create and Overwrite (Update) Behavior** 
- When set to **Yes**, product titles on Shopify will always be updated (overwritten) by the connector. 
- When set to **No**, product titles will only be sent to Shopify during product creation. Subsequent syncs will not update (overwrite) data on Shopify. 
 
**Change Impact and Support Required** 
- Changing from **Yes → No** can be done by a client. 
- Changing from **No → Yes** should be coordinated with Rapid staff. A full resync is recommended to apply the updated product titles on Shopify. 
 
---
 
### Product Inventory Qty 
 
- **Column Name:** `ITEM_QTY_METH` 
- **Default Value:** Item Qty Available 
- **Default Type:** Recommended 
 
**Purpose** 
- Controls which inventory quantity field in Counterpoint is used to populate product inventory levels on Shopify. 
 
**Valid Values** 
- **Item Qty Available** – Uses the available quantity in Counterpoint, which reflects stock available for sale. 
- **Item Qty on Hand** – Uses the on-hand quantity in Counterpoint, which reflects total physical stock without accounting for commitments (such as unposted tickets), allocations or reservations. 
 
**Recommendation** 
- Choose **Item Qty Available**. This ensures that inventory levels on Shopify reflect what is actually available for sale. It accounts for unposted tickets and other committed inventory, helping prevent overselling on Shopify. 
 
**Notes** 
- None 
 
**Create and Overwrite (Update) Behavior** 
- Quantity on Shopify will always be updated (overwritten) by the connector. 
 
**Change Impact and Support Required** 
- Consult Rapid staff. 
- A full resync is recommended to apply the updated inventory levels on Shopify. 
 
---
 
### Hide Out of Stock Inventory 
 
- **Column Name:** `HIDE_OUT_OF_STOCK_INVENTORY` 
- **Default Value:** N 
- **Default Type:** Common 
 
**Purpose** 
- Controls whether products on Shopify are hidden when their inventory quantity reaches zero. 
 
**Valid Values** 
- **Yes** – Products with zero inventory will be hidden on Shopify and will not be visible to customers. 
- **No** – Products with zero inventory will remain visible on Shopify but will be shown as out of stock. 
 
**Recommendation** 
- Choosing **no** keeps out-of-stock products visible. It allows customers to see that the product is carried, even if it is currently unavailable. This helps maintain product visibility and supports searchability and SEO. 
- However, if your products are not typically replenished once they are sold out, choosing **yes** may be preferred to avoid displaying unavailable products. 
 
**Notes** 
- This functionality works by removing the product from the **Online Sales Channel** on Shopify, which hides it from the customer-facing website. 
- This setting only applies to items where the item type in Counterpoint is **Inventory** and the **Continue Selling Out of Stock** option in the Shopify Item Record is not enabled. 
 
**Create and Overwrite (Update) Behavior** 
- When set to **Yes**, product visibility on Shopify will be updated (overwritten) by the connector. 
- When set to **No**, product visibility on Shopify will not be updated (overwritten) by the connector. 
 
**Change Impact and Support Required** 
- Consult Rapid staff. 
- A full resync is recommended to apply the updated product visibility on Shopify. 
 
---
 
### Product Price 
 
- **Column Name:** `ITEM_PRC_METH` 
- **Default Value:** Price-1 
- **Default Type:** Common 
 
**Purpose** 
- Controls which price in Counterpoint is used to populate the product price on Shopify. 
 
**Valid Values** 
- **Price-1** – Uses Price-1 as the product price on Shopify. 
- **Price-2** – Uses Price-2 as the product price on Shopify. 
- **Price-3** – Uses Price-3 as the product price on Shopify. 
- **Price-4** – Uses Price-4 as the product price on Shopify. 
- **Price-5** – Uses Price-5 as the product price on Shopify. 
- **Price-6** – Uses Price-6 as the product price on Shopify. 
- **Regular Price** – Uses Regular Price as the product price on Shopify. 
- **Calculated Price** – Uses the calculated price in Counterpoint based on a limited set of price rules (see documentation for more details). 
 
**Recommendation** 
- Typically **Price-1** is the standard selling price in Counterpoint. Use alternative price levels only if they are specifically configured for selling online. 
 
**Notes** 
- If the selected price level is blank for an item, the connector will use Price-1 as a fallback. 
- Price-4, Price-5, and Price-6 are only available in Counterpoint for clients with an Advanced Pricing subscription from NCR Counterpoint. 
 
**Create and Overwrite (Update) Behavior** 
- Price on Shopify will always be updated (overwritten) by the connector. 
 
**Change Impact and Support Required** 
- Consult Rapid staff. 
- A full resync is recommended to apply the updated pricing on Shopify. 
 
---
 
### Product Compare At Price 
 
- **Column Name:** `ITEM_COMPARE_AT_PRC_METH` 
- **Default Value:** Price-1 
- **Default Type:** No Preference 
 
**Purpose** 
- Controls which price in Counterpoint is used to populate the product "Compare At" price on Shopify. 
 
**Valid Values** 
- **Price-1** – Uses Price-1 as the product compare at price on Shopify. 
- **Price-2** – Uses Price-2 as the product compare at price on Shopify. 
- **Price-3** – Uses Price-3 as the product compare at price on Shopify. 
- **Price-4** – Uses Price-4 as the product compare at price on Shopify. 
- **Price-5** – Uses Price-5 as the product compare at price on Shopify. 
- **Price-6** – Uses Price-6 as the product compare at price on Shopify. 
- **Regular Price** – Uses Regular Price as the product compare at price on Shopify. 
- **Calculated Price** – Uses the calculated price in Counterpoint based on a limited set of price rules (see documentation for more details). 
 
**Recommendation** 
- To omit the Compare At Price, **select the same price field** used for the product price. Shopify will ignore the value when both prices are equal. 
- To display a Compare At Price, **select a price that is typically higher** than the product price. 
 
**Notes** 
- The Compare At Price on Shopify is typically used to display a higher “original” price alongside a lower selling price. 
- Shopify requires the Compare At Price to be greater than the product price. If a value equal to or lower than the product price is sent, Shopify will ignore it. 
- If the selected price level is blank for an item, the connector will use Price-1 as a fallback. 
 
**Create and Overwrite (Update) Behavior** 
- Compare At Price on Shopify will always be updated (overwritten) by the connector. 
 
**Change Impact and Support Required** 
- Consult Rapid staff. 
- A full resync is recommended to apply the updated pricing on Shopify. 
 
---
 
### Product Vendor Default 
 
- **Column Name:** `PRODUCT_VENDOR_DEFAULT` 
- **Default Value:** Primary Vendor Name 
- **Default Type:** No Preference 
 
**Purpose** 
- Controls the fallback vendor assigned to products on Shopify when the Product Vendor field on the Shopify Item Record in Counterpoint is blank. 
 
**Valid Values** 
- **Primary Vendor Name** – Uses the primary vendor from the Item Record in Counterpoint as the product vendor on Shopify (only when the Product Vendor field on the Shopify Item Record is blank).
- **None** – No value is sent to Shopify. Shopify will default the vendor to the store name.
 
**Recommendation** 
- Choose **Primary Vendor Name** if sending product vendor values from Counterpoint is helpful for organization or reporting in Shopify. 
- Choose **None** if you plan to regularly populate the Product Vendor field on the Shopify Item Record, or if you prefer Shopify to default the vendor to the store name. 
 
**Notes** 
- The Product Vendor field on the Shopify Item Record always takes priority over this (fallback) setting. This setting is only used when the Product Vendor field is left blank. 
- The product vendor on Shopify is typically not displayed on the customer-facing website and is most often used for internal organization and filtering within Shopify. 
- _Special Note:_ 
  - The Product Vendor field on the Shopify Item Record can be populated with any value and does not need to match a vendor in Counterpoint. 
  - Some clients use this field to store alternate values such as brand names instead of vendor names. 
 
**Create and Overwrite (Update) Behavior** 
- Product Vendor on Shopify will always be updated (overwritten) by the connector.
 
**Change Impact and Support Required** 
- Consult Rapid staff. 
- A full resync is recommended to apply the updated product vendor values on Shopify. 
 
---
 
### Filter Item Barcode by ID 
 
- **Column Name:** `BARCODE_ID_FILTER` 
- **Default Value:** _null_ 
- **Default Type:** No Preference 
 
**Purpose** 
- Controls which barcode from Counterpoint is selected and sent to Shopify based on barcode type. 
 
**Valid Values** 
- **[Null]** – Sends the first barcode listed in the barcode table for the item, regardless of barcode type. 
- **[Barcode Type]** – Sends the first barcode that matches the selected type. Configuration examples include **ITEM**, **UPC**, **SKU**, or any other type defined in the barcode table in Counterpoint. 
 
**Recommendation** 
- Select a specific barcode type to ensure a consistent and predictable barcode is sent to Shopify.
- Counterpoint allows only one barcode with a type of **ITEM** per item, making it the most consistent and predictable option. Using ITEM ensures the same barcode is always sent to Shopify.
- If multiple barcodes exist for other types (such as UPC), it may be difficult to control which barcode is listed first in Counterpoint and therefore which one is sent to Shopify.
- If many items do not have a barcode defined with a type of ITEM, consider using another type or leaving this value as Null so that at least the first available barcode is sent to Shopify.
 
**Notes** 
- Items in Counterpoint can have multiple barcodes, each optionally assigned a type. 
- When a specific barcode type is selected, the connector will send the first barcode that matches that type. 
- When set to Null, the connector will send the first available barcode regardless of type. 
 
**Create and Overwrite (Update) Behavior** 
- Barcode on Shopify will always be updated (overwritten) by the connector. 
 
**Change Impact and Support Required** 
- Consult Rapid staff. 
- A full resync is recommended to apply the updated barcodes on Shopify. 
 
---
 
### Handle Definition Query 
 
- **Column Name:** `HANDLE_DEFINITION_QUERY` 
- **Default Value:** _null_ 
- **Default Type:** No Preference 
 
**Purpose** 
- Controls how the product handle (URL slug) is generated for products on Shopify. 
 
**Valid Values** 
- **[Null]** – Uses the Item Number from Counterpoint as the fallback product handle on Shopify. 
- **[Query]** – Uses the configured query to generate the product handle on Shopify. This might include some combination of multiple fields from Counterpoint such as description and item number or long description and item number. 
- _Query Output Examples:_ 
  - website.com/Description-ItemNumber 
  - website.com/LongDescription-ItemNumber 
 
**Recommendation** 
- Use a **query** that generates customer-friendly, descriptive handles if product URLs are important for SEO or usability. 
- Otherwise, using the fallback of Item Number provides a simple and consistent default. Based on the **Update Handle** setting, the handle can then be customized on Shopify if a more descriptive value is desired. 
 
**Notes** 
- The product handle on Shopify is used in the product URL and should be unique and URL-friendly. When using a query, including the Item Number as part of the URL can help ensure the handle remains unique. 
- Whether the handle is updated after the initial synchronization is controlled by the **Update Handle** configuration setting. 
 
**Create and Overwrite (Update) Behavior** 
- Whether the handle is sent only during product creation or is updated on subsequent syncs is controlled by the **Update Handle** config setting. 
 
**Change Impact and Support Required** 
- Consult Rapid staff. 
- This query should be written and reviewed by Rapid staff. 
- If Update Handle is Yes, a full resync is recommended to apply the updated handles on Shopify. 
- If Update Handle is No, this setting applies only to newly created Shopify Item Records. 
 
---
 
### Update Handle 
 
- **Column Name:** `UPDATE_HANDLE` 
- **Default Value:** N 
- **Default Type:** No Preference 
 
**Purpose** 
- Controls whether the product handle (URL slug) on Shopify is updated when the corresponding item in Counterpoint is updated. 
 
**Valid Values** 
- **Yes** – The product handle on Shopify will be updated based on the Handle Definition Query when the item is updated in Counterpoint. 
- **No** – The product handle on Shopify will only be set during the initial synchronization and will not be updated on subsequent changes. 
 
**Recommendation** 
- Choose **yes** if the handle is derived from data in Counterpoint (such as description or naming conventions) and should stay in sync as that data changes. 
- Choose **no** if handles are edited or managed directly on Shopify, or if maintaining stable URLs is important for SEO and external links. 
 
**Notes** 
- This setting works in conjunction with the **Handle Definition Query** configuration. Changes to the query or underlying data in Counterpoint will only be reflected on Shopify if this setting is set to Yes. 
 
**Create and Overwrite (Update) Behavior** 
- When set to **Yes**, product handles on Shopify will always be updated (overwritten) by the connector. 
- When set to **No**, product handles will only be sent to Shopify during product creation. Subsequent syncs will **not** update (overwrite) data on Shopify. 
 
**Change Impact and Support Required** 
- Changing from **Yes → No** can be done by a client. 
- Changing from **No → Yes** should be coordinated with Rapid staff. A full resync is recommended to apply the updated handles on Shopify. 
 
---
 
### Update Html Description 
 
- **Column Name:** `UPDATE_HTML_DESCR` 
- **Default Value:** N 
- **Default Type:** Recommended 
 
**Purpose** 
- Controls whether the HTML description on Shopify is updated when the corresponding Shopify Item Record in Counterpoint is updated. 
 
**Valid Values** 
- **Yes** – The HTML Description field on the Shopify Item Record in Counterpoint will overwrite the product description on Shopify when updated. 
- **No** – The HTML Description will only be set during the initial synchronization and will not overwrite changes made on Shopify. 
 
**Recommendation** 
- Choose **no**. It is easier to manage product descriptions directly on Shopify, where a WYSIWYG editor allows for easier formatting and content management without requiring HTML. 
 
**Notes** 
- The HTML Description field on the Shopify Item Record in Counterpoint allows for plain text or HTML-formatted content to be entered. 
- This value is sent to Shopify when the product is first synchronized. 
- When this setting is enabled, any updates to the HTML Description in Counterpoint will overwrite the existing product description on Shopify. 
 
**Create and Overwrite (Update) Behavior** 
- When set to **Yes**, product descriptions on Shopify will always be updated (overwritten) by the connector. 
- When set to **No**, product descriptions will only be sent to Shopify during product creation. Subsequent syncs will **not** update (overwrite) data on Shopify. 
 
**Change Impact and Support Required** 
- Changing from **Yes → No** can be done by a client. 
- Changing from **No → Yes** should be coordinated with Rapid staff. A full resync is recommended to apply the updated HTML descriptions on Shopify. 
 
---
 
### Item Categories as Product Type 
 
- **Column Name:** `ITEM_CATEG_AS_PRODUCT_TYPE` 
- **Default Value:** N 
- **Default Type:** No Preference 
 
**Purpose** 
- Controls whether item categories in Counterpoint are used to populate the product type on Shopify. 
 
**Valid Values** 
- **Yes** – The item category from Counterpoint will be used as the product type on Shopify. 
- **No** – The product type on Shopify will not be populated from item categories. 
 
**Recommendation** 
- Choose **yes** if it is helpful to sync the item category to the product type on Shopify. 
- Choose **no** if product types are managed directly on Shopify or if item categories in Counterpoint do not reflect how products should be organized on Shopify. 
 
**Notes** 
- While the item category in Counterpoint is limited to a 10-character code, when this setting is enabled, the connector sends the full description of that code as the product type on Shopify. 
- The product type on Shopify is used for internal organization, filtering, and reporting. It is not commonly displayed on the customer-facing website. 
 
**Create and Overwrite (Update) Behavior** 
- When set to **Yes**, product type on Shopify will always be updated (overwritten) by the connector. 
- When set to **No**, product type will **not** update (overwrite) data on Shopify. 
 
**Change Impact and Support Required** 
- Consult Rapid staff. 
- A full resync is recommended to apply the updated product type on Shopify. 
 
---
 
### Sub-Categories To Collections 
 
- **Column Name:** `SUBCAT_TO_COLLECTIONS` 
- **Default Value:** N 
- **Default Type:** Recommended 
 
**Purpose** 
- Controls whether sub-categories in Counterpoint are used to create or assign collections on Shopify. 
 
**Valid Values** 
- **Yes** – The sub-category from Counterpoint will be used to create and assign products to collections on Shopify. 
- **No** – Sub-categories will not be used to create or assign collections on Shopify. 
 
**Recommendation** 
- Choose **no** if collections are managed directly on Shopify or if sub-categories in Counterpoint do not reflect ecommerce navigation or merchandising needs. 
- Only choose **yes** if sub-categories in Counterpoint are well-structured and align with how products should be grouped and displayed on Shopify. 
 
**Notes** 
- The connector sends the description of the code, not the sub-category code. 
- If the sub-category for an item is changed in Counterpoint, the product will be added to the new collection on Shopify, but it will not be removed from any existing collections. The connector only adds products to collections and does not remove collections. 
 
**Create and Overwrite (Update) Behavior** 
- When set to **Yes**, subcategories will be added on Shopify as collections. Existing collections will not be updated (overwritten) by the connector. 
- When set to **No**, subcategories will not be added on Shopify as collections. Existing collections will not be updated (overwritten) by the connector. 
 
**Change Impact and Support Required** 
- Changing from **Yes → No** can be done by a client and applies only to newly created Shopify Item Records (existing collections must be manually removed on Shopify). 
- Changing from **No → Yes** should be coordinated with Rapid staff. A full resync is recommended to apply the updated collections on Shopify. 
 
---
 
### Use Item Attributes For Tags 
 
- **Column Name:** `USE_ITEM_ATTRIBUTES_AS_TAGS` 
- **Default Value:** N 
- **Default Type:** Recommended 
 
**Purpose** 
- Controls whether all six item attributes in Counterpoint are used to populate product tags on Shopify. 
 
**Valid Values** 
- **Yes** – All item attribute fields from Counterpoint will be used to populate product tags on Shopify. 
- **No** – Item attributes will not be used to populate product tags on Shopify. 
 
**Recommendation** 
- Choose **no**. Most clients do not have consistent attribute data, which can lead to cluttered tags. Managing tags on Shopify or using custom metafields to sync specific item attributes is typically a better approach. 
 
**Notes** 
- Product tags on Shopify are used for filtering, search, and automated collection rules and are often managed directly on Shopify. 
- Instead of syncing attributes as tags, many clients prefer to sync specific attributes as metadata using the custom mapping table (a separate configuration option). 
- Up to six item attribute fields can be defined per item in Counterpoint. When enabled, these are located on the Description tab of the Item Record. Example item attributes include values such as brand or color, and are defined and customized per client. Most clients do not use all six fields. 
- When this setting is enabled, all populated attribute values will be sent to Shopify as product tags. 
- The connector sends the description of the attribute value, not the attribute code. 
- If an attribute value is changed in Counterpoint, a new tag will be added on Shopify, but existing tags will not be removed. The connector only adds tags and does not delete them. 
- Instead of using attribute fields, some clients choose to populate tags on the Shopify Item Record or directly on Shopify. 
 
**Create and Overwrite (Update) Behavior** 
- When set to **Yes**, item attributes will be added on Shopify as tags. Existing tags will not be updated (overwritten) by the connector. 
- When set to **No**, item attributes will not be added on Shopify as tags. Existing tags will **not** be updated (overwritten) by the connector. 
 
**Change Impact and Support Required** 
- Changing from **Yes → No** can be done by a client and applies only to newly created Shopify Item Records (existing tags must be manually removed on Shopify). 
- Changing from **No → Yes** should be coordinated with Rapid staff. A full resync is recommended to apply the updated tags on Shopify. 
 
---
 
### Tags Item Field 
 
- **Column Name:** ITEM_FIELD_TO_TAGS 
- **Default Value:** _null_ 
- **Default Type:** Recommended 
 
**Purpose** 
- Controls which single field in Counterpoint is used to populate a product tag on Shopify. 
 
**Valid Values** 
- **[Null]** – No additional tag will be sent from a Counterpoint field. 
- **[Item Field]** – The selected field from the Item Record in Counterpoint will be sent as a product tag on Shopify. 
 
**Recommendation** 
- Do not use this setting unless there is a single field in Counterpoint that consistently maps to a meaningful tag on Shopify. In most cases, this can lead to inconsistent or less useful tags, and alternative approaches such as managing tags on Shopify or using custom metafields are preferred. 
 
**Notes** 
- Only one field can be selected using this setting. 
- If a field such as a category, profile code, or attribute code is selected, the code value will be sent, not the description. 
 
**Create and Overwrite (Update) Behavior** 

 
**Change Impact and Support Required** 
- Changing from **[Item Field] → [Null]** can be done by a client and applies only to newly created Shopify Item Records (existing tags must be manually removed on Shopify). 
- Changing from **[Null] → [Item Field]** should be coordinated with Rapid staff. A full resync is recommended to apply the updated tags on Shopify. 
 
---
 
### Product Metafield Namespace 
 
- **Column Name:** `PRODUCT_METAFIELD_NAMESPACE` 
- **Default Value:** Rapid 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Controls the namespace used when creating product metafields on Shopify. 
 
**Valid Values** 
- **Rapid** – Uses the default namespace for all product metafields created by the connector. 
- **[Custom Value]** – Uses a custom namespace for product metafields on Shopify; however, using a custom value is not recommended and would need to be quoted separately. 
 
**Recommendation** 
The standard namespace used by the connector is "**Rapid**" and should not be changed. Using a consistent namespace ensures compatibility and prevents conflicts with other metafields or integrations. 
 
**Notes** 
- This setting is used in conjunction with custom field mappings from Counterpoint, where item fields are synced as product metafields on Shopify. 
- Shopify metafields use a combination of namespace (prefix) and key to uniquely identify each field. 
- The connector uses the namespace as a prefix when creating metafields (e.g., rapid.brand, rapid.color). 
- Namespaces help organize metafields and prevent naming conflicts with other apps or data. 
 
**Create and Overwrite (Update) Behavior** 
- When the custom mapping table is used to create product metafields on Shopify, those fields will always be updated (overwritten) by the connector. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
### [↑ Back to Top](#quick-links)
 
---
 
## Orders Down 
 
### Add Orders Down 
 
- **Column Name:** `ADD_ORDERS_DOWN` 
- **Default Value:** Y 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Controls whether orders on Shopify are imported into Counterpoint. 
 
**Valid Values** 
- **Yes** – Orders on Shopify will be imported into Counterpoint. 
- **No** – Orders on Shopify will not be imported into Counterpoint. 
 
**Recommendation** 
- Choose **yes**. This should always be set to yes to ensure that orders are always imported into Counterpoint. 
- Choosing no will require approval as well as additional configuration and testing, which will result in billable services from Rapid. 
 
**Notes** 
- This setting is typically used by Rapid staff for troubleshooting to temporarily disable order synchronization and should not be adjusted by clients. 
 
**Create and Overwrite (Update) Behavior** 
- When set to **Yes**, orders on Shopify will be imported (created) in Counterpoint by the connector. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Use Shopify Order Number as Ticket # 
 
- **Column Name:** `USE_SHOPIFY_ORDER_NO_AS_TKT_NO` 
- **Default Value:** Y 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Controls whether the Shopify order number is used as the order number in Counterpoint. 
 
**Valid Values** 
- **Yes** – The Shopify order number will be used as the Counterpoint order number. 
- **No** – Counterpoint will use the next available order number based on the Store order number configuration. 
 
**Recommendation** 
- Choose **yes**. Using the Shopify order number ensures consistency between Shopify and Counterpoint and simplifies order tracking and customer support. 
 
**Notes** 
- Shopify allows a prefix to be added to order numbers. It is recommended to keep this prefix to four or fewer characters. Otherwise, if the resulting order number is too long, Counterpoint may be unable to process it, which can prevent orders from being imported. 
 
**Create and Overwrite (Update) Behavior** 
- Used when importing (creating) orders in Counterpoint. 
- Changes do **not** update (overwrite) existing orders in Counterpoint. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Order Source 
 
- **Column Name:** `ORDER_SOURCE` 
- **Default Value:** All 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Controls which Shopify sales channels are used when importing orders into Counterpoint. 
 
**Valid Values** 
- **All** – Orders from all sales channels will be imported into Counterpoint. 
- **Web** – Only orders from the Online Store sales channel will be imported. 
- **POS** – Only orders from the Shopify POS sales channel will be imported. 
 
**Recommendation** 
- This will be set to All to ensure all orders are consistently imported into Counterpoint without additional filtering. 
- Selecting a more restrictive option (Web or POS) may require additional configuration and testing, which will result in billable services from Rapid. 
 
**Notes** 
- None 
 
**Create and Overwrite (Update) Behavior** 
- Used when importing (creating) orders in Counterpoint. 
- Changes do **not** update (overwrite) existing orders in Counterpoint. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Customer Shopify Notes to Document Notes 
 
- **Column Name:** `ORDER_NOTE` 
- **Default Value:** Y 
- **Default Type:** Common 
 
**Purpose** 
- Controls whether customer-entered order notes from Shopify are saved as document notes in Counterpoint. 
 
**Valid Values** 
- **Yes** – The Shopify order note entered during checkout will be saved as a document note on the order in Counterpoint. 
- **No** – The Shopify order note will not be saved in Counterpoint. 
 
**Recommendation** 
- Choose **yes**. This ensures customer-provided notes (such as special instructions) are available in Counterpoint for order review and processing.
- Chose **no** if customer notes are not needed or are managed separately.
 
**Notes** 
- Customers can enter notes during checkout on Shopify, which may include special instructions or additional information. 
- When enabled, these notes are stored in Counterpoint for reference on the order. A Counterpoint user must open the document note to review the content (no notification or pop-up is generated). 
 
**Create and Overwrite (Update) Behavior** 
- Used when importing (creating) orders in Counterpoint. 
- Changes do **not** update (overwrite) existing orders in Counterpoint. 
 
**Change Impact and Support Required** 
- Change can be made by a client. 
- Applies only to newly imported Shopify orders. 
 
---
 
### Store 
 
- **Column Name:** `STR_ID` 
- **Default Value:** 201 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Controls which store in Counterpoint is assigned to orders imported from Shopify. 
 
**Valid Values** 
- **[Store ID]** – The selected store in Counterpoint will be assigned to all imported Shopify orders. 
 
**Recommendation** 
- This will be set to store **201** to ensure consistency amongst clients. Rapid staff are trained to recognize store 201 as the designated Shopify store. 
- Choosing a different store number will require approval as well as additional configuration and testing, which will result in billable services from Rapid. 
 
**Notes** 
- It is important to use a dedicated store for Shopify orders to support accurate tracking and reporting. Orders can still be reviewed and fulfilled from other stores in Counterpoint as needed. 
- Store 201 is the default store created by the installer for Shopify orders in Counterpoint. 
- This store will be used for Shopify orders and will be saved as the store number in the order header. 
 
**Create and Overwrite (Update) Behavior** 
- Used when importing (creating) orders in Counterpoint. 
- Changes do **not** update (overwrite) existing orders in Counterpoint. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Station 
 
- **Column Name:** `STA_ID` 
- **Default Value:** 201-01 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Controls which station in Counterpoint is assigned to orders imported from Shopify. 
 
**Valid Values** 
- **[Station ID]** – The selected station in Counterpoint will be assigned to all imported Shopify orders. 
 
**Recommendation** 
- This will be set to station **201-01** to ensure consistency amongst clients. Rapid staff are trained to recognize station 201-01 as the designated Shopify station. 
- Choosing a different station number will require approval as well as additional configuration and testing, which will result in billable services from Rapid. 
 
**Notes** 
- It is important to use a dedicated station for Shopify orders to support accurate tracking and reporting. Orders can still be reviewed and fulfilled from other stores and stations in Counterpoint as needed. 
- Station 201-01 is the default station created by the installer for Shopify orders in Counterpoint. 
- This station will be used for Shopify orders and will be saved as the station number in the order header. 
 
**Create and Overwrite (Update) Behavior** 
- Used when importing (creating) orders in Counterpoint. 
- Changes do **not** update (overwrite) existing orders in Counterpoint. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Drawer 
 
- **Column Name:** DRW_ID 
- **Default Value:** 201-01 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Controls which drawer in Counterpoint is assigned to orders imported from Shopify. 
 
**Valid Values** 
- **[Drawer ID]** – The selected drawer in Counterpoint will be assigned to all imported Shopify orders. 
 
**Recommendation** 
- This will be set to drawer **201-01** to ensure consistency amongst clients. Rapid staff are trained to recognize drawer 201-01 as the designated Shopify drawer. 
- Choosing a different drawer number will require approval as well as additional configuration and testing, which will result in billable services from Rapid. 
 
**Notes** 
- It is important to use a dedicated drawer for Shopify orders to support accurate tracking and reporting. Orders can still be reviewed and fulfilled from other stores, stations, and drawers in Counterpoint as needed. 
- Drawer 201-01 is the default drawer created by the installer for Shopify orders in Counterpoint. 
- This drawer will be used for Shopify orders and will be saved as the drawer number in the order header. 
 
**Create and Overwrite (Update) Behavior** 
- Used when importing (creating) orders in Counterpoint. 
- Changes do **not** update (overwrite) existing orders in Counterpoint. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### User 
 
- **Column Name:** `USR_ID` 
- **Default Value:** EC_SHOPIFY 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Controls which user in Counterpoint is assigned to orders imported from Shopify. 
 
**Valid Values** 
- **[User ID]** – The selected user in Counterpoint will be assigned to all imported Shopify orders. 
 
**Recommendation** 
- This will be set to user **EC_SHOPIFY** to ensure consistency amongst clients. Rapid staff are trained to recognize user EC_SHOPIFY as the designated Shopify user. 
- Choosing a different user will require approval as well as additional configuration and testing, which will result in billable services from Rapid. 
 
**Notes** 
- It is important to use a dedicated user for Shopify orders to support accurate tracking and reporting. The EC_SHOPIFY user cannot login to Touchscreen. Orders must be reviewed and fulfilled by actual users in Counterpoint. 
- User EC_SHOPIFY is the default user created by the installer for Shopify orders in Counterpoint. 
- This user will be assigned to Shopify orders and recorded as the user who created the order in the order header. 
 
**Create and Overwrite (Update) Behavior** 
- Used when importing (creating) orders in Counterpoint. 
- Changes do not update (overwrite) existing orders in Counterpoint. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Shipping Misc Chrg # 
 
- **Column Name:** `MISC_CHRG_NO_FOR_SHIPPING` 
- **Default Value:** 4 
- **Default Type:** Common 
 
**Purpose** 
- Controls which miscellaneous charge in Counterpoint is used to record shipping charges from Shopify orders. 
 
**Valid Values** 
- **[Misc Charge #]** – The selected miscellaneous charge number will be used to record shipping charges on imported Shopify orders. 
 
**Recommendation** 
- **Misc Charge 4** is typically configured as the shipping charge and is the most common setup. Alternative miscellaneous charge numbers (1, 2, 3, or 5) may be used if preferred. 
 
**Notes** 
- Shipping charges calculated by Shopify will be imported into Counterpoint as a miscellaneous charge on the order. 
- To ensure shipping charges import correctly, the selected miscellaneous charge must be configured in all of the following locations in Counterpoint: 
  - System > Quick Setup > Point of Sale Tab > Misc Charges 
  - Setup > POS > Point of Sale Control > Misc Charges > Misc Charge 
  - Setup > POS > Stores > Shopify Store > Misc Charges Tab > Misc Chg 
 
**Create and Overwrite (Update) Behavior** 
- Used when importing (creating) orders in Counterpoint. 
- Changes do not update (overwrite) existing orders in Counterpoint. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Pay Code 
 
- **Column Name:** `PAYCOD_ID` 
- **Default Value:** EC_SHOPIFY 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Controls which pay code in Counterpoint is assigned to orders imported from Shopify. 
 
**Valid Values** 
- **[Pay Code ID]** – The selected pay code in Counterpoint will be assigned to all imported Shopify orders. 
 
**Recommendation** 
- This will be set to pay code **EC_SHOPIFY** to ensure consistency amongst clients. Rapid staff are trained to recognize pay code EC_SHOPIFY as the designated Shopify pay code. 
- Choosing a different pay code will require approval as well as additional configuration and testing, which will result in billable services from Rapid. 
 
**Notes** 
- It is important to use a dedicated pay code for Shopify orders to support accurate tracking and reporting. 
- EC_SHOPIFY is the default pay code, created by the installer for Shopify orders in Counterpoint. 
- This pay code will be assigned to Shopify orders and recorded in the order header to indicate payment was collected on Shopify, representing the “paid on Shopify” tender. 
 
**Create and Overwrite (Update) Behavior** 
- Used when importing (creating) orders in Counterpoint. 
- Changes do **not** update (overwrite) existing orders in Counterpoint. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Order Line Item Description Column 
 
- **Column Name:** `ORDER_LINE_ITEM_DESCR_COLUMN` 
- **Default Value:** _null_ 
- **Default Type:** Common 
 
**Purpose** 
- Controls which field is used for the line item description on orders imported into Counterpoint. 
 
**Valid Values** 
- **[Null]** – Uses the product title from Shopify as the line item description on imported orders. 
- **DESCR** – Uses the Description field from Counterpoint as the line item description. 
- **LONG_DESCR** – Uses the Long Description field from Counterpoint as the line item description. 
 
**Recommendation** 
- **DESCR** is the recommended option, as it aligns with the line item description typically used in Counterpoint. This ensures consistency across orders, even if product titles on Shopify differ from item descriptions in Counterpoint. 
- Use **Null** if it is important for the order in Counterpoint to match exactly what the customer saw during checkout for the Shopify product title. 
 
**Notes** 
- By default, the product title from Shopify is used as the line item description when orders are imported into Counterpoint. 
- If the **Update Title** setting is set to **No**, product titles on Shopify may differ from item descriptions in Counterpoint. 
- When a value is selected, that field from Counterpoint will override the Shopify product title for the line item description on imported orders. 
 
**Create and Overwrite (Update) Behavior** 
- Used when importing (creating) orders in Counterpoint. 
- Changes do **not** update (overwrite) existing orders in Counterpoint. 
 
**Change Impact and Support Required** 
- Change can be made by a client. 
- Applies only to newly imported Shopify orders. 
- Consult Rapid staff if guidance is needed on entering the appropriate field name. 
 
---
 
### Match by Item # 
 
- **Column Name:** `MATCH_BY_ITEM_NO` 
- **Default Value:** Y 
- **Default Type:** Recommended 
 
**Purpose** 
- Controls whether the connector attempts to match Shopify order line items to Counterpoint items using the Shopify SKU mapped to the Counterpoint Item Number when a primary match is not found. 
 
**Valid Values** 
- **Yes** – If no match is found using the Shopify Variant ID or Shopify Product ID, the connector will attempt to match the Shopify line item SKU to a Counterpoint item number. 
- **No** – The connector will not attempt an additional match if the primary match fails. 
 
**Recommendation** 
- Choose **yes**. This provides a fallback matching method and can help prevent unmatched items during order import. 
 
**Notes** 
- When importing orders, the connector first attempts to match products using the Shopify Variant ID. If no match is found, it then attempts to match using the Shopify Product ID. 
- This setting acts as a fallback mechanism for improperly configured Shopify products, as the Shopify Variant ID and/or Product ID should normally match to Counterpoint. 
- If no match is found and this setting is enabled, the connector will then attempt to match the Shopify line item SKU to a Counterpoint item number. 
 
**Create and Overwrite (Update) Behavior** 
- Used when importing (creating) orders in Counterpoint. 
- Changes do **not** update (overwrite) existing orders in Counterpoint. 
 
**Change Impact and Support Required** 
- Change can be made by a client. 
- Applies only to newly imported Shopify orders. 
 
---
 
### Match by Barcode 
 
- **Column Name:** `MATCH_BY_BARCOD` 
- **Default Value:** Y 
- **Default Type:** Recommended 
 
**Purpose** 
- Controls whether the connector attempts to match Shopify order line items to Counterpoint items using the Shopify SKU mapped to a barcode in Counterpoint when a primary match is not found. 
 
**Valid Values** 
- **Yes** – If no match is found using the Shopify Variant ID or Shopify Product ID, the connector will attempt to match the Shopify line item SKU to a barcode in Counterpoint. 
- **No** – The connector will not attempt an additional match if the primary match fails. 
 
**Recommendation** 
- Choose **yes**. This provides a fallback matching method and can help prevent unmatched items during order import. 
 
**Notes** 
- When importing orders, the connector first attempts to match products using the Shopify Variant ID. If no match is found, it then attempts to match using the Shopify Product ID. 
- This setting acts as a fallback mechanism for improperly configured Shopify products, as the Shopify Variant ID and/or Product ID should normally match to Counterpoint. 
- If no match is found and this setting is enabled, the connector will then attempt to match the Shopify line item SKU to a barcode in Counterpoint. 
 
**Create and Overwrite (Update) Behavior** 
- Used when importing (creating) orders in Counterpoint. 
- Changes do **not** update (overwrite) existing orders in Counterpoint. 
 
**Change Impact and Support Required** 
- Change can be made by a client. 
- Applies only to newly imported Shopify orders. 
 
---
 
### Interim Item # 
 
- **Column Name:** `INTERIM_ITEM_NO` 
- **Default Value:** SHOPIFY_INTERIM_ITEM 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Controls which Counterpoint item number is used as a placeholder when a Shopify order line item cannot be matched to an item in Counterpoint. 
 
**Valid Values** 
- **[Item Number]** – The selected item number will be used as a placeholder for any unmatched line items. 
- **Null** – Orders with unmatched items will not be imported into Counterpoint. 
 
**Recommendation** 
- Use the default value of **SHOPIFY_INTERIM_ITEM** to allow orders with unmatched items to be imported and reviewed. 
- Only use **null** if unmatched items should prevent the order from being imported into Counterpoint. 
 
**Notes** 
- When an order is downloaded, each line item is checked for a match in Counterpoint. If no match is found, the connector will use this value as the Counterpoint Item Number for that line. 
- The default value is SHOPIFY_INTERIM_ITEM and should not be changed. 
- This placeholder item allows the order to be imported, but the order cannot be released until the interim item is replaced with a valid Counterpoint item. 
- If Import Orders as Tickets is set to Yes, this value must be left null. In that case, orders containing unmatched items will error out and will not be imported into Counterpoint. 
 
**Create and Overwrite (Update) Behavior** 
- Used when importing (creating) orders in Counterpoint. 
- Changes do **not** update (overwrite) existing orders in Counterpoint. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
### [↑ Back to Top](#quick-links)
 
---
 
## Orders Up
 
### Update Orders Up 
 
- **Column Name:** `UPDATE_ORDERS_UP` 
- **Default Value:** N 
- **Default Type:** No Preference 
 
**Purpose** 
- Controls whether line-level order fulfillment in Counterpoint is pushed up to Shopify. 
 
**Valid Values** 
- **Yes** – When order lines are released in Counterpoint, the fulfilled quantities will be sent up to Shopify at the line level. Shopify will use this information to mark orders as fulfilled or partially fulfilled. 
- **No** – Fulfillment quantities will not be sent to Shopify. Orders must be marked as fulfilled manually in Shopify. 
 
**Recommendation** 
- Choose **yes** to automate fulfillment updates from Counterpoint to Shopify and keep order status automatically aligned between systems. 
- Choose **no** if fulfillment is managed directly in Shopify or if order edits in Counterpoint are common. 
 
**Notes** 
- This setting pushes fulfillment from Counterpoint up to Shopify, not the other way around. 
- When enabled, fulfillment updates in Counterpoint (released tickets) will be reflected in Shopify and may trigger customer notifications (such as fulfillment emails). 
- Only items that match the original Shopify order can be fulfilled. If an order line is edited in Counterpoint, the updated line will not be reflected in Shopify, and the order must be marked as fulfilled manually in Shopify. 
- If an order contains the SHOPIFY_INTERIM_ITEM, the line must be replaced with the correct item before fulfillment can be sent to Shopify. Because this requires editing the line, the update will not be reflected in Shopify. 
 
**Create and Overwrite (Update) Behavior** 
- When set to **Yes**, orders on Shopify will be updated (overwritten) by the connector to have lines marked as fulfilled when the specific requirements are met. 
- When set to **No**, Counterpoint will **not** update (overwrite) fulfillment data on Shopify. 
 
**Change Impact and Support Required** 
- Change can be made by a client. 
- Applies only to newly released lines in Counterpoint. 
 
---
 
### Add Refunds Up 
 
- **Column Name:** `ADD_REFUNDS_UP` 
- **Default Value:** N 
- **Default Type:** No Preference 
 
**Purpose** 
- Controls whether validated returns in Counterpoint are pushed up to Shopify to automatically process refunds on the original order. 
 
**Valid Values** 
- **Yes** – Validated returns in Counterpoint using the EC_SHOPIFY pay code will be sent up to Shopify. Shopify will automatically process the refund to the original payment method used on the order. 
- **No** – Validated returns will not be sent to Shopify. Refunds must be processed either directly in Shopify or manually in Counterpoint. 
 
**Recommendation** 
- Choose **yes** if validated returns are processed in Counterpoint and refunds should be automatically applied to the original Shopify order and payment method. 
- Choose **no** if refunds are managed directly in Shopify or if returns are commonly processed using alternate payment methods (such as cash or in-store credit). 
 
**Notes** 
- This setting pushes order refunds from Counterpoint up to Shopify, not the other way around. 
- This applies to validated returns created from both posted and unposted tickets in Counterpoint. 
- Only lines that match the original Shopify order can be updated from Counterpoint. If an order line is edited in Counterpoint, the returned line will not be reflected in Shopify, and the line must be marked as returned manually in Shopify. 
- When enabled, only returns using the EC_SHOPIFY pay code will be sent to Shopify. These will be applied to the original form of payment (such as the customer’s credit card). 
- Returns processed with other pay codes (such as CASH) are assumed to be handled outside of Shopify and will not trigger a refund to the original payment method. 
 
**Create and Overwrite (Update) Behavior** 
- When set to **Yes**, orders on Shopify will be updated (overwritten) by the connector to have lines marked as refunded when the specific requirements are met. 
- When set to **No**, Counterpoint will not update (overwrite) refund data on Shopify. 
 
**Change Impact and Support Required** 
- Change can be made by a client. 
- Applies only to newly refunded lines in Counterpoint. 
- Consult Rapid staff if guidance is needed on accessing the EC_SHOPIFY pay code in Touchscreen. 
 
---
 
### Add Cancelled Orders Up 
 
- **Column Name:** `ADD_CANCELLED_ORDERS_UP` 
- **Default Value:** N 
- **Default Type:** No Preference 
 
**Purpose** 
- Controls whether order cancellations in Counterpoint are pushed up to Shopify to automatically cancel the original order and process a refund. 
 
**Valid Values** 
- **Yes** – Order cancellations in Counterpoint that use the EC_SHOPIFY pay code for the associated refund will be sent up to Shopify. Shopify will automatically process the refund to the original payment method used on the order. 
- **No** – Order cancellations in Counterpoint will not be sent to Shopify. Orders must be cancelled manually in Shopify. 
 
**Recommendation** 
- Choose **yes** if order cancellations are processed in Counterpoint and refunds should be automatically applied to the original Shopify order and payment method. 
- Choose **no** if cancelled orders and their associated refunds are managed directly in Shopify or if returns are commonly processed using alternate payment methods (such as cash or in-store credit). 
 
**Notes** 
- This setting pushes order cancellations from Counterpoint up to Shopify, not the other way around.
- When enabled, cancelling an order in Counterpoint will update the order status in Shopify.
- Only orders that match the original Shopify order can be cancelled from Counterpoint. If an order is edited in Counterpoint, the order cancellation will not be reflected in Shopify, and the order must be marked as cancelled manually in Shopify.
- When enabled, only refunds using the EC_SHOPIFY pay code from canceled orders in Counterpoint will be sent to Shopify. These will be applied to the original order and returned to the original form of payment (such as the customer’s credit card). 
- Refunds processed with other pay codes (such as CASH) are assumed to be handled outside of Shopify and will not trigger a refund to the original payment method.
 
**Create and Overwrite (Update) Behavior** 
- When set to **Yes**, orders on Shopify will be updated (overwritten) by the connector as cancelled when the specific requirements are met. 
- When set to **No**, Counterpoint will not update (overwrite) cancellation data on Shopify. 
 
**Change Impact and Support Required** 
- Change can be made by a client. 
- Applies only to newly canceled orders in Counterpoint. 
- Consult Rapid staff if guidance is needed on accessing the EC_SHOPIFY pay code in Touchscreen. 
 
### [↑ Back to Top](#quick-links)
 
---
 
## Customers Down 
 
### Workgroup 
 
- **Column Name:** `WRKGRP_ID` 
- **Default Value:** 201 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
-  Controls which workgroup in Counterpoint is used by the connector when processing Shopify orders and creating customers. 
 
**Valid Values** 
- **[Workgroup ID]** – The selected workgroup in Counterpoint will be used by the connector for processing Shopify orders. 
 
**Recommendation** 
-  This will be set to workgroup **201** to ensure consistency amongst clients. Rapid staff are trained to recognize workgroup 201 as the designated Shopify workgroup. 
-  Choosing a different workgroup number will require approval as well as additional configuration and testing, which will result in billable services from Rapid. 
 
**Notes** 
- Workgroups in Counterpoint are used to control defaults, permissions, and system behavior, including how users interact with data and workflows. 
- Workgroup 201 is the default workgroup created by the installer for importing Shopify orders and customers into Counterpoint. 
- The workgroup determines which template customer is used when creating new customers from Shopify orders. For Shopify orders, this will be the **EC_SHOPIFY** template customer. When a new customer is created in Counterpoint from a Shopify order, the default values from the EC_SHOPIFY template customer will be applied. 
- Using a separate workgroup (and therefore template customer) allows ecommerce customers to have different default values than customers created in-store. 
 
**Create and Overwrite (Update) Behavior** 
- Used when importing (creating) orders and customers in Counterpoint. 
- Does not update (overwrite) existing orders or customers. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Phone Format 
 
- **Column Name:** `PHONE_FORMAT` 
- **Default Value:** ###-###-#### 
- **Default Type:** No Preference 
 
**Purpose** 
-  Controls the format (mask) used when importing Shopify customer phone numbers into Counterpoint. 
 
**Valid Values** 
- **###-###-####** – Formats phone numbers with hyphens (e.g., 123-456-7890). 
- **(###) ###-####** – Formats phone numbers with parentheses and a space (e.g., (123) 456-7890). 
- **##########** – Formats phone numbers as a continuous string of digits (e.g., 1234567890). 
- **[Custom 10-digit mask]** – Any custom format may be used, as long as it contains exactly 10 digits represented by #. 
 
**Recommendation** 
-  Most clients choose ###-###-#### and this is also the default. However, any preferred format may be selected. 
 
**Notes** 
- This setting determines how customer phone numbers from Shopify are formatted when saved in Counterpoint. 
- The selected format will be applied consistently to all imported customer phone numbers. 
 
**Create and Overwrite (Update) Behavior** 
- Used when creating customers in Counterpoint. 
- Does **not** update (overwrite) existing customer phone numbers in Counterpoint. 
 
**Change Impact and Support Required** 
- Change can be made by a client. 
- Applies only to newly imported customer phone numbers in Counterpoint. 
 
---
 
### Capitalize Customer Fields 
 
- **Column Name:** `CAPITALIZE_CUSTOMER_FIELDS` 
- **Default Value:** N 
- **Default Type:** No Preference 
 
**Purpose** 
-  Controls whether customer name and address fields are capitalized when imported into Counterpoint. 
 
**Valid Values** 
- **Yes** – Customer fields will be converted to uppercase when imported into Counterpoint. 
- **No** – Customer fields will be imported as they appear in Shopify. 
 
**Recommendation** 
-  Most clients choose **no** as they prefer to preserve the original formatting from Shopify. 
-  Some clients choose **yes** when uppercase formatting is important for consistency. 

**Notes** 
- This setting applies to customer fields such as name, address, city, and state. 
- When enabled, all applicable fields will be converted to uppercase. 
 
**Create and Overwrite (Update) Behavior** 
- Used when creating customers in Counterpoint. 
- Does not update (overwrite) existing customer addresses in Counterpoint. 
 
**Change Impact and Support Required** 
- Change can be made by a client. 
- Applies only to newly imported/created customers in Counterpoint. 
 
---
 
### Order Billing Address Overrides Customer Address 
 
- **Column Name:** `BILLING_ADDR_OVERRIDES_CUSTOMER_ADDR` 
- **Default Value:** N 
- **Default Type:** Common 
 
**Purpose** 
-  Controls whether the billing address from a Shopify order overrides the address on an existing customer record in Counterpoint. 
 
**Valid Values** 
- **Yes** – The billing address from Shopify will overwrite the existing customer address in Counterpoint when a match is found. 
- **No** – The existing customer address in Counterpoint will not be overwritten. 
 
**Recommendation** 
-  Most clients choose **no** as they prefer to preserve the existing customer address in Counterpoint to avoid unintended changes from individual orders. 
-  Choose **yes** if the billing address from each Shopify order should be treated as the most current and authoritative customer address. 
 
**Notes** 
- Shopify maintains multiple address types, including default, billing, and shipping addresses. 
- If no matching customer is found in Counterpoint, a new customer record is always created using the billing address from Shopify. 
- If a matching customer is found, a new customer record will not be created. Instead, the order will be added to the existing customer record. 
- When this setting is enabled, the billing address from Shopify will overwrite the existing customer’s address in Counterpoint. 
- When disabled, the billing address will remain on the order only and will not affect the customer record. 
 
**Create and Overwrite (Update) Behavior** 
- When set to **Yes**, existing customer addresses in Counterpoint will be updated (overwritten) by the connector. 
- When set to **No**, existing customer addresses in Counterpoint will not be updated (overwritten). 
 
**Change Impact and Support Required** 
- Change can be made by a client. 
- Applies only to newly imported Shopify orders with customer updates. 
 
### [↑ Back to Top](#quick-links)
 
---

## CRON Job Schedules 
 
### Daily Event Execution Time 
 
- **Column Name:** `DAILY_EVENT_EXEC_TIME` 
- **Default Value:** 0 6 * * * 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- CRON schedule controlling the frequency of the daily event execution. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Order Sync Execution Time 
 
- **Column Name:** `ORDER_SYNC_EXEC_TIME` 
- **Default Value:** */15 * * * * 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- CRON schedule controlling the frequency of order synchronization. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Item Sync Execution Time 
 
- **Column Name:** `ITEM_SYNC_EXEC_TIME` 
- **Default Value:** */15 * * * * 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- CRON schedule controlling the frequency of item synchronization. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Customer Sync Execution Time 
 
- **Column Name:** `CUSTOMER_SYNC_EXEC_TIME` 
- **Default Value:** */15 * * * * 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- CRON schedule controlling the frequency of customer synchronization. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Manual Run Connector Execution Time 
 
- **Column Name:** `RUN_CONNECTOR_EXEC_TIME` 
- **Default Value:** * * * * * 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- CRON schedule controlling how frequently the system checks for the Manual Run Connector action flag. 
- When the action flag is detected, if the Shopify connector is not currently running, it will execute for all configured Shopify accounts, typically within one minute. If the connector is already running, the system waits for the current execution to complete, then automatically restarts the connector for all configured Shopify accounts. 
- In both scenarios, the action flag is automatically cleared when execution begins. 
  
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Manual Run Connector 
 
- **Column Name:** `RUN_CONNECTOR` 
- **Default Value:** N 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- When the **Run Shopify Connector** menu option is selected, this action flag is set. 
- This flag functions as a one-time execution request and remains enabled until it is processed by the connector. The action flag is automatically cleared when execution begins. 
- Execution occurs in the background on the server (not on the workstation) to prevent overlapping executions. 
 
**Change Impact and Support Required** 
- This flag is changed to **yes** by clicking the **Run Shopify Connector** button (menu option), and then automatically cleared (set to **no**) when execution begins. 
 
### [↑ Back to Top](#quick-links)
 
---
 
## Sync Limits 
 
### Orders Down Start Date 
 
- **Column Name:** `ORDERS_DOWN_START_DAT` 
- **Default Value:** _null_, set during install 
- **Default Type:** No Preference 
 
**Purpose** 
- Used to define the earliest date from which Shopify orders will be imported into Counterpoint. 
- Typically set to the go-live date unless otherwise specified. 
 
**Change Impact and Support Required** 
- Change can be made by a client. 
 
---
 
### Orders Down Lookback Days 
 
- **Column Name:** `ORDERS_DOWN_LOOK_BACK_DAYS` 
- **Default Value:** -2 
- **Default Type:** Recommended 
 
**Purpose** 
- Defines how many days back the connector checks for Shopify orders that have not yet been imported. 
- Helps ensure orders are synchronized after a power outage or temporary connector interruption. 
- The **Orders Down Start Date** is always respected as the absolute limit. 
 
**Change Impact and Support Required** 
- Consult Rapid Staff. 
- Changes to this value will impact log file size and may increase the overall runtime of the connector. 
 
---
 
### Max Number of Items to Sync 
 
- **Column Name:** `MAX_ITEMS_TO_SYNC` 
- **Default Value:** 500 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Used to optimize connector performance. 
- Defines the maximum number of items that can be synchronized in a single connector run. 
- Items with the most recent sync status of 2 will be processed first. 
  
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
- This setting is specifically configured to optimize the connector’s efficiency and stability. Changing this value may impact connector performance. 
 
---
 
### Max Number of Customers to Sync 
 
- **Column Name:** `MAX_CUSTOMERS_TO_SYNC` 
- **Default Value:** 250 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Used to optimize connector performance. 
- Defines the maximum number of customers that can be synchronized in a single connector run. 
- Customers with the most recent sync status of 2 will be processed first. 
  
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
- This setting is specifically configured to optimize the connector’s efficiency and stability. Changing this value may impact connector performance. 
 
---
 
## Log Files and Alerts 
 
### Max Number of Log Files to Keep 
 
- **Column Name:** `LOG_MAX_FILES_TO_KEEP` 
- **Default Value:** 10 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- By default, the connector retains 10 log files, each up to 10 MB in size. 
- This typically provides sufficient historical data for troubleshooting without consuming excessive server storage. 
- A new log file is created each day. 
- If extended log history is required, these settings can be adjusted by Rapid staff. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
- Increasing this value will consume additional server storage. Reducing this value will limit the availability of historical data used for troubleshooting and diagnostics. 
 
---
 
### Max Log File Size 
 
- **Column Name:** `LOG_MAX_FILE_SIZE` 
- **Default Value:** 10000000 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- By default, the connector retains log files up to 10 MB in size. 
- This typically provides sufficient detail for troubleshooting without consuming excessive server storage. 
- If larger log files are required, this setting can be adjusted by Rapid staff. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
- Increasing this value will consume additional server storage. Reducing this value will limit the availability of historical data used for troubleshooting and diagnostics. 
 
---
 
### Message Group # 
 
- **Column Name:** `MAIL_GRP_ID` 
- **Default Value:** EC_SHOPIFY 
- **Default Type:** Sticky (Read-Only) 
 
**Purpose** 
- Defines the Message Group ID (MAIL_GRP_ID) used for Shopify connector alert messages in Counterpoint. 
- When an error or issue is encountered, alerts are sent to the Counterpoint users associated with this message group. 
- It is recommended to assign 1–3 users to receive these alerts. 
- This value must reference a valid Message Group containing the appropriate Counterpoint User IDs. 
 
**Change Impact and Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Mark Alerts as Read in Message Center After Days 
 
- **Column Name:** `MSG_CENTER_MARK_AS_READ_DAYS` 
- **Default Value:** 3 
- **Default Type:** Recommended 
 
**Purpose** 
- Defines the number of days after which connector alerts are automatically marked as read. 
- This helps prevent older messages from repeatedly appearing as pop-ups when logging into Counterpoint, reducing workflow interruptions. 
 
**Change Impact and Support Required** 
- Change can be made by a client. 
 
### [↑ Back to Top](#quick-links)
 
---
 
## Troubleshooting Controls 
 
### Skip All Orders Except 
 
- **Column Name:** `SKIP_ALL_ORDERS_EXCEPT` 
- **Default Value:** _null_ 
- **Default Type:** Recommended 
 
**Purpose** 
- Used by Rapid staff for troubleshooting or testing. 
- Allows a single specific Shopify order to be imported, regardless of fulfillment status. 
- The value should be the Shopify Order ID. 
 
**Valid Values** 
- **0** - Because this value does not match any Shopify Order IDs, setting it to 0 will prevent all orders from importing. 
- **_Null_** - Leaving this value blank (null) allows all orders to import, based on other configured parameters. 
- **[Single Shopify Order ID]** - When set to a specific Shopify Order ID, the connector will only attempt to import that order during execution (regardless of fulfillment status). If the order already exists in Rapid POS, it will not be re-imported or updated. 
  
**Change Impact and Support Required** 
- This setting should only be modified with a clear understanding of its impact. 
- Incorrect use can unintentionally block all order imports or restrict processing to a single order. 
 
---
 
### Skip All Items Except 
 
- **Column Name:** `SKIP_ALL_ORDERS_EXCEPT` 
- **Default Value:** _null_ 
- **Default Type:** Recommended 
 
**Purpose** 
- Used by Rapid staff for troubleshooting or testing. 
- Allows a single specific item from Counterpoint to be synchronized. 
- The value should be the Counterpoint Item Number. 
 
**Valid Values** 
- **0** - Because this value does not match any Counterpoint Item Numbers, setting it to 0 will prevent all items from syncing. 
- **_Null_** - Leaving this value blank (null) allows all Shopify Item Records to sync. 
- **[Single Counterpoint Item Number]** - When set to a specific Counterpoint Item Number, the connector will only attempt to sync that Shopify Item Record during execution. 
  
**Change Impact and Support Required** 
- This setting should only be modified with a clear understanding of its impact. 
- Incorrect use can unintentionally block all item synchronization or restrict processing to a single item.
 
### [↑ Back to Top](#quick-links)
 
---
 
### Field 
 
- **Column Name:** 
- **Default Value:** 
- **Default Type:** 
 
**Purpose** 
-  
 
**Valid Values** 
- 
 
**Recommendation** 
-  
 
**Notes** 
- 
 
**Create and Overwrite (Update) Behavior** 
- 
 
**Change Impact and Support Required** 
- 
 
