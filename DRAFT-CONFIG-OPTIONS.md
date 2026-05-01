# DRAFT Shopify Connector Configuration

## Overall

### Account Name

- **Column Name:** `ACCOUNT_NAME`
- **Default Type:** Read-Only/Sticky
- **Default Value:** null

**Explanation**  
Identifies the Shopify account and its associated credentials.

**Valid Values**  
Rapid will populate this field during install.

**Change Support Required**  
Change should be made by Rapid staff.

---

### Enabled

- **Column Name:** `IS_ENABLED`
- **Default Type:** Read-Only/Sticky
- **Default Value:** null

**Explanation**  
Used to temporarily disable the connector while troubleshooting or testing.

**Valid Values**  
Rapid will populate this field during install.

**Change Support Required**  
Change should be made by Rapid staff.

---

### API URL

- **Column Name:** `API_URL`
- **Default Type:** Read-Only/Sticky
- **Default Value:** null

**Explanation**  
Identifies the Shopify account and its associated credentials.

**Valid Values**  
Rapid will populate this field during install.

**Change Support Required**  
Change should be made by Rapid staff.

---

### API KEY

- **Column Name:** `API_KEY`
- **Default Type:** Read-Only/Sticky
- **Default Value:** null

**Explanation**  
Identifies the Shopify account and its associated credentials.

**Valid Values**  
Rapid will populate this field during install.

**Change Support Required**  
Change should be made by Rapid staff.

---

### Encrypted API Access Token

- **Column Name:** `API_PWD`
- **Default Type:** Read-Only/Sticky
- **Default Value:** null

**Explanation**  
Identifies the Shopify account and its associated credentials.

**Valid Values**  
Rapid will populate this field during install.

**Change Support Required**  
Change should be made by Rapid staff.

---

### Last Sync Date Time

- **Column Name:** `LST_SYNC_DT`
- **Default Type:** Read-Only/Sticky
- **Default Value:** null

**Explanation**  
Displays the current connector version and the most recent maintenance information for reference.

**Valid Values**  
This field will be automatically populated by the connector.

**Change Support Required**  
Read-Only. Automatically updated.

---

### Version

- **Column Name:** `APP_VERSION`
- **Default Type:** Read-Only/Sticky
- **Default Value:** null

**Explanation**  
Displays the current connector version and the most recent maintenance information for reference.

**Valid Values**  
This field will be automatically populated by the connector.

**Change Support Required**  
Read-Only. Automatically updated.

---

### Lasy Maintained By

- **Column Name:** `LST_MAINT_USR_ID`
- **Default Type:** Read-Only/Sticky
- **Default Value:** null

**Explanation**  
Displays the current connector version and the most recent maintenance information for reference.

**Valid Values**  
This field will be automatically populated by the connector.

**Change Support Required**  
Read-Only. Automatically updated.

---

### Last Maintained

- **Column Name:** `LST_MAINT_DT`
- **Default Type:** Read-Only/Sticky
- **Default Value:** null

**Explanation**  
Displays the current connector version and the most recent maintenance information for reference.

**Valid Values**  
This field will be automatically populated by the connector.

**Change Support Required**  
Read-Only. Automatically updated.

---

## Items Up 
 
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
