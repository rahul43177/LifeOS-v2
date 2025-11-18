#rlnaindex
##### The issue description : 
Issue :  Grouping > Store grouping > Downloaded file > Updated at and Created at time stamp is coming as 00:00:00

Expected : Its should be same as UI (Only date in MM/DD/YYYY)
Actual : MM/DD/YYYY along with 00:00:00

Present in following screen
Store Group download -  can be removed
Product Group download -  can be removed
Product Mapping UI  - Time should be in EDT
Store mapping UI-  Time should be in EDT





##### The API which is causing the issue from the network browser , The CURL :
```
curl --location 'localhost:8085/api/v2/core/group/store/download' \
--header 'time_zone: US/eastern' \
--header 'sec-ch-ua-platform: "macOS"' \
--header 'Authorization: eyJhbGciOiJSUzI1NiIsImtpZCI6IjM4MDI5MzRmZTBlZWM0NmE1ZWQwMDA2ZDE0YTFiYWIwMWUzNDUwODMiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJodHRwczovL3NlY3VyZXRva2VuLmdvb2dsZS5jb20vaW1wYWN0c21hcnQiLCJhdWQiOiJpbXBhY3RzbWFydCIsImF1dGhfdGltZSI6MTc2MTU0NTY4MSwidXNlcl9pZCI6ImExclJjVlNpM0ZnbnBFMk42cEtaR29TZXQyczEiLCJzdWIiOiJhMXJSY1ZTaTNGZ25wRTJONnBLWkdvU2V0MnMxIiwiaWF0IjoxNzYzNDQ3OTM5LCJleHAiOjE3NjM0NTE1MzksImVtYWlsIjoicWFAaW1wYWN0YW5hbHl0aWNzLmNvIiwiZW1haWxfdmVyaWZpZWQiOmZhbHNlLCJmaXJlYmFzZSI6eyJpZGVudGl0aWVzIjp7ImVtYWlsIjpbInFhQGltcGFjdGFuYWx5dGljcy5jbyJdfSwic2lnbl9pbl9wcm92aWRlciI6InBhc3N3b3JkIiwidGVuYW50IjoicmFscGgtbGF1cmVuLXVzem9xIn19.Ms-cCdIYsnlN6yxVkhfZDtzdp_wtE0Ip9N5cEVw6-xKd8E98Q5R9g6weGkRBrzW0QBfdJ1o1BPV8sp3jsLBOFb5DZ7HsZo39Lm2-0U2fYoeZ61hGqay7nWjY2dFW7mhkCbPI_wTGIOlesM36Qh8FW-xRAYzKHIDdAs5H-FfD31peqwL64jAHlQCJggr8aEhjpoIZpcEZ9ULoVdd57W-N0qu31650Cqc8q63rUN_3gGVw6MEGFFAL-8W-UBKusWtrw1GGg2KOSwgMZ3S0KCnSI4eM6dqWVhty3a6ubDRV0DxHoNxo-Mia0srVULfM45A_gZiPBVBFIAA9Gp2sRojSOw' \
--header 'Referer: https://ralph-lauren.test.impactsmartsuite.com/inventory-smart/store-eligibility-grouping' \
--header 'sec-ch-ua: "Chromium";v="142", "Google Chrome";v="142", "Not_A Brand";v="99"' \
--header 'sec-ch-ua-mobile: ?0' \
--header 'time_format: MM-DD-YYYY' \
--header 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/142.0.0.0 Safari/537.36' \
--header 'object-id: undefined' \
--header 'screen-name: Inventorysmart Store Eligibility Group' \
--header 'Content-Type: application/json' \
--header 'application-code: 1' \
--data '{
    "total_count": 391,
    "columns": [],
    "filters": [
        {
            "filter_name": "Channel",
            "filter_id": "channel",
            "filter_type": "cascaded",
            "dimension": "store",
            "display_type": "dropdown",
            "check_configuration": [
                {
                    "checkedRows": [
                        "PFS"
                    ]
                }
            ],
            "values": [
                "PFS"
            ],
            "attribute_name": "channel",
            "operator": "in",
            "column_name": "channel"
        }
    ],
    "meta": {
        "search": [],
        "range": [],
        "sort": [],
        "limit": {
            "limit": -1,
            "page": 0
        }
    },
    "application_code": 1,
    "params": {
        "level": null
    }
}'
```


##### The logs after calling the API in the local : 
```plain text 
2025-11-18 12:28:58,778 LOCAL INFO [mtp-core-LOCAL] [logger.py:184] - IA-INFO: Created Redis client for worker (PID: 15563) | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '691c1932000000000db5767741caa77d', 'span_id': '768465564589918475', 'service': 'fastapi', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.

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
2025-11-18 12:28:58,886 LOCAL ERROR [mtp-core-LOCAL] [logger.py:184] - IA-ERROR: Redis connection error (Worker PID: 15563): Error 8 connecting to redis-11871.c18098.us-central1-1.gcp.cloud.rlrcp.com:11871. nodename nor servname provided, or not known. | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '691c1932000000000db5767741caa77d', 'span_id': '768465564589918475', 'service': 'fastapi', 'version': '', 'env': ''}
2025-11-18 12:28:58,887 LOCAL WARNING [mtp-core-LOCAL] [logger.py:184] - IA-WARNING: Redis failure #1. Next retry in 60.0 seconds (exponential backoff) | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '691c1932000000000db5767741caa77d', 'span_id': '768465564589918475', 'service': 'fastapi', 'version': '', 'env': ''}
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
[DB DEBUG] Query: select name,attribute_value from global.tenant_attribute_master where application_code = '3' AND name = 'store_group_download' 
==================================================

🔍 [EXECUTABLE SQL FOR DBEAVER - EXECUTE QUERY]:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
select name,attribute_value from global.tenant_attribute_master where application_code = '3' AND name = 'store_group_download' 
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

2025-11-18 12:29:12,973 LOCAL WARNING [mtp-core-LOCAL] [logger.py:184] - IA-WARNING: Skipping Redis check: exponential backoff active. Retry in 45.9 seconds (attempt 2, backoff: 60.0s) | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '691c1932000000000db5767741caa77d', 'span_id': '670613209803632685', 'service': 'fastapi', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.
[DB DEBUG] Query executed successfully
[DB DEBUG] DataFrame shape: (1, 2)
[DB DEBUG] DataFrame columns: ['name', 'attribute_value']
[DB DEBUG] execute_query() COMPLETED


==================================================
[DB DEBUG] execute_parameterized_query() STARTED
[DB DEBUG] Tenant: localhost
[DB DEBUG] Return Type: dataframe
[DB DEBUG] Fetch All: True
[DB DEBUG] Query: 
        SELECT CASE WHEN EXISTS (
            SELECT 1
            FROM information_schema.tables
            WHERE table_schema = 'global'
            AND table_name = 'product_store_attributes_filter'
        ) THEN true ELSE false END AS table_exists;
    
[DB DEBUG] Parameters: {}
[DB DEBUG] Application: None
[DB DEBUG] Use Secondary DB: False
[DB DEBUG] Additional kwargs: {}
==================================================

🔍 [EXECUTABLE SQL FOR DBEAVER - PARAMETERIZED]:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

        SELECT CASE WHEN EXISTS (
            SELECT 1
            FROM information_schema.tables
            WHERE table_schema = 'global'
            AND table_name = 'product_store_attributes_filter'
        ) THEN true ELSE false END AS table_exists;
    
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[DB DEBUG] Executing parameterized query...
[DB DEBUG] DataFrame created with shape: (1, 1)
[DB DEBUG] Records fetched: 1
[DB DEBUG] execute_parameterized_query() COMPLETED


==================================================
[DB DEBUG] execute_parameterized_query() STARTED
[DB DEBUG] Tenant: localhost
[DB DEBUG] Return Type: dataframe
[DB DEBUG] Fetch All: True
[DB DEBUG] Query: 
        select column_name
        from information_schema.columns
        where table_schema  = 'global' and table_name = 'store_groups'
    
[DB DEBUG] Parameters: {}
[DB DEBUG] Application: None
[DB DEBUG] Use Secondary DB: False
[DB DEBUG] Additional kwargs: {}
==================================================

🔍 [EXECUTABLE SQL FOR DBEAVER - PARAMETERIZED]:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

        select column_name
        from information_schema.columns
        where table_schema  = 'global' and table_name = 'store_groups'
    
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[DB DEBUG] Executing parameterized query...
[DB DEBUG] DataFrame created with shape: (12, 1)
[DB DEBUG] Records fetched: 12
[DB DEBUG] execute_parameterized_query() COMPLETED


==================================================
[DB DEBUG] execute_query() STARTED
[DB DEBUG] Tenant: localhost
[DB DEBUG] Return Type: dataframe
[DB DEBUG] Timeout: 200
[DB DEBUG] Connection provided: False
[DB DEBUG] Application: None
[DB DEBUG] Use Secondary DB: False
[DB DEBUG] Query: select name,attribute_value from global.tenant_attribute_master where application_code = '3' AND name = 'tenant_time_config' 
==================================================

🔍 [EXECUTABLE SQL FOR DBEAVER - EXECUTE QUERY]:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
select name,attribute_value from global.tenant_attribute_master where application_code = '3' AND name = 'tenant_time_config' 
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

2025-11-18 12:29:14,252 LOCAL WARNING [mtp-core-LOCAL] [logger.py:184] - IA-WARNING: Skipping Redis check: exponential backoff active. Retry in 44.6 seconds (attempt 2, backoff: 60.0s) | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '691c1932000000000db5767741caa77d', 'span_id': '5945169485961697557', 'service': 'fastapi', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.
[DB DEBUG] Query executed successfully
[DB DEBUG] DataFrame shape: (1, 2)
[DB DEBUG] DataFrame columns: ['name', 'attribute_value']
[DB DEBUG] execute_query() COMPLETED


==================================================
[DB DEBUG] execute_query() STARTED
[DB DEBUG] Tenant: localhost
[DB DEBUG] Return Type: dataframe
[DB DEBUG] Timeout: 200
[DB DEBUG] Connection provided: False
[DB DEBUG] Application: None
[DB DEBUG] Use Secondary DB: False
[DB DEBUG] Query: select name,attribute_value from global.tenant_attribute_master where application_code = '3' AND name = 'tenant_time_config' 
==================================================

🔍 [EXECUTABLE SQL FOR DBEAVER - EXECUTE QUERY]:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
select name,attribute_value from global.tenant_attribute_master where application_code = '3' AND name = 'tenant_time_config' 
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

2025-11-18 12:29:14,683 LOCAL WARNING [mtp-core-LOCAL] [logger.py:184] - IA-WARNING: Skipping Redis check: exponential backoff active. Retry in 44.2 seconds (attempt 2, backoff: 60.0s) | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '691c1932000000000db5767741caa77d', 'span_id': '15461601108624576274', 'service': 'fastapi', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.
[DB DEBUG] Query executed successfully
[DB DEBUG] DataFrame shape: (1, 2)
[DB DEBUG] DataFrame columns: ['name', 'attribute_value']
[DB DEBUG] execute_query() COMPLETED

Store procedure-- global.store_group_list_aggregation_download_main
SP Inputs-- ['{"channel": [{"type": "list", "operator": "in", "values": ["PFS"]}]}', '{}', '{}', '{"search": [], "range": [], "query_type": "AND", "download_rows_limit_check": false}', ['retail_facility_code', 'store_name', 'country']]

🔍 [EXECUTABLE SQL FOR DBEAVER - GENERATOR CURSOR]:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CALL global.store_group_list_aggregation_download_main ('7afb370a-e3c2-48d0-bc2f-e332ddedbe56', '{"channel": [{"type": "list", "operator": "in", "values": ["PFS"]}]}', '{}', '{}', '{"search": [], "range": [], "query_type": "AND", "download_rows_limit_check": false}', '["retail_facility_code", "store_name", "country"]')
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

failed to send, dropping 32 traces to intake at http://localhost:8126/v0.5/traces after 3 retries [1 skipped]

```

##### The Database findings : 
- So I called the SP in the dbeaver which we got from the log , and with that the output query is found.
- Upon calling the output query -- we got the response table 
- I have pasted that response table as well. 
- And in that the created_at and updated_at is perfect and we are not getting timestamp as well. 
```sql
SELECT *
FROM global.store_group_list_aggregation_download_main(
    '7afb370a-e3c2-48d0-bc2f-e332ddedbe56',
    '{"channel": [{"type": "list", "operator": "in", "values": ["PFS"]}]}',
    '{}',
    '{}',
    '{"search": [], "range": [], "query_type": "AND", "download_rows_limit_check": false}',
    '{retail_facility_code,store_name,country}'::text[]
);

--output query 
SELECT *
FROM
  (SELECT sg.name AS name,
          sg.special_classification AS special_classification,
          sg.channel,
          to_char(sg.created_at AT TIME ZONE 'AMERICA/NEW_YORK', 'MM-DD-YYYY') AS created_at,
          to_char(sg.updated_at AT TIME ZONE 'AMERICA/NEW_YORK', 'MM-DD-YYYY') AS updated_at,
          um.name AS created_by,
          umup.name AS updated_by ,
          sgmNew.retail_facility_code AS retail_facility_code,
          sgmNew.store_name AS store_name,
          sgmNew.country AS country,
          (CASE
               WHEN sg.extra IS NOT NULL THEN sg.extra
               ELSE 'FALSE'
           END)::varchar extra
   FROM
     (SELECT sg_code,
             sg.name,
             sg.special_classification,
             sg.created_at,
             sg.updated_at,
             sg.created_by,
             sg.channel,
             sg.updated_by,
             sg.extra->>'is_uploaded' AS extra
      FROM "global".store_groups sg
      WHERE (channel::varchar = any('{"PFS"}'::varchar[]))
        AND (is_deleted::bool = 'false'::bool)) sg
   LEFT JOIN
     (SELECT user_code,
             name
      FROM "global".user_master um
      WHERE (um.is_deleted::bool = 'false'::bool)) um ON sg.created_by = um.user_code
   LEFT JOIN
     (SELECT user_code,
             name
      FROM "global".user_master um
      WHERE (um.is_deleted::bool = 'false'::bool)) umup ON sg.updated_by = umup.user_code
   JOIN
     (SELECT sgm.sg_code
      FROM
        (SELECT *
         FROM global.store_master
         WHERE (active::bool = 'true'::bool)) x
      JOIN
        (SELECT store_code
         FROM "global".store_attributes_filter) y ON x.store_code = y.store_code
      JOIN "global".store_groups_mapping sgm ON x.store_code = sgm.store_code
      GROUP BY sgm.sg_code) f ON sg.sg_code = f.sg_code
   LEFT JOIN
     (SELECT sg_code,
             channel ,
             retail_facility_code,
             store_name,
             country
      FROM "global".store_groups_mapping
      JOIN
        (SELECT channel ,
                retail_facility_code,
                store_name,
                country,
                store_code
         FROM global.store_attributes_filter
         WHERE active) saf USING (store_code)
      WHERE sg_code IS NOT NULL
      GROUP BY sg_code,
               channel ,
               retail_facility_code,
               store_name,
               country) sgmNew ON sg.sg_code = sgmNew.sg_code) X
               
               
               
-- data response 
name       |special_classification|channel|created_at|updated_at|created_by  |updated_by  |retail_facility_code|store_name                         |country                 |extra|
-----------+----------------------+-------+----------+----------+------------+------------+--------------------+-----------------------------------+------------------------+-----+
Default PFS|manual                |PFS    |05-19-2023|11-19-2024|Testtesttest|Testtesttest|00001               |LAKE BUENA VISTA                   |UNITED STATES OF AMERICA|FALSE|
Default PFS|manual                |PFS    |05-19-2023|11-19-2024|Testtesttest|Testtesttest|00003               |FREEPORT                           |UNITED STATES OF AMERICA|FALSE|
Default PFS|manual                |PFS    |05-19-2023|11-19-2024|Testtesttest|Testtesttest|00004               |AURORA FARMS                       |UNITED STATES OF AMERICA|FALSE|
Default PFS|manual                |PFS    |05-19-2023|11-19-2024|Testtesttest|Testtesttest|00005               |DEER PARK                          |UNITED STATES OF AMERICA|FALSE|
Default PFS|manual                |PFS    |05-19-2023|11-19-2024|Testtesttest|Testtesttest|00007               |LEESBURG                           |UNITED STATES OF AMERICA|FALSE|
Default PFS|manual                |PFS    |05-19-2023|11-19-2024|Testtesttest|Testtesttest|00009               |MANCHESTER -CLOSED                 |UNITED STATES OF AMERICA|FALSE|
Default PFS|manual                |PFS    |05-19-2023|11-19-2024|Testtesttest|Testtesttest|00013               |NEW RIVER                          |UNITED STATES OF AMERICA|FALSE|
Default PFS|manual                |PFS    |05-19-2023|11-19-2024|Testtesttest|Testtesttest|00014               |SAWGRASS MILLS                     |UNITED STATES OF AMERICA|FALSE|
Default PFS|manual                |PFS    |05-19-2023|11-19-2024|Testtesttest|Testtesttest|00015               |WOODBURN                           |UNITED STATES OF AMERICA|FALSE|
Default PFS|manual                |PFS    |05-19-2023|11-19-2024|Testtesttest|Testtesttest|00018               |CONCORD MILLS B__ia_char_13T-CLOSED|UNITED STATES OF AMERICA|FALSE|
Default PFS|manual                |PFS    |05-19-2023|11-19-2024|Testtesttest|Testtesttest|00022               |MICHIGAN CITY                      |UNITED STATES OF AMERICA|FALSE|
Default PFS|manual                |PFS    |05-19-2023|11-19-2024|Testtesttest|Testtesttest|00024               |OSAGE BEACH-CLOSED                 |UNITED STATES OF AMERICA|FALSE|




```

###### The SP definition : 
```sql 
--liquibase formatted sql
--changeset rahul.mishra@impactanalytics.co:store_group_list_aggregation_download_main_rl_na runOnChange:true stripComments:false splitStatements:false context:MTP-113784 labels:MTP-113784
--comment: format created_at and updated_at as MM-DD-YYYY in US/Eastern timezone
--rollback: SELECT 1
DROP FUNCTION IF EXISTS "global".store_group_list_aggregation_download_main(input refcursor, jsonb, jsonb, jsonb, jsonb, text[]);

CREATE OR REPLACE FUNCTION global.store_group_list_aggregation_download_main(input refcursor, jsonb, jsonb, jsonb, jsonb, text[])
 RETURNS refcursor
 LANGUAGE plpgsql
AS $function$ 
/*
  * Function/Procedure name: global.store_group_list_aggregation_download_main
  * Created by: Shreyan Haldankar
  * Created at: 28-Feb-2024
  * No of input parameter: 6
  * Parameter Description : $1 = Input Refcursor 
  *                         $2 = JSON for Store Group Filter
  * 						$3 = JSON for Store Master Filter
  *                         $5 = JSON for search, sort and limit clause
  *                         $6 = JSON for store_attribute_filter_columns
  * Purpose: This function been created to get the store group list after select the different filter like store, store_attribute, product and product_attribute
  * Calling Statement:
  *  select * from global.store_group_list_aggregation_download_main(
  * 		'edbc89dd-f873-41d8-8f2c-961a18583ae1',
  * 		'{"channel": [{"type": "list", "operator": "in", "values": ["PFS"]}], "application_code": [{"type": "custom", "operator": "=", "values": 1}]}',
  * 		'{}',
  * 		'{"country": [{"type": "list", "operator": "in", "values": ["CANADA"]}]}',			
  * 		'{"search": [], "sort": [{"column": "updated_at", "order": "desc"}], "range": [], "limit": null, "query_type": "AND"}',
  * 		array['store_code', 'store_name', 'country'])
  * 		
  *
  * if any modification done in same function/procedure please record the changes in below format
  *
  * Updated_by       	Updated_on      Purpose
  * ----------       	-----------     --------
  * Shreyan Haldankar     01-Mar-2024     Add SG Filter Aggregation Download SP
  * Shreyan Haldankar	  26-Mar-2024	  Updated SQL Function to handle store_code if not present (for rl retail_facility_code)
  * Rahul Mishra          4-Nov-2025     Updated the date format and timzone - MM-DD-YYYY and EDT
  */
declare 
	_query_sm text := '';
	_query_sa text := '';
	_query_table_filters text := '';
	_query_combine text := '';
	_main_filter_cnt int := 0;
	_attr_filter_cnt int := 0;
	_filter_con text := ' ';
	_query_sg text;
	_query_sa_where_clause text := '';
	store_attribute_filter_array text[] := $6;
	store_attribute_filter_parameters text := '';
	store_attribute_filter_final_select text := '';
	store_attribute_filter_required_params_array text[];
	store_attribute_filter_required_params text := '';
	val text := '';
	store_code_array_index int;
	_sa_final_select_flag boolean := false;
	_sa_filter_parameters_flag boolean := false;
	_sa_attribute_filter_required_params boolean := false;
	
	begin
		$2 := $2 || ('{"is_deleted": [{"type": "custom", "operator": "=", "values": false}]}'::jsonb);
		$3 := $3 || ('{"active": [{"type": "custom", "operator": "=", "values": true}]}'::jsonb);
		_query_sg := global.form_main_table_filters('store_groups', $2);
		$2 := $2 || ('{"store_name": []}'::jsonb);

		SELECT count(*) INTO _main_filter_cnt from jsonb_each_text($3);
		select count(*) into _attr_filter_cnt from jsonb_each_text($2);
		raise notice '%,%', _main_filter_cnt, _attr_filter_cnt;

		store_attribute_filter_required_params_array := store_attribute_filter_required_params_array || store_attribute_filter_array;
		store_code_array_index := array_position(store_attribute_filter_required_params_array, 'store_code');

		if store_code_array_index is null then
			store_attribute_filter_required_params_array := array_append(store_attribute_filter_required_params_array, 'store_code');
		end if;

		foreach val in array store_attribute_filter_array loop 
			_sa_final_select_flag := true;
			_sa_filter_parameters_flag := true;
			store_attribute_filter_final_select := store_attribute_filter_final_select || 'sgmNew.' || val || ' AS ' || val || ', ';
			store_attribute_filter_parameters := store_attribute_filter_parameters || val || ', ';
		end loop;

		foreach val in array store_attribute_filter_required_params_array loop 
			_sa_attribute_filter_required_params := true;
			store_attribute_filter_required_params := store_attribute_filter_required_params || val || ', ';
		end loop;
		store_attribute_filter_final_select := LEFT(store_attribute_filter_final_select, LENGTH(store_attribute_filter_final_select) - 2 );
		store_attribute_filter_parameters := LEFT(store_attribute_filter_parameters, LENGTH(store_attribute_filter_parameters) - 2);
		store_attribute_filter_required_params := LEFT(store_attribute_filter_required_params, LENGTH(store_attribute_filter_required_params) - 2);
		
		if _sa_final_select_flag = true then
			store_attribute_filter_final_select := ' ,' || store_attribute_filter_final_select;
		end if;
		
		if _sa_filter_parameters_flag = true then
			store_attribute_filter_parameters := ' ,' || store_attribute_filter_parameters;
		end if;
		
		if _sa_attribute_filter_required_params = true then
			store_attribute_filter_required_params := ' ,' || store_attribute_filter_required_params;
		end if;
		
		raise notice '%,%,%', store_attribute_filter_final_select, store_attribute_filter_parameters, store_attribute_filter_required_params;
		_query_table_filters := global.form_table_query($5);

		raise notice ' _main_filter_cnt : %', _main_filter_cnt;
		raise notice ' _attr_filter_cnt : % ', _attr_filter_cnt;

		if _main_filter_cnt = 0 and _attr_filter_cnt != 0 then
			_query_sa := global.form_attribute_table_filters_v2('store_attributes', 'store_code', $4);
			_filter_con := ' JOIN (SELECT sgm.sg_code FROM (' || _query_sa || ') x JOIN "global".store_groups_mapping sgm ON x.store_code = sgm.store_code group by sgm.sg_code) f ON sg.sg_code = f.sg_code ';
		elseif _main_filter_cnt != 0 and _attr_filter_cnt = 0 then
			_query_sm := 'SELECT * FROM global.store_master' || (global.form_main_table_filters('store_master', $3));
			_filter_con := ' JOIN (SELECT sgm.sg_code FROM (' || _query_sm || ') x JOIN "global".store_groups_mapping sgm ON x.store_code = sgm.store_code group by sgm.sg_code) f ON sg.sg_code = f.sg_code ';
		elseif _main_filter_cnt != 0 and _attr_filter_cnt != 0 then
			_query_sm := 'SELECT * FROM global.store_master' || (global.form_main_table_filters('store_master', $3));
			_query_sa := global.form_attribute_table_filters_v2('store_attributes', 'store_code', $4);
			_filter_con := ' JOIN (SELECT sgm.sg_code FROM (' || _query_sm || ') x JOIN (' || _query_sa || ') y on x.store_code = y.store_code join "global".store_groups_mapping sgm ON x.store_code = sgm.store_code group by sgm.sg_code) f ON sg.sg_code = f.sg_code ';
		end if;
		raise notice '_filter_con%', _filter_con;
		--combine query
		_query_combine := 'SELECT * FROM (
				select
				sg.name as name,
				sg.special_classification as special_classification,
				sg.channel,
				to_char(sg.created_at AT TIME ZONE ''America/New_York'', ''MM-DD-YYYY'') as created_at,
				to_char(sg.updated_at AT TIME ZONE ''America/New_York'', ''MM-DD-YYYY'') as updated_at,
				um.name as created_by,
				umup.name as updated_by
				' || store_attribute_filter_final_select || ',
				(case
					when sg.extra is not null then sg.extra
					else ''FALSE''
				end)::varchar extra
			from
			(
				select
					sg_code,
					sg.name,
					sg.special_classification,
					sg.created_at,
					sg.updated_at,
					sg.created_by,
					sg.channel,
					sg.updated_by,
					sg.extra->>''is_uploaded'' as extra
				from
					"global".store_groups sg ' 
						|| _query_sg || '  ) sg
					left join
						(
						select
							user_code,
							name 
						from
							"global".user_master um 
						where
							(
								um.is_deleted::bool = ''false''::bool
							)
						)
						um 
						on sg.created_by = um.user_code 
					left join
						(
						select
							user_code,
							name 
						from
							"global".user_master um 
						where
							(
								um.is_deleted::bool = ''false''::bool
							)
						)
						umup 
						on sg.updated_by = umup.user_code'
						|| _filter_con || '
			
					left join
						(
						select
							sg_code,
							channel
							' || store_attribute_filter_parameters || '
						from
							"global".store_groups_mapping 
							join
								(
									select
										channel
										' || store_attribute_filter_required_params || ' 
									from
										global.store_attributes_filter 
									where
										active 
								)
								saf using (store_code) 
						where
							sg_code is not null 
						group by
							sg_code,
							channel
							'|| store_attribute_filter_parameters ||'
						)
						sgmNew 
						on sg.sg_code = sgmNew.sg_code 
			) X ' || _query_table_filters;
		raise notice '%',_query_combine;
		open $1 for execute _query_combine;
		return $1;
end $function$
;

```
##### Repos to look at : 
###### My findings : 
Store Group Download API Flow Summary
Based on my analysis, here's the complete flow for the /group/store/download API and where the data is being fetched:

API Flow:
Controller Layer (group.py line 922):

download_all_store_groups() method
Processes request body, extracts filters, columns, etc.
Service Layer (group.py line 1405):

get_all_store_group_info() method
When is_download_request = True, calls data access layer
Data Access Layer (group.py line 893):

download_store_groups() method
This is where the actual data fetching happens
Calls execute_store_procedure_generator() with stored procedure: SP_STORE_GROUP_LIST_AGGREGATION_DOWNLOAD
Key Data Fetching Point:
The main data fetching happens in group.py at lines 924-930, where it calls:

Where created_at and updated_at are Handled:
The tenant_datetime_format parameter passed to execute_store_procedure_generator() controls how the datetime fields (including created_at and updated_at) are formatted in the downloaded file.

I've Added Print Statements At:
Controller Layer - Shows incoming request data, user info, filters
Service Layer - Shows processed filters, download params, and result
Data Access Layer - Shows stored procedure details, headers map, datetime format, and download params
These print statements will help you see:

What filters are being applied
What columns are being requested
The tenant datetime format being used
The user making the request
The actual stored procedure being called
All the parameters being passed to the data fetching layer
When you make a request to download store groups, you'll see detailed logging showing exactly how the created_at and updated_at fields are being processed throughout the entire flow.


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
8. And help me fix this issue 




