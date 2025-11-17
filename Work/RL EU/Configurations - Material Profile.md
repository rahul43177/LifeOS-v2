# Backend Configuration Instructions - Ralph Lauren IA Product Profile Edits

## Overview
This document provides step-by-step instructions for the backend engineer to enable the "IA Product Profile Edits" table feature **ONLY for Ralph Lauren clients** (Ralph Lauren NA and Ralph Lauren EU).

---

## Required Changes

### 1. Database Configuration File Location

**For Ralph Lauren EU:**
```
/Users/rahulmishra/Desktop/mtp-database/database/ralph_lauren_eu_is/data/global/tenant_attribute_master.csv
```

**For Ralph Lauren NA:**
```
/Users/rahulmishra/Desktop/mtp-database/database/ralph_lauren_na_is/data/global/tenant_attribute_master.csv
```

---

### 2. Add New Configuration Entry

#### Current Status
- ✅ `core_screen_configuration` exists (line 54)
- ✅ `assort_smart_screen_configuration` exists (line 59)
- ❌ `inventorysmart_screen_configuration` **DOES NOT EXIST** - needs to be created

#### Action Required
Add a **new row** to `tenant_attribute_master.csv` with the following values:

---

### 3. Exact CSV Row to Add

**Copy this entire line and add it as a new row at the end of the CSV file:**

```csv
3005,inventorysmart_screen_configuration,APPLICATION,module wise configuration for client - inventorysmart,TRUE,"{""inventorysmart_create_product_profile"": {""showIAProductProfileEdits"": true}}",1,TRUE,
```

---

### 4. Field-by-Field Breakdown

| Field | Value | Description |
|-------|-------|-------------|
| **attribute_code** | `3005` | Next available unique ID (current highest is 3004) |
| **name** | `inventorysmart_screen_configuration` | Configuration key name |
| **attribute_type** | `APPLICATION` | Type of configuration |
| **description** | `module wise configuration for client - inventorysmart` | Human-readable description |
| **status** | `TRUE` | Active status |
| **attribute_value** | `{"inventorysmart_create_product_profile": {"showIAProductProfileEdits": true}}` | JSON configuration (see below) |
| **application_code** | `1` | 1 = inventorysmart module |
| **user_edited** | `TRUE` | Can be edited by users |
| **module_code** | *(empty)* | Optional module grouping |

---

### 5. JSON Structure in attribute_value

The `attribute_value` field contains this JSON (double-quoted for CSV format):

```json
{
  "inventorysmart_create_product_profile": {
    "showIAProductProfileEdits": true
  }
}
```

**CSV-escaped version (what goes in the CSV file):**
```
"{""inventorysmart_create_product_profile"": {""showIAProductProfileEdits"": true}}"
```

---

### 6. How the Frontend Reads This Config

#### API Endpoint
```
GET /core/get-tenant-config/inventorysmart
```

#### Expected API Response
```json
{
  "inventorysmartScreenConfig": {
    "inventorysmart_create_product_profile": {
      "showIAProductProfileEdits": true
    }
  }
}
```

#### Frontend Redux Mapping
The frontend reads this value from Redux state:
```javascript
inventorysmartReducer?.inventorySmartCommonService?.inventorysmartScreenConfig
  ?.inventorysmart_create_product_profile?.showIAProductProfileEdits
```

---

### 7. Application Code Reference

For future configurations, here's the mapping:

| application_code | Module |
|-----------------|--------|
| `1` | inventorysmart |
| `2` | assortsmart |
| `3` | core |
| `4` | plansmart |

---

### 8. Testing Steps

After adding the configuration:

1. **Restart the backend service** to load the new config
2. **Test the API endpoint:**
   ```bash
   curl -X GET "https://<your-backend-url>/core/get-tenant-config/inventorysmart" \
     -H "Authorization: Bearer <token>"
   ```
3. **Verify the response** contains:
   ```json
   {
     "inventorysmartScreenConfig": {
       "inventorysmart_create_product_profile": {
         "showIAProductProfileEdits": true
       }
     }
   }
   ```
4. **Frontend testing:**
   - Login to Ralph Lauren EU tenant
   - Navigate to: `/inventory-smart/product-profile`
   - Click on "User Created" tab
   - Verify "IA Product Profile Edits" table appears below "Details table"

---

### 9. For Other Clients (Non-Ralph Lauren)

**IMPORTANT:** Do NOT add this configuration to other client tenant configs.

The frontend has a safety check:
```javascript
{props.productProfileConfig?.showIAProductProfileEdits && (
  // IA Product Profile Edits table renders here
)}
```

If the flag is missing or false, the table:
- ❌ Will NOT render
- ❌ Will NOT call the API endpoint
- ❌ Will NOT affect the user experience

This ensures **zero impact** on other clients.

---

### 10. Rollback Instructions

If you need to disable this feature:

**Option 1: Set to false**
```csv
3005,inventorysmart_screen_configuration,APPLICATION,module wise configuration for client - inventorysmart,TRUE,"{""inventorysmart_create_product_profile"": {""showIAProductProfileEdits"": false}}",1,TRUE,
```

**Option 2: Delete the row**
Remove the entire row with `attribute_code = 3005`

**Option 3: Set status to FALSE**
```csv
3005,inventorysmart_screen_configuration,APPLICATION,module wise configuration for client - inventorysmart,FALSE,"{""inventorysmart_create_product_profile"": {""showIAProductProfileEdits"": true}}",1,TRUE,
```

---

## Summary

### What needs to be done:
1. Open `tenant_attribute_master.csv` for Ralph Lauren EU (and Ralph Lauren NA if needed)
2. Add the new row with `attribute_code = 3005`
3. Ensure JSON is properly escaped with double quotes (`""`)
4. Restart backend service
5. Test the API endpoint
6. Verify frontend displays the new table

### Who is affected:
- ✅ **Ralph Lauren EU** - Will see the new "IA Product Profile Edits" table
- ✅ **Ralph Lauren NA** - Will see the new table (if config added)
- ❌ **All other clients** - NO CHANGES, feature remains hidden

---

## Questions?

If you have any questions about this configuration, please contact the frontend team or refer to:
- Frontend implementation: `src/modules/inventorysmart/pages-inventorysmart/Product-Profile/Product-Profile-Dashboard/dashboard-table.jsx:540-587`
- API endpoint constant: `src/modules/inventorysmart/constants-inventorysmart/apiConstants.js:77-78`
