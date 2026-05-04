# DRAFT Shopify Connector Configuration 
 
## Overall 
 
### Account Name 
 
- **Column Name:** `ACCOUNT_NAME` 
- **Default Type:** Read-Only/Sticky 
- **Default Value:** _null_ 
 
**Explanation**  
- Identifies the Shopify account and its associated credentials. 
 
**Valid Values**  
- Rapid will populate this field during install. 
 
**Change Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Enabled 
 
- **Column Name:** `IS_ENABLED` 
- **Default Type:** Read-Only/Sticky 
- **Default Value:** _null_ 
 
**Explanation** 
- Used to temporarily disable the connector while troubleshooting or testing. 
 
**Valid Values** 
- Rapid will populate this field during install. 
 
**Change Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### API URL 
 
- **Column Name:** `API_URL` 
- **Default Type:** Read-Only/Sticky 
- **Default Value:** _null_ 
 
**Explanation** 
- Identifies the Shopify account and its associated credentials. 
 
**Valid Values** 
- Rapid will populate this field during install. 
 
**Change Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### API KEY 
 
- **Column Name:** `API_KEY` 
- **Default Type:** Read-Only/Sticky 
- **Default Value:** _null_ 
 
**Explanation** 
- Identifies the Shopify account and its associated credentials. 
 
**Valid Values** 
- Rapid will populate this field during install. 
 
**Change Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Encrypted API Access Token 
 
- **Column Name:** `API_PWD` 
- **Default Type:** Read-Only/Sticky 
- **Default Value:** _null_ 
 
**Explanation** 
- Identifies the Shopify account and its associated credentials. 
 
**Valid Values** 
- Rapid will populate this field during install. 
 
**Change Support Required** 
- Change should be made by Rapid staff. 
 
---
 
### Last Sync Date Time 
 
- **Column Name:** `LST_SYNC_DT` 
- **Default Type:** Read-Only/Sticky 
- **Default Value:** _null_ 
 
**Explanation** 
- Displays the current connector version and the most recent maintenance information for reference. 
 
**Valid Values** 
- This field will be automatically populated by the connector. 
 
**Change Support Required** 
- Read-Only. Automatically updated. 
 
---
 
### Version 
 
- **Column Name:** `APP_VERSION` 
- **Default Type:** Read-Only/Sticky 
- **Default Value:** _null_ 
 
**Explanation** 
- Displays the current connector version and the most recent maintenance information for reference. 
 
**Valid Values** 
- This field will be automatically populated by the connector. 
 
**Change Support Required** 
- Read-Only. Automatically updated. 
 
---
 
### Lasy Maintained By 
 
- **Column Name:** `LST_MAINT_USR_ID` 
- **Default Type:** Read-Only/Sticky 
- **Default Value:** _null_ 
 
**Explanation** 
- Displays the current connector version and the most recent maintenance information for reference. 
 
**Valid Values** 
- This field will be automatically populated by the connector. 
 
**Change Support Required** 
- Read-Only. Automatically updated. 
 
---
 
### Last Maintained 
 
- **Column Name:** `LST_MAINT_DT` 
- **Default Type:** Read-Only/Sticky 
- **Default Value:** _null_ 
 
**Explanation** 
- Displays the current connector version and the most recent maintenance information for reference. 
 
**Valid Values** 
- This field will be automatically populated by the connector. 
 
**Change Support Required** 
- Read-Only. Automatically updated. 
 
---
 
## Items Up 
 
### Add Update Items Up 
 
- **Column Name:** `ADD_UPDATE_ITEMS_UP` 
- **Default Type:** Sticky 
- **Default Value:** Y 
 
**Explanation** 
- Controls whether newly added or updated items in Counterpoint with a Shopify Item Record are synchronized to Shopify as products. 
 
**Valid Values** 
- **Yes** – Newly added or updated items in Counterpoint with a Shopify Item Record will be created or updated as products in Shopify. 
- **No** – Newly added or updated items in Counterpoint will not be synchronized to Shopify. 
 
**Recommendations** 
- Choose **yes**. This should always be set to **yes** to ensure that product data is synchronized to Shopify. 
- Choosing no will require approval as well as additional configuration and testing, which will result in billable services from Rapid. 
 
**Notes** 
- This setting is typically used by Rapid staff for troubleshooting to temporarily disable item synchronization and should not be adjusted by clients. 
  
**Create and Overwrite (Update) Notes** 
- When set to yes, products on Shopify will be created and updated by the connector. 
  
**Change Support Required** 
- Change should be made by Rapid staff. 
  
---
 
### Copy From Applies to Shopify Items 
 
- **Column Name:** `ENABLE_COPY_FROM` 
- **Default Type:** No Preference 
- **Default Value:** N 
 
**Explanation** 
- Controls whether Shopify Item Record fields are copied when creating a new item in Counterpoint using the “Copy From” functionality. 
 
**Valid Values** 
- **Yes** – Shopify Item Record fields will be copied from the source item used in the “Copy From” process. 
- **No** – Shopify Item Record fields will not be copied and will use default values. 
 
**Recommendations** 
- Choose **yes** to maintain consistency when creating similar items that should share Shopify configuration. 
- Choose **no** if Shopify Item Record fields should be set manually for each new item. 
 
**Notes** 
- This setting applies only when creating new items using the “Copy From” functionality on the Item Record in Counterpoint. 
- When enabled, the Shopify Item Record will inherit values from the source item's Shopify Item Record. 
  
**Create and Overwrite (Update) Notes** 
- None 
 
**Change Support Required** 
- Change can be made by a client. 
- Applies to newly created items using "Copy From" going forward. 
  
---
 
### Default Product Status 
 
- **Column Name:** `DEFAULT_PRODUCT_STATUS` 
- **Default Type:** Recommended 
- **Default Value:** Draft 
 
**Explanation** 
- Controls the default status assigned to products on Shopify when they are first synchronized from Counterpoint. 
 
**Valid Values** 
- **Draft** – Products are created on Shopify but are not visible to customers. 
- **Active** – Products are created and immediately available for sale on Shopify. 
- **Archived** – Products are created on Shopify but are not active and cannot be sold. 
 
**Recommendations** 
- Choose **draft**. It allows for review and enhance of products on Shopify before they are made available for sale. This is especially important for adding images and detailed product descriptions prior to publishing the product. 
 
**Notes** 
- This setting applies when products are first synchronized from Counterpoint to Shopify. 
- Product status can be changed later directly on Shopify. 
  
**Create and Overwrite (Update) Notes** 
- None 
 
**Change Support Required** 
- Change can be made by a client. 
- Applies to newly created Shopify Item Records going forward. 
 
---
 
### Delete Item Type 
 
- **Column Name:** `DELETE_ITEM_TYPE` 
- **Default Type:** Recommended 
- **Default Value:** Archive 
 
**Explanation** 
- Controls how products on Shopify are handled when the corresponding Shopify Item Record in Counterpoint is deleted. 
 
**Valid Values** 
- **Archive** – Products are archived on Shopify and are no longer active or available for sale. 
- **Unpublish** – Products remain active on Shopify but are removed from all sales channels and are not visible to customers. 
- **Nothing** – No action is taken on Shopify; the product remains unchanged. 
 
**Recommendations** 
- Choose **archive**. This removes products from sale while preserving product data and history. It also helps prevent outdated or no longer synced products from remaining visible, while keeping them clearly segregated within Shopify. 
 
**Notes** 
- The connector will never delete products in Shopify; it can only archive or unpublish them. This is a safety mechanism to ensure the connector never fully removes a product from Shopify. 
- If a product needs to be permanently deleted, it must be deleted directly on Shopify. 
 
**Create and Overwrite (Update) Notes** 
- When set to **Archive** or **Unpublish**, products on Shopify can be archived or unpublished by the connector. 
 
**Change Support Required** 
- Change can be made by a client. 
- Applies to newly deleted Shopify Item Records going forward. 
 
---
 
### Product Title Field 
 
- **Column Name:** `UPDATE_TITLE_FIELD` 
- **Default Type:** No Preference 
- **Default Value:** DESCR 
 
**Explanation** 
- Controls which field in Counterpoint is used to populate the product title on Shopify. 
 
**Valid Values** 
- **DESCR** – Uses the Description field in Counterpoint as the product title on Shopify. 
- **LONG_DESCR** – Uses the Long Description field in Counterpoint as the product title on Shopify. 
- **SHORT_DESCR** – Uses the Short Description field in Counterpoint as the product title on Shopify. 
- **ADDL_DESCR_1** – Uses the Additional Description 1 field in Counterpoint as the product title on Shopify. 
- **ADDL_DESCR_2** – Uses the Additional Description 2 field in Counterpoint as the product title on Shopify. 
- **ADDL_DESCR_3** – Uses the Additional Description 3 field in Counterpoint as the product title on Shopify. 
 
**Recommendations** 
- Choose the field that is best suited for use as a customer-facing product title on Shopify. This should be a field that is consistently populated and appropriate for ecommerce display. 
- Alternatively, choose a field that provides enough detail to be used during initial synchronization, with the understanding that the product title can then be edited on Shopify for improved clarity and customer-facing presentation. 
 
**Notes** 
- If the selected field is blank, the connector will use the **Description** field as a fallback when populating the product title on Shopify. 
- Product titles on Shopify are not required to be unique and have a maximum length of 255 characters. Most fields in Counterpoint have shorter character limits. 
- Whether the product title is sent only during the initial synchronization or on subsequent updates is controlled by the **Update Title** configuration setting. 
 
**Create and Overwrite (Update) Notes** 
- Whether the product title is sent only during product creation or is updated on subsequent syncs is controlled by the **Update Title** config setting. 
 
**Change Support Required** 
- Consult Rapid staff. 
- If Update Title is Yes, a full resync is recommended to update product titles on Shopify. 
- If Update Title is No, this setting can be changed by a client and applies to newly created Shopify Item Records going forward. 
 
---
 
### Update Title 
 
- **Column Name:** `UPDATE_TITLE` 
- **Default Type:** Recommended 
- **Default Value:** N 
 
**Explanation** 
- Controls whether the product title on Shopify is updated when the corresponding item in Counterpoint is updated. 
 
**Valid Values** 
- **Yes** – The product title on Shopify will be updated based on the selected Product Title Field whenever the item is updated in Counterpoint. 
- **No** – The product title on Shopify will only be set during the initial synchronization and will not be updated on subsequent changes in Counterpoint. 
 
**Recommendations** 
- Choosing **no** allows product titles to be maintained directly on Shopify, which supports longer and more descriptive titles. Many fields in Counterpoint are designed for internal use and may not be ideal for customer-facing product titles. Managing titles on Shopify enables more detailed, customer-friendly, and searchable product names. 
- Choose **yes** only if the data in Counterpoint is consistently maintained at a level suitable for use as a customer-facing product title on Shopify and product titles will not be edited directly on Shopify. 
 
**Notes** 
- This setting works in conjunction with the **Product Title Field** configuration. 
- Shopify allows longer and more flexible product titles (up to 255 characters) compared to most fields in Counterpoint, which are typically limited to 30, 50 or 80 characters. 
 
**Create and Overwrite (Update) Notes** 
- When set to **Yes**, product titles on Shopify will always be updated (overwritten) by the connector. 
- When set to **No**, product titles will only be sent to Shopify during product creation. Subsequent syncs will not update (overwrite) data on Shopify. 
 
**Change Support Required** 
- Changing from **Yes → No** can be done by a client. 
- Changing from **No → Yes** should be coordinated with Rapid staff. A full resync is recommended to update product titles on Shopify. 
 
---
 
### Product Inventory Qty 
 
- **Column Name:** `ITEM_QTY_METH`
- **Default Type:** Recommended 
- **Default Value:** Item Qty Available 
 
**Explanation** 
- Controls which inventory quantity field in Counterpoint is used to populate product inventory levels on Shopify. 
 
**Valid Values** 
- **Item Qty Available** – Uses the available quantity in Counterpoint, which reflects stock available for sale. 
- **Item Qty on Hand** – Uses the on-hand quantity in Counterpoint, which reflects total physical stock without accounting for commitments (such as unposted tickets), allocations or reservations. 
 
**Recommendations** 
- Choose **Item Qty Available**. This ensures that inventory levels on Shopify reflect what is actually available for sale. It accounts for unposted tickets and other committed inventory, helping prevent overselling on Shopify. 
 
**Notes** 
- None 
 
**Create and Overwrite (Update) Notes** 
- Quantity on Shopify will always be updated (overwritten) by the connector. 
 
**Change Support Required** 
- Consult Rapid staff. 
- A full resync is recommended to update inventory levels on Shopify. 
 
---
 
### Hide Out of Stock Inventory 
 
- **Column Name:** `HIDE_OUT_OF_STOCK_INVENTORY` 
- **Default Type:** Common 
- **Default Value:** N 
 
**Explanation** 
- Controls whether products on Shopify are hidden when their inventory quantity reaches zero. 
 
**Valid Values** 
- **Yes** – Products with zero inventory will be hidden on Shopify and will not be visible to customers. 
- **No** – Products with zero inventory will remain visible on Shopify but will be shown as out of stock. 
 
**Recommendations** 
- Choosing **no** keeps out-of-stock products visible. It allows customers to see that the product is carried, even if it is currently unavailable. This helps maintain product visibility and supports searchability and SEO. 
- However, if your products are not typically replenished once they are sold out, choosing **yes** may be preferred to avoid displaying unavailable products. 
 
**Notes** 
- This functionality works by removing the product from the **Online Sales Channel** on Shopify, which hides it from the customer-facing website. 
- This setting only applies to items where the item type in Counterpoint is **Inventory** and the **Continue Selling Out of Stock** option in the Shopify Item Record is not enabled. 
 
**Create and Overwrite (Update) Notes** 
- When set to **Yes**, product visibility on Shopify will be updated (overwritten) by the connector. 
- When set to **No**, product visibility on Shopify will not be updated (overwritten) by the connector. 
 
**Change Support Required** 
- Consult Rapid staff. 
- A full resync is recommended to update product visibility on Shopify. 
 
---
 
### Product Price 
 
- **Column Name:** `ITEM_PRC_METH` 
- **Default Type:** Common 
- **Default Value:** Price-1 
 
**Explanation** 
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
 
**Recommendations** 
- Typically **Price-1** is the standard selling price in Counterpoint. Use alternative price levels only if they are specifically configured for selling online. 
 
**Notes** 
- If the selected price level is blank for an item, the connector will use Price-1 as a fallback. 
- Price-4, Price-5, and Price-6 are only available in Counterpoint for clients with an Advanced Pricing subscription from NCR Counterpoint. 
 
**Create and Overwrite (Update) Notes** 
- Price on Shopify will always be updated (overwritten) by the connector. 
 
**Change Support Required** 
- Consult Rapid staff. 
- A full resync is recommended to update pricing on Shopify. 
 
---
 
### Product Compare At Price 
 
- **Column Name:** `ITEM_COMPARE_AT_PRC_METH` 
- **Default Type:** No Preference 
- **Default Value:** Price-1 
 
**Explanation** 
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
 
**Recommendations** 
- To omit the Compare At Price, **select the same price field** used for the product price. Shopify will ignore the value when both prices are equal. 
- To display a Compare At Price, **select a price that is typically higher** than the product price. 
 
**Notes** 
- The Compare At Price on Shopify is typically used to display a higher “original” price alongside a lower selling price. 
- Shopify requires the Compare At Price to be greater than the product price. If a value equal to or lower than the product price is sent, Shopify will ignore it. 
- If the selected price level is blank for an item, the connector will use Price-1 as a fallback. 
 
**Create and Overwrite (Update) Notes** 
- Compare At Price on Shopify will always be updated (overwritten) by the connector. 
 
**Change Support Required** 
- Consult Rapid staff. 
- A full resync is recommended to update pricing on Shopify. 
 
---
 
### Product Vendor Default 
 
- **Column Name:** `PRODUCT_VENDOR_DEFAULT` 
- **Default Type:** No Preference 
- **Default Value:** Primary Vendor Name 
 
**Explanation** 
- Controls the fallback vendor assigned to products on Shopify when the Product Vendor field on the Shopify Item Record in Counterpoint is blank. 
 
**Valid Values** 
- **Primary Vendor Name** – Uses the primary vendor from the Item Record in Counterpoint as the product vendor on Shopify (only when the Product Vendor field on the Shopify Item Record is blank).
- **None** – No value is sent to Shopify. Shopify will default the vendor to the store name.
 
**Recommendations** 
- Choose **Primary Vendor Name** if sending product vendor values from Counterpoint is helpful for organization or reporting in Shopify. 
- Choose **None** if you plan to regularly populate the Product Vendor field on the Shopify Item Record, or if you prefer Shopify to default the vendor to the store name. 
 
**Notes** 
- The Product Vendor field on the Shopify Item Record always takes priority over this (fallback) setting. This setting is only used when the Product Vendor field is left blank. 
- The product vendor on Shopify is typically not displayed on the customer-facing website and is most often used for internal organization and filtering within Shopify. 
- _Special Note:_ 
  - The Product Vendor field on the Shopify Item Record can be populated with any value and does not need to match a vendor in Counterpoint. 
  - Some clients use this field to store alternate values such as brand names instead of vendor names. 
 
**Create and Overwrite (Update) Notes** 
- Product Vendor on Shopify will always be updated (overwritten) by the connector.
 
**Change Support Required** 
- Consult Rapid staff. 
- A full resync is recommended to update product vendor values on Shopify. 
 
---
 
### Filter Item Barcode by ID 
 
- **Column Name:** `BARCODE_ID_FILTER` 
- **Default Type:** No Preference 
- **Default Value:** _null_ 
 
**Explanation** 
- Controls which barcode from Counterpoint is selected and sent to Shopify based on barcode type. 
 
**Valid Values** 
- **[Null]** – Sends the first barcode listed in the barcode table for the item, regardless of barcode type. 
- **[Barcode Type]** – Sends the first barcode that matches the selected type. Configuration examples include **ITEM**, **UPC**, **SKU**, or any other type defined in the barcode table in Counterpoint. 
 
**Recommendations** 
- Select a specific barcode type to ensure a consistent and predictable barcode is sent to Shopify.
- Counterpoint allows only one barcode with a type of **ITEM** per item, making it the most consistent and predictable option. Using ITEM ensures the same barcode is always sent to Shopify.
- If multiple barcodes exist for other types (such as UPC), it may be difficult to control which barcode is listed first in Counterpoint and therefore which one is sent to Shopify.
- If many items do not have a barcode defined with a type of ITEM, consider using another type or leaving this value as Null so that at least the first available barcode is sent to Shopify.
 
**Notes** 
- Items in Counterpoint can have multiple barcodes, each optionally assigned a type. 
- When a specific barcode type is selected, the connector will send the first barcode that matches that type. 
- When set to Null, the connector will send the first available barcode regardless of type. 
 
**Create and Overwrite (Update) Notes** 
- Barcode on Shopify will always be updated (overwritten) by the connector. 
 
**Change Support Required** 
- Consult Rapid staff. 
- A full resync is recommended to update barcodes on Shopify. 
 
---
 
### Handle Definition Query 
 
- **Column Name:** `HANDLE_DEFINITION_QUERY` 
- **Default Type:** No Preference 
- **Default Value:** _null_ 
 
**Explanation** 
- Controls how the product handle (URL slug) is generated for products on Shopify. 
 
**Valid Values** 
- **[Null]** – Uses the Item Number from Counterpoint as the fallback product handle on Shopify. 
- **[Query]** – Uses the configured query to generate the product handle on Shopify. This might include some combination of multiple fields from Counterpoint such as description and item number or long description and item number. 
- _Query Output Examples:_ 
  - website.com/Description-ItemNumber 
  - website.com/LongDescription-ItemNumber 
 
**Recommendations** 
- Use a **query** that generates customer-friendly, descriptive handles if product URLs are important for SEO or usability. 
- Otherwise, using the fallback of Item Number provides a simple and consistent default. Based on the **Update Handle** setting, the handle can then be customized on Shopify if a more descriptive value is desired. 
 
**Notes** 
- The product handle on Shopify is used in the product URL and should be unique and URL-friendly. When using a query, including the Item Number as part of the URL can help ensure the handle remains unique. 
- Whether the handle is updated after the initial synchronization is controlled by the **Update Handle** configuration setting. 
 
**Create and Overwrite (Update) Notes** 
- Whether the handle is sent only during product creation or is updated on subsequent syncs is controlled by the **Update Handle** config setting. 
 
**Change Support Required** 
- Consult Rapid staff. 
- This query should be written and reviewed by Rapid staff. 
- If Update Handle is Yes, a full resync is recommended to update handles on Shopify. 
- If Update Handle is No, this setting applies to newly created Shopify Item Records going forward. 
 
---
 
### Update Handle 
 
- **Column Name:** `UPDATE_HANDLE` 
- **Default Type:** No Preference 
- **Default Value:** N 
 
**Explanation** 
- Controls whether the product handle (URL slug) on Shopify is updated when the corresponding item in Counterpoint is updated. 
 
**Valid Values** 
- **Yes** – The product handle on Shopify will be updated based on the Handle Definition Query when the item is updated in Counterpoint. 
- **No** – The product handle on Shopify will only be set during the initial synchronization and will not be updated on subsequent changes. 
 
**Recommendations** 
- Choose **yes** if the handle is derived from data in Counterpoint (such as description or naming conventions) and should stay in sync as that data changes. 
- Choose **no** if handles are edited or managed directly on Shopify, or if maintaining stable URLs is important for SEO and external links. 
 
**Notes** 
- This setting works in conjunction with the **Handle Definition Query** configuration. Changes to the query or underlying data in Counterpoint will only be reflected on Shopify if this setting is set to Yes. 
 
**Create and Overwrite (Update) Notes** 
- When set to **Yes**, product handles on Shopify will always be updated (overwritten) by the connector. 
- When set to **No**, product handles will only be sent to Shopify during product creation. Subsequent syncs will **not** update (overwrite) data on Shopify. 
 
**Change Support Required** 
- Changing from **Yes → No** can be done by a client. 
- Changing from **No → Yes** should be coordinated with Rapid staff. A full resync is recommended to update handles on Shopify. 
 
---
 
### Update Html Description 
 
- **Column Name:** `UPDATE_HTML_DESCR` 
- **Default Type:** Recommended 
- **Default Value:** N 
 
**Explanation** 
- Controls whether the HTML description on Shopify is updated when the corresponding Shopify Item Record in Counterpoint is updated. 
 
**Valid Values** 
- **Yes** – The HTML Description field on the Shopify Item Record in Counterpoint will overwrite the product description on Shopify when updated. 
- **No** – The HTML Description will only be set during the initial synchronization and will not overwrite changes made on Shopify. 
 
**Recommendations** 
- Choose **no**. It is easier to manage product descriptions directly on Shopify, where a WYSIWYG editor allows for easier formatting and content management without requiring HTML. 
 
**Notes** 
- The HTML Description field on the Shopify Item Record in Counterpoint allows for plain text or HTML-formatted content to be entered. 
- This value is sent to Shopify when the product is first synchronized. 
- When this setting is enabled, any updates to the HTML Description in Counterpoint will overwrite the existing product description on Shopify. 
 
**Create and Overwrite (Update) Notes** 
- When set to **Yes**, product descriptions on Shopify will always be updated (overwritten) by the connector. 
- When set to **No**, product descriptions will only be sent to Shopify during product creation. Subsequent syncs will **not** update (overwrite) data on Shopify. 
 
**Change Support Required** 
- Changing from **Yes → No** can be done by a client. 
- Changing from **No → Yes** should be coordinated with Rapid staff. A full resync is recommended to update HTML descriptions on Shopify. 
 
---
 
### Item Categories as Product Type 
 
- **Column Name:** `ITEM_CATEG_AS_PRODUCT_TYPE` 
- **Default Type:** No Preference 
- **Default Value:** N 
 
**Explanation** 
- Controls whether item categories in Counterpoint are used to populate the product type on Shopify. 
 
**Valid Values** 
- **Yes** – The item category from Counterpoint will be used as the product type on Shopify. 
- **No** – The product type on Shopify will not be populated from item categories. 
 
**Recommendations** 
- Choose **yes** if it is helpful to sync the item category to the product type on Shopify. 
- Choose **no** if product types are managed directly on Shopify or if item categories in Counterpoint do not reflect how products should be organized on Shopify. 
 
**Notes** 
- While the item category in Counterpoint is limited to a 10-character code, when this setting is enabled, the connector sends the full description of that code as the product type on Shopify. 
- The product type on Shopify is used for internal organization, filtering, and reporting. It is not commonly displayed on the customer-facing website. 
 
**Create and Overwrite (Update) Notes** 
- When set to **Yes**, product type on Shopify will always be updated (overwritten) by the connector. 
- When set to **No**, product type will **not** update (overwrite) data on Shopify. 
 
**Change Support Required** 
- Consult Rapid staff. 
- A full resync is recommended to update product type on Shopify. 
 
---
 
### Sub-Categories To Collections 
 
- **Column Name:** `SUBCAT_TO_COLLECTIONS` 
- **Default Type:** Recommended 
- **Default Value:** N 
 
**Explanation** 
- Controls whether sub-categories in Counterpoint are used to create or assign collections on Shopify. 
 
**Valid Values** 
- **Yes** – The sub-category from Counterpoint will be used to create and assign products to collections on Shopify. 
- **No** – Sub-categories will not be used to create or assign collections on Shopify. 
 
**Recommendations** 
- Choose **no** if collections are managed directly on Shopify or if sub-categories in Counterpoint do not reflect ecommerce navigation or merchandising needs. 
- Only choose **yes** if sub-categories in Counterpoint are well-structured and align with how products should be grouped and displayed on Shopify. 
 
**Notes** 
- The connector sends the description of the code, not the sub-category code. 
- If the sub-category for an item is changed in Counterpoint, the product will be added to the new collection on Shopify, but it will not be removed from any existing collections. The connector only adds products to collections and does not remove collections. 
 
**Create and Overwrite (Update) Notes** 
- When set to **Yes**, subcategories will be added on Shopify as collections. Existing collections will not be updated (overwritten) by the connector. 
- When set to **No**, subcategories will not be added on Shopify as collections. Existing collections will not be updated (overwritten) by the connector. 
 
**Change Support Required** 
- Changing from **Yes → No** can be done by a client and applies to newly created Shopify Item Records only (existing collections must be manually removed on Shopify). 
- Changing from **No → Yes** should be coordinated with Rapid staff. A full resync is recommended to update collections on Shopify. 
 
---
 
### Use Item Attributes For Tags 
 
- **Column Name:** `USE_ITEM_ATTRIBUTES_AS_TAGS` 
- **Default Type:** Recommended 
- **Default Value:** N 
 
**Explanation** 
- Controls whether all six item attributes in Counterpoint are used to populate product tags on Shopify. 
 
**Valid Values** 
- **Yes** – All item attribute fields from Counterpoint will be used to populate product tags on Shopify. 
- **No** – Item attributes will not be used to populate product tags on Shopify. 
 
**Recommendations** 
- Choose **no**. Most clients do not have consistent attribute data, which can lead to cluttered tags. Managing tags on Shopify or using custom metafields to sync specific item attributes is typically a better approach. 
 
**Notes** 
- Product tags on Shopify are used for filtering, search, and automated collection rules and are often managed directly on Shopify. 
- Instead of syncing attributes as tags, many clients prefer to sync specific attributes as metadata using the custom mapping table (a separate configuration option). 
- Up to six item attribute fields can be defined per item in Counterpoint. When enabled, these are located on the Description tab of the Item Record. Example item attributes include values such as brand or color, and are defined and customized per client. Most clients do not use all six fields. 
- When this setting is enabled, all populated attribute values will be sent to Shopify as product tags. 
- The connector sends the description of the attribute value, not the attribute code. 
- If an attribute value is changed in Counterpoint, a new tag will be added on Shopify, but existing tags will not be removed. The connector only adds tags and does not delete them. 
- Instead of using attribute fields, some clients choose to populate tags on the Shopify Item Record or directly on Shopify. 
 
**Create and Overwrite (Update) Notes** 
- When set to **Yes**, item attributes will be added on Shopify as tags. Existing tags will not be updated (overwritten) by the connector. 
- When set to **No**, item attributes will not be added on Shopify as tags. Existing tags will **not** be updated (overwritten) by the connector. 
 
**Change Support Required** 
- Changing from **Yes → No** can be done by a client and applies to newly created Shopify Item Records only (existing tags must be manually removed on Shopify). 
- Changing from **No → Yes** should be coordinated with Rapid staff. A full resync is recommended to update tags on Shopify. 
 
---
 
### [Field] 
 
- **Column Name:** 
- **Default Type:** 
- **Default Value:** 
 
**Explanation** 

 
**Valid Values** 

 
**Recommendations** 

 
**Notes** 

 
**Create and Overwrite (Update) Notes** 

 
**Change Support Required** 

 
---
 
### [Field] 
 
- **Column Name:** 
- **Default Type:** 
- **Default Value:** 
 
**Explanation** 

 
**Valid Values** 

 
**Recommendations** 

 
**Notes** 

 
**Create and Overwrite (Update) Notes** 

 
**Change Support Required** 

 
---
 
### [Field] 
 
- **Column Name:** 
- **Default Type:** 
- **Default Value:** 
 
**Explanation** 

 
**Valid Values** 

 
**Recommendations** 

 
**Notes** 

 
**Create and Overwrite (Update) Notes** 

 
**Change Support Required** 

 
---
 
### [Field] 
 
- **Column Name:** 
- **Default Type:** 
- **Default Value:** 
 
**Explanation** 

 
**Valid Values** 

 
**Recommendations** 

 
**Notes** 

 
**Create and Overwrite (Update) Notes** 

 
**Change Support Required** 

 
---
 
### [Field] 
 
- **Column Name:** 
- **Default Type:** 
- **Default Value:** 
 
**Explanation** 

 
**Valid Values** 

 
**Recommendations** 

 
**Notes** 

 
**Create and Overwrite (Update) Notes** 

 
**Change Support Required** 

 
---
 
### [Field] 
 
- **Column Name:** 
- **Default Type:** 
- **Default Value:** 
 
**Explanation** 

 
**Valid Values** 

 
**Recommendations** 

 
**Notes** 

 
**Create and Overwrite (Update) Notes** 

 
**Change Support Required** 

 

