---
  Required Backend Configuration Flags

  1. Main Visibility Flag (REQUIRED)

  Controls whether the "IA Product Profile Edits" table appears at all.

  {
    "inventorysmart_create_product_profile": {
      "showIAProductProfileEdits": true
    }
  }

  Location in code: dashboard-table.jsx:540
  {props.productProfileConfig?.showIAProductProfileEdits && (
    <CustomAccordion label="IA Product Profile Edits">

  ---
  2. Infinite Scrolling Flag (OPTIONAL)

  Controls the pagination behavior for the IA Product Profile Edits table.

  {
    "infiniteScrolling": [
      "MPUserCreatedDetailsTable",           // existing - for Details table
      "MPIAProductProfileEditsTable"         // NEW - for IA Product Profile Edits table
    ]
  }

  Location in code: dashboard-table.jsx:558-571
  {...(props.inventorysmartScreenConfigForInfiniteScrolling?.includes(
    "MPIAProductProfileEditsTable"
  )
    ? {
        pagination: false,
        rowModelType: "infinite",
        cacheOverflowSize: 2,
        hideSelectCurrentPageRecords: true,
      }
    : {
        rowModelType: "serverSide",
        serverSideStoreType: "partial"
      }
  )}

  ---
  Complete Backend Config Example

  Here's what the complete tenant configuration should look like for Ralph Lauren:

  {
    "client": "ralph_lauren_na",  // or "ralph_lauren_eu"

    // Main product profile configuration
    "inventorysmart_create_product_profile": {
      "showIAProductProfileEdits": true,    // ✅ REQUIRED - Shows the new table
      "disablePinnedRows": true,            // existing config
      "enableSaveEdit": true,               // existing config
      "salesAttributes": ["retirement"],    // existing config
      "maxPriceAttribute": 100              // existing config
    },

    // Infinite scrolling configuration
    "infiniteScrolling": [
      "MPIARecommendedDetailsTable",        // existing
      "MPUserCreatedDetailsTable",          // existing
      "MPIAProductProfileEditsTable",       // ✅ OPTIONAL - Enables infinite scroll for new table
      "MPUserCreatedStoreContributionsMaterialDescription"  // existing
    ]
  }

  ---
  Flag Summary Table

  | Flag Name                                               | Type            | Required? | Purpose
                           |
  |---------------------------------------------------------|-----------------|-----------|------------------------------------------------------
  -------------------------|
  | showIAProductProfileEdits                               | Boolean         | YES       | Controls visibility of the entire "IA Product Profile
   Edits" table            |
  | MPIAProductProfileEditsTable in infiniteScrolling array | String in Array | NO        | Enables infinite scroll for the table (otherwise uses
   server-side pagination) |

  ---
  What Happens Without Each Flag?

  Without showIAProductProfileEdits:

  - ❌ "IA Product Profile Edits" table will NOT appear at all
  - ✅ No errors, table is just hidden (backward compatible)

  Without MPIAProductProfileEditsTable in infiniteScrolling:

  - ✅ Table will still appear (if showIAProductProfileEdits is true)
  - ℹ️ Will use server-side pagination instead of infinite scroll
  - ✅ Still fully functional, just different pagination behavior

  ---
  Backend Team Action Items

  To enable this feature for Ralph Lauren, the backend team needs to:

  1. Add to tenant config API response for Ralph Lauren clients:
  {
    "inventorysmart_create_product_profile": {
      "showIAProductProfileEdits": true
    }
  }
  2. (Optional) If they want infinite scrolling:
  {
    "infiniteScrolling": [
      "MPIAProductProfileEditsTable"
    ]
  }

  The API endpoint that returns this config is:
  GET /core/get-tenant-config/inventorysmart