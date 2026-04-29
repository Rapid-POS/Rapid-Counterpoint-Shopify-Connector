# Shopify Connector Configuration

## Overall

### Shopify Store URL

- **Column Name:** `SHOPIFY_STORE_URL`
- **Data Type:** String
- **Default Type:** Sticky

**Explanation**  
The Shopify Store URL that the connector will communicate with. This should be the full `.myshopify.com` domain.

**Valid Values**  
- Must be a valid Shopify store domain  
- Example: `yourstore.myshopify.com`

**Notes**  
- This value is required for the connector to function  
- Ensure there are no trailing spaces or incorrect formatting

---

### Shopify API Key

- **Column Name:** `SHOPIFY_API_KEY`
- **Data Type:** String
- **Default Type:** Sticky

**Explanation**  
The API Key generated from the Shopify custom app used for integration.

**Notes**  
- This value is obtained from the Shopify Admin under Apps → Develop Apps  
- Required for authentication

---

### Shopify API Secret

- **Column Name:** `SHOPIFY_API_SECRET`
- **Data Type:** String
- **Default Type:** Sticky

**Explanation**  
The API Secret associated with the Shopify custom app.

**Notes**  
- Used in conjunction with the API Key for secure communication  
- Should be kept confidential

---

### Shopify Access Token

- **Column Name:** `SHOPIFY_ACCESS_TOKEN`
- **Data Type:** String
- **Default Type:** Sticky

**Explanation**  
The Admin API access token generated from the Shopify custom app.

**Notes**  
- This token is required for all API calls  
- If regenerated, the connector must be updated with the new value

---

### Shopify API Version

- **Column Name:** `SHOPIFY_API_VERSION`
- **Data Type:** String
- **Default Type:** Sticky
- **Default Value:** 2023-10

**Explanation**  
Defines which version of the Shopify API the connector will use.

**Valid Values**  
- Must be a valid Shopify API version  
- Example: `2023-10`, `2024-01`

**Recommendations**  
- Use a stable, supported version  
- Avoid deprecated versions

**Notes**  
- Shopify periodically deprecates older API versions  
- Updating this value may require testing to ensure compatibility

---

### Enable Logging

- **Column Name:** `ENABLE_LOGGING`
- **Data Type:** Boolean
- **Default Type:** No preference
- **Default Value:** Y

**Explanation**  
Controls whether the connector generates logs for troubleshooting and monitoring.

**Valid Values**  
- **Y** → Logging enabled  
- **N** → Logging disabled

**Recommendations**  
- Recommended to keep enabled, especially during setup and troubleshooting

**Notes**  
- Logs may consume disk space over time  
- Can be disabled in stable production environments if not needed

---

### Log Retention Days

- **Column Name:** `LOG_RETENTION_DAYS`
- **Data Type:** Integer
- **Default Type:** No preference
- **Default Value:** 30

**Explanation**  
Determines how long logs are retained before being automatically purged.

**Valid Values**  
- Any positive integer representing number of days

**Recommendations**  
- 30–90 days is typical depending on storage availability

**Notes**  
- Lower values reduce disk usage  
- Higher values provide more historical troubleshooting data

---
