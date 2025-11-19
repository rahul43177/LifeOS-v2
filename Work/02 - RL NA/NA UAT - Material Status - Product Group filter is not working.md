#rlnaindex 
##### The issue description : 
Issue : Material status > Product group filter is not working
##### The API which is causing the issue from the network browser , The CURL :
```
curl --location 'ralph-lauren.uat.localhost:8085/api/v2/master/dimension-table/store' \
--header 'time_zone: US/eastern' \
--header 'sec-ch-ua-platform: "macOS"' \
--header 'Authorization: eyJhbGciOiJSUzI1NiIsImtpZCI6IjM4MDI5MzRmZTBlZWM0NmE1ZWQwMDA2ZDE0YTFiYWIwMWUzNDUwODMiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJodHRwczovL3NlY3VyZXRva2VuLmdvb2dsZS5jb20vaW1wYWN0c21hcnQtcHJvZCIsImF1ZCI6ImltcGFjdHNtYXJ0LXByb2QiLCJhdXRoX3RpbWUiOjE3NTkxNTc2ODUsInVzZXJfaWQiOiJGSXFXVkdHeFVtVUtHaG9Nb05OVmJZek1odlMyIiwic3ViIjoiRklxV1ZHR3hVbVVLR2hvTW9OTlZiWXpNaHZTMiIsImlhdCI6MTc2MzQ5MDM4NSwiZXhwIjoxNzYzNDkzOTg1LCJlbWFpbCI6InFhQGltcGFjdGFuYWx5dGljcy5jbyIsImVtYWlsX3ZlcmlmaWVkIjpmYWxzZSwiZmlyZWJhc2UiOnsiaWRlbnRpdGllcyI6eyJlbWFpbCI6WyJxYUBpbXBhY3RhbmFseXRpY3MuY28iXX0sInNpZ25faW5fcHJvdmlkZXIiOiJwYXNzd29yZCIsInRlbmFudCI6InJhbHBoLWxhdXJlbi11YXQtNHZuZHUifX0.kE38r4GfO2VOwf8WYVfICXyMu5VjcLpBLpa0N2o0fzrMf6NKJPjHnrJNQqaexgTSmYtqb5wtbHRgUgprxpqb-FrRI4cXvbdvElxnWB7qFM2jjSDahVkkp9GAN7KqnprQYg61YsX3-Gj41lTXCmuXsj-fcOz3v9ha4fSUPbPW3GshsaoYLMuDCeX3c1bKnrqMIHzxpge66clObYL97cKcWcYvJvu8mmxIc4qr0GRlKq3PieUSIzebojYMzwvsvGggfTU38hjqQdzNVLIBdw8S-1B7DkFD_IFPQ8vYYxQTZPkFlGGSngRCPEmtwEyznOSokU-C5qdFQHqjxx5U7EFFkQ' \
--header 'Referer: https://ralph-lauren.uat.impactsmartsuite.com/inventory-smart/configuration?tab=Store-Product' \
--header 'sec-ch-ua: "Chromium";v="142", "Google Chrome";v="142", "Not_A Brand";v="99"' \
--header 'sec-ch-ua-mobile: ?0' \
--header 'time_format: MM-DD-YYYY' \
--header 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/142.0.0.0 Safari/537.36' \
--header 'object-id: undefined' \
--header 'screen-name: Inventorysmart Configurations' \
--header 'Content-Type: application/json' \
--header 'application-code: 1' \
--data '{"filters":[{"filter_name":"Channel","filter_id":"channel","filter_type":"cascaded","dimension":"store","display_type":"dropdown","check_configuration":[{"checkedRows":[null]}],"values":["PFS"],"attribute_name":"channel","operator":"in"},{"filter_name":"Store Group","filter_id":"store_group","filter_type":"non-cascaded","dimension":"store","display_type":"dropdown","check_configuration":[{"checkedRows":["C_ALL DOORS"]}],"values":["C_ALL DOORS"],"attribute_name":"store_group","operator":"in"},{"attribute_name":"channel","operator":"not in","values":["RLE","RLW","CME","CMS","CMW","CMFS"],"filter_type":"cascaded","dimension":"store","system_filter":true},{"attribute_name":"dc_flag","operator":"not in","values":["true"],"filter_type":"cascaded","dimension":"store","system_filter":true}],"meta":{"search":[],"range":[],"sort":[],"limit":{"limit":10,"page":1}},"headers":[],"selection":{"data":[],"unique_columns":["store_code"]}}'
```

##### The logs after calling the API in the local 
```plain text
==================================================
[DB DEBUG] execute_parameterized_query() STARTED
[DB DEBUG] Tenant: ralph-lauren
[DB DEBUG] Return Type: None
[DB DEBUG] Fetch All: True
[DB DEBUG] Query: 
                SELECT user_code FROM global.user_master WHERE lower(email)= %(input_email)s AND is_deleted = false
            
[DB DEBUG] Parameters: {'input_email': 'qa@impactanalytics.co'}
[DB DEBUG] Application: None
[DB DEBUG] Use Secondary DB: False
[DB DEBUG] Additional kwargs: {}
==================================================
ddtracer_context {'trace_id': '691cbb9600000000b192f0e0755176ba', 'span_id': '8292813697229338939', 'service': 'fastapi', 'version': '', 'env': ''}
ddtracer_context {'trace_id': '691cbb9600000000b192f0e0755176ba', 'span_id': '8292813697229338939', 'service': 'fastapi', 'version': '', 'env': ''}
ddtracer_context {'trace_id': '691cbb9600000000b192f0e0755176ba', 'span_id': '12233430372209634103', 'service': 'fastapi', 'version': '', 'env': ''}
ddtracer_context {'trace_id': '691cbb9600000000b192f0e0755176ba', 'span_id': '12233430372209634103', 'service': 'fastapi', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.

🔍 [EXECUTABLE SQL FOR DBEAVER - PARAMETERIZED]:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

                SELECT user_code FROM global.user_master WHERE lower(email)= 'qa@impactanalytics.co' AND is_deleted = false
            
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[DB DEBUG] Executing parameterized query...
ddtracer_context {'trace_id': '691cbb9600000000b192f0e0755176ba', 'span_id': '16536856036978127121', 'service': 'fastapi', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.
[DB DEBUG] Records fetched: 1
[DB DEBUG] execute_parameterized_query() COMPLETED

Error uploading (ddog_prof_Exporter_send failed: client error (Connect): tcp connect error: Connection refused (os error 61): Connection refused (os error 61))
Error uploading (ddog_prof_Exporter_send failed: client error (Connect): tcp connect error: Connection refused (os error 61): Connection refused (os error 61))
Error uploading (ddog_prof_Exporter_send failed: client error (Connect): tcp connect error: Connection refused (os error 61): Connection refused (os error 61))
ddtracer_context {'trace_id': '691cbb9600000000b192f0e0755176ba', 'span_id': '97377328786505271', 'service': 'fastapi', 'version': '', 'env': ''}
ddtracer_context {'trace_id': '691cbb9600000000b192f0e0755176ba', 'span_id': '97377328786505271', 'service': 'fastapi', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.

==================================================
[DB DEBUG] execute_query() STARTED
[DB DEBUG] Tenant: ralph-lauren
[DB DEBUG] Return Type: dataframe
[DB DEBUG] Timeout: 200
[DB DEBUG] Connection provided: False
[DB DEBUG] Application: None
[DB DEBUG] Use Secondary DB: False
[DB DEBUG] Query:   SELECT
                distinct attribute_name, tc_code
                FROM (
                SELECT
                    tc.tc_code,
                    tcm."label",
                    tcm.column_name
                FROM
                    global.table_configurations tc
                JOIN
                    global.table_configurations_mapping tcm
                ON
                    tc.tc_code = tcm.tc_code
                WHERE
                    tc.name = 'product_status' ) tbl_config
                RIGHT JOIN (
                    SELECT
                        attribute_name,
                        is_hierarchy
                    FROM
                        global.product_attributes_list
                    WHERE
                        is_attribute = true ) pal
                    ON
                    tbl_config.column_name = pal.attribute_name
                 OR pal.is_hierarchy = true;
==================================================

🔍 [EXECUTABLE SQL FOR DBEAVER - EXECUTE QUERY]:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  SELECT
                distinct attribute_name, tc_code
                FROM (
                SELECT
                    tc.tc_code,
                    tcm."label",
                    tcm.column_name
                FROM
                    global.table_configurations tc
                JOIN
                    global.table_configurations_mapping tcm
                ON
                    tc.tc_code = tcm.tc_code
                WHERE
                    tc.name = 'product_status' ) tbl_config
                RIGHT JOIN (
                    SELECT
                        attribute_name,
                        is_hierarchy
                    FROM
                        global.product_attributes_list
                    WHERE
                        is_attribute = true ) pal
                    ON
                    tbl_config.column_name = pal.attribute_name
                 OR pal.is_hierarchy = true;
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

ddtracer_context {'trace_id': '691cbb9600000000b192f0e0755176ba', 'span_id': '7800196514939481173', 'service': 'fastapi', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.
[DB DEBUG] Query executed successfully
[DB DEBUG] DataFrame shape: (52, 2)
[DB DEBUG] DataFrame columns: ['attribute_name', 'tc_code']
[DB DEBUG] execute_query() COMPLETED

Error uploading (ddog_prof_Exporter_send failed: client error (Connect): tcp connect error: Connection refused (os error 61): Connection refused (os error 61))

==================================================
[DB DEBUG] get_count_of_sp_call_result() STARTED
[DB DEBUG] Tenant: ralph-lauren
[DB DEBUG] Tenant Schema ID: global
[DB DEBUG] SP Name: product_status_list
[DB DEBUG] Arguments: ('{"product_group": [{"type": "list", "operator": "in", "values": ["pod grp", "Michelle_test"]}], "is_deleted": [{"type": "list", "operator": "in", "values": [false]}]}', '{"l0_name": [{"type": "list", "operator": "in", "values": ["33-MENS APPAREL"]}], "l1_name": [{"type": "list", "operator": "in", "values": ["33-M CLOTHING"]}], "brand": [], "color": [], "size": [], "l4_name": [], "article": [], "style_color_id": [], "l3_name": [], "l2_name": [], "supersede_flag": []}', '{"search": [], "range": [], "query_type": "AND", "download_rows_limit_check": false}', '{"l0_name": [{"type": "list", "operator": "in", "values": ["33-MENS APPAREL"]}], "attribute_name": [{"type": "list", "operator": "in", "values": ["status"]}]}')
[DB DEBUG] Cursor Based: False
[DB DEBUG] Application: None
[DB DEBUG] Use Secondary DB: False
[DB DEBUG] Additional kwargs: {}
==================================================
ddtracer_context {'trace_id': '691cbb9600000000b192f0e0755176ba', 'span_id': '6584528800338463266', 'service': 'fastapi', 'version': '', 'env': ''}
ddtracer_context {'trace_id': '691cbb9600000000b192f0e0755176ba', 'span_id': '6584528800338463266', 'service': 'fastapi', 'version': '', 'env': ''}
ddtracer_context {'trace_id': '691cbb9600000000b192f0e0755176ba', 'span_id': '7315834369737672017', 'service': 'fastapi', 'version': '', 'env': ''}
ddtracer_context {'trace_id': '691cbb9600000000b192f0e0755176ba', 'span_id': '7315834369737672017', 'service': 'fastapi', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.

============================================================
[DB DEBUG] execute_store_procedure() STARTED
[DB DEBUG] Tenant: ralph-lauren
[DB DEBUG] Procedure Name: global.product_status_list
[DB DEBUG] Input Parameters: ['{"product_group": [{"type": "list", "operator": "in", "values": ["pod grp", "Michelle_test"]}], "is_deleted": [{"type": "list", "operator": "in", "values": [false]}]}', '{"l0_name": [{"type": "list", "operator": "in", "values": ["33-MENS APPAREL"]}], "l1_name": [{"type": "list", "operator": "in", "values": ["33-M CLOTHING"]}], "brand": [], "color": [], "size": [], "l4_name": [], "article": [], "style_color_id": [], "l3_name": [], "l2_name": [], "supersede_flag": []}', '{"search": [], "sort": [{"column": "product_code", "order": "asc"}], "range": [], "limit": {"limit": 10, "page": 1, "offset": 0}, "query_type": "AND", "download_rows_limit_check": false}', '{"l0_name": [{"type": "list", "operator": "in", "values": ["33-MENS APPAREL"]}], "attribute_name": [{"type": "list", "operator": "in", "values": ["status"]}]}']
[DB DEBUG] Cursor Based: False
[DB DEBUG] Fetch Rows Count: False
[DB DEBUG] Min Max Columns: None
[DB DEBUG] Distinct Columns: None
[DB DEBUG] Table Query: None
[DB DEBUG] Timeout: 200
[DB DEBUG] Application: None
[DB DEBUG] Use Secondary DB: False
[DB DEBUG] Additional kwargs: {}
[DB DEBUG] Generated SP Query: global.product_status_list('{"product_group": [{"type": "list", "operator": "in", "values": ["pod grp", "Michelle_test"]}], "is_deleted": [{"type": "list", "operator": "in", "values": [false]}]}', '{"l0_name": [{"type": "list", "operator": "in", "values": ["33-MENS APPAREL"]}], "l1_name": [{"type": "list", "operator": "in", "values": ["33-M CLOTHING"]}], "brand": [], "color": [], "size": [], "l4_name": [], "article": [], "style_color_id": [], "l3_name": [], "l2_name": [], "supersede_flag": []}', '{"search": [], "sort": [{"column": "product_code", "order": "asc"}], "range": [], "limit": {"limit": 10, "page": 1, "offset": 0}, "query_type": "AND", "download_rows_limit_check": false}', '{"l0_name": [{"type": "list", "operator": "in", "values": ["33-MENS APPAREL"]}], "attribute_name": [{"type": "list", "operator": "in", "values": ["status"]}]}')
============================================================
ddtracer_context {'trace_id': '691cbb9600000000b192f0e0755176ba', 'span_id': '10316911697719374629', 'service': 'fastapi', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.
ddtracer_context {'trace_id': '691cbb9600000000b192f0e0755176ba', 'span_id': '254296344206769172', 'service': 'fastapi', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.
[DB DEBUG] Full Procedure Name: global.product_status_list

🔍 [EXECUTABLE SQL FOR DBEAVER]:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
select * from global.product_status_list ('{"product_group": [{"type": "list", "operator": "in", "values": ["pod grp", "Michelle_test"]}], "is_deleted": [{"type": "list", "operator": "in", "values": [false]}]}', '{"l0_name": [{"type": "list", "operator": "in", "values": ["33-MENS APPAREL"]}], "l1_name": [{"type": "list", "operator": "in", "values": ["33-M CLOTHING"]}], "brand": [], "color": [], "size": [], "l4_name": [], "article": [], "style_color_id": [], "l3_name": [], "l2_name": [], "supersede_flag": []}', '{"search": [], "sort": [{"column": "product_code", "order": "asc"}], "range": [], "limit": {"limit": 10, "page": 1, "offset": 0}, "query_type": "AND", "download_rows_limit_check": false}', '{"l0_name": [{"type": "list", "operator": "in", "values": ["33-MENS APPAREL"]}], "attribute_name": [{"type": "list", "operator": "in", "values": ["status"]}]}')
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

INFO:     127.0.0.1:58030 - "POST /api/v2/master/dimension-table/product HTTP/1.1" 500 Internal Server Error
```


##### The Database findings : 
###### The SP which is getting called found from the local logs : 
The SP definition at -- /Users/rahulmishra/Desktop/mtp-database/database/ralph_lauren_na/schemas/global/functions/product_status_list.sql

```sql
SELECT *
FROM global.product_status_list ('{"product_group": [{"type": "list", "operator": "in", "values": ["pod grp", "Michelle_test"]}], "is_deleted": [{"type": "list", "operator": "in", "values": [false]}]}', '{"l0_name": [{"type": "list", "operator": "in", "values": ["33-MENS APPAREL"]}], "l1_name": [{"type": "list", "operator": "in", "values": ["33-M CLOTHING"]}], "brand": [], "color": [], "size": [], "l4_name": [], "article": [], "style_color_id": [], "l3_name": [], "l2_name": [], "supersede_flag": []}', '{"search": [], "sort": [{"column": "product_code", "order": "asc"}], "range": [], "limit": {"limit": 10, "page": 1, "offset": 0}, "query_type": "AND", "download_rows_limit_check": false}', '{"l0_name": [{"type": "list", "operator": "in", "values": ["33-MENS APPAREL"]}], "attribute_name": [{"type": "list", "operator": "in", "values": ["status"]}]}')

--the output 
ffdf l0_name
{channel}
{l0_name,l1_name,l2_name}
here
size
_attr_cols {size}
after loop<NULL>
here
brand
_attr_cols {size,brand}
after loop<NULL>
here
color
_attr_cols {size,brand,color}
after loop<NULL>
here
article
_attr_cols {size,brand,color,article}
after loop<NULL>
here
l0_name
_attr_cols {size,brand,color,article,l0_name}
after loop1
here
l1_name
_attr_cols {size,brand,color,article,l0_name,l1_name}
after loop1
here
l2_name
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name}
after loop0
here
l3_name
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name,l3_name}
after loop0
here
l4_name
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name,l3_name,l4_name}
after loop0
here
is_deleted
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name,l3_name,l4_name,is_deleted}
after loop1
here
product_name
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name,l3_name,l4_name,is_deleted,product_name}
after loop0
here
product_group
product_group group
{"pod grp",Michelle_test}
{"( product_code in (select distinct x.product_code from global.product_groups gp join global.product_groups_mapping x on gp.pg_code = x.pg_code where is_deleted = false and name = any('{\"pod grp\",Michelle_test}'::varchar[])) )"}
after loop1
here
style_color_id
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name,l3_name,l4_name,is_deleted,product_name,style_color_id}
after loop0
here
supersede_flag
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name,l3_name,l4_name,is_deleted,product_name,style_color_id,supersede_flag}
after loop0
here
product_description
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name,l3_name,l4_name,is_deleted,product_name,style_color_id,supersede_flag,product_description}
after loop0
here
reference_product_codes
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name,l3_name,l4_name,is_deleted,product_name,style_color_id,supersede_flag,product_description,reference_product_codes}
after loop0
here
replacement_product_codes
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name,l3_name,l4_name,is_deleted,product_name,style_color_id,supersede_flag,product_description,reference_product_codes,replacement_product_codes}
after loop0
 combination <NULL>
{channel}
{l0_name,l1_name,l2_name}
_query_pa SELECT size, brand, color, article, l0_name, l1_name, l2_name, l3_name, l4_name, is_deleted, product_name, style_color_id, supersede_flag, product_description, reference_product_codes, replacement_product_codes, product_code FROM "global".product_attributes_filter  WHERE (l0_name::varchar = any('{"33-MENS APPAREL"}'::varchar[])) AND (l1_name::varchar = any('{"33-M CLOTHING"}'::varchar[])) AND (is_deleted::varchar = any('{false}'::varchar[])) AND ( product_code in (select distinct x.product_code from global.product_groups gp join global.product_groups_mapping x on gp.pg_code = x.pg_code where is_deleted = false and name = any('{"pod grp",Michelle_test}'::varchar[])) )s
 ORDER BY product_code asc nulls last , LIMIT 10 OFFSET 0,
 WHERE (l0_name::varchar = any('{"33-MENS APPAREL"}'::varchar[])) AND (attribute_name::varchar = any('{"status"}'::varchar[]))
{'size',X.size,'brand',X.brand,'color',X.color,'article',X.article,'l0_name',X.l0_name,'l1_name',X.l1_name,'l2_name',X.l2_name,'l3_name',X.l3_name,'l4_name',X.l4_name,'is_deleted',X.is_deleted,'product_group',X.product_group,'style_color_id',X.style_color_id,'supersede_flag',X.supersede_flag,'aggregation_code',X.article}
SELECT size, brand, color, article, l0_name, l1_name, l2_name, l3_name, l4_name, is_deleted, product_name, style_color_id, supersede_flag, product_description, reference_product_codes, replacement_product_codes, product_code FROM "global".product_attributes_filter  WHERE (l0_name::varchar = any('{"33-MENS APPAREL"}'::varchar[])) AND (l1_name::varchar = any('{"33-M CLOTHING"}'::varchar[])) AND (is_deleted::varchar = any('{false}'::varchar[])) AND ( product_code in (select distinct x.product_code from global.product_groups gp join global.product_groups_mapping x on gp.pg_code = x.pg_code where is_deleted = false and name = any('{"pod grp",Michelle_test}'::varchar[])) )

with cte as  (SELECT size, brand, color, article, l0_name, l1_name, l2_name, l3_name, l4_name, is_deleted, product_name, style_color_id, supersede_flag, product_description, reference_product_codes, replacement_product_codes, product_code FROM "global".product_attributes_filter  WHERE (l0_name::varchar = any('{"33-MENS APPAREL"}'::varchar[])) AND (l1_name::varchar = any('{"33-M CLOTHING"}'::varchar[])) AND (is_deleted::varchar = any('{false}'::varchar[])) AND ( product_code in (select distinct x.product_code from global.product_groups gp join global.product_groups_mapping x on gp.pg_code = x.pg_code where is_deleted = false and name = any('{"pod grp",Michelle_test}'::varchar[])) )) 
							select
		  					   X.product_code,
		  					   X.product_name,
		  					   X.replacement_product_codes as replacement_product_codes, 
		  					   X.reference_product_codes as reference_product_codes,
		  					   json_build_object('size' ,X.size ,'brand' ,X.brand ,'color' ,X.color ,'article' ,X.article ,'l0_name' ,X.l0_name ,'l1_name' ,X.l1_name ,'l2_name' ,X.l2_name ,'l3_name' ,X.l3_name ,'l4_name' ,X.l4_name ,'is_deleted' ,X.is_deleted ,'product_group' ,X.product_group ,'style_color_id' ,X.style_color_id ,'supersede_flag' ,X.supersede_flag ,'aggregation_code' ,X.article),
		  					   b.status_obj as status_obj,
		  					   X.product_description,
							   b.updated_by,
							   b.change_time
		  					FROM cte X 
							join (select json_agg(jsonb_build_object('status_start_time', concat(start_time)::varchar, 'status_end_time', concat(end_time)::varchar, 'status', attribute_value , 'time_attr_id', product_time_attr_id) ORDER BY start_time) status_obj, product_code, max(um.name) as updated_by, TO_CHAR(max(pg_xact_commit_timestamp(pta.xmin)) AT TIME ZONE 'EDT', 'MM/DD/YYYY') as change_time from 
						                      	"global".product_time_attributes pta left join "global".user_master um on pta.updated_by = um.user_code  WHERE (l0_name::varchar = any('{"33-MENS APPAREL"}'::varchar[])) AND (attribute_name::varchar = any('{"status"}'::varchar[]))
						                      	group by product_code)b using(product_code)  ORDER BY product_code asc nulls last  LIMIT 10 OFFSET 0

						                      	
-- From this the executable part is : 

WITH cte AS
  (SELECT SIZE,
          brand,
          color,
          article,
          l0_name,
          l1_name,
          l2_name,
          l3_name,
          l4_name,
          is_deleted,
          product_name,
          style_color_id,
          supersede_flag,
          product_description,
          reference_product_codes,
          replacement_product_codes,
          product_code
   FROM "global".product_attributes_filter
   WHERE (l0_name::varchar = any('{"33-MENS APPAREL"}'::varchar[]))
     AND (l1_name::varchar = any('{"33-M CLOTHING"}'::varchar[]))
     AND (is_deleted::varchar = any('{false}'::varchar[]))
     AND (product_code IN
            (SELECT DISTINCT x.product_code
             FROM global.product_groups gp
             JOIN global.product_groups_mapping x ON gp.pg_code = x.pg_code
             WHERE is_deleted = FALSE
               AND name = any('{"pod grp",Michelle_test}'::varchar[]))))
SELECT X.product_code,
       X.product_name,
       X.replacement_product_codes AS replacement_product_codes,
       X.reference_product_codes AS reference_product_codes,
       json_build_object('size', X.size, 'brand', X.brand, 'color', X.color, 'article', X.article, 'l0_name', X.l0_name, 'l1_name', X.l1_name, 'l2_name', X.l2_name, 'l3_name', X.l3_name, 'l4_name', X.l4_name, 'is_deleted', X.is_deleted, 'product_group', X.product_group, 'style_color_id', X.style_color_id, 'supersede_flag', X.supersede_flag, 'aggregation_code', X.article),
       b.status_obj AS status_obj,
       X.product_description,
       b.updated_by,
       b.change_time
FROM cte X
JOIN
  (SELECT json_agg(jsonb_build_object('status_start_time', concat(start_time)::varchar, 'status_end_time', concat(end_time)::varchar, 'status', attribute_value, 'time_attr_id', product_time_attr_id)
                   ORDER BY start_time) status_obj,
          product_code,
          max(um.name) AS updated_by,
          TO_CHAR(max(pg_xact_commit_timestamp(pta.xmin)) AT TIME ZONE 'EDT', 'MM/DD/YYYY') AS change_time
   FROM "global".product_time_attributes pta
   LEFT JOIN "global".user_master um ON pta.updated_by = um.user_code
   WHERE (l0_name::varchar = any('{"33-MENS APPAREL"}'::varchar[]))
     AND (attribute_name::varchar = any('{"status"}'::varchar[]))
   GROUP BY product_code)b USING(product_code)
ORDER BY product_code ASC NULLS LAST
LIMIT 10
OFFSET 0


-- The error coming as -- 
--SQL Error [42703]: ERROR: column x.product_group does not exist
  --Position: 1364
  
  

```

###### The Database findings : 
So basically what we found that the with adding the product group as a filter the API is failing. 
❌ product_group column does NOT exist in product_attributes_filter

The function internally creates product_group only when grouping, but the base table global.product_attributes_filter does not have a column named product_group.

So this part inside your json_build_object is invalid:

I went to check the query of store status as well -- there the store group filter is working fine and the query is not giving any error 
```sql 
--store status 
select * from global.store_status_list ('{"store_group": [{"type": "list", "operator": "in", "values": ["C_ALL DOORS"]}], "is_deleted": [{"type": "list", "operator": "in", "values": [false]}]}', '{"channel": [{"type": "list", "operator": "in", "values": ["PFS"]}, {"type": "list", "operator": "not in", "values": ["RLE", "RLW", "CME", "CMS", "CMW", "CMFS"]}], "dc_flag": [{"type": "list", "operator": "not in", "values": ["true"]}], "climate": [], "retail_facility_code": [], "store_size": [], "zipcode": []}', '{"search": [], "sort": [{"column": "store_code", "order": "asc"}], "range": [], "limit": {"limit": 10, "page": 1, "offset": 0}, "query_type": "AND", "download_rows_limit_check": false}', '{}')



SELECT X.store_name,
       X.store_code,
       X.store_description,
       X.active AS active,
       json_build_object('channel', X.channel, 'climate', X.climate, 'dc_flag', X.dc_flag, 'zipcode', X.zipcode, 'store_size', X.store_size, 'retail_facility_code', X.retail_facility_code),
       status_obj,
       X.updated_by,
       TO_CHAR(X.change_time AT TIME ZONE 'US/EASTERN', 'MM/DD/YYYY') AS change_time,
       CASE
           WHEN TRUE THEN COALESCE(is_auto_allocation_active, TRUE) :: TEXT
           ELSE -- If limit does not exist
 CASE
     WHEN COALESCE(is_auto_allocation_active, TRUE) THEN 'Active'
     ELSE 'Inactive'
 END
       END AS is_auto_allocation_active
FROM
  (SELECT sm.*,
          pta.status AS status_obj,
          greatest(pta.change_time, auto_allocation_status.updated_at) AS change_time,
          CASE
              WHEN pta.change_time >= auto_allocation_status.updated_at THEN pta.updated_by::text
              ELSE coalesce(auto_allocation_status.updated_by::text, pta.updated_by::text)
          END AS updated_by,
          auto_allocation_status.is_auto_allocation_active AS is_auto_allocation_active
   FROM
     (SELECT main.store_name,
             main.store_description,
             main.active AS active, --  main.special_classification as special_classification,
 attributes.*
      FROM
        (SELECT *
         FROM global.store_master
         WHERE (is_deleted::bool = any('{false}'::bool[]))
           AND (store_code IN
                  (SELECT DISTINCT x.store_code
                   FROM global.store_groups gp
                   JOIN global.store_groups_mapping x ON gp.sg_code = x.sg_code
                   WHERE is_deleted = FALSE
                     AND name = any('{"C_ALL DOORS"}'::varchar[])))) main
      JOIN
        (SELECT channel,
                climate,
                dc_flag,
                zipcode,
                store_size,
                retail_facility_code,
                store_code
         FROM "global".store_attributes_filter
         WHERE (channel::varchar = any('{PFS}'::varchar[]))
           AND NOT(channel::varchar = any('{RLE,RLW,CME,CMS,CMW,CMFS}'::varchar[]))
           AND NOT(dc_flag::bool = any('{true}'::bool[]))) attributes ON main.store_code = attributes.store_code) sm
   LEFT JOIN
     (SELECT store_code AS store_code,
             json_agg(jsonb_build_object('status_start_time', CASE
                                                                  WHEN EXTRACT(YEAR
                                                                               FROM status_start_time::date) IN (2022, 2023) THEN CURRENT_DATE::varchar
                                                                  ELSE status_start_time::varchar
                                                              END, 'status_end_time', concat(status_end_time)::varchar, 'status', status, 'time_attr_id', store_time_attr_id)
                      ORDER BY status_start_time) status,
             max(updated_by) AS updated_by,
             max(change_time) AS change_time
      FROM
        (SELECT store_code,
                start_time AS status_start_time,
                end_time AS status_end_time,
                attribute_value AS status,
                store_time_attr_id,
                um.name AS updated_by,
                pg_xact_commit_timestamp(sta.xmin) AS change_time
         FROM "global".store_time_attributes sta
         LEFT JOIN "global".user_master um ON sta.updated_by = um.user_code
         WHERE attribute_name = 'status'
           AND end_time >= CURRENT_DATE) a
      GROUP BY store_code) pta ON sm.store_code = pta.store_code
   LEFT JOIN
     (SELECT aass.store_code AS store_code,
             aass.is_auto_allocation_active,
             aass.updated_at,
             um.name AS updated_by
      FROM inventory_smart.auto_allocation_store_status aass
      LEFT JOIN "global".user_master um ON aass.updated_by = um.user_code) auto_allocation_status ON sm.store_code = auto_allocation_status.store_code
   WHERE 1=1) X
ORDER BY store_code ASC NULLS LAST
LIMIT 10
OFFSET 0
```
We can take reference from there. 

More database findings I can provide if you ask me anything regarding running the queries in the dbeaver if you want more data or info on anything. 

##### Repos to look at : 

###### core backend : 
```
/Users/rahulmishra/Desktop/mtp-core-backend/backend
```
- Backend code related core and to the API is written inside mtp-core-backend 
- There is one utils file which is being used to execute everything related to data like -> Executing a query , Executing a stored procedure and etc. 
- This utils file is installed from mtp-utils repo which is mentioned in the toml file so you can check this as well , if you would like or of any help : 
``` 
/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-zfxLRh0v-py3.12/lib/python3.12/site-packages/database/utils.py
```

###### mtp-database : 
```
/Users/rahulmishra/Desktop/mtp-database
```
- All the stored procedure which are being called in the API is stored here inside the folder of functions 
- Configurations are stored here in the form of csv. 
- The data for each client is seperated by the folder for example right now we are working with the `ralph_lauren_na` , so functions and the config for this client is stored in here 
- If some function is not present then it must be taking from the : `/Users/rahulmishra/Desktop/mtp-database/database/schemas/global/functions` -> common for everyone 
- So if we want to make something client specific we can take it from - `/Users/rahulmishra/Desktop/mtp-database/database/schemas/global/functions` and create the function inside the client or tenant folder

##### Note : 
- So the backend is mtp (multi-tenant platform) which means single codebase is being used by multiple clients 
- So single change in the codebase can affect all the client in the bakcend 
- Hence , Most of the logic is handled with Store Procedure (SP) inside the mtp-database 
- Each client have their own folder where the configurations data in the form of `csv` is stored , SP in the form of `.sql` and in the SP function we mostly handle the client specific logic. One such example of configuration is : `tenant_attribute_master.csv` where tenant specific configurations are present. 
- Some SP are stored in the `global` schema which means are common for all the clients.
- I work with `signet` client. 
- Sometime the global SP we are using is not aligned with our client so we have to make that specific file in our folder and then make the changes and use , that will have the preference over the global outside schema. 


##### Request 
1. Please check the curl I have given , from that : 
	1. Please check the end point of the API 
	2. Payload by which we are calling and the filters in the payload
2. Please check the backend repo properly 
	1. check the entire flow of the API 
	2. And find out the logic as how things are working
	3. At what point it is breaking , check it from the logs as well. 
3. Please check the stored procedure involved and try to find out the logic or the error
4. If error logs are given please check those and try to find out the solid RCA
5. I want you to find out the problematic part of the code and the piece of code which is throwing error or causing the issue.
6. If you would like to debug more efficiently for some difficult bug , you can also suggest me the places to add the breakpoints in the backend codebase to stop the execution of the code and check the value , which I can provide you. 
7. Please go step by step and go deep and try to find out the root cause of the issue.




