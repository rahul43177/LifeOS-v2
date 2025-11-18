
## Project Overview

  

Make the Store & Size Contribution table editable for Material Profile IA Recommendations, allowing users to modify:

1. Size-level columns (1-Size 1, 2-Size 2, 3-Size 3, etc.)

2. Overall Proportion % column

  

With comprehensive validation ensuring data integrity.

  

---

  

## Business Requirements

  

### Editability Requirements

- **Columns to Make Editable:**

- All size columns (size_1, size_2, size_3, size_11, size_12, size_13, etc.)

- Overall Proportion % column

- Both in IA Recommended and User Created tabs

  

### Validation Requirements

  

#### 1. Horizontal Validation (Per Store)

- **Rule**: For each store, the sum of all size column percentages must equal 100%

- **Example**:

```

Store: MADRID CHILDRENS

1-Size 1: 0.62%

2-Size 2: 42.37%

3-Size 3: 49.70%

11-Size 11: 0.00%

12-Size 12: 7.30%

13-Size 13: 0.02%

─────────────────

Total: 100.00% ✓

```

  

#### 2. Vertical Validation (Overall Proportion)

- **Rule**: The sum of all stores' Overall Proportion % must equal 100%

- **Example**:

```

MADRID CHILDRENS: 16.11%

LA VALLEE CW: 13.52%

KILDARE CHILDRENS: 8.86%

... (all stores)

─────────────────

Total: 100.00% ✓

```

  

### UI/UX Requirements

- Cells should be editable with double-click

- Save button appears below table when changes are made

- Validation runs before saving

- Error dialog shows all validation issues with details

- Total row should remain non-editable (pinned row)

- Success message after successful save

- Table refreshes with latest data after save

  

---

  

## Technical Architecture

  

### File Structure

```

mtp-frontend/frontend/src/

├── modules/inventorysmart/

│ ├── pages-inventorysmart/

│ │ └── Product-Profile/

│ │ └── Product-Profile-Dashboard/

│ │ └── store-size-contribution.jsx (MAIN FILE)

│ ├── services-inventorysmart/

│ │ └── Product-Profile/

│ │ └── product-profile-dashboard-service.js

│ └── constants-inventorysmart/

│ └── apiConstants.js

```

  

### Data Flow

  

```

User Clicks Material Profile

↓

API: GET_STORE_SIZE_CONTRIBUTION_DATA

↓

Backend returns: { columns: [...], data: [...] }

↓

Frontend hardcodes is_editable = true for size & overall_proportion columns

↓

agGridColumnFormatter processes columns (sets up CellRenderers)

↓

AgGrid displays editable table

↓

User edits cell → onBlur event

↓

updateEditedRowState() → userStoreContributionUpdate state

↓

Save button appears (userStoreContributionUpdate.length > 0)

↓

User clicks "Save Edits"

↓

validateAllChanges() runs

↓

┌─────────────────┐

│ Validation Pass? │

└────────┬────────┘

│

No ──┴── Yes

↓ ↓

Dialog → Save API Call

Shows UPDATE_STORE_CONTRIBUTION_DATA

Errors ↓

Refetch data

↓

Show success message

```

  

---

  

## Implementation Plan

  

### Phase 1: Column Configuration Override (Frontend Hardcoding)

  

**Objective**: Make columns editable without waiting for backend database configuration

  

**Task 1.1**: Set `is_editable` BEFORE agGridColumnFormatter

- Loop through columns from backend

- Find `overall_proportion` column → set `is_editable = true`

- Find `product_profile_pen` parent column → set `is_editable = true` on all `sub_headers`

- Collect all editable column names into `editableColumnNames` array

  

**Why Before Formatter?**

- `agGridColumnFormatter` reads `is_editable` flag

- If set, formatter automatically configures:

- CellRenderer components

- Event handlers (onBlur)

- Editable cell behavior

- Input types based on column type

- Setting after formatting doesn't trigger these setups

  

**Implementation Location**: Lines 75-90 in store-size-contribution.jsx

  

---

  

### Phase 2: State Management

  

**Objective**: Track edited cells and manage component state

  

**State Variables**:

```javascript

const [userStoreContributionUpdate, setUserStoreContributionUpdate] = useState([]);

const userStoreContributionUpdateRef = useRef([]);

const [validationErrors, setValidationErrors] = useState([]);

const [showValidationDialog, setShowValidationDialog] = useState(false);

const [editableColumnNames, setEditableColumnNames] = useState([]);

```

  

**State Structure**:

```javascript

// userStoreContributionUpdate example:

[

{

store_code: "00627",

store_name: "MADRID CHILDRENS",

size_1: 0.25, // edited value

size_2: 49.70,

overall_proportion: 16.11

},

{

store_code: "00670",

...

}

]

```

  

**Key Functions**:

- `updateEditedRowState(data)` - Updates state when cell is edited

- `onBlur()` - Captures cell changes and triggers state update

- Ref (`userStoreContributionUpdateRef`) - Maintains reference for performance

  

---

  

### Phase 3: Validation Logic

  

**Objective**: Ensure data integrity before saving

  

#### Validation Function 1: Horizontal Sum (Per Store)

  

```javascript

const validateHorizontalSum = () => {

const errors = [];

  

// For each edited row (or all rows)

rowsToValidate.forEach((row) => {

if (row.store_name === 'Total') return; // Skip pinned row

  

let sum = 0;

editableColumnNames.forEach((colName) => {

sum += getCurrentValue(row, colName);

});

  

// Check if sum equals 100% (with 0.01% tolerance)

if (Math.abs(sum - 100) > 0.01) {

errors.push({

type: 'horizontal',

storeCode: row.store_code,

storeName: row.store_name,

currentSum: sum.toFixed(2),

message: `Store "${row.store_name}" sums to ${sum}% (expected 100%)`

});

}

});

  

return errors;

};

```

  

#### Validation Function 2: Vertical Sum (Overall Proportion)

  

```javascript

const validateVerticalSum = () => {

let sum = 0;

  

dataToValidate.forEach((row) => {

if (row.store_name === 'Total') return;

sum += getCurrentValue(row, 'overall_proportion');

});

  

if (Math.abs(sum - 100) > 0.01) {

return {

type: 'vertical',

currentSum: sum.toFixed(2),

message: `Overall Proportion sums to ${sum}% (expected 100%)`

};

}

  

return null;

};

```

  

#### Master Validation

  

```javascript

const validateAllChanges = () => {

const horizontalErrors = validateHorizontalSum();

const verticalError = validateVerticalSum();

  

const allErrors = [...horizontalErrors];

if (verticalError) allErrors.push(verticalError);

  

if (allErrors.length > 0) {

setValidationErrors(allErrors);

setShowValidationDialog(true);

return false; // Validation failed

}

  

return true; // Validation passed

};

```

  

**Tolerance**: 0.01% to account for floating-point precision

  

---

  

### Phase 4: UI Components

  

#### Component 1: Save Button

  

**Location**: Below AgGrid table

**Visibility**: Only when `userStoreContributionUpdate.length > 0`

  

```jsx

{userStoreContributionUpdate.length > 0 && (

<div style={{ display: 'flex', justifyContent: 'center', margin: '1rem 0' }}>

<Button

color="primary"

variant="contained"

onClick={saveUserCreatedStoreContributionPercentage}

>

Save Edits

</Button>

</div>

)}

```

  

#### Component 2: Validation Error Dialog

  

**Material-UI Dialog with**:

- Error title in red

- List of all validation errors

- Each error shows:

- Error message

- Store code (for horizontal errors)

- Current sum vs expected sum

- Close button to dismiss

  

```jsx

<Dialog open={showValidationDialog} maxWidth="md" fullWidth>

<DialogTitle style={{ color: '#d32f2f' }}>

Validation Errors

</DialogTitle>

<DialogContent>

{validationErrors.map((error, index) => (

<div key={index} style={{ backgroundColor: '#ffebee', padding: '8px' }}>

• {error.message}

{error.type === 'horizontal' && (

<Typography variant="caption">

Store Code: {error.storeCode}

</Typography>

)}

</div>

))}

</DialogContent>

<DialogActions>

<Button onClick={() => setShowValidationDialog(false)}>Close</Button>

</DialogActions>

</Dialog>

```

  

---

  

### Phase 5: API Integration

  

#### API Endpoint

```javascript

// apiConstants.js

export const UPDATE_STORE_CONTRIBUTION_DATA =

"inventory-smart/product-profile/contribution/store-size-edit/user";

```

  

#### Service Function

```javascript

// product-profile-dashboard-service.js

export const updateUserStoreContribution = (data) => () => {

return axiosInstance({

url: UPDATE_STORE_CONTRIBUTION_DATA,

method: "POST",

data: data.body,

});

};

```

  

#### Payload Format

```javascript

{

pp_code: "830903657001",

data: [

{

store_code: "00627",

original_overall_proportion: "0.161100000",

new_overall_proportion: "0.165000000",

original_size_level_proportion: {

size_1: "0.006200000",

size_2: "0.497000000",

...

},

new_size_level_proportion: {

size_1: "0.002500000", // changed

size_2: "0.497000000",

...

}

},

...

]

}

```

  

#### Save Flow

```javascript

const saveUserCreatedStoreContributionPercentage = async () => {

// 1. Validate

if (!validateAllChanges()) return;

  

// 2. Prepare payload

const body = {

pp_code: props.selectedPPCode,

data: preparePayloadOnEdit()

};

  

// 3. Call API

const response = await props.updateUserStoreContribution({ body });

  

// 4. Refetch data

if (props.tabState === 0) {

// IA Recommended

await props.getStoreSizeContributionData(props.queryParam);

} else {

// User Created

await props.getStoreSizeContributionForUserData(props.queryParam);

}

  

// 5. Show success & reset state

displaySnackMessages(UPDATED_MESSAGE, "success");

setUserStoreContributionUpdate([]);

};

```

  

---

  

### Phase 6: AgGrid Configuration

  

#### Props Passed to AgGridComponent

  

```javascript

<AgGridComponent

rowdata={storeSizeContributionData}

columns={storeSizeContributionColumns} // with is_editable set

uniqueRowId={"store_code"}

  

// Editing support

onBlur={onBlur} // Capture cell changes

loadTableInstance={setUserStoreContributionTableInstance} // Grid API access

  

// Other props

pagination={false}

getRowStyle={getRowStyle} // Bold styling for Total row

pinnedTopRowData={pinnedRow} // Pin Total row to top

sizeColumnsToFitFlag

downloadAsExcel={true}

/>

```

  

#### Cell Editing Behavior

- **Double-click** to edit (default AgGrid behavior with `is_editable`)

- **Tab** or **Enter** to move to next cell

- **Blur** (click outside) triggers `onBlur` event

- Changes immediately update state

- Cell renderer handles input type based on column type (percentage)

  

---

  

## Database Configuration (Future)

  

**Once backend team updates CSV configuration**, remove hardcoding and columns will be editable automatically.

  

**Files to Update**:

```

/mtp-database/database/{tenant}/data/inventory_smart/table_configurations.csv

```

  

**Configuration Example**:

```csv

table_name,column_name,is_editable,type,...

product_profile_store_contribution,overall_proportion,true,percentage,...

product_profile_store_contribution,size_1,true,percentage,...

product_profile_store_contribution,size_2,true,percentage,...

...

```

  

**When this is done**, remove lines 75-90 in store-size-contribution.jsx:

```javascript

// DELETE THIS BLOCK when backend config is updated:

copyOfStoreSizeContributionData.forEach((item) => {

if (item.column_name === "overall_proportion") {

item.is_editable = true; // HARDCODED

}

if (item.column_name === "product_profile_pen") {

item?.sub_headers?.forEach((subCol) => {

subCol.is_editable = true; // HARDCODED

});

}

});

```

  

---

  

## Testing Plan

  

### Unit Testing Scenarios

  

1. **Edit Single Cell**

- Edit one size column value

- Verify Save button appears

- Verify state updates

  

2. **Horizontal Validation - Pass**

- Edit size columns so sum = 100%

- Click Save

- Should pass validation and save

  

3. **Horizontal Validation - Fail**

- Edit size columns so sum ≠ 100%

- Click Save

- Dialog should show error with store name and sum

  

4. **Vertical Validation - Pass**

- Edit overall_proportion values so sum = 100%

- Click Save

- Should pass validation and save

  

5. **Vertical Validation - Fail**

- Edit overall_proportion so sum ≠ 100%

- Click Save

- Dialog should show error with total sum

  

6. **Multiple Errors**

- Create both horizontal and vertical errors

- Click Save

- Dialog should show all errors

  

7. **Total Row Non-Editable**

- Try to edit cells in Total row

- Should not be editable (disabled)

  

8. **Floating Point Tolerance**

- Set sum to 99.99% or 100.01%

- Should pass (within 0.01% tolerance)

  

9. **Tab Switching**

- Switch between IA Recommended and User Created tabs

- Verify state resets appropriately

  

10. **Save and Refresh**

- Make valid edits and save

- Verify table refreshes with saved data

- Verify Save button disappears

  

---

  

## Edge Cases & Error Handling

  

### Edge Case 1: Null/Empty Values

- **Scenario**: Cell has null or empty value

- **Handling**: Treat as 0 in validation

  

### Edge Case 2: Non-Numeric Input

- **Scenario**: User types non-numeric characters

- **Handling**: AgGrid validates based on column type (percentage)

  

### Edge Case 3: Network Failure

- **Scenario**: API call fails

- **Handling**:

- Show error message

- Keep edited state

- User can try again

  

### Edge Case 4: Concurrent Edits

- **Scenario**: Multiple users editing same profile

- **Handling**: Last save wins (optimistic locking not implemented)

  

### Edge Case 5: Very Small Percentages

- **Scenario**: Store has 0.01% size distribution

- **Handling**: Precision maintained up to 0.01%

  

---

  

## Performance Considerations

  

### Optimization 1: useRef for State

- Uses `userStoreContributionUpdateRef` to avoid re-renders

- Only updates state when necessary

  

### Optimization 2: Validation Only on Save

- Doesn't validate on every keystroke

- Validates once when user clicks Save button

  

### Optimization 3: Selective Re-fetching

- After save, only refetches affected data

- Uses correct API based on current tab

  

---

  

## Security Considerations

  

1. **Input Validation**: Client-side and server-side

2. **Authorization**: User must have edit permissions

3. **Audit Trail**: Backend should log all changes

4. **Data Integrity**: Validation ensures sum = 100%

  

---

  

## Success Criteria

  

- ✅ Size columns are editable

- ✅ Overall Proportion column is editable

- ✅ Save button appears when changes are made

- ✅ Validation prevents invalid data

- ✅ Error dialog shows clear messages

- ✅ Data saves successfully to backend

- ✅ Table refreshes after save

- ✅ Total row remains non-editable

- ✅ Works for both IA Recommended and User Created tabs

  

---

  

## Timeline Estimate

  

- **Phase 1-2**: 2 hours (Column config + State management)

- **Phase 3**: 2 hours (Validation logic)

- **Phase 4**: 1 hour (UI components)

- **Phase 5**: 1 hour (API integration)

- **Phase 6**: 1 hour (AgGrid setup)

- **Testing**: 2 hours

- **Total**: ~9 hours

  

---

  

## Future Enhancements

  

1. **Real-time Validation**

- Show sum as user types

- Highlight cells in red if sum ≠ 100%

  

2. **Auto-distribute Feature**

- Button to evenly distribute percentages

- Automatically make sum = 100%

  

3. **Undo/Redo**

- Allow users to undo changes

- History of edits

  

4. **Batch Operations**

- Edit multiple stores at once

- Apply same percentage across stores

  

5. **Export Validation Report**

- Download list of validation errors

- CSV format for analysis

  

6. **Optimistic Locking**

- Prevent concurrent edit conflicts

- Show warning if data changed by another user

  

---

  

## Support & Maintenance

  

### Common Issues

  

**Issue**: Cells not editable

- **Solution**: Check if `is_editable` is set before formatter runs

  

**Issue**: Save button doesn't appear

- **Solution**: Check if `onBlur` is wired up correctly

  

**Issue**: Validation always fails

- **Solution**: Check floating-point tolerance (0.01%)

  

**Issue**: Total row is editable

- **Solution**: Verify `setCellsToBeDisabled` function

  

### Monitoring

  

- Track save success/failure rates

- Monitor validation error frequency

- Log performance metrics (save time)

  

---

  

## Documentation

  

- **User Guide**: How to edit and save changes

- **API Documentation**: Payload format and response

- **Error Codes**: List of validation error messages

- **FAQ**: Common questions and answers