#### The issue : 
1. Whenever the user is trying to create a store group in test instance and there is a checkbox called : Include store groups 
2. When the user is clicking on that in the test instance , it is keep on loading indefinitely 
3. But that is working fine in the UAT 

#### The code for that `storeFilters.jsx` 
###### Test code : 
```js
import { FormControlLabel, Paper, Typography } from "@mui/material";

import Button from "@mui/material/Button";

import globalStyles from "core/Styles/globalStyles";

import { getTenantConfigApplicationLevel } from "core/actions/tenantConfigActions";

import { storeGrouping } from "config/routes";

import AgGridTable from "core/Utils/agGrid";

import CellRenderers from "core/Utils/agGrid/cellRenderer";

import agGridColumnFormatter from "core/Utils/agGrid/column-formatter";

import {

checkForEmptyTableUserConfig,

replaceSpecialCharacter,

} from "core/Utils/functions/utils";

import { StyledCheckbox } from "core/Utils/selection/selection";

import RequestsTable from "core/pages/product-grouping/components/product-group-components/clusterRequestsTable";

import { fetchGradeList } from "core/pages/store-grading/grading-services";

import { Prompt } from "impact-ui";

import { cloneDeep, isEmpty } from "lodash";

import { isNonPrimitiveArray } from "modules/inventorysmart/pages-inventorysmart/Create-Allocation/helperFunctions";

import moment from "moment";

import { forwardRef, useCallback, useEffect, useRef, useState } from "react";

import { connect } from "react-redux";

import { useLocation, useNavigate } from "react-router-dom-v5-compat";

import { setSelectedFilters } from "../../../actions/filterAction";

import { addSnack } from "../../../actions/snackbarActions";

import { getColumnsAg } from "../../../actions/tableColumnActions";

import {

ToggleLoader,

addSelectedGroups,

addStoresToGroups,

addToExistingStores,

deletedGrpsInEdit,

deletedRowsInEdit,

fetchStoreGroupCustomClusterInfo,

fetchStoreGroups,

fetchStoreGrpFilteredStores,

newGrpsInEdit,

newRowsInEdit,

setClassificationValue,

setClusterParamters,

setClusterTimeFormat,

setClusterTimePeriod,

setGroupsCols,

setSelectedCluster,

setSelectedClusterFilters,

setSelectedStores,

setSelectedStoresSelectAllState,

setStoreGroupCustomLoaderValue,

setStoreGroupFilteredStores,

updateGrp,

} from "../services-store-grouping/custom-store-group-service";

import {

capitalizeFirstLetterDropdown,

formatFiltersDependency,

renderGroupTypeCell,

} from "./common-functions";

import "./groupTable.scss";

import GroupName from "./storeGroupName";

  

const FilteredStores = forwardRef((props, ref) => {

const globalClasses = globalStyles();

const [open, setopen] = useState(false);

const navigate = useNavigate();

let location = useLocation();

const [isIncludeGrpsChecked, setisIncludeGrpsChecked] = useState(false);

const [grpColumns, setgroupColumns] = useState([]);

const [columns, setColumns] = useState([]);

const [confirmPopUp, setconfirmPopUp] = useState(false);

const [openViewClusterStatus, setopenViewClusterStatus] = useState(false);

const [confirmBox, showConfirmBox] = useState(false);

const isCancelledOrUpdated = useRef(false);

const isCancelledOrUpdatedGrps = useRef(false);

const noneditableStores = useRef({});

const [storeGradeFlag, setStoreGradeFlag] = useState(false);

const goBack = () => {

if (props.isEdit) {

const urlSplitArr = location.pathname.split("/");

const grpId = urlSplitArr.pop();

props.prevScr

? navigate(`${props.prevScr}/view/${grpId}`, {

state: {

prevScr: props.prevScr,

from: location.pathname,

},

})

: navigate(`${storeGrouping.viewGroup}/${grpId}`, {

state: {

from: location.pathname,

},

});

} else {

props.prevScr

? navigate(props.prevScr, {

state: {

from: location.pathname,

},

})

: navigate(storeGrouping.home, {

state: {

from: location.pathname,

},

});

}

};

  

useEffect(() => {

const fetchColumns = async () => {

if (isIncludeGrpsChecked) {

props.ToggleLoader(true);

let cols = [];

if (props.groupsCols.length === 0) {

cols = await props.getColumnsAg("table_name=store_group");

} else {

cols = cloneDeep(props.groupsCols);

}

cols = cols.map((col) => {

if (col.accessor === "special_classification") {

col = renderGroupTypeCell(col);

}

return col;

});

  

props.setGroupsCols(cols);

setgroupColumns(cols);

ref?.storeGroupTableRef?.current?.api?.refreshServerSideStore({

purge: true,

});

}

};

fetchColumns();

}, [isIncludeGrpsChecked]);

  

useEffect(() => {

if (!isIncludeGrpsChecked) {

props.addSelectedGroups([]);

}

}, [isIncludeGrpsChecked, props.filteredStores]);

  

useEffect(() => {

const fetchCols = async () => {

let cols = cloneDeep(props.columns);

let gradeFlag = false;

cols.forEach((item) => {

if (item.column_name === "grade" && item.is_editable) {

gradeFlag = true;

}

});

if (gradeFlag) {

const { data } = await fetchGradeList();

let { data: config } = await props.getTenantConfigApplicationLevel(1, {

attribute_name: "filter_attributes_display_config",

});

let nonEditStores =

config?.data[0]?.attribute_value?.store?.store_code

?.display_order_top;

noneditableStores.current = nonEditStores;

cols = cols.map((item) => {

if (item.column_name === "grade") {

item.options = data.data

.filter((item) => item.name !== "ECOM")

.map((item) => {

return {

label: item.name,

id: item.name,

value: item.name,

};

});

item.initialData = item.options;

item.cellRenderer = (cellProps, extraProps) => {

if (cellProps.value === "ECOM") {

return <>{cellProps.value}</>; // Render "ECOM" as non-editable text

} else {

return (

<CellRenderers

cellData={cellProps}

column={item}

extraProps={extraProps}

></CellRenderers>

);

}

};

}

return item;

});

const formattedResponse = agGridColumnFormatter(cols);

setColumns(formattedResponse);

setStoreGradeFlag(true);

} else {

setColumns(cols);

}

};

fetchCols();

}, [props.columns]);

  

useEffect(() => {

let obj = {};

obj["store_hierarchy"] = [];

props.setSelectedFilters(obj);

}, []);

  

const rowSelectionHandler = (rows, data) => {

const unselectdRows = data.filter((storeNode) => {

return !rows.some((select) => {

return select.store_code === storeNode.data.store_code;

});

});

if (props.isEdit) {

//selected rows

//Already mapped - and in delete window - Remove from Delete

//Not mapped -

//If it is not mapped => Add it to new window

//If it is mapped and excluded => Add it to delete window

let should_include_in_delete = [];

let should_exclude_in_delete = [];

let should_include_in_new = [];

let should_exclude_in_new = [];

rows.forEach((row, _idx) => {

if (row.is_mapped) {

if (

props.deleteEditStores.some((del) => {

return del.store_code === row.store_code;

})

) {

should_exclude_in_delete.push(row);

}

} else {

if (

!props.newEditStores.some((newone) => {

return newone.store_code === row.store_code;

})

) {

should_include_in_new.push(row);

}

}

});

unselectdRows.forEach((row, _idx) => {

if (row.data.is_mapped) {

if (

!props.deleteEditStores.some((del) => {

return del.store_code === row.data.store_code;

})

) {

should_include_in_delete.push(row.data);

}

} else {

if (

props.newEditStores.some((newone) => {

return newone.store_code === row.data.store_code;

})

) {

should_exclude_in_new.push(row.data);

}

}

});

  

let updatedDelete = props.deleteEditStores.filter((del) => {

return !should_exclude_in_delete.some((exclude) => {

return exclude.store_code === del.store_code;

});

});

updatedDelete = [...updatedDelete, ...should_include_in_delete];

props.newRowsInEdit(should_include_in_new);

props.deletedRowsInEdit(updatedDelete);

} else {

props.setSelectedStores(rows);

}

};

  

const grpSelectionHandler = (grps, data) => {

if (props.isEdit) {

//selected rows

//Already mapped - and in delete window - Remove from Delete

//Not mapped -

//If it is not mapped => Add it to new window

//If it is mapped and excluded => Add it to delete window

let should_include_in_delete = [];

let should_exclude_in_delete = [];

let should_include_in_new = [];

let should_exclude_in_new = [];

const unselectdRows = data.filter((prod) => {

return !grps.some((select) => {

return select.sg_code === prod.data.sg_code;

});

});

grps.forEach((grp, _idx) => {

if (grp.is_mapped) {

if (

props.deleteEditGrps.some((del) => {

return del.sg_code === grp.sg_code;

})

) {

should_exclude_in_delete.push(grp);

}

} else {

if (

!props.newEditGrps.some((newone) => {

return newone.sg_code === grp.sg_code;

})

) {

should_include_in_new.push(grp);

}

}

});

unselectdRows.forEach((row, _idx) => {

if (row.data.is_mapped) {

if (

!props.deleteEditGrps.some((del) => {

return del.sg_code === row.data.sg_code;

})

) {

should_include_in_delete.push(row.data);

}

} else {

if (

props.newEditGrps.some((newone) => {

return newone.sg_code === row.data.sg_code;

})

) {

should_exclude_in_new.push(row.data);

}

}

});

  

let updatedDelete = props.deleteEditGrps.filter((del) => {

return !should_exclude_in_delete.some((exclude) => {

return exclude.sg_code === del.sg_code;

});

});

updatedDelete = [...updatedDelete, ...should_include_in_delete];

props.newGrpsInEdit(should_include_in_new);

props.deletedGrpsInEdit(updatedDelete);

} else {

props.addSelectedGroups(grps);

}

};

  

const toggleModalState = (status) => {

if (props.isEdit) {

onUpdate();

return;

}

setopen(status);

};

  

const onUpdate = async () => {

const body = {

name: props.grpObj.name,

special_classification: props.selectedGroupType,

channel:

props?.grpObj?.channel || (props?.allowMultiChannel ? "MC" : "NC"),

};

let selectedFilters = [];

if (ref.storeFiltersRef.current) {

const storeFilters = formatFiltersDependency(

ref.storeFiltersRef.current,

null,

true

);

selectedFilters.push(...storeFilters);

let selectedData = ref.storeTableRef.current?.api

?.getSelectedNodes()

.map((node) => {

return node.data;

});

let store_grade = selectedData

.filter((item) => item.grade)

.map((item) => {

return {

store_code: item.store_code,

store_grade: item.grade,

};

});

if (storeGradeFlag) {

body.store_grades = store_grade;

}

}

  

body["store_ids"] = {

filters: selectedFilters,

meta: {

search: [],

range: [],

sort: [],

},

metrics: [],

selection: {

data: [

{

searchColumns: {

is_mapped: {

filterType: "bool",

filter: true,

},

},

checkAll: true,

},

...(ref.storeTableRef?.current?.api?.checkConfiguration || []),

],

unique_columns: ["store_code"],

},

};

body["store_group_ids"] = {

filters: selectedFilters,

meta: {

search: [],

range: [],

sort: [],

},

metrics: [],

selection: {

data: ref.storeGroupTableRef?.current?.api?.checkConfiguration || [],

unique_columns: ["sg_code"],

},

};

try {

props.ToggleLoader(true);

const urlSplitArr = location.pathname.split("/");

const grpId = urlSplitArr.pop();

await props.updateGrp(grpId, body);

props.newRowsInEdit([]);

props.deletedRowsInEdit([]);

props.newGrpsInEdit([]);

props.deletedGrpsInEdit([]);

props.addSnack({

message: "Updated successfully",

options: {

variant: "success",

},

});

isCancelledOrUpdated.current = true;

refreshTables();

props.ToggleLoader(false);

} catch (error) {

props.ToggleLoader(false);

props.addSnack({

message: "Update Failed",

options: {

variant: "error",

},

});

}

};

  

const updateDatatodisableDropdown = (arr) => {

return arr.map((item) => {

if (noneditableStores.current.indexOf(item.store_code) > -1) {

item.disableStoreGrade = true;

} else {

item.disableStoreGrade = false;

}

return item;

});

};

const manualCallBack = async (body, pageIndex, params) => {

let manualbody = {};

manualbody = {

filters: [],

meta: { ...body },

metrics: [],

};

if (props.selectedGroupType === "custom") {

let dependency = props.selectedClusterFilters

? props.selectedClusterFilters.map((item) => {

return {

attribute_name: item.filter_id,

operator: "in",

column_name: item.filter_id,

dimension: item.dimension || "store",

values: Array.isArray(item.values)

? item.values.map((opt) => opt.value)

: item.values,

filter_type: item.filter_type,

};

})

: [];

manualbody = {

...manualbody,

filters: dependency,

request_id: props.selectedCluster.id,

};

} else {

let selectedFilters = [];

if (ref.storeFiltersRef.current) {

selectedFilters.push(...ref.storeFiltersRef.current);

}

let dependency = selectedFilters.map((item) => {

return {

attribute_name: item.filter_id,

operator: "in",

column_name: item.filter_id,

dimension: item.dimension || "store",

values: Array.isArray(item.values)

? item.values.map((opt) => opt.value || opt)

: item.values,

filter_type: item.filter_type,

};

});

manualbody = {

...manualbody,

filters: dependency,

};

}

try {

props.ToggleLoader(true);

if (!manualbody?.filters?.length) {

props.ToggleLoader(false);

return {

data: [],

totalCount: 0,

};

}

if (props.isEdit) {

manualbody = {

...manualbody,

selection: {

data: isCancelledOrUpdated.current

? [

{

searchColumns: {

is_mapped: {

filterType: "bool",

filter: true,

},

},

checkAll: true,

},

]

: [

{

searchColumns: {

is_mapped: {

filterType: "bool",

filter: true,

},

},

checkAll: true,

},

...params?.api?.checkConfiguration,

],

unique_columns: ["store_code"],

},

};

const urlSplitArr = location.pathname.split("/");

const grpId = urlSplitArr.pop();

const res = await props.fetchStoreGrpFilteredStores(

manualbody,

grpId,

pageIndex + 1

);

let updatedRowData = cloneDeep(res);

  

props.setStoreGroupFilteredStores({

data: res.data.data,

count: res.data.total,

});

if (isCancelledOrUpdated.current) {

params.api.setCheckConfiguration([]);

}

props.ToggleLoader(false);

isCancelledOrUpdated.current = false;

if (noneditableStores?.current?.length > 0) {

updatedRowData.data.data = updateDatatodisableDropdown(

updatedRowData.data.data

);

}

return {

data: updatedRowData.data.data,

totalCount: updatedRowData.data.total,

};

} else {

manualbody = {

...manualbody,

selection: {

data: params?.api?.checkConfiguration,

unique_columns: ["store_code"],

},

};

const res = await props.fetchStoreGrpFilteredStores(

manualbody,

"",

pageIndex + 1

);

let updatedRowData = cloneDeep(res);

  

props.setStoreGroupFilteredStores({

data: res.data.data,

count: res.data.total,

});

if (isCancelledOrUpdated.current) {

params.api.setCheckConfiguration([]);

}

props.ToggleLoader(false);

isCancelledOrUpdated.current = false;

if (noneditableStores?.current?.length > 0) {

updatedRowData.data.data = updateDatatodisableDropdown(

updatedRowData.data.data

);

}

return {

data: updatedRowData.data.data,

totalCount: updatedRowData.data.total,

};

}

} catch (error) {

props.ToggleLoader(false);

props.addSnack({

message: "Something went wrong.",

options: {

variant: "error",

},

});

//Error handling

}

};

  

const manualGrpCallBack = async (body, pageIndex, params) => {

try {

props.ToggleLoader(true);

let selectedFilters = [];

if (ref.storeFiltersRef.current) {

const storeFilters = formatFiltersDependency(

ref.storeFiltersRef.current,

null,

true

);

selectedFilters.push(...storeFilters);

}

let dependency = selectedFilters;

if (dependency.length === 0) {

props.ToggleLoader(false);

return {

data: [],

totalCount: 0,

};

}

let manualbody = {

filters: dependency,

meta: { ...body },

metrics: [],

};

if (props.isEdit) {

manualbody = {

...manualbody,

selection: {

data: params?.api?.checkConfiguration,

unique_columns: ["sg_code"],

},

};

const urlSplitArr = location.pathname.split("/");

const grpId = urlSplitArr.pop();

const res = await props.fetchStoreGroups(

manualbody,

grpId,

pageIndex + 1

);

if (isCancelledOrUpdatedGrps.current) {

params.api.setCheckConfiguration([]);

}

props.ToggleLoader(false);

isCancelledOrUpdatedGrps.current = false;

return {

data: res.data.data,

totalCount: res.data.total,

};

} else {

manualbody = {

...manualbody,

selection: {

data: params?.api?.checkConfiguration,

unique_columns: ["sg_code"],

},

};

const res = await props.fetchStoreGroups(manualbody, "", pageIndex + 1);

  

if (isCancelledOrUpdatedGrps.current) {

params.api.setCheckConfiguration([]);

}

props.ToggleLoader(false);

isCancelledOrUpdatedGrps.current = false;

return {

data: res.data.data,

totalCount: res.data.total,

};

}

} catch (error) {

//Error handling

props.ToggleLoader(false);

props.addSnack({

message: "Something went wrong.",

options: {

variant: "error",

},

});

}

};

  

const handleClose = () => {

setconfirmPopUp(false);

};

  

const onProceed = () => {

setconfirmPopUp(false);

if (props.isEdit) {

const urlSplitArr = location.pathname.split("/");

const grpId = urlSplitArr.pop();

navigate(`${storeGrouping.viewGroup}/${grpId}`);

} else {

navigate(storeGrouping.home);

}

};

  

const onClickViewClusterStatus = () => {

setopenViewClusterStatus(true);

};

  

const closeViewClusterStatus = async (callBackData = {}) => {

setopenViewClusterStatus(false);

if (!isEmpty(callBackData)) {

props.setStoreGroupCustomLoaderValue(true);

const reqInfo = await props.fetchStoreGroupCustomClusterInfo(

callBackData.id

);

  

const body = {

filters: reqInfo.data.data.metrics.filters,

sort: [],

range: [],

search: [],

definitions: [],

request_id: callBackData.id,

};

/**

* Here assign the cluster filters to respective variables to populate

*/

const filters = reqInfo.data.data.metrics.filters.map((filter) => {

return {

...filter,

filter_id: filter.attribute_name,

values: filter.values.map((val) => {

return {

label: val,

value: val,

};

}),

};

});

props.setSelectedClusterFilters(filters);

props.setClassificationValue(

reqInfo.data.data.metrics.metrics.classification

);

props.setClusterParamters(

capitalizeFirstLetterDropdown(reqInfo.data.data.metrics.metrics.value)

);

props.setClusterTimeFormat(

capitalizeFirstLetterDropdown([

reqInfo.data.data.metrics.metrics.time_format,

])

);

props.setClusterTimePeriod([

moment(reqInfo.data.data.metrics.metrics.start_date, "YYYY-MM-DD"),

moment(reqInfo.data.data.metrics.metrics.end_date, "YYYY-MM-DD"),

]);

const res = await props.fetchStoreGrpFilteredStores(body);

props.setStoreGroupFilteredStores({

data: res.data.data,

count: res.data.total,

});

props.setSelectedCluster(reqInfo.data.data);

props.setStoreGroupCustomLoaderValue(false);

}

};

  

useEffect(() => {

closeViewClusterStatus(props.selectedCluster);

}, [props.selectedCluster?.id]);

  

const onStoreLevelSelectionChanged = (event) => {

const selectedRows = event.api.getSelectedRows();

let finalSelectedRows = cloneDeep(selectedRows);

rowSelectionHandler(finalSelectedRows, event.api.getRenderedNodes());

};

  

const onStoreGroupLevelSelectionChanged = (event) => {

const selectedGrpRows = event.api.getSelectedRows();

grpSelectionHandler(selectedGrpRows, event.api.getRenderedNodes());

};

  

const refreshTables = () => {

ref.storeTableRef.current.api.deselectAll();

ref.storeTableRef.current.api.refreshServerSideStore({ purge: true });

if (isIncludeGrpsChecked) {

ref.storeGroupTableRef.current.api.deselectAll();

ref.storeGroupTableRef.current.api.refreshServerSideStore({

purge: false,

});

}

};

  

const onCancel = () => {

if (

props.isEdit &&

!props.newEditStores.length &&

!props.newEditGrps.length &&

!props.deleteEditStores.length &&

!props.deleteEditGrps.length

) {

props.addSnack({

message: "No changes are made",

options: {

variant: "warning",

},

});

return;

}

  

if (

!props.isEdit &&

checkForEmptyTableUserConfig(ref.storeTableRef) &&

checkForEmptyTableUserConfig(ref.storeGroupTableRef)

) {

props.addSnack({

message: "No changes are made",

options: {

variant: "warning",

},

});

return;

}

showConfirmBox(true);

};

  

/**

* @function

* @description Handle selected stores channel and filter validation and call bulk/store api after payload creation

* @returns {Boolean} false if validation fails

*/

const handleAddStores = async () => {

const channel = Array.from(

new Set(props.selectedStoreGroups.map((item) => item.channel))

);

if (

channel.length === 1 &&

channel[0] !=

ref?.storeFiltersRef?.current?.filter(

(filter) => filter.filter_id === "channel"

)[0].values[0]

) {

props.addSnack({

message: "Cross channel store addition is not allowed.",

options: {

variant: "warning",

},

});

return;

}

const body = {

store_groups: {

filters: props.groupFilterDependency,

meta: {

search: [],

range: [],

sort: [],

},

metrics: [],

selection: {

data: props.checkConfiguration,

unique_columns: ["sg_code"],

},

},

};

let selectedFilters = [];

if (ref.storeFiltersRef.current) {

const storeFilters = formatFiltersDependency(

ref.storeFiltersRef.current,

null,

true

);

selectedFilters.push(...storeFilters);

let selectedData = ref.storeTableRef.current?.api

?.getSelectedNodes()

.map((node) => {

return node.data;

});

let store_grade = selectedData

.filter((item) => item.grade)

.map((item) => {

return {

store_code: item.store_code,

store_grade: item.grade,

};

});

if (storeGradeFlag) {

body.store_grades = store_grade;

}

}

  

body["store_ids"] = {

filters: selectedFilters,

meta: {

search: [],

range: [],

sort: [],

},

metrics: [],

selection: {

data: [

{

searchColumns: {

is_mapped: {

filterType: "bool",

filter: true,

},

},

checkAll: true,

},

...(ref.storeTableRef?.current?.api?.checkConfiguration || []),

],

unique_columns: ["store_code"],

},

};

body["store_group_ids"] = {

filters: selectedFilters,

meta: {

search: [],

range: [],

sort: [],

},

metrics: [],

selection: {

data: ref.storeGroupTableRef?.current?.api?.checkConfiguration || [],

unique_columns: ["sg_code"],

},

};

try {

props.ToggleLoader(true);

let response = await props.addStoresToGroups(body);

props.newRowsInEdit([]);

props.deletedRowsInEdit([]);

props.newGrpsInEdit([]);

props.deletedGrpsInEdit([]);

isCancelledOrUpdated.current = true;

refreshTables();

props.ToggleLoader(false);

props.addSnack({

message: `${response?.data?.message}`,

options: {

variant: "success",

onClose: navigate(props.prevScr),

},

});

} catch (error) {

props.ToggleLoader(false);

props.addSnack({

message: "Add Store operation failed.",

options: {

variant: "error",

},

});

}

};

// this code would be removed once it's handled in generic way (value getter)

  

const processCellForClipboard = useCallback((params) => {

let l_cellValue = cloneDeep(params.value);

if (Array.isArray(l_cellValue)) {

return isNonPrimitiveArray(l_cellValue)

? l_cellValue.map((val) => val.label)?.join(" | ")

: l_cellValue;

}

return replaceSpecialCharacter(l_cellValue);

}, []);

  

return (

<>

<Prompt

isOpen={confirmBox}

title="Cancel Changes"

subHeading="Your changes will be discarded if you proceed. Are you sure you want to cancel?"

infoList={[]}

primaryButtonProps={{

children: "Yes",

onClick: () => {

isCancelledOrUpdated.current = true;

if (isIncludeGrpsChecked) isCancelledOrUpdatedGrps.current = true;

refreshTables();

showConfirmBox(false);

},

}}

tertiaryButtonProps={{

children: "No",

onClick: () => showConfirmBox(false),

}}

variant="warning"

/>

<Prompt

isOpen={confirmPopUp}

title="Leave Page"

subHeading="Changes will be lost. Are you sure want to proceed?"

infoList={[]}

primaryButtonProps={{

children: "Confirm",

onClick: () => onProceed(),

}}

tertiaryButtonProps={{

children: "Cancel",

onClick: () => handleClose(),

}}

variant="warning"

/>

{open && (

<GroupName

ref={{

storeTableRef: ref.storeTableRef.current,

storeGroupTableRef: ref.storeGroupTableRef.current,

storeFiltersRef: ref.storeFiltersRef.current,

}}

id="storeGrpingGrpNameComp"

open={open}

handleClose={() => toggleModalState(false)}

prevScr={props.prevScr}

storeGradeFlag={storeGradeFlag}

refreshTables={refreshTables}

/>

)}

{openViewClusterStatus && (

<RequestsTable

dimension="store"

selectedGroupType={props.selectedGroupType}

open={openViewClusterStatus}

handleClose={closeViewClusterStatus}

/>

)}

{columns.length !== 0 && (

<Paper

id={props.isEdit ? "storeGrpingEditCont" : "storeGrpingCrtCont"}

elevation={0}

className={globalClasses.marginBottom}

>

<div

className={`${globalClasses.flexRow} ${globalClasses.layoutAlignBetweenCenter} ${globalClasses.paddingVertical}`}

>

<Typography variant="h5" id="storeGrpingCrtEditTableTitle">

Filtered Stores

</Typography>

  

{props.selectedGroupType === "manual" ? (

<FormControlLabel

id="storeGrpingIncldGrpsFormLabel"

control={

<StyledCheckbox

id="storeGrpingIncldGrpsChckbox"

color="primary"

checked={isIncludeGrpsChecked}

onChange={(event) =>

setisIncludeGrpsChecked(event.target.checked)

}

/>

}

label="Include Store Groups"

/>

) : null}

{props.selectedGroupType !== "manual" &&

(!location?.pathname?.includes("add-stores") ||

props.enableMultiEdit) ? (

<Button

onClick={onClickViewClusterStatus}

variant="contained"

color="primary"

>

View Cluster Status

</Button>

) : null}

</div>

<AgGridTable

processCellForClipboard={processCellForClipboard}

columns={columns}

selectAllHeaderComponent={true}

sizeColumnsToFitFlag

onGridChanged

onRowSelected

manualCallBack={(body, pageIndex, params) =>

manualCallBack(body, pageIndex, params)

}

loadTableInstance={(gridInstance) => {

ref.storeTableRef.current = gridInstance;

}}

ignoreClearSelectionOnSearchandSort={true}

customCellRenderer={(cellProps, item) => {

if (cellProps.data.disableStoreGrade) {

return cellProps.value

? replaceSpecialCharacter(cellProps.value)

: cellProps.value;

} else {

return (

<CellRenderers

cellData={cellProps}

column={item}

></CellRenderers>

);

}

}}

rowModelType="serverSide"

serverSideStoreType="partial"

cacheBlockSize={10}

uniqueRowId={"store_code"}

onSelectionChanged={onStoreLevelSelectionChanged}

/>

</Paper>

)}

{isIncludeGrpsChecked && grpColumns.length > 0 && (

<Paper

id={

props.isEdit ? "storeGrpingEditGrpsCont" : "storeGrpingCrtGrpsCont"

}

className={globalClasses.marginTop}

elevation={0}

>

<div className={`${globalClasses.paddingVertical}`}>

<Typography variant="h5" id="storeGrpingCrtEditTableTitle">

Filtered Groups

</Typography>

</div>

<AgGridTable

columns={grpColumns}

selectAllHeaderComponent={true}

sizeColumnsToFitFlag

onGridChanged

onRowSelected

manualCallBack={(body, pageIndex, params) =>

manualGrpCallBack(body, pageIndex, params)

}

loadTableInstance={(gridInstance) => {

ref.storeGroupTableRef.current = gridInstance;

}}

ignoreClearSelectionOnSearchandSort={true}

rowModelType="serverSide"

serverSideStoreType="partial"

cacheBlockSize={10}

uniqueRowId={"sg_code"}

onSelectionChanged={onStoreGroupLevelSelectionChanged}

/>

</Paper>

)}

<div

className={`${globalClasses.flexRow} ${globalClasses.gap} ${globalClasses.marginTop}`}

>

<Button

variant="outlined"

onClick={() => {

location?.pathname?.includes("add-stores")

? navigate(props.prevScr, {

state: {

from: location.pathname,

},

})

: goBack();

}}

id={props.isEdit ? "storeGrpingEditBackBtn" : "storeGrpingCrtBackBtn"}

>

Go Back

</Button>

<Button

variant="contained"

color="primary"

onClick={() =>

location?.pathname?.includes("add-stores")

? handleAddStores()

: toggleModalState(true)

}

id={props.isEdit ? "storeGrpingUpdBtn" : "storeGrpingSaveBtn"}

disabled={

location?.pathname?.includes("add-stores")

? !props.isEdit && (

(ref?.storeTableRef?.current?.api?.getSelectedRows()?.length === 0) &&

(!isIncludeGrpsChecked || ref?.storeGroupTableRef?.current?.api?.getSelectedRows()?.length === 0)

)

: !props.isEdit && (

ref?.storeTableRef?.current?.api?.getSelectedRows()?.length === 0 &&

ref?.storeGroupTableRef?.current?.api?.getSelectedRows()?.length === 0

)

}

>

{location?.pathname?.includes("add-stores")

? "Add Stores"

: props.isEdit

? "Update"

: "Save"}

</Button>

  

<Button

variant="outlined"

onClick={() => {

onCancel();

}}

id={props.isEdit ? "storeGrpingEditCnclBtn" : "storeGrpingCrtCnclBtn"}

>

{" "}

Cancel

</Button>

</div>

</>

);

});

  

const mapStateToProps = (state) => {

return {

selectedStores: state.storeGroupReducer.selectedstores,

columns: state.storeGroupReducer.manualFilteredStoresCols,

selectedFilters: state.filterReducer.selectedFilters["store_hierarchy"],

manualSelectedStoreFilters:

state.filterReducer.selectedFilters["store_filters_create_group"],

manualSelectedProductFilters:

state.filterReducer.selectedFilters["product_filters_create_group"],

filteredStores: state.storeGroupReducer.manualFilteredStores,

filteredStoresCount: state.storeGroupReducer.manualFilteredStoresCount,

selectedManualFilterType: state.storeGroupReducer.selectedManualFilterType,

groupsCols: [...state.storeGroupReducer.groupsTableCols],

selectedGrps: state.storeGroupReducer.manualselectedGroups,

existingStores: state.storeGroupReducer.exisitingStoresInEdit,

newEditStores: state.storeGroupReducer.newStoresInEdit,

deleteEditStores: state.storeGroupReducer.deletedStoresInEdit,

selectedGroupType: state.storeGroupReducer.selectedGroupType,

newEditGrps: state.storeGroupReducer.newGrpsInEdit,

deleteEditGrps: state.storeGroupReducer.deletedGrpsInEdit,

selectedCluster: state.storeGroupReducer.selectedCluster,

selectedClusterFilters: state.storeGroupReducer.selectedClusterFilters,

isSelectAll: state.storeGroupReducer.isSelectAll,

groupFilterDependency: state.storeGroupReducer.groupFilterDependency,

checkConfiguration: state.storeGroupReducer.checkConfiguration,

enableMultiEdit:

state.tenantConfigReducer.coreScreenNames.attribute_value?.storeGrouping

?.enableMultiEdit,

allowMultiChannel: state.storeGroupReducer.allowMultiChannelFlag,

};

};

  

const mapActionsToProps = {

fetchStoreGrpFilteredStores,

setStoreGroupFilteredStores,

setSelectedStores,

ToggleLoader,

fetchStoreGroups,

setGroupsCols,

addSelectedGroups,

addToExistingStores,

newRowsInEdit,

deletedRowsInEdit,

updateGrp,

addSnack,

setSelectedFilters,

deletedGrpsInEdit,

newGrpsInEdit,

setSelectedStoresSelectAllState,

setStoreGroupCustomLoaderValue,

fetchStoreGroupCustomClusterInfo,

setClassificationValue,

setClusterParamters,

setClusterTimeFormat,

setClusterTimePeriod,

setSelectedCluster,

setSelectedClusterFilters,

addStoresToGroups,

getColumnsAg,

getTenantConfigApplicationLevel,

};

  

export default connect(mapStateToProps, mapActionsToProps, null, {

forwardRef: true,

})(FilteredStores);
```

###### UAT Code : 
```js 
import { FormControlLabel, Paper, Typography } from "@mui/material";

import Button from "@mui/material/Button";

import globalStyles from "core/Styles/globalStyles";

import AgGridTable from "core/Utils/agGrid";

import {

checkForEmptyTableUserConfig,

replaceSpecialCharacter,

} from "core/Utils/functions/utils";

import { StyledCheckbox } from "core/Utils/selection/selection";

import { storeGrouping } from "config/routes";

import { Prompt } from "impact-ui";

import { cloneDeep, isEmpty } from "lodash";

import moment from "moment";

import RequestsTable from "core/pages/product-grouping/components/product-group-components/clusterRequestsTable";

import { forwardRef, useCallback, useEffect, useRef, useState } from "react";

import { connect } from "react-redux";

import { useLocation, useNavigate } from "react-router-dom-v5-compat";

import { getTenantConfigApplicationLevel } from "core/actions/tenantConfigActions";

import { setSelectedFilters } from "../../../actions/filterAction";

import { addSnack } from "../../../actions/snackbarActions";

import { getColumnsAg } from "../../../actions/tableColumnActions";

import CellRenderers from "core/Utils/agGrid/cellRenderer";

import agGridColumnFormatter from "core/Utils/agGrid/column-formatter";

import { fetchGradeList } from "core/pages/store-grading/grading-services";

import {

ToggleLoader,

addSelectedGroups,

addStoresToGroups,

addToExistingStores,

deletedGrpsInEdit,

deletedRowsInEdit,

fetchStoreGroupCustomClusterInfo,

fetchStoreGroups,

fetchStoreGrpFilteredStores,

newGrpsInEdit,

newRowsInEdit,

setClassificationValue,

setClusterParamters,

setClusterTimeFormat,

setClusterTimePeriod,

setGroupsCols,

setSelectedCluster,

setSelectedClusterFilters,

setSelectedStores,

setSelectedStoresSelectAllState,

setStoreGroupCustomLoaderValue,

setStoreGroupFilteredStores,

updateGrp,

} from "../services-store-grouping/custom-store-group-service";

import {

capitalizeFirstLetterDropdown,

formatFiltersDependency,

renderGroupTypeCell,

} from "./common-functions";

import "./groupTable.scss";

import GroupName from "./storeGroupName";

import { isNonPrimitiveArray } from "modules/inventorysmart/pages-inventorysmart/Create-Allocation/helperFunctions";

  

const FilteredStores = forwardRef((props, ref) => {

const globalClasses = globalStyles();

const [open, setopen] = useState(false);

const navigate = useNavigate();

let location = useLocation();

const [isIncludeGrpsChecked, setisIncludeGrpsChecked] = useState(false);

const [grpColumns, setgroupColumns] = useState([]);

const [columns, setColumns] = useState([]);

const [confirmPopUp, setconfirmPopUp] = useState(false);

const [openViewClusterStatus, setopenViewClusterStatus] = useState(false);

const [confirmBox, showConfirmBox] = useState(false);

const isCancelledOrUpdated = useRef(false);

const isCancelledOrUpdatedGrps = useRef(false);

const noneditableStores = useRef({});

const [storeGradeFlag, setStoreGradeFlag] = useState(false);

const goBack = () => {

if (props.isEdit) {

const urlSplitArr = location.pathname.split("/");

const grpId = urlSplitArr.pop();

props.prevScr

? navigate(`${props.prevScr}/view/${grpId}`, {

state: {

prevScr: props.prevScr,

from: location.pathname,

},

})

: navigate(`${storeGrouping.viewGroup}/${grpId}`, {

state: {

from: location.pathname,

},

});

} else {

props.prevScr

? navigate(props.prevScr, {

state: {

from: location.pathname,

},

})

: navigate(storeGrouping.home, {

state: {

from: location.pathname,

},

});

}

};

  

useEffect(() => {

const fetchColumns = async () => {

if (isIncludeGrpsChecked) {

props.ToggleLoader(true);

let cols = [];

if (props.groupsCols.length === 0) {

cols = await props.getColumnsAg("table_name=store_group");

} else {

cols = cloneDeep(props.groupsCols);

}

cols = cols.map((col) => {

if (col.accessor === "special_classification") {

col = renderGroupTypeCell(col);

}

return col;

});

  

props.setGroupsCols(cols);

setgroupColumns(cols);

ref?.storeGroupTableRef?.current?.api?.refreshServerSideStore({

purge: true,

});

}

};

fetchColumns();

}, [isIncludeGrpsChecked]);

  

useEffect(() => {

if (!isIncludeGrpsChecked) {

props.addSelectedGroups([]);

}

}, [isIncludeGrpsChecked, props.filteredStores]);

  

useEffect(() => {

const fetchCols = async () => {

let cols = cloneDeep(props.columns);

let gradeFlag = false;

cols.forEach((item) => {

if (item.column_name === "grade" && item.is_editable) {

gradeFlag = true;

}

});

if (gradeFlag) {

const { data } = await fetchGradeList();

let { data: config } = await props.getTenantConfigApplicationLevel(1, {

attribute_name: "filter_attributes_display_config",

});

let nonEditStores =

config?.data[0]?.attribute_value?.store?.store_code

?.display_order_top;

noneditableStores.current = nonEditStores;

cols = cols.map((item) => {

if (item.column_name === "grade") {

item.options = data.data

.filter((item) => item.name !== "ECOM")

.map((item) => {

return {

label: item.name,

id: item.name,

value: item.name,

};

});

item.initialData = item.options;

item.cellRenderer = (cellProps, extraProps) => {

if (cellProps.value === "ECOM") {

return <>{cellProps.value}</>; // Render "ECOM" as non-editable text

} else {

return (

<CellRenderers

cellData={cellProps}

column={item}

extraProps={extraProps}

></CellRenderers>

);

}

};

}

return item;

});

const formattedResponse = agGridColumnFormatter(cols);

setColumns(formattedResponse);

setStoreGradeFlag(true);

} else {

setColumns(cols);

}

};

fetchCols();

}, [props.columns]);

  

useEffect(() => {

let obj = {};

obj["store_hierarchy"] = [];

props.setSelectedFilters(obj);

}, []);

  

const rowSelectionHandler = (rows, data) => {

const unselectdRows = data.filter((storeNode) => {

return !rows.some((select) => {

return select.store_code === storeNode.data.store_code;

});

});

if (props.isEdit) {

//selected rows

//Already mapped - and in delete window - Remove from Delete

//Not mapped -

//If it is not mapped => Add it to new window

//If it is mapped and excluded => Add it to delete window

let should_include_in_delete = [];

let should_exclude_in_delete = [];

let should_include_in_new = [];

let should_exclude_in_new = [];

rows.forEach((row, _idx) => {

if (row.is_mapped) {

if (

props.deleteEditStores.some((del) => {

return del.store_code === row.store_code;

})

) {

should_exclude_in_delete.push(row);

}

} else {

if (

!props.newEditStores.some((newone) => {

return newone.store_code === row.store_code;

})

) {

should_include_in_new.push(row);

}

}

});

unselectdRows.forEach((row, _idx) => {

If (row. Data. Is_mapped) {

If (

!props.DeleteEditStores.Some ((del) => {

Return del. Store_code === row. Data. Store_code;

})

) {

Should_include_in_delete.Push (row. Data);

}

} else {

If (

Props.NewEditStores.Some ((newone) => {

Return newone. Store_code === row. Data. Store_code;

})

) {

Should_exclude_in_new.Push (row. Data);

}

}

});

  

Let updatedDelete = props.DeleteEditStores.Filter ((del) => {

Return !Should_exclude_in_delete.Some ((exclude) => {

Return exclude. Store_code === del. Store_code;

});

});

UpdatedDelete = [... UpdatedDelete, ... Should_include_in_delete];

Props.NewRowsInEdit (should_include_in_new);

Props.DeletedRowsInEdit (updatedDelete);

} else {

Props.SetSelectedStores (rows);

}

};

  

Const grpSelectionHandler = (grps, data) => {

If (props. IsEdit) {

//selected rows

//Already mapped - and in delete window - Remove from Delete

//Not mapped -

//If it is not mapped => Add it to new window

//If it is mapped and excluded => Add it to delete window

Let should_include_in_delete = [];

Let should_exclude_in_delete = [];

Let should_include_in_new = [];

Let should_exclude_in_new = [];

Const unselectdRows = data.Filter ((prod) => {

Return !Grps.Some ((select) => {

Return select. Sg_code === prod. Data. Sg_code;

});

});

Grps.ForEach ((grp, _idx) => {

If (grp. Is_mapped) {

If (

Props.DeleteEditGrps.Some ((del) => {

Return del. Sg_code === grp. Sg_code;

})

) {

Should_exclude_in_delete.Push (grp);

}

} else {

If (

!props.NewEditGrps.Some ((newone) => {

Return newone. Sg_code === grp. Sg_code;

})

) {

Should_include_in_new.Push (grp);

}

}

});

UnselectdRows.ForEach ((row, _idx) => {

If (row. Data. Is_mapped) {

If (

!props.DeleteEditGrps.Some ((del) => {

Return del. Sg_code === row. Data. Sg_code;

})

) {

Should_include_in_delete.Push (row. Data);

}

} else {

If (

Props.NewEditGrps.Some ((newone) => {

Return newone. Sg_code === row. Data. Sg_code;

})

) {

Should_exclude_in_new.Push (row. Data);

}

}

});

  

Let updatedDelete = props.DeleteEditGrps.Filter ((del) => {

Return !Should_exclude_in_delete.Some ((exclude) => {

Return exclude. Sg_code === del. Sg_code;

});

});

UpdatedDelete = [... UpdatedDelete, ... Should_include_in_delete];

Props.NewGrpsInEdit (should_include_in_new);

Props.DeletedGrpsInEdit (updatedDelete);

} else {

Props.AddSelectedGroups (grps);

}

};

  

Const toggleModalState = (status) => {

If (props. IsEdit) {

OnUpdate ();

Return;

}

Setopen (status);

};

  

Const onUpdate = async () => {

Const body = {

Name: props. GrpObj. Name,

Special_classification: props. SelectedGroupType,

Channel:

Props?. GrpObj?. Channel || (props?. AllowMultiChannel ? "MC" : "NC"),

};

Let selectedFilters = [];

If (ref. StoreFiltersRef. Current) {

Const storeFilters = formatFiltersDependency (

Ref. StoreFiltersRef. Current,

Null,

True

);

SelectedFilters.Push (... StoreFilters);

Let selectedData = ref. StoreTableRef. Current?. Api

?.GetSelectedNodes ()

.map ((node) => {

Return node. Data;

});

Let store_grade = selectedData

.filter ((item) => item. Grade)

.map ((item) => {

Return {

Store_code: item. Store_code,

Store_grade: item. Grade,

};

});

If (storeGradeFlag) {

Body. Store_grades = store_grade;

}

}

  

Body["store_ids"] = {

Filters: selectedFilters,

Meta: {

Search: [],

Range: [],

Sort: [],

},

Metrics: [],

Selection: {

Data: [

{

SearchColumns: {

Is_mapped: {

FilterType: "bool",

Filter: true,

},

},

CheckAll: true,

},

... (ref. StoreTableRef?. Current?. Api?. CheckConfiguration || []),

],

Unique_columns: ["store_code"],

},

};

Body["store_group_ids"] = {

Filters: selectedFilters,

Meta: {

Search: [],

Range: [],

Sort: [],

},

Metrics: [],

Selection: {

Data: ref. StoreGroupTableRef?. Current?. Api?. CheckConfiguration || [],

Unique_columns: ["sg_code"],

},

};

Try {

Props.ToggleLoader (true);

Const urlSplitArr = location.Pathname.Split ("/");

Const grpId = urlSplitArr.Pop ();

Await props.UpdateGrp (grpId, body);

Props.NewRowsInEdit ([]);

Props.DeletedRowsInEdit ([]);

Props.NewGrpsInEdit ([]);

Props.DeletedGrpsInEdit ([]);

Props.AddSnack ({

Message: "Updated successfully",

Options: {

Variant: "success",

},

});

IsCancelledOrUpdated. Current = true;

RefreshTables ();

Props.ToggleLoader (false);

} catch (error) {

Props.ToggleLoader (false);

Props.AddSnack ({

Message: "Update Failed",

Options: {

Variant: "error",

},

});

}

};

  

Const updateDatatodisableDropdown = (arr) => {

Return arr.Map ((item) => {

If (noneditableStores.Current.IndexOf (item. Store_code) > -1) {

Item. DisableStoreGrade = true;

} else {

Item. DisableStoreGrade = false;

}

Return item;

});

};

Const manualCallBack = async (body, pageIndex, params) => {

Let manualbody = {};

Manualbody = {

Filters: [],

Meta: { ... Body },

Metrics: [],

};

If (props. SelectedGroupType === "custom") {

Let dependency = props. SelectedClusterFilters

? Props.SelectedClusterFilters.Map ((item) => {

Return {

Attribute_name: item. Filter_id,

Operator: "in",

Column_name: item. Filter_id,

Dimension: item. Dimension || "store",

Values: Array.IsArray (item. Values)

? Item.Values.Map ((opt) => opt. Value)

: item. Values,

Filter_type: item. Filter_type,

};

})

: [];

Manualbody = {

... Manualbody,

Filters: dependency,

Request_id: props. SelectedCluster. Id,

};

} else {

Let selectedFilters = [];

If (ref. StoreFiltersRef. Current) {

SelectedFilters.Push (... Ref. StoreFiltersRef. Current);

}

Let dependency = selectedFilters.Map ((item) => {

Return {

Attribute_name: item. Filter_id,

Operator: "in",

Column_name: item. Filter_id,

Dimension: item. Dimension || "store",

Values: Array.IsArray (item. Values)

? Item.Values.Map ((opt) => opt. Value || opt)

: item. Values,

Filter_type: item. Filter_type,

};

});

Manualbody = {

... Manualbody,

Filters: dependency,

};

}

Try {

Props.ToggleLoader (true);

If (! Manualbody?. Filters?. Length) {

Props.ToggleLoader (false);

Return {

Data: [],

TotalCount: 0,

};

}

If (props. IsEdit) {

Manualbody = {

... Manualbody,

Selection: {

Data: isCancelledOrUpdated. Current

? [

{

SearchColumns: {

Is_mapped: {

FilterType: "bool",

Filter: true,

},

},

CheckAll: true,

},

]

: [

{

SearchColumns: {

Is_mapped: {

FilterType: "bool",

Filter: true,

},

},

CheckAll: true,

},

... Params?. Api?. CheckConfiguration,

],

Unique_columns: ["store_code"],

},

};

Const urlSplitArr = location.Pathname.Split ("/");

Const grpId = urlSplitArr.Pop ();

Const res = await props.FetchStoreGrpFilteredStores (

Manualbody,

GrpId,

PageIndex + 1

);

Let updatedRowData = cloneDeep (res);

  

Props.SetStoreGroupFilteredStores ({

Data: res. Data. Data,

Count: res. Data. Total,

});

If (isCancelledOrUpdated. Current) {

Params.Api.SetCheckConfiguration ([]);

}

Props.ToggleLoader (false);

IsCancelledOrUpdated. Current = false;

If (noneditableStores?. Current?. Length > 0) {

UpdatedRowData. Data. Data = updateDatatodisableDropdown (

UpdatedRowData. Data. Data

);

}

Return {

Data: updatedRowData. Data. Data,

TotalCount: updatedRowData. Data. Total,

};

} else {

Manualbody = {

... Manualbody,

Selection: {

Data: params?. Api?. CheckConfiguration,

Unique_columns: ["store_code"],

},

};

Const res = await props.FetchStoreGrpFilteredStores (

Manualbody,

"",

PageIndex + 1

);

Let updatedRowData = cloneDeep (res);

  

Props.SetStoreGroupFilteredStores ({

Data: res. Data. Data,

Count: res. Data. Total,

});

If (isCancelledOrUpdated. Current) {

Params.Api.SetCheckConfiguration ([]);

}

Props.ToggleLoader (false);

IsCancelledOrUpdated. Current = false;

If (noneditableStores?. Current?. Length > 0) {

UpdatedRowData. Data. Data = updateDatatodisableDropdown (

UpdatedRowData. Data. Data

);

}

Return {

Data: updatedRowData. Data. Data,

TotalCount: updatedRowData. Data. Total,

};

}

} catch (error) {

Props.ToggleLoader (false);

Props.AddSnack ({

Message: "Something went wrong.",

Options: {

Variant: "error",

},

});

//Error handling

}

};

  

Const manualGrpCallBack = async (body, pageIndex, params) => {

Try {

Props.ToggleLoader (true);

Let selectedFilters = [];

If (ref. StoreFiltersRef. Current) {

Const storeFilters = formatFiltersDependency (

Ref. StoreFiltersRef. Current,

Null,

True

);

SelectedFilters.Push (... StoreFilters);

}

Let dependency = selectedFilters;

If (dependency. Length === 0) {

Props.ToggleLoader (false);

Return {

Data: [],

TotalCount: 0,

};

}

Let manualbody = {

Filters: dependency,

Meta: { ... Body },

Metrics: [],

};

If (props. IsEdit) {

Manualbody = {

... Manualbody,

Selection: {

Data: params?. Api?. CheckConfiguration,

Unique_columns: ["sg_code"],

},

};

Const urlSplitArr = location.Pathname.Split ("/");

Const grpId = urlSplitArr.Pop ();

Const res = await props.FetchStoreGroups (

Manualbody,

GrpId,

PageIndex + 1

);

If (isCancelledOrUpdatedGrps. Current) {

Params.Api.SetCheckConfiguration ([]);

}

Props.ToggleLoader (false);

IsCancelledOrUpdatedGrps. Current = false;

Return {

Data: res. Data. Data,

TotalCount: res. Data. Total,

};

} else {

Manualbody = {

... Manualbody,

Selection: {

Data: params?. Api?. CheckConfiguration,

Unique_columns: ["sg_code"],

},

};

Const res = await props.FetchStoreGroups (manualbody, "", pageIndex + 1);

  

If (isCancelledOrUpdatedGrps. Current) {

Params.Api.SetCheckConfiguration ([]);

}

Props.ToggleLoader (false);

IsCancelledOrUpdatedGrps. Current = false;

Return {

Data: res. Data. Data,

TotalCount: res. Data. Total,

};

}

} catch (error) {

//Error handling

Props.ToggleLoader (false);

Props.AddSnack ({

Message: "Something went wrong.",

Options: {

Variant: "error",

},

});

}

};

  

Const handleClose = () => {

SetconfirmPopUp (false);

};

  

Const onProceed = () => {

SetconfirmPopUp (false);

If (props. IsEdit) {

Const urlSplitArr = location.Pathname.Split ("/");

Const grpId = urlSplitArr.Pop ();

Navigate (`${storeGrouping. ViewGroup}/${grpId}`);

} else {

Navigate (storeGrouping. Home);

}

};

  

Const onClickViewClusterStatus = () => {

SetopenViewClusterStatus (true);

};

  

Const closeViewClusterStatus = async (callBackData = {}) => {

SetopenViewClusterStatus (false);

If (! IsEmpty (callBackData)) {

Props.SetStoreGroupCustomLoaderValue (true);

Const reqInfo = await props.FetchStoreGroupCustomClusterInfo (

CallBackData. Id

);

  

Const body = {

Filters: reqInfo. Data. Data. Metrics. Filters,

Sort: [],

Range: [],

Search: [],

Definitions: [],

Request_id: callBackData. Id,

};

/**

* Here assign the cluster filters to respective variables to populate

*/

Const filters = reqInfo.Data.Data.Metrics.Filters.Map ((filter) => {

Return {

... Filter,

Filter_id: filter. Attribute_name,

Values: filter.Values.Map ((val) => {

Return {

Label: val,

Value: val,

};

}),

};

});

Props.SetSelectedClusterFilters (filters);

Props.SetClassificationValue (

ReqInfo. Data. Data. Metrics. Metrics. Classification

);

Props.SetClusterParamters (

CapitalizeFirstLetterDropdown (reqInfo. Data. Data. Metrics. Metrics. Value)

);

Props.SetClusterTimeFormat (

CapitalizeFirstLetterDropdown ([

ReqInfo. Data. Data. Metrics. Metrics. Time_format,

])

);

Props.SetClusterTimePeriod ([

Moment (reqInfo. Data. Data. Metrics. Metrics. Start_date, "YYYY-MM-DD"),

Moment (reqInfo. Data. Data. Metrics. Metrics. End_date, "YYYY-MM-DD"),

]);

Const res = await props.FetchStoreGrpFilteredStores (body);

Props.SetStoreGroupFilteredStores ({

Data: res. Data. Data,

Count: res. Data. Total,

});

Props.SetSelectedCluster (reqInfo. Data. Data);

Props.SetStoreGroupCustomLoaderValue (false);

}

};

  

UseEffect (() => {

CloseViewClusterStatus (props. SelectedCluster);

}, [props. SelectedCluster?. Id]);

  

Const onStoreLevelSelectionChanged = (event) => {

Const selectedRows = event.Api.GetSelectedRows ();

Let finalSelectedRows = cloneDeep (selectedRows);

RowSelectionHandler (finalSelectedRows, event.Api.GetRenderedNodes ());

};

  

Const onStoreGroupLevelSelectionChanged = (event) => {

Const selectedGrpRows = event.Api.GetSelectedRows ();

GrpSelectionHandler (selectedGrpRows, event.Api.GetRenderedNodes ());

};

  

Const refreshTables = () => {

Ref.StoreTableRef.Current.Api.DeselectAll ();

Ref.StoreTableRef.Current.Api.RefreshServerSideStore ({ purge: true });

If (isIncludeGrpsChecked) {

Ref.StoreGroupTableRef.Current.Api.DeselectAll ();

Ref.StoreGroupTableRef.Current.Api.RefreshServerSideStore ({

Purge: false,

});

}

};

  

Const onCancel = () => {

If (

Props. IsEdit &&

!props. NewEditStores. Length &&

!props. NewEditGrps. Length &&

!props. DeleteEditStores. Length &&

!props. DeleteEditGrps. Length

) {

Props.AddSnack ({

Message: "No changes are made",

Options: {

Variant: "warning",

},

});

Return;

}

  

If (

!props. IsEdit &&

CheckForEmptyTableUserConfig (ref. StoreTableRef) &&

CheckForEmptyTableUserConfig (ref. StoreGroupTableRef)

) {

Props.AddSnack ({

Message: "No changes are made",

Options: {

Variant: "warning",

},

});

Return;

}

ShowConfirmBox (true);

};

  

/**

* @function

* @description Handle selected stores channel and filter validation and call bulk/store api after payload creation

* @returns {Boolean} false if validation fails

*/

Const handleAddStores = async () => {

Const channel = Array.From (

New Set (props.SelectedStoreGroups.Map ((item) => item. Channel))

);

If (

Channel. Length === 1 &&

Channel[0] !=

Ref?.StoreFiltersRef?.Current?.Filter (

(filter) => filter. Filter_id === "channel"

)[0]. Values[0]

) {

Props.AddSnack ({

Message: "Cross channel store addition is not allowed.",

Options: {

Variant: "warning",

},

});

Return;

}

Const body = {

Store_groups: {

Filters: props. GroupFilterDependency,

Meta: {

Search: [],

Range: [],

Sort: [],

},

Metrics: [],

Selection: {

Data: props. CheckConfiguration,

Unique_columns: ["sg_code"],

},

},

};

Let selectedFilters = [];

If (ref. StoreFiltersRef. Current) {

Const storeFilters = formatFiltersDependency (

Ref. StoreFiltersRef. Current,

Null,

True

);

SelectedFilters.Push (... StoreFilters);

Let selectedData = ref. StoreTableRef. Current?. Api

?.GetSelectedNodes ()

.map ((node) => {

Return node. Data;

});

Let store_grade = selectedData

.filter ((item) => item. Grade)

.map ((item) => {

Return {

Store_code: item. Store_code,

Store_grade: item. Grade,

};

});

If (storeGradeFlag) {

Body. Store_grades = store_grade;

}

}

  

Body["store_ids"] = {

Filters: selectedFilters,

Meta: {

Search: [],

Range: [],

Sort: [],

},

Metrics: [],

Selection: {

Data: [

{

SearchColumns: {

Is_mapped: {

FilterType: "bool",

Filter: true,

},

},

CheckAll: true,

},

... (ref. StoreTableRef?. Current?. Api?. CheckConfiguration || []),

],

Unique_columns: ["store_code"],

},

};

Body["store_group_ids"] = {

Filters: selectedFilters,

Meta: {

Search: [],

Range: [],

Sort: [],

},

Metrics: [],

Selection: {

Data: ref. StoreGroupTableRef?. Current?. Api?. CheckConfiguration || [],

Unique_columns: ["sg_code"],

},

};

Try {

Props.ToggleLoader (true);

Let response = await props.AddStoresToGroups (body);

Props.NewRowsInEdit ([]);

Props.DeletedRowsInEdit ([]);

Props.NewGrpsInEdit ([]);

Props.DeletedGrpsInEdit ([]);

IsCancelledOrUpdated. Current = true;

RefreshTables ();

Props.ToggleLoader (false);

Props.AddSnack ({

Message: `${response?. Data?. Message}`,

Options: {

Variant: "success",

OnClose: navigate (props. PrevScr),

},

});

} catch (error) {

Props.ToggleLoader (false);

Props.AddSnack ({

Message: "Add Store operation failed.",

Options: {

Variant: "error",

},

});

}

};

// this code would be removed once it's handled in generic way (value getter)

  

Const processCellForClipboard = useCallback ((params) => {

Let l_cellValue = cloneDeep (params. Value);

If (Array.IsArray (l_cellValue)) {

Return isNonPrimitiveArray (l_cellValue)

? L_cellValue.Map ((val) => val. Label)?.Join (" | ")

: l_cellValue;

}

Return replaceSpecialCharacter (l_cellValue);

}, []);

  

Return (

<>

<Prompt

IsOpen={confirmBox}

Title="Cancel Changes"

SubHeading="Your changes will be discarded if you proceed. Are you sure you want to cancel?"

InfoList={[]}

PrimaryButtonProps={{

Children: "Yes",

OnClick: () => {

IsCancelledOrUpdated. Current = true;

If (isIncludeGrpsChecked) isCancelledOrUpdatedGrps. Current = true;

RefreshTables ();

ShowConfirmBox (false);

},

}}

TertiaryButtonProps={{

Children: "No",

OnClick: () => showConfirmBox (false),

}}

Variant="warning"

/>

<Prompt

IsOpen={confirmPopUp}

Title="Leave Page"

SubHeading="Changes will be lost. Are you sure want to proceed?"

InfoList={[]}

PrimaryButtonProps={{

Children: "Confirm",

OnClick: () => onProceed (),

}}

TertiaryButtonProps={{

Children: "Cancel",

OnClick: () => handleClose (),

}}

Variant="warning"

/>

{open && (

<GroupName

Ref={{

StoreTableRef: ref. StoreTableRef. Current,

StoreGroupTableRef: ref. StoreGroupTableRef. Current,

StoreFiltersRef: ref. StoreFiltersRef. Current,

}}

Id="storeGrpingGrpNameComp"

Open={open}

HandleClose={() => toggleModalState (false)}

PrevScr={props. PrevScr}

StoreGradeFlag={storeGradeFlag}

RefreshTables={refreshTables}

/>

)}

{openViewClusterStatus && (

<RequestsTable

Dimension="store"

SelectedGroupType={props. SelectedGroupType}

Open={openViewClusterStatus}

HandleClose={closeViewClusterStatus}

/>

)}

{columns. Length !== 0 && (

<Paper

Id={props. IsEdit ? "storeGrpingEditCont" : "storeGrpingCrtCont"}

Elevation={0}

ClassName={globalClasses. MarginBottom}

>

<div

ClassName={`${globalClasses. FlexRow} ${globalClasses. LayoutAlignBetweenCenter} ${globalClasses. PaddingVertical}`}

>

<Typography variant="h5" id="storeGrpingCrtEditTableTitle">

Filtered Stores

</Typography>

  

{props. SelectedGroupType === "manual" ? (

<FormControlLabel

Id="storeGrpingIncldGrpsFormLabel"

Control={

<StyledCheckbox

Id="storeGrpingIncldGrpsChckbox"

Color="primary"

Checked={isIncludeGrpsChecked}

OnChange={(event) =>

SetisIncludeGrpsChecked (event. Target. Checked)

}

/>

}

Label="Include Store Groups"

/>

) : null}

{props. SelectedGroupType !== "manual" &&

(! Props.Location?.Pathname?.Includes ("add-stores") ||

Props. EnableMultiEdit) ? (

<Button

OnClick={onClickViewClusterStatus}

Variant="contained"

Color="primary"

>

View Cluster Status

</Button>

) : null}

</div>

<AgGridTable

ProcessCellForClipboard={processCellForClipboard}

Columns={columns}

SelectAllHeaderComponent={true}

SizeColumnsToFitFlag

OnGridChanged

OnRowSelected

ManualCallBack={(body, pageIndex, params) =>

ManualCallBack (body, pageIndex, params)

}

LoadTableInstance={(gridInstance) => {

Ref. StoreTableRef. Current = gridInstance;

}}

IgnoreClearSelectionOnSearchandSort={true}

CustomCellRenderer={(cellProps, item) => {

If (cellProps. Data. DisableStoreGrade) {

Return cellProps. Value

? ReplaceSpecialCharacter (cellProps. Value)

: cellProps. Value;

} else {

Return (

<CellRenderers

CellData={cellProps}

Column={item}

></CellRenderers>

);

}

}}

RowModelType="serverSide"

ServerSideStoreType="partial"

CacheBlockSize={10}

UniqueRowId={"store_code"}

OnSelectionChanged={onStoreLevelSelectionChanged}

/>

</Paper>

)}

{isIncludeGrpsChecked && grpColumns. Length > 0 && (

<Paper

Id={

Props. IsEdit ? "storeGrpingEditGrpsCont" : "storeGrpingCrtGrpsCont"

}

ClassName={globalClasses. MarginTop}

Elevation={0}

>

<div className={`${globalClasses.paddingVertical}`}>

<Typography variant="h5" id="storeGrpingCrtEditTableTitle">

Filtered Groups

</Typography>

</div>

<AgGridTable

Columns={grpColumns}

SelectAllHeaderComponent={true}

SizeColumnsToFitFlag

OnGridChanged

OnRowSelected

ManualCallBack={(body, pageIndex, params) =>

ManualGrpCallBack (body, pageIndex, params)

}

LoadTableInstance={(gridInstance) => {

Ref. StoreGroupTableRef. Current = gridInstance;

}}

IgnoreClearSelectionOnSearchandSort={true}

RowModelType="serverSide"

ServerSideStoreType="partial"

CacheBlockSize={10}

UniqueRowId={"sg_code"}

OnSelectionChanged={onStoreGroupLevelSelectionChanged}

/>

</Paper>

)}

<div

ClassName={`${globalClasses. FlexRow} ${globalClasses. Gap} ${globalClasses. MarginTop}`}

>

<Button

Variant="outlined"

OnClick={() => {

Location?.Pathname?.Includes ("add-stores")

? Navigate (props. PrevScr, {

State: {

From: location. Pathname,

},

})

: goBack ();

}}

Id={props. IsEdit ? "storeGrpingEditBackBtn" : "storeGrpingCrtBackBtn"}

>

Go Back

</Button>

<Button

Variant="contained"

Color="primary"

OnClick={() =>

Location?.Pathname?.Includes ("add-stores")

? HandleAddStores ()

: toggleModalState (true)

}

Id={props. IsEdit ? "storeGrpingUpdBtn" : "storeGrpingSaveBtn"}

Disabled={

!props. IsEdit &&

Ref?.StoreTableRef?.Current?.Api?.GetSelectedRows ()?. Length === 0 &&

Ref?.StoreGroupTableRef?.Current?.Api?.GetSelectedRows ()?. Length ===

0

}

>

{location?.Pathname?.Includes ("add-stores")

? "Add Stores"

: props. IsEdit

? "Update"

: "Save"}

</Button>

  

<Button

Variant="outlined"

OnClick={() => {

OnCancel ();

}}

Id={props. IsEdit ? "storeGrpingEditCnclBtn" : "storeGrpingCrtCnclBtn"}

>

{" "}

Cancel

</Button>

</div>

</>

);

});

  

Const mapStateToProps = (state) => {

Return {

SelectedStores: state. StoreGroupReducer. Selectedstores,

Columns: state. StoreGroupReducer. ManualFilteredStoresCols,

SelectedFilters: state. FilterReducer. SelectedFilters["store_hierarchy"],

ManualSelectedStoreFilters:

State. FilterReducer. SelectedFilters["store_filters_create_group"],

ManualSelectedProductFilters:

State. FilterReducer. SelectedFilters["product_filters_create_group"],

FilteredStores: state. StoreGroupReducer. ManualFilteredStores,

FilteredStoresCount: state. StoreGroupReducer. ManualFilteredStoresCount,

SelectedManualFilterType: state. StoreGroupReducer. SelectedManualFilterType,

GroupsCols: [... State. StoreGroupReducer. GroupsTableCols],

SelectedGrps: state. StoreGroupReducer. ManualselectedGroups,

ExistingStores: state. StoreGroupReducer. ExisitingStoresInEdit,

NewEditStores: state. StoreGroupReducer. NewStoresInEdit,

DeleteEditStores: state. StoreGroupReducer. DeletedStoresInEdit,

SelectedGroupType: state. StoreGroupReducer. SelectedGroupType,

NewEditGrps: state. StoreGroupReducer. NewGrpsInEdit,

DeleteEditGrps: state. StoreGroupReducer. DeletedGrpsInEdit,

SelectedCluster: state. StoreGroupReducer. SelectedCluster,

SelectedClusterFilters: state. StoreGroupReducer. SelectedClusterFilters,

IsSelectAll: state. StoreGroupReducer. IsSelectAll,

GroupFilterDependency: state. StoreGroupReducer. GroupFilterDependency,

CheckConfiguration: state. StoreGroupReducer. CheckConfiguration,

EnableMultiEdit:

State. TenantConfigReducer. CoreScreenNames. Attribute_value?. StoreGrouping

?. EnableMultiEdit,

AllowMultiChannel: state. StoreGroupReducer. AllowMultiChannelFlag,

};

};

  

Const mapActionsToProps = {

FetchStoreGrpFilteredStores,

SetStoreGroupFilteredStores,

SetSelectedStores,

ToggleLoader,

FetchStoreGroups,

SetGroupsCols,

AddSelectedGroups,

AddToExistingStores,

NewRowsInEdit,

DeletedRowsInEdit,

UpdateGrp,

AddSnack,

SetSelectedFilters,

DeletedGrpsInEdit,

NewGrpsInEdit,

SetSelectedStoresSelectAllState,

SetStoreGroupCustomLoaderValue,

FetchStoreGroupCustomClusterInfo,

SetClassificationValue,

SetClusterParamters,

SetClusterTimeFormat,

SetClusterTimePeriod,

SetSelectedCluster,

SetSelectedClusterFilters,

AddStoresToGroups,

GetColumnsAg,

GetTenantConfigApplicationLevel,

};

  

Export default connect (mapStateToProps, mapActionsToProps, null, {

ForwardRef: true,

})(FilteredStores);
```
 
#### Request : 
1. Why is it working fine in the UAT and hanging in the test instance
2. Can you please check the difference and it is mostly I have figured out it is something related to the `disabled ={}` code whatever is present in there 
3. Can you please help me with what is the root cause and how to fix this ?
