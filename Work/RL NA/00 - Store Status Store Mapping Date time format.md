##### The issue description : 
We need to change the updated_at date format to `MM/DD/YYYY`

##### The API which is causing the issue from the network browser , The CURL :
```
curl 'https://ralph-lauren.test.impactsmartsuite.com/api/v2/master/dimension-table/store' \
  -H 'time_zone: US/eastern' \
  -H 'sec-ch-ua-platform: "macOS"' \
  -H 'Authorization: eyJhbGciOiJSUzI1NiIsImtpZCI6IjdlYTA5ZDA1NzI2MmU2M2U2MmZmNzNmMDNlMDRhZDI5ZDg5Zjg5MmEiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJodHRwczovL3NlY3VyZXRva2VuLmdvb2dsZS5jb20vaW1wYWN0c21hcnQiLCJhdWQiOiJpbXBhY3RzbWFydCIsImF1dGhfdGltZSI6MTc2MTU0NTY4MSwidXNlcl9pZCI6ImExclJjVlNpM0ZnbnBFMk42cEtaR29TZXQyczEiLCJzdWIiOiJhMXJSY1ZTaTNGZ25wRTJONnBLWkdvU2V0MnMxIiwiaWF0IjoxNzYxODE4MTc3LCJleHAiOjE3NjE4MjE3NzcsImVtYWlsIjoicWFAaW1wYWN0YW5hbHl0aWNzLmNvIiwiZW1haWxfdmVyaWZpZWQiOmZhbHNlLCJmaXJlYmFzZSI6eyJpZGVudGl0aWVzIjp7ImVtYWlsIjpbInFhQGltcGFjdGFuYWx5dGljcy5jbyJdfSwic2lnbl9pbl9wcm92aWRlciI6InBhc3N3b3JkIiwidGVuYW50IjoicmFscGgtbGF1cmVuLXVzem9xIn19.NAc-hfoQ6rZ5khnhxaeReGCmhFZueGZOQ-t0NnX5jLMM3NFXqlD--3CgBSJylEo_TUHV_fGtpY9lEE2qqaxOTfj6G4KQTXl53aE63sWDOW7OtjE9EstwHFHtlEl_giExD6UjTJR7pfQ5rghKlGq2TxNh-RfBuLeZGcEZ_AXlgcz1IY4au7b2tiQmAbYfc47Cs-oYpvodMxSBM7h4th4hbAn2zTz-noSi0W8d-uDxc5RypXkejKVIG5MwCRDElqXfUy4iXQRXS3ZaCMCaAg8gae0finjennQv2PY40-Z2EMnZtBW77MPVzN53TV9hmW42OiesRKBvKlY4NkatrQGkbg' \
  -H 'Referer: https://ralph-lauren.test.impactsmartsuite.com/inventory-smart/configuration' \
  -H 'sec-ch-ua: "Google Chrome";v="141", "Not?A_Brand";v="8", "Chromium";v="141"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'time_format: MM-DD-YYYY' \
  -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/141.0.0.0 Safari/537.36' \
  -H 'object-id: undefined' \
  -H 'screen-name: Inventorysmart Configurations' \
  -H 'Content-Type: application/json' \
  -H 'application-code: 1' \
  --data-raw '{"filters":[{"values":["PFS"],"operator":"in","dimension":"store","startYear":null,"disablePast":null,"disableType":null,"filter_type":"cascaded","display_type":"dropdown","disableFuture":null,"attribute_name":"channel","disablePastWeeks":null,"disableFutureWeeks":null,"filter_id":"channel"},{"attribute_name":"channel","operator":"not in","values":["RLE","RLW","CME","CMS","CMW","CMFS"],"filter_type":"cascaded","dimension":"store","system_filter":true},{"attribute_name":"dc_flag","operator":"not in","values":["true"],"filter_type":"cascaded","dimension":"store","system_filter":true}],"meta":{"search":[],"range":[],"sort":[],"limit":{"limit":10,"page":1}},"headers":[],"selection":{"data":[],"unique_columns":["store_code"]}}'
```


##### The logs after calling the API in the local : 
```plain text 

==================================================
[DB DEBUG] execute_parameterized_query() STARTED
[DB DEBUG] Tenant: localhost
[DB DEBUG] Return Type: None
[DB DEBUG] Fetch All: True
[DB DEBUG] Query: 
                SELECT user_code FROM global.user_master WHERE lower(email)= %(input_email)s AND is_deleted = false
            
[DB DEBUG] Parameters: {'input_email': 'qa@impactanalytics.co'}
[DB DEBUG] Application: None
[DB DEBUG] Use Secondary DB: False
[DB DEBUG] Additional kwargs: {}
==================================================

🔍 [EXECUTABLE SQL FOR DBEAVER - PARAMETERIZED]:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

                SELECT user_code FROM global.user_master WHERE lower(email)= 'qa@impactanalytics.co' AND is_deleted = false
            
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[DB DEBUG] Executing parameterized query...
2025-10-30 15:29:56,205 LOCAL ERROR [mtp-core-LOCAL] [logger.py:184] - IA-ERROR: Redis connection error (Worker PID: 73852): Error 8 connecting to redis-11871.c18098.us-central1-1.gcp.cloud.rlrcp.com:11871. nodename nor servname provided, or not known. | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '6903371b00000000784753605cbcea48', 'span_id': '4422615056323807062', 'service': 'fastapi', 'version': '', 'env': ''}
2025-10-30 15:29:56,206 LOCAL WARNING [mtp-core-LOCAL] [logger.py:184] - IA-WARNING: Redis failure #1. Next retry in 60.0 seconds (exponential backoff) | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '6903371b00000000784753605cbcea48', 'span_id': '4422615056323807062', 'service': 'fastapi', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.
[DB DEBUG] Records fetched: 1
[DB DEBUG] execute_parameterized_query() COMPLETED


==================================================
[DB DEBUG] execute_query() STARTED
[DB DEBUG] Tenant: localhost
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
                    tc.name = 'store_status' ) tbl_config
                RIGHT JOIN (
                    SELECT
                        attribute_name,
                        is_hierarchy
                    FROM
                        global.store_attributes_list
                    WHERE
                        is_attribute = true ) pal
                    ON
                    tbl_config.column_name = pal.attribute_name
                 OR pal.attribute_name = 'channel'
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
                    tc.name = 'store_status' ) tbl_config
                RIGHT JOIN (
                    SELECT
                        attribute_name,
                        is_hierarchy
                    FROM
                        global.store_attributes_list
                    WHERE
                        is_attribute = true ) pal
                    ON
                    tbl_config.column_name = pal.attribute_name
                 OR pal.attribute_name = 'channel'
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[DB DEBUG] Query executed successfully
[DB DEBUG] DataFrame shape: (27, 2)
[DB DEBUG] DataFrame columns: ['attribute_name', 'tc_code']
[DB DEBUG] execute_query() COMPLETED


============================================================
[DB DEBUG] execute_store_procedure() STARTED
[DB DEBUG] Tenant: localhost
[DB DEBUG] Procedure Name: global.store_status_list
[DB DEBUG] Input Parameters: ['{"is_deleted": [{"type": "list", "operator": "in", "values": [false]}]}', '{"channel": [{"type": "list", "operator": "in", "values": ["PFS"]}, {"type": "list", "operator": "not in", "values": ["RLE", "RLW", "CME", "CMS", "CMW", "CMFS"]}], "dc_flag": [{"type": "list", "operator": "not in", "values": ["true"]}], "store_size": [], "zipcode": [], "retail_facility_code": [], "climate": []}', '{"search": [], "sort": [{"column": "store_code", "order": "asc"}], "range": [], "limit": {"limit": 10, "page": 1, "offset": 0}, "query_type": "AND", "download_rows_limit_check": false}', '{}']
[DB DEBUG] Cursor Based: False
[DB DEBUG] Fetch Rows Count: False
[DB DEBUG] Min Max Columns: None
[DB DEBUG] Distinct Columns: None
[DB DEBUG] Table Query: None
[DB DEBUG] Timeout: 200
[DB DEBUG] Application: None
[DB DEBUG] Use Secondary DB: False
[DB DEBUG] Additional kwargs: {}
[DB DEBUG] Generated SP Query: global.store_status_list('{"is_deleted": [{"type": "list", "operator": "in", "values": [false]}]}', '{"channel": [{"type": "list", "operator": "in", "values": ["PFS"]}, {"type": "list", "operator": "not in", "values": ["RLE", "RLW", "CME", "CMS", "CMW", "CMFS"]}], "dc_flag": [{"type": "list", "operator": "not in", "values": ["true"]}], "store_size": [], "zipcode": [], "retail_facility_code": [], "climate": []}', '{"search": [], "sort": [{"column": "store_code", "order": "asc"}], "range": [], "limit": {"limit": 10, "page": 1, "offset": 0}, "query_type": "AND", "download_rows_limit_check": false}', '{}')
============================================================

==================================================
[DB DEBUG] get_count_of_sp_call_result() STARTED
[DB DEBUG] Tenant: localhost
[DB DEBUG] Tenant Schema ID: global
[DB DEBUG] SP Name: store_status_list
[DB DEBUG] Arguments: ('{"is_deleted": [{"type": "list", "operator": "in", "values": [false]}]}', '{"channel": [{"type": "list", "operator": "in", "values": ["PFS"]}, {"type": "list", "operator": "not in", "values": ["RLE", "RLW", "CME", "CMS", "CMW", "CMFS"]}], "dc_flag": [{"type": "list", "operator": "not in", "values": ["true"]}], "store_size": [], "zipcode": [], "retail_facility_code": [], "climate": []}', '{"search": [], "range": [], "query_type": "AND", "download_rows_limit_check": false}', '{}')
[DB DEBUG] Cursor Based: False
[DB DEBUG] Application: None
[DB DEBUG] Use Secondary DB: False
[DB DEBUG] Additional kwargs: {}
==================================================

🔍 [EXECUTABLE SQL FOR DBEAVER]:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
select * from global.store_status_list ('{"is_deleted": [{"type": "list", "operator": "in", "values": [false]}]}', '{"channel": [{"type": "list", "operator": "in", "values": ["PFS"]}, {"type": "list", "operator": "not in", "values": ["RLE", "RLW", "CME", "CMS", "CMW", "CMFS"]}], "dc_flag": [{"type": "list", "operator": "not in", "values": ["true"]}], "store_size": [], "zipcode": [], "retail_facility_code": [], "climate": []}', '{"search": [], "sort": [{"column": "store_code", "order": "asc"}], "range": [], "limit": {"limit": 10, "page": 1, "offset": 0}, "query_type": "AND", "download_rows_limit_check": false}', '{}')
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[DB DEBUG] Full Procedure Name: global.store_status_list
[DB DEBUG] Final result count: 10
[DB DEBUG] Result type: list
[DB DEBUG] execute_store_procedure() COMPLETED
============================================================

[DB DEBUG] Count result: 198
[DB DEBUG] get_count_of_sp_call_result() COMPLETED
==================================================

INFO:     127.0.0.1:55400 - "POST /api/v2/master/dimension-table/store HTTP/1.1" 200 OK
```

##### The Database findings : 
###### The Database findings : 
The SP file : /Users/rahulmishra/Desktop/mtp-database/database/ralph_lauren_na/schemas/global/functions/store_status_list.sql
```sql 
select * from global.store_status_list ('{"is_deleted": [{"type": "list", "operator": "in", "values": [false]}]}', '{"channel": [{"type": "list", "operator": "in", "values": ["PFS"]}, {"type": "list", "operator": "not in", "values": ["RLE", "RLW", "CME", "CMS", "CMW", "CMFS"]}], "dc_flag": [{"type": "list", "operator": "not in", "values": ["true"]}], "store_size": [], "zipcode": [], "retail_facility_code": [], "climate": []}', '{"search": [], "sort": [{"column": "store_code", "order": "asc"}], "range": [], "limit": {"limit": 10, "page": 1, "offset": 0}, "query_type": "AND", "download_rows_limit_check": false}', '{}');

  

  

store_name |store_code|store_description|active|attributes |status_obj |updated_by |updated_at |is_auto_allocation_active|

-----------------------+----------+-----------------+------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+------------+-----------------------------+-------------------------+

VAUGHAN MILLS CHILDRENS|1000900000| |true |{"channel" : "PFS", "climate" : "NORTH", "dc_flag" : false, "zipcode" : "L4K 5W4", "store_size" : null, "retail_facility_code" : "00364"}|[{"status": "active", "time_attr_id": 48290, "status_end_time": "2050-12-31", "status_start_time": "2024-11-24"}]|Testtesttest|2025-05-27 12:37:55.800 +0530|true |

TINTON FALLS |1002800001| |true |{"channel" : "PFS", "climate" : "CORE", "dc_flag" : false, "zipcode" : "07753", "store_size" : null, "retail_facility_code" : "00042"} |[{"status": "active", "time_attr_id": 48287, "status_end_time": "2050-12-31", "status_start_time": "2024-11-24"}]|Testtesttest|2025-09-05 15:26:11.547 +0530|false |

CITADEL |10036713 | |true |{"channel" : "PFS", "climate" : "SOUTH", "dc_flag" : false, "zipcode" : "90040", "store_size" : null, "retail_facility_code" : "00470"} |[{"status": "active", "time_attr_id": 47927, "status_end_time": "2050-12-31", "status_start_time": "2024-11-24"}]|Testtesttest|2025-04-29 20:18:22.011 +0530|false |

NASHVILLE |10037259 | |true |{"channel" : "PFS", "climate" : "CORE", "dc_flag" : false, "zipcode" : "37013", "store_size" : null, "retail_facility_code" : "00471"} |[{"status": "active", "time_attr_id": 47930, "status_end_time": "2050-12-31", "status_start_time": "2024-11-24"}]|Testtesttest|2025-04-29 20:18:22.011 +0530|false |

ASHEVILLE |10038711 | |true |{"channel" : "PFS", "climate" : "CORE", "dc_flag" : false, "zipcode" : "28806", "store_size" : null, "retail_facility_code" : "00473"} |[{"status": "active", "time_attr_id": 47933, "status_end_time": "2050-12-31", "status_start_time": "2024-11-24"}]|Testtesttest|2025-04-29 20:18:22.011 +0530|false |

COLUMBUS |101100000 | |true |{"channel" : "PFS", "climate" : "NORTH", "dc_flag" : false, "zipcode" : "43074", "store_size" : null, "retail_facility_code" : "00229"} |[{"status": "active", "time_attr_id": 47936, "status_end_time": "2050-12-31", "status_start_time": "2024-11-24"}]|Testtesttest|2025-04-29 20:18:22.011 +0530|false |

LEESBURG |101500000 | |true |{"channel" : "PFS", "climate" : "CORE", "dc_flag" : false, "zipcode" : "20176", "store_size" : null, "retail_facility_code" : "00007"} |[{"status": "active", "time_attr_id": 47939, "status_end_time": "2050-12-31", "status_start_time": "2024-11-24"}]|Testtesttest|2025-04-29 20:18:22.011 +0530|false |

BARSTOW |103200000 | |true |{"channel" : "PFS", "climate" : "CORE", "dc_flag" : false, "zipcode" : "92311", "store_size" : null, "retail_facility_code" : "00248"} |[{"status": "active", "time_attr_id": 47941, "status_end_time": "2050-12-31", "status_start_time": "2025-10-30"}]|Testtesttest|2025-04-29 20:18:22.011 +0530|false |

LAS VEGAS SOUTH |104000000 | |true |{"channel" : "PFS", "climate" : "SOUTH", "dc_flag" : false, "zipcode" : "89123", "store_size" : null, "retail_facility_code" : "00249"} |[{"status": "active", "time_attr_id": 47943, "status_end_time": "2050-12-31", "status_start_time": "2025-10-30"}]|Testtesttest|2025-04-29 20:18:22.011 +0530|false |

NAPA |104300001 | |true |{"channel" : "PFS", "climate" : "CORE", "dc_flag" : false, "zipcode" : "94558", "store_size" : null, "retail_facility_code" : "00230"} |[{"status": "active", "time_attr_id": 47944, "status_end_time": "2050-12-31", "status_start_time": "2025-10-30"}]|Testtesttest|2025-04-29 20:18:22.011 +0530|false |

  

  

  

-- here the updated at column if we see :

2025-05-27 12:37:55.800 +0530

2025-09-05 15:26:11.547 +0530

2025-04-29 20:18:22.011 +0530

2025-04-29 20:18:22.011 +0530

2025-04-29 20:18:22.011 +0530

2025-04-29 20:18:22.011 +0530

2025-04-29 20:18:22.011 +0530

2025-04-29 20:18:22.011 +0530

2025-04-29 20:18:22.011 +0530

2025-04-29 20:18:22.011 +0530

  

  

--So the updated_at should be basically - MM/DD/YYYY

  

--The SP definition :

-- DROP FUNCTION "global".store_status_list(jsonb, jsonb, jsonb, jsonb);

  

CREATE OR REPLACE FUNCTION global.store_status_list(input jsonb, jsonb, jsonb, jsonb)

RETURNS TABLE(store_name character varying, store_code character varying, store_description text, active boolean, attributes json, status_obj json, updated_by text, updated_at timestamp with time zone, is_auto_allocation_active text)

LANGUAGE plpgsql

AS $function$

declare

_query_sm text := '';

_query_sa text := '';

_query_table_filters text := '';

_query_combine text := '';

_where_and_clause text:= '';

_where text:= '';

_final_query text := '';

__attribute_json_build_column_for_filter text[]:= array[]::text[];

_key text;

_value text;

_limit_exists bool := false;

/*

* Function/Procedure name: global.store_status_list

*

* Updated_by Updated_on Purpose

* ---------- ----------- --------

* Akshay Jain 07-06-2022: To accomodate fetching multiple status corresponding to one store as json object.

* changes : 1. fetching all status for some store as jsonb array

* 2. Added extra input param($4) which makes where clause to filter results

* 3. changed return type of status to json and removed start-date and end-date

* Akshay Jain 13-06-2022 Changed return column status to status_obj

* Akshay Jain 04-08-2022 Changed start_time to status_start_time and end_time to status_end_time inside status object

* Akshay Jain 22-08-2022 MIgrated to refcursor based SP

* Akshay Jain 17-05-2023 updated_by, updated_at column handled using join with user_master table

* Chaitanya 15-08-2024 filtered for rl only future records and not past time periods

* Sameer Q 15-10-2024 is_auto_allocation_active added in response and return latest updated_at and updated_by

* Chaitanya 02-12-2024 auto allocation download issue fixed

*/

begin

for _key, _value in SELECT * FROM jsonb_each_text($2) WHERE value IS NOT NULL loop

continue when _key = 'group';

__attribute_json_build_column_for_filter := array_append(array_append(__attribute_json_build_column_for_filter, ''''||_key||''''),'X.'|| _key ||'');

end loop;

_query_sm := 'SELECT * FROM global.store_master' || (global.form_main_table_filters('store_master', $1));

_query_sa := global.form_attribute_table_filters_v2('store_attributes', 'store_code', $2);

_query_table_filters := global.form_table_query($3);

_where_and_clause := global.form_where_clause('varchar', $4::jsonb);

  

SELECT ($3 ->> 'limit') IS NOT NULL INTO _limit_exists;

if _where_and_clause::text ='' then

_where:= 'where 1=1';

else

_where:= 'where status is not null';

end if;

_query_combine := '

select

X.store_name,

X.store_code,

X.store_description,

X.active as active,

json_build_object(' || array_to_string(__attribute_json_build_column_for_filter, ' ,') ||'),

status_obj,

X.updated_by,

X.change_time,

CASE

WHEN ' || _limit_exists || ' THEN

COALESCE(is_auto_allocation_active, true) :: TEXT

ELSE -- If limit does not exist

CASE

WHEN COALESCE(is_auto_allocation_active, true) THEN ''Active''

ELSE ''Inactive''

END

END AS is_auto_allocation_active

from

(

select

sm.*,

pta.status as status_obj,

greatest(pta.change_time, auto_allocation_status.updated_at) as change_time,

CASE

WHEN pta.change_time >= auto_allocation_status.updated_at

THEN pta.updated_by::text

ELSE coalesce(auto_allocation_status.updated_by::text, pta.updated_by::text)

END AS updated_by,

auto_allocation_status.is_auto_allocation_active as is_auto_allocation_active

from (

select

main.store_name,

main.store_description,

main.active as active,

-- main.special_classification as special_classification,

attributes.*

from

(' || _query_sm || ') main

join (' || _query_sa || ') attributes on

main.store_code = attributes.store_code) sm

left join (

select

store_code as store_code,

json_agg(jsonb_build_object(''status_start_time'', CASE

WHEN EXTRACT(YEAR FROM status_start_time::date) IN (2022, 2023) THEN CURRENT_DATE::varchar

ELSE status_start_time::varchar

END, ''status_end_time'', concat(status_end_time)::varchar, ''status'', status, ''time_attr_id'', store_time_attr_id) ORDER BY status_start_time) status, max(updated_by) as updated_by, max(change_time) as change_time

from

(

select store_code, start_time as status_start_time, end_time as status_end_time, attribute_value as status, store_time_attr_id, um.name as updated_by, pg_xact_commit_timestamp(sta.xmin) as change_time

from

"global".store_time_attributes sta left join "global".user_master um on sta.updated_by = um.user_code

where

attribute_name = ''status'' AND end_time >= CURRENT_DATE

) a

' || _where_and_clause || '

group by store_code

) pta

on sm.store_code = pta.store_code

left join(

select

aass.store_code as store_code,

aass.is_auto_allocation_active,

aass.updated_at,

um.name as updated_by

from inventory_smart.auto_allocation_store_status aass

left join "global".user_master um on aass.updated_by = um.user_code

) auto_allocation_status

on sm.store_code = auto_allocation_status.store_code

' || _where || '

) X' || _query_table_filters ;

raise notice '%',_query_combine;

-- return query execute _query_combine;

return query execute _query_combine;

end

$function$

;
```

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
- Configurations are stored here in the form of csv and then the data which 

##### Note : 
- So the backend is mtp (multi-tenant platform) which means single codebase is being used by multiple clients 
- So single change in the codebase can affect all the client in the bakcend 
- Hence , Most of the logic is handled with Store Procedure (SP) inside the mtp-database 
- Each client have their own folder where the configurations data in the form of `csv` is stored , SP in the form of `.sql` and in the SP function we mostly handle the client specific logic. One such example of configuration is : `tenant_attribute_master.csv` where tenant specific configurations are present. 
- Some SP are stored in the `global` schema which means are common for all the clients.
- I work with `ralph_lauren_na` client. 
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
8. I want to change the date format to be in `MM/DD/YYYY` in the updated_at




