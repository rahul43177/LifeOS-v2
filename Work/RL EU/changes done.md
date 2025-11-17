 File: store-size-contribution.jsx

  ---
  Change 1: Editability Function (Lines 130-143)

  Added localhost check:
  // Line 130-131
  const isLocalhost = window.location.hostname === "localhost" ||
                     window.location.hostname === "127.0.0.1";

  // Line 143
  const shouldEnableEdit = isLocalhost || isRalphLaurenEU || isEditingEnabled;

  ---
  Change 2: IA Recommended Save Button (Lines 693-697)

  Added localhost check:
  // Line 693-697
  {userStoreContributionUpdate.length > 0 &&
    (window.location.hostname === "localhost" ||
     window.location.hostname === "127.0.0.1" ||
     props.inventorysmartScreenConfig?.client === "rl_eu" ||
     props.inventorysmartScreenConfig?.client === "ralphlauren_eu" ||
     props.productProfileConfig?.enableMaterialProfileEdit) && (

  ---
  Change 3: User Created Save Button (Lines 726-731)

  Added localhost check:
  // Line 726-731
  {(window.location.hostname === "localhost" ||
    window.location.hostname === "127.0.0.1" ||
    props.inventorysmartScreenConfig?.client === "signet" ||
    props.inventorysmartScreenConfig?.client === "rl_eu" ||
    props.inventorysmartScreenConfig?.client === "ralphlauren_eu" ||
    props.productProfileConfig?.enableSaveEdit) && (

  ---
  Change 4: API Payload (Line 567)

  Added client_code:
  // Line 567
  client_code: props.inventorysmartScreenConfig?.client || "unknown",

  ---
  Summary

  - File: store-size-contribution.jsx
  - Lines Changed: 130-131, 143, 567, 693-697, 726-731
  - What: Added window.location.hostname === "localhost" checks in 3 places + added client_code to API payload
  - Result: Feature now active on localhost for development