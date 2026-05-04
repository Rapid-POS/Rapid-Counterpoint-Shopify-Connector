# DRAFT Shopify Connector Configuration 
 
## Overall 
 
### Account Name 
 
- **Column Name:** `ACCOUNT_NAME` 
- **Default Type:** Read-Only/Sticky 
- **Default Value:** null 
 
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
- **Default Value:** null 
 
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
- **Default Value:** null 
 
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
- **Default Value:** null 
 
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
- **Default Value:** null 
 
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
- **Default Value:** null 
 
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
- **Default Value:** null 
 
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
- **Default Value:** null 
 
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
- **Default Value:** null 
 
**Explanation** 
- Displays the current connector version and the most recent maintenance information for reference. 
 
**Valid Values** 
- This field will be automatically populated by the connector. 
 
**Change Support Required** 
- Read-Only. Automatically updated. 
 
---
 
## Items Up 
 
### Add Update Items Up 
 
- **Column Name:** ADD_UPDATE_ITEMS_UP 
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
 
- **Column Name:** ENABLE_COPY_FROM 
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
 
- **Column Name:** DEFAULT_PRODUCT_STATUS 
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
 
- **Column Name:** DELETE_ITEM_TYPE 
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
 
- **Column Name:** UPDATE_TITLE_FIELD 
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
 
- **Column Name:** UPDATE_TITLE 
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

 
