Great news! The CLAUDE.md file has already been updated with a comprehensive Frontend Navigation Guide, including a detailed walkthrough of the exact Product Profile screen you're showing!

Let me give you a quick summary and practical example:

Frontend Flow (vs Backend Flow)

Backend: Route → Controller → Service → Database
Frontend: Route → Component → Redux Actions/Services → API Calls

---

For Your Material Profile Screen: Step-by-Step Navigation

1️⃣ Start with the URL

```
/inventory-smart/product-profile
```

2️⃣ Find Route Constant

```javascript
src/modules/inventorysmart/constants-inventorysmart/routesConstants.js:5
export const PRODUCT_PROFILE = "/inventory-smart/product-profile";
```

3️⃣ Find Route Configuration

```javascript
src/modules/inventorysmart/routes-inventorysmart/routes.js:430-435
{
  path: PRODUCT_PROFILE,
  component: ProductProfileComponent,  // ← This tells you the main component
  title: "Product Profile",
  screenName: "Product Profile",
  module: "inventorysmart_product_profile",
}
```

4️⃣ Open Main Component

```
src/modules/inventorysmart/pages-inventorysmart/Product-Profile/index.js
```

This file contains:
- Lines 249-256: Tab component ("IA Recommended" | "User Created")
- Lines 258-278: "Create Material Profile" button
- Lines 291-297: "Details table" accordion with <DashboardTable /> component

5️⃣ Find Sub-Component (Details Table)

```
src/modules/inventorysmart/pages-inventorysmart/Product-Profile/Product-Profile-Dashboard/dashboard-table.jsx
```

This renders the actual data grid you see.

6️⃣ Check Services (Redux + API)

```
src/modules/inventorysmart/services-inventorysmart/Product-Profile/product-profile-dashboard-service.js
```

Key functions:
- Lines 84-90: getIARecommededTableData() - API call for IA Recommended tab
- Lines 92-98: getUserCreatedTableData() - API call for User Created tab

7️⃣ API Endpoints

```javascript
src/modules/inventorysmart/constants-inventorysmart/apiConstants.js:73-76
export const GET_IA_RECOMMENDED_TABLE_DATA = "inventory-smart/product-profile/ia";
export const GET_USER_CREATED_TABLE_DATA = "inventory-smart/product-profile/user";
```

---

Quick Navigation Pattern

For any screen you want to modify:

1. See URL in browser → Note the path (e.g., /inventory-smart/product-profile)
2. Find route constant → constants-{module}/routesConstants.js
3. Find route definition → routes-{module}/routes.js (get component name)
4. Open main component → pages-{module}/{feature-name}/index.js
5. Find UI elements → Look in JSX return statement for buttons, tabs, tables
6. Find sub-components → Same directory, look for imported components
7. Check services → services-{module}/{feature-name}/
8. Find API endpoints → constants-{module}/apiConstants.js

---

Pro Tips

Search for visible text:
If you see "Create Material Profile" on screen:

```bash
grep -r "Create Material Profile" src/
```

Module structure is consistent:

```
src/modules/{module}/
  ├── pages-{module}/        # UI components
  ├── services-{module}/     # API calls & Redux
  ├── constants-{module}/    # Routes & API endpoints
  └── routes-{module}/       # Route definitions
```

The CLAUDE.md file (lines 78-333) has the complete guide with more examples and patterns. It's your map to navigating the frontend codebase!
