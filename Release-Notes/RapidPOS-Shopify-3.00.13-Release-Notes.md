# Rapid POS Shopify Connector v3.00.13 Release Notes  

_Release Date: May 19, 2026_

---

## Bug Fixes and Performance Enhancements

- Fixed an issue where `GetBarcode` could return a null barcode when `BARCODE_ID_FILTER` was null.

- Updated Shopify SQL installation scripts to improve configuration defaults and database schema consistency.
  - Updated default values for:
    - `PRODUCT_VENDOR_DEFAULT` → `N`
    - `DELETE_ITEM_TYPE` → `archive`
    - `BILLING_ADDR_OVERRIDES_CUSTOMER_ADDR` → `N`
    - `ORDER_SOURCE` → `all`
    - `ORDERS_DOWN_LOOK_BACK_DAYS` → `-2`
    - `ENABLE_COPY_FROM` → `N`

- Updated GraphQL `VariantsList` processing to improve memory management, pagination handling, error reporting, and overall code maintainability.
  - Added support for pagination using Shopify’s root-level `productVariants` GraphQL collection.
  - Added fallback handling to return an empty list when no variant data is available.
  - Improved formatting and consistency within `BulkCreateVariant` and `BulkUpdateVariant` methods.

- Refactored `ItemInterface` processing for improved maintainability and error handling.
  - Removed unused code and redundant logging statements.
  - Updated variant creation logic to directly append newly created variants to the `productVariants` list.
  - Enhanced error handling in `ListAsync` and other methods by throwing descriptive exceptions.
  - Replaced `return null` patterns with exception handling to improve error propagation and troubleshooting visibility.

## Additional Notes
- This release primarily focuses on GraphQL stability improvements, barcode handling fixes, configuration consistency, memory management improvements, and overall code maintainability enhancements.
