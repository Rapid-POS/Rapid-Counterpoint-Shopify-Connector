# Shopify Connector v3.01.04 Release Notes
### Note: These release notes were updated after initial publishing to include the final bug fix. This increased the version number from v3.01.03 to v3.01.04.

_Release Date: August 12, 2026_

---

## Bug Fixes and Performance Enhancements

### Order Download Failure on Orders with Refunded Line Items

Some orders with discounted line items were failing to download from Shopify due to a database error on the discount table (`PS_DOC_DISC`). This happened when an order included a line item that had been fully refunded down to a zero quantity, which caused the connector to attempt to insert a discount record for the 0 quantity item and fail the download.

- The connector's order creation process now excludes line items with a current quantity of 0 when building the order, preventing that discount record from being created.
- This resolves order download errors such as "Violation of PRIMARY KEY constraint 'PK_PS_DOC_DISC'. Cannot insert duplicate key in object 'dbo.PS_DOC_DISC'."

### Friendlier Error Message for Misaligned Shopify Variants

Previously, if an item was synced to Shopify, and that product already had pre-existing variants that didn't match the grid cells or alternate units from Counterpoint, the connector failed with a generic technical error.

- When this happens, the connector now shows a friendly error explaining that the pre-existing Shopify variants should be removed (or that the Shopify product and the Shopify Item Record should be fully recreated) before resyncing.
- This replaces raw errors such as "BulkCreateVariant failed," "Sequence contains no matching element," or "Sequence contains more than one matching element."

### Gridded Items Not Populating the `USER_SHOPIFY_ITEM_VARIANTS` Table

Some gridded (variant) items were not creating records in the `USER_SHOPIFY_ITEM_VARIANTS` table, which the connector uses to track variant details. Affected Shopify products were missing barcode, SKU, or quantity information as a result.

- A trigger-nesting restriction in `USER_TR_USER_SHOPIFY_ITEMS_IU` was blocking the nested trigger execution needed to populate variant records, and has been removed.
- Two new triggers were added to keep `USER_SHOPIFY_ITEM_VARIANTS` in sync with grid cell changes: `USER_TR_SHOPIFY_IM_INV_CELL_IU` updates records when a grid cell is inserted or updated, and `USER_TR_SHOPIFY_IM_INV_CELL_D` removes records when a grid cell is deleted.
