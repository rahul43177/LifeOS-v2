#signetindex 
##### The issue description : 
The API for the store search is failing
So I want to run it in the dev , but the backend code is behind , so I connected to the test branch updated code and the database connection is dev 
I am getting the below error 
In dev database I have all the read write powers on the database 
Please find the rootcause and help me resolve it effectively 
##### The API which is causing the issue from the network browser , The CURL :
```
curl --location 'localhost:8000/api/v2/inventory-smart/constraints/store-search-custom' \
--header 'accept: */*' \
--header 'accept-language: en-US,en;q=0.9' \
--header 'application-code: 1' \
--header 'authorization: eyJhbGciOiJSUzI1NiIsImtpZCI6IjdlYTA5ZDA1NzI2MmU2M2U2MmZmNzNmMDNlMDRhZDI5ZDg5Zjg5MmEiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJodHRwczovL3NlY3VyZXRva2VuLmdvb2dsZS5jb20vaW1wYWN0c21hcnQiLCJhdWQiOiJpbXBhY3RzbWFydCIsImF1dGhfdGltZSI6MTc2MDM0MTc1NSwidXNlcl9pZCI6IjA2aVNybUJDU0dVS0tNYXBOWHVJZVB2NVlwVjIiLCJzdWIiOiIwNmlTcm1CQ1NHVUtLTWFwTlh1SWVQdjVZcFYyIiwiaWF0IjoxNzYxNTQ1NDY3LCJleHAiOjE3NjE1NDkwNjcsImVtYWlsIjoicWFAaW1wYWN0YW5hbHl0aWNzLmNvIiwiZW1haWxfdmVyaWZpZWQiOmZhbHNlLCJmaXJlYmFzZSI6eyJpZGVudGl0aWVzIjp7ImVtYWlsIjpbInFhQGltcGFjdGFuYWx5dGljcy5jbyJdfSwic2lnbl9pbl9wcm92aWRlciI6InBhc3N3b3JkIiwidGVuYW50Ijoic2lnbmV0LWRldi1hZGkxZCJ9fQ.ME5FsGNf5CUtw7qHM_SXT4SbXGHLKDAV6IIap7MJui4rjcze2OJR0Skhkc--w5Rnseq858nSRckv0IJU8ebWviM56uI7P_z1s-6JU3jZS6yS505r0zfCjlQAR4gqKaG-I-sLyn-NlzL-EFbduIvvd7ehGu4gN6ADQLPjSaknFWOMaUCR-ZbRVYVYRhJpXv11ZsONZ2LKBsziZRkKGjW8jOvS9QobJgVM3GMPiwoDF9PxNRjmHtS9FwHvNCOLPUgsi2UFa0VCAzMrAKyEhTvVSfh2Cvs9hicM06c3toOyrz_QpaGfotTaL1Q-TGJseJLmP_EW343YEcdfOZyjsIGtTw' \
--header 'content-type: application/json' \
--header 'object-id: undefined' \
--header 'origin: https://signet.test.impactsmartsuite.com' \
--header 'priority: u=1, i' \
--header 'referer: https://signet.test.impactsmartsuite.com/inventory-smart/constraints' \
--header 'screen-name: Inventorysmart Constraints' \
--header 'sec-ch-ua: "Google Chrome";v="141", "Not?A_Brand";v="8", "Chromium";v="141"' \
--header 'sec-ch-ua-mobile: ?0' \
--header 'sec-ch-ua-platform: "Linux"' \
--header 'sec-fetch-dest: empty' \
--header 'sec-fetch-mode: cors' \
--header 'sec-fetch-site: same-origin' \
--header 'time_format: MM-DD-YYYY' \
--header 'time_zone: US/central' \
--header 'user-agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/141.0.0.0 Safari/537.36' \
--header 'Cookie: ph_phc_OBW3O5JZTqdyFZPMcGNdW39hiPYwAJgHbRH6xKOzhf3_posthog=%7B%22distinct_id%22%3A%7B%22email%22%3A%22rohanpowar.v%40impactanalytics.co%22%7D%2C%22%24device_id%22%3A%22019a0f8a-b4cb-757f-a3cf-a3c31ca69faf%22%2C%22%24user_state%22%3A%22identified%22%2C%22%24sesid%22%3A%5B1761203863406%2C%22019a0fee-31b5-7bad-bf43-db2e56228e09%22%2C1761203859830%5D%2C%22%24client_session_props%22%3A%7B%22sessionId%22%3A%22019a0fee-31b5-7bad-bf43-db2e56228e09%22%2C%22props%22%3A%7B%22initialPathName%22%3A%22%2Finventory-smart%2Fconstraints%22%2C%22referringDomain%22%3A%22%24direct%22%7D%7D%2C%22%24session_recording_enabled_server_side%22%3Atrue%2C%22%24console_log_recording_enabled_server_side%22%3Atrue%2C%22%24session_recording_recorder_version_server_side%22%3A%22v2%22%2C%22%24autocapture_disabled_server_side%22%3Afalse%2C%22%24active_feature_flags%22%3A%5B%5D%2C%22%24enabled_feature_flags%22%3A%7B%7D%2C%22%24feature_flag_payloads%22%3A%7B%7D%2C%22%24stored_person_properties%22%3A%7B%22email%22%3A%22rohanpowar.v%40impactanalytics.co%22%2C%22host%22%3A%22signet.uat.impactsmartsuite.com%22%7D%2C%22%24user_id%22%3A%7B%22email%22%3A%22rohanpowar.v%40impactanalytics.co%22%7D%7D; Path=/; ph_phc_jdfaPUcheTjuLkcagCcjqQx4ebTtQLcSiq115zfZQJj_posthog=%7B%22distinct_id%22%3A%7B%22email%22%3A%22qa%40impactanalytics.co%22%7D%2C%22%24device_id%22%3A%22019a0f44-a5fd-7711-a53a-af5a66d09209%22%2C%22%24user_state%22%3A%22identified%22%2C%22%24sesid%22%3A%5B1761548124368%2C%22019a245c-3242-77a4-b453-dcbc1536e6a4%22%2C1761546613314%5D%2C%22%24stored_person_properties%22%3A%7B%22email%22%3A%22qa%40impactanalytics.co%22%2C%22host%22%3A%22signet.test.impactsmartsuite.com%22%7D%2C%22%24user_id%22%3A%7B%22email%22%3A%22qa%40impactanalytics.co%22%7D%2C%22%24client_session_props%22%3A%7B%22sessionId%22%3A%22019a245c-3242-77a4-b453-dcbc1536e6a4%22%2C%22props%22%3A%7B%22initialPathName%22%3A%22%2Finventory-smart%2Fconstraints%22%2C%22referringDomain%22%3A%22%24direct%22%7D%7D%7D' \
--data '{
    "filters": [
        {
            "filter_name": "Sub Sku Division Name",
            "filter_id": "product_channel_name",
            "filter_type": "cascaded",
            "dimension": "product",
            "display_type": "dropdown",
            "check_configuration": [
                {
                    "checkedRows": [
                        "BANTER"
                    ]
                }
            ],
            "values": [
                "BANTER"
            ],
            "attribute_name": "product_channel_name",
            "operator": "in"
        },
        {
            "filter_name": "Department",
            "filter_id": "l0_name",
            "filter_type": "cascaded",
            "dimension": "product",
            "display_type": "dropdown",
            "check_configuration": [
                {
                    "checkedRows": [
                        "551_DIAMOND __ia_char_13 BRIDAL"
                    ]
                }
            ],
            "values": [
                "551_DIAMOND __ia_char_13 BRIDAL"
            ],
            "attribute_name": "l0_name",
            "operator": "in"
        },
        {
            "filter_name": "Channel",
            "filter_id": "channel",
            "filter_type": "cascaded",
            "dimension": "store",
            "display_type": "dropdown",
            "check_configuration": [
                {
                    "checkedRows": [
                        "BANTER"
                    ]
                }
            ],
            "values": [
                "BANTER"
            ],
            "attribute_name": "channel",
            "operator": "in"
        },
        {
            "attribute_name": "channel",
            "operator": "not in",
            "values": [
                "WHS",
                "ECOMM",
                "W",
                "DC",
                "Other",
                "Main DC",
                "ZALES.COM",
                "PEOPLES DC",
                "BANTER Main DC",
                "PEOPLES Main DC",
                "BANTER.COM",
                "BANTER DC",
                "PEOPLES.COM",
                "KAY.COM",
                "JARED.COM",
                "KAY OUTLET.COM",
                "KAY JARED DC",
                "KAY JARED Main DC",
                "KAY JARED W",
                "K/J",
                "K__ia_char_03J",
                "ZPB"
            ],
            "filter_type": "cascaded",
            "dimension": "store",
            "system_filter": true
        }
    ],
    "meta": {
        "search": [],
        "range": [],
        "sort": [],
        "limit": {
            "limit": 10,
            "page": 1
        }
    },
    "popupLink": null
}'
```


##### The logs after calling the API in the local : 
```plain text 
2025-10-27 12:39:55,926 LOCAL ERROR [mtp-core-LOCAL] [logger.py:185] - Exception getting key from redis : Redis Flag is set to 'False' in environ variable | transaction.id=None trace.id=None span.id=None
ERROR:mtp-core-LOCAL:Exception getting key from redis : Redis Flag is set to 'False' in environ variable
ddtracer_context {'trace_id': '68ff1ab3000000003f617f28b56c4876', 'span_id': '9534006831910642991', 'service': 'fastapi', 'version': '', 'env': ''}

================================================================================
[LOCAL DEBUG] execute_query() - STARTING
[LOCAL DEBUG] Tenant: localhost
[LOCAL DEBUG] Query: 
select dc_code, name from "global".distribution_centres dc where is_deleted = false and is_active = true

[LOCAL DEBUG] Return type: dataframe
[LOCAL DEBUG] Using existing connection: False
[LOCAL DEBUG] Timeout: 200
[LOCAL DEBUG] Cursor factory: RealDictCursor
================================================================================
[LOCAL DEBUG] Executing query...

================================================================================
[LOCAL DEBUG] execute_store_procedure() - STARTING
[LOCAL DEBUG] Tenant: localhost
[LOCAL DEBUG] Procedure Name: inventory_smart.constraints_store_list
[LOCAL DEBUG] Input Parameters: ('{"product_channel_name": [{"type": "list", "operator": "in", "values": ["BANTER"]}], "l0_name": [{"type": "list", "operator": "in", "values": ["551_DIAMOND __ia_char_13 BRIDAL"]}]}', '{"channel": [{"type": "list", "operator": "in", "values": ["BANTER"]}, {"type": "list", "operator": "not in", "values": ["WHS", "ECOMM", "W", "DC", "Other", "Main DC", "ZALES.COM", "PEOPLES DC", "BANTER Main DC", "PEOPLES Main DC", "BANTER.COM", "BANTER DC", "PEOPLES.COM", "KAY.COM", "JARED.COM", "KAY OUTLET.COM", "KAY JARED DC", "KAY JARED Main DC", "KAY JARED W", "K/J", "K__ia_char_03J", "ZPB"]}], "is_deleted": [{"type": "custom", "values": "false", "operator": "="}], "active": [{"type": "custom", "values": "true", "operator": "="}]}', '{}', '{"search": [], "sort": [], "range": [], "limit": {"limit": 10, "page": 1, "offset": 0, "sub_offset": 0}, "query_type": "AND"}')
[LOCAL DEBUG] Table Query --------> :
 None
[LOCAL DEBUG] Cursor Based: True
[LOCAL DEBUG] Fetch Rows Count: False
[LOCAL DEBUG] Min Max Columns: None
[LOCAL DEBUG] Distinct Columns: None
[LOCAL DEBUG] Timeout: 200
[LOCAL DEBUG] Cursor Factory: RealDictCursor
================================================================================
[LOCAL DEBUG] Starting transaction (BEGIN)

================================================================================
[LOCAL DEBUG] execute_parameterized_query() - STARTING
[LOCAL DEBUG] Tenant ID: localhost
[LOCAL DEBUG] Query: 
        select
                tc_code
            from
                global.table_configurations
            where
                name = %(table_name)s
        
[LOCAL DEBUG] Parameters: {'table_name': 'inventorysmart_constraints_store_list'}
[LOCAL DEBUG] Return type: dict
[LOCAL DEBUG] Fetch all: True
[LOCAL DEBUG] Timeout: 200
================================================================================
[LOCAL DEBUG] Using RealDictCursor for return type: dict
2025-10-27 12:39:55,931 LOCAL ERROR [mtp-core-LOCAL] [logger.py:185] - Exception getting key from redis : Redis Flag is set to 'False' in environ variable | transaction.id=None trace.id=None span.id=None
ERROR:mtp-core-LOCAL:Exception getting key from redis : Redis Flag is set to 'False' in environ variable
ddtracer_context {'trace_id': '68ff1ab3000000003f617f28b56c4876', 'span_id': '9534006831910642991', 'service': 'fastapi', 'version': '', 'env': ''}
2025-10-27 12:39:55,932 LOCAL ERROR [mtp-core-LOCAL] [logger.py:185] - Exception getting key from redis : Redis Flag is set to 'False' in environ variable | transaction.id=None trace.id=None span.id=None
ERROR:mtp-core-LOCAL:Exception getting key from redis : Redis Flag is set to 'False' in environ variable
ddtracer_context {'trace_id': '68ff1ab3000000003f617f28b56c4876', 'span_id': '9534006831910642991', 'service': 'fastapi', 'version': '', 'env': ''}
2025-10-27 12:39:55,932 LOCAL ERROR [mtp-core-LOCAL] [logger.py:185] - Exception getting key from redis : Redis Flag is set to 'False' in environ variable | transaction.id=None trace.id=None span.id=None
ERROR:mtp-core-LOCAL:Exception getting key from redis : Redis Flag is set to 'False' in environ variable
ddtracer_context {'trace_id': '68ff1ab3000000003f617f28b56c4876', 'span_id': '9534006831910642991', 'service': 'fastapi', 'version': '', 'env': ''}
 Error while pushing  logs to pubsub: 
ERROR:platform-logging: Error while pushing  logs to pubsub: 
[LOCAL DEBUG] Cursor-based SP call with cursor_name: f961302b-ed35-403e-a21f-eddbf38fd114
[LOCAL DEBUG] Final input args: ['f961302b-ed35-403e-a21f-eddbf38fd114', '{"product_channel_name": [{"type": "list", "operator": "in", "values": ["BANTER"]}], "l0_name": [{"type": "list", "operator": "in", "values": ["551_DIAMOND __ia_char_13 BRIDAL"]}]}', '{"channel": [{"type": "list", "operator": "in", "values": ["BANTER"]}, {"type": "list", "operator": "not in", "values": ["WHS", "ECOMM", "W", "DC", "Other", "Main DC", "ZALES.COM", "PEOPLES DC", "BANTER Main DC", "PEOPLES Main DC", "BANTER.COM", "BANTER DC", "PEOPLES.COM", "KAY.COM", "JARED.COM", "KAY OUTLET.COM", "KAY JARED DC", "KAY JARED Main DC", "KAY JARED W", "K/J", "K__ia_char_03J", "ZPB"]}], "is_deleted": [{"type": "custom", "values": "false", "operator": "="}], "active": [{"type": "custom", "values": "true", "operator": "="}]}', '{}', '{"search": [], "sort": [], "range": [], "limit": {"limit": 10, "page": 1, "offset": 0, "sub_offset": 0}, "query_type": "AND"}']
[LOCAL DEBUG] Calling stored procedure: inventory_smart.constraints_store_list
[LOCAL DEBUG] Generated SQL Query: SELECT inventory_smart.constraints_store_list('f961302b-ed35-403e-a21f-eddbf38fd114', '{"product_channel_name": [{"type": "list", "operator": "in", "values": ["BANTER"]}], "l0_name": [{"type": "list", "operator": "in", "values": ["551_DIAMOND __ia_char_13 BRIDAL"]}]}', '{"channel": [{"type": "list", "operator": "in", "values": ["BANTER"]}, {"type": "list", "operator": "not in", "values": ["WHS", "ECOMM", "W", "DC", "Other", "Main DC", "ZALES.COM", "PEOPLES DC", "BANTER Main DC", "PEOPLES Main DC", "BANTER.COM", "BANTER DC", "PEOPLES.COM", "KAY.COM", "JARED.COM", "KAY OUTLET.COM", "KAY JARED DC", "KAY JARED Main DC", "KAY JARED W", "K/J", "K__ia_char_03J", "ZPB"]}], "is_deleted": [{"type": "custom", "values": "false", "operator": "="}], "active": [{"type": "custom", "values": "true", "operator": "="}]}', '{}', '{"search": [], "sort": [], "range": [], "limit": {"limit": 10, "page": 1, "offset": 0, "sub_offset": 0}, "query_type": "AND"}');
[LOCAL DEBUG] Query executed successfully
[LOCAL DEBUG] Fetched 4 rows
[LOCAL DEBUG] Column names: ['dc_code', 'name']
[LOCAL DEBUG] Dataframe shape: (4, 2)
[LOCAL DEBUG] execute_query() - COMPLETED
================================================================================

LocalFileLogger is not available, skipping file log.
WARNING:platform-logging:LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.
WARNING:platform-logging:LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.
WARNING:platform-logging:LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.
WARNING:platform-logging:LocalFileLogger is not available, skipping file log.
/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/aiopg/pool.py:392: ResourceWarning: Invalid transaction status on released connection: 3
  warnings.warn(
2025-10-27 12:39:56,562 LOCAL ERROR [mtp-core-LOCAL] [logger.py:185] - Exception getting key from redis : Redis Flag is set to 'False' in environ variable | transaction.id=None trace.id=None span.id=None
ERROR:mtp-core-LOCAL:Exception getting key from redis : Redis Flag is set to 'False' in environ variable
ddtracer_context {'trace_id': '68ff1ab3000000003f617f28b56c4876', 'span_id': '9534006831910642991', 'service': 'fastapi', 'version': '', 'env': ''}
2025-10-27 12:39:56,630 LOCAL ERROR [mtp-core-LOCAL] [logger.py:185] - Error : API endpoint: '/api/v2/inventory-smart/constraints/store-search-custom' - permission denied for materialized view ph_master
CONTEXT:  SQL statement "
        WITH paf AS (SELECT *, article AS product_code FROM inventory_smart.ph_master ph  WHERE (l0_name::varchar = any('{"551_DIAMOND __ia_char_13 BRIDAL"}'::varchar[])) AND (product_channel_name::varchar = any('{"BANTER"}'::varchar[]))),
        saf AS (SELECT * FROM global.store_attributes_filter saf  WHERE (active::bool = 'true'::bool) AND (channel::varchar = any('{"BANTER"}'::varchar[])) AND NOT(channel::varchar = any('{"WHS", "ECOMM", "W", "DC", "Other", "Main DC", "ZALES.COM", "PEOPLES DC", "BANTER Main DC", "PEOPLES Main DC", "BANTER.COM", "BANTER DC", "PEOPLES.COM", "KAY.COM", "JARED.COM", "KAY OUTLET.COM", "KAY JARED DC", "KAY JARED Main DC", "KAY JARED W", "K/J", "K__ia_char_03J", "ZPB"}'::varchar[])) AND (is_deleted::bool = 'false'::bool)),
        pmps_partition AS (
            SELECT * FROM global.product_mapping_product_store  WHERE (l0_name::varchar = any('{"551_DIAMOND __ia_char_13 BRIDAL"}'::varchar[]))
        ),
        product_master_filters_data AS (
            SELECT 
                pmps_partition.product_code, pmps_partition.mapping_code, pmps_partition.store_code,
                paf.article_status_tag, paf.l0_name, paf.l1_name, paf.l2_name, paf.product_channel_name,
                paf.article, paf.store_pack_size, paf.product_description, paf.planning_ownership,
                paf.merchandise_category, paf.merchandise_brand, paf.metal_color, paf.metal_type,
                paf.sku_grade, paf.drop_ship_ind, paf.dotcom_exclusive,
                saf.store_name, saf.district, saf.dma_name, saf.shop_in_shop, saf.combo_store, saf.channel
            FROM pmps_partition  
            INNER JOIN saf USING(store_code)
            INNER JOIN paf USING (l0_name, product_code)
        ),
        constraint_master_partition AS (
            SELECT * FROM inventory_smart.constraint_master  WHERE (l0_name::varchar = any('{"551_DIAMOND __ia_char_13 BRIDAL"}'::varchar[]))
        ),
        filtered_constraint_master_partition AS (
            SELECT 
                pmps.*, COALESCE(c.updated_by, c.created_by) AS user_code,
                TO_CHAR(COALESCE(c.updated_at, c.created_at) AT TIME ZONE 'EST', 'YYYY-MM-DD HH24:MI:SS') AS updated_at,
                                jsonb_build_array(
                                        jsonb_build_object(
                                                'wos', c.wos::TEXT,
                                                'min_store', c.min_stock::TEXT,
                                                'max_store', c.max_stock::TEXT,
                                                'min_store_sum', c.min_stock::TEXT,
                                                'max_store_sum', c.max_stock::TEXT
                        ) 
                                ) AS stores
            FROM constraint_master_partition c
            JOIN product_master_filters_data pmps USING(product_code, store_code)
            WHERE c.mapping_code IS NOT NULL
        ),
        constraint_data AS (
            SELECT 
                pmps.product_code, pmps.mapping_code, pmps.store_code, pmps.district, pmps.product_channel_name,
                pmps.l0_name, pmps.l1_name, pmps.l2_name, pmps.article, pmps.product_description, pmps.article_status_tag,
                pmps.store_name, pmps.channel, pmps.planning_ownership, pmps.dma_name AS dma, pmps.combo_store AS combo_store_flag,
                pmps.shop_in_shop, pmps.store_pack_size, pmps.metal_color, pmps.metal_type, pmps.merchandise_brand,
                pmps.merchandise_category, pmps.sku_grade, pmps.drop_ship_ind, pmps.dotcom_exclusive, asg.grade AS store_grade,
                CASE 
                    WHEN asg.grade = 'AAA' THEN 1 
                                        WHEN asg.grade = 'AA' THEN 2
                    WHEN asg.grade = 'A' THEN 3 
                                        WHEN asg.grade = 'B' THEN 4
                    WHEN asg.grade = 'C' THEN 5 
                                        WHEN asg.grade = 'D' THEN 6
                    ELSE 11
                END AS store_grade_priority,
                pmps.stores, pmps.user_code, pmps.updated_at
            FROM filtered_constraint_master_partition pmps
            LEFT JOIN inventory_smart.article_store_grade asg USING (store_code, article)
            ORDER BY article ASC, product_code ASC, store_code ASC
        ),
        constraint_data_limit_and_query AS (
            SELECT * FROM constraint_data WHERE TRUE  LIMIT 10 OFFSET 0
        ),
        final AS (
            SELECT cd.*, name AS updated_by FROM constraint_data_limit_and_query cd
            LEFT JOIN global.user_master um USING (user_code)
        )
        SELECT * FROM final;
    "
PL/pgSQL function inventory_smart.constraints_store_list(refcursor,jsonb,jsonb,jsonb,jsonb) line 116 at OPEN
 
Traceback: Traceback (most recent call last):
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/common/inferring_router.py", line 78, in custom_route_handler
    response = await original_route_handler(request)
               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/fastapi/routing.py", line 301, in app
    raw_response = await run_endpoint_function(
                   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/fastapi/routing.py", line 212, in run_endpoint_function
    return await dependant.call(**values)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/common/inferring_router.py", line 271, in wrapper
    return await func(request=request, *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/common/inferring_router.py", line 193, in handle_request
    return await func(request=request, *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/rahulmishra/Desktop/mtp-inventorysmart-backend/backend/inventory_smart/controller/constraints.py", line 96, in constraints_store_list_custom
    ) = await constraints_service.constraints_store_list_with_custom_filters(input_data, request.state.tenant)
        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/rahulmishra/Desktop/mtp-inventorysmart-backend/backend/inventory_smart/service/constraints.py", line 204, in constraints_store_list_with_custom_filters
    all_dc_name, query_result, table_config = await asyncio.gather(
                                              ^^^^^^^^^^^^^^^^^^^^^
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/ddtrace/contrib/internal/asyncio/patch.py", line 56, in traced_coro
    return await coro
           ^^^^^^^^^^
  File "/Users/rahulmishra/Desktop/mtp-inventorysmart-backend/backend/inventory_smart/data/constraints.py", line 87, in constraints_store_list_custom_filters
    result= await execute_store_procedure(
            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/database/utils.py", line 608, in execute_store_procedure
    await cursor.callproc(procedure_name, input_args)
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/aiopg/connection.py", line 465, in callproc
    await self._conn._poll(waiter, timeout)
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/aiopg/connection.py", line 881, in _poll
    await asyncio.wait_for(self._waiter, timeout)
  File "/Users/rahulmishra/.pyenv/versions/3.12.1/lib/python3.12/asyncio/tasks.py", line 520, in wait_for
    return await fut
           ^^^^^^^^^
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/aiopg/connection.py", line 788, in _ready
    state = self._conn.poll()
            ^^^^^^^^^^^^^^^^^
psycopg2.errors.InsufficientPrivilege: permission denied for materialized view ph_master
CONTEXT:  SQL statement "
        WITH paf AS (SELECT *, article AS product_code FROM inventory_smart.ph_master ph  WHERE (l0_name::varchar = any('{"551_DIAMOND __ia_char_13 BRIDAL"}'::varchar[])) AND (product_channel_name::varchar = any('{"BANTER"}'::varchar[]))),
        saf AS (SELECT * FROM global.store_attributes_filter saf  WHERE (active::bool = 'true'::bool) AND (channel::varchar = any('{"BANTER"}'::varchar[])) AND NOT(channel::varchar = any('{"WHS", "ECOMM", "W", "DC", "Other", "Main DC", "ZALES.COM", "PEOPLES DC", "BANTER Main DC", "PEOPLES Main DC", "BANTER.COM", "BANTER DC", "PEOPLES.COM", "KAY.COM", "JARED.COM", "KAY OUTLET.COM", "KAY JARED DC", "KAY JARED Main DC", "KAY JARED W", "K/J", "K__ia_char_03J", "ZPB"}'::varchar[])) AND (is_deleted::bool = 'false'::bool)),
        pmps_partition AS (
            SELECT * FROM global.product_mapping_product_store  WHERE (l0_name::varchar = any('{"551_DIAMOND __ia_char_13 BRIDAL"}'::varchar[]))
        ),
        product_master_filters_data AS (
            SELECT 
                pmps_partition.product_code, pmps_partition.mapping_code, pmps_partition.store_code,
                paf.article_status_tag, paf.l0_name, paf.l1_name, paf.l2_name, paf.product_channel_name,
                paf.article, paf.store_pack_size, paf.product_description, paf.planning_ownership,
                paf.merchandise_category, paf.merchandise_brand, paf.metal_color, paf.metal_type,
                paf.sku_grade, paf.drop_ship_ind, paf.dotcom_exclusive,
                saf.store_name, saf.district, saf.dma_name, saf.shop_in_shop, saf.combo_store, saf.channel
            FROM pmps_partition  
            INNER JOIN saf USING(store_code)
            INNER JOIN paf USING (l0_name, product_code)
        ),
        constraint_master_partition AS (
            SELECT * FROM inventory_smart.constraint_master  WHERE (l0_name::varchar = any('{"551_DIAMOND __ia_char_13 BRIDAL"}'::varchar[]))
        ),
        filtered_constraint_master_partition AS (
            SELECT 
                pmps.*, COALESCE(c.updated_by, c.created_by) AS user_code,
                TO_CHAR(COALESCE(c.updated_at, c.created_at) AT TIME ZONE 'EST', 'YYYY-MM-DD HH24:MI:SS') AS updated_at,
                                jsonb_build_array(
                                        jsonb_build_object(
                                                'wos', c.wos::TEXT,
                                                'min_store', c.min_stock::TEXT,
                                                'max_store', c.max_stock::TEXT,
                                                'min_store_sum', c.min_stock::TEXT,
                                                'max_store_sum', c.max_stock::TEXT
                        ) 
                                ) AS stores
            FROM constraint_master_partition c
            JOIN product_master_filters_data pmps USING(product_code, store_code)
            WHERE c.mapping_code IS NOT NULL
        ),
        constraint_data AS (
            SELECT 
                pmps.product_code, pmps.mapping_code, pmps.store_code, pmps.district, pmps.product_channel_name,
                pmps.l0_name, pmps.l1_name, pmps.l2_name, pmps.article, pmps.product_description, pmps.article_status_tag,
                pmps.store_name, pmps.channel, pmps.planning_ownership, pmps.dma_name AS dma, pmps.combo_store AS combo_store_flag,
                pmps.shop_in_shop, pmps.store_pack_size, pmps.metal_color, pmps.metal_type, pmps.merchandise_brand,
                pmps.merchandise_category, pmps.sku_grade, pmps.drop_ship_ind, pmps.dotcom_exclusive, asg.grade AS store_grade,
                CASE 
                    WHEN asg.grade = 'AAA' THEN 1 
                                        WHEN asg.grade = 'AA' THEN 2
                    WHEN asg.grade = 'A' THEN 3 
                                        WHEN asg.grade = 'B' THEN 4
                    WHEN asg.grade = 'C' THEN 5 
                                        WHEN asg.grade = 'D' THEN 6
                    ELSE 11
                END AS store_grade_priority,
                pmps.stores, pmps.user_code, pmps.updated_at
            FROM filtered_constraint_master_partition pmps
            LEFT JOIN inventory_smart.article_store_grade asg USING (store_code, article)
            ORDER BY article ASC, product_code ASC, store_code ASC
        ),
        constraint_data_limit_and_query AS (
            SELECT * FROM constraint_data WHERE TRUE  LIMIT 10 OFFSET 0
        ),
        final AS (
            SELECT cd.*, name AS updated_by FROM constraint_data_limit_and_query cd
            LEFT JOIN global.user_master um USING (user_code)
        )
        SELECT * FROM final;
    "
PL/pgSQL function inventory_smart.constraints_store_list(refcursor,jsonb,jsonb,jsonb,jsonb) line 116 at OPEN


Payload: {
    "filters": [
        {
            "filter_name": "Sub Sku Division Name",
            "filter_id": "product_channel_name",
            "filter_type": "cascaded",
            "dimension": "product",
            "display_type": "dropdown",
            "check_configuration": [
                {
                    "checkedRows": [
                        "BANTER"
                    ]
                }
            ],
            "values": [
                "BANTER"
            ],
            "attribute_name": "product_channel_name",
            "operator": "in"
        },
        {
            "filter_name": "Department",
            "filter_id": "l0_name",
            "filter_type": "cascaded",
            "dimension": "product",
            "display_type": "dropdown",
            "check_configuration": [
                {
                    "checkedRows": [
                        "551_DIAMOND __ia_char_13 BRIDAL"
                    ]
                }
            ],
            "values": [
                "551_DIAMOND __ia_char_13 BRIDAL"
            ],
            "attribute_name": "l0_name",
            "operator": "in"
        },
        {
            "filter_name": "Channel",
            "filter_id": "channel",
            "filter_type": "cascaded",
            "dimension": "store",
            "display_type": "dropdown",
            "check_configuration": [
                {
                    "checkedRows": [
                        "BANTER"
                    ]
                }
            ],
            "values": [
                "BANTER"
            ],
            "attribute_name": "channel",
            "operator": "in"
        },
        {
            "attribute_name": "channel",
            "operator": "not in",
            "values": [
                "WHS",
                "ECOMM",
                "W",
                "DC",
                "Other",
                "Main DC",
                "ZALES.COM",
                "PEOPLES DC",
                "BANTER Main DC",
                "PEOPLES Main DC",
                "BANTER.COM",
                "BANTER DC",
                "PEOPLES.COM",
                "KAY.COM",
                "JARED.COM",
                "KAY OUTLET.COM",
                "KAY JARED DC",
                "KAY JARED Main DC",
                "KAY JARED W",
                "K/J",
                "K__ia_char_03J",
                "ZPB"
            ],
            "filter_type": "cascaded",
            "dimension": "store",
            "system_filter": true
        }
    ],
    "meta": {
        "search": [],
        "range": [],
        "sort": [],
        "limit": {
            "limit": 10,
            "page": 1
        }
    },
    "popupLink": null
} | transaction.id=None trace.id=None span.id=None
ERROR:mtp-core-LOCAL:Error : API endpoint: '/api/v2/inventory-smart/constraints/store-search-custom' - permission denied for materialized view ph_master
CONTEXT:  SQL statement "
        WITH paf AS (SELECT *, article AS product_code FROM inventory_smart.ph_master ph  WHERE (l0_name::varchar = any('{"551_DIAMOND __ia_char_13 BRIDAL"}'::varchar[])) AND (product_channel_name::varchar = any('{"BANTER"}'::varchar[]))),
        saf AS (SELECT * FROM global.store_attributes_filter saf  WHERE (active::bool = 'true'::bool) AND (channel::varchar = any('{"BANTER"}'::varchar[])) AND NOT(channel::varchar = any('{"WHS", "ECOMM", "W", "DC", "Other", "Main DC", "ZALES.COM", "PEOPLES DC", "BANTER Main DC", "PEOPLES Main DC", "BANTER.COM", "BANTER DC", "PEOPLES.COM", "KAY.COM", "JARED.COM", "KAY OUTLET.COM", "KAY JARED DC", "KAY JARED Main DC", "KAY JARED W", "K/J", "K__ia_char_03J", "ZPB"}'::varchar[])) AND (is_deleted::bool = 'false'::bool)),
        pmps_partition AS (
            SELECT * FROM global.product_mapping_product_store  WHERE (l0_name::varchar = any('{"551_DIAMOND __ia_char_13 BRIDAL"}'::varchar[]))
        ),
        product_master_filters_data AS (
            SELECT 
                pmps_partition.product_code, pmps_partition.mapping_code, pmps_partition.store_code,
                paf.article_status_tag, paf.l0_name, paf.l1_name, paf.l2_name, paf.product_channel_name,
                paf.article, paf.store_pack_size, paf.product_description, paf.planning_ownership,
                paf.merchandise_category, paf.merchandise_brand, paf.metal_color, paf.metal_type,
                paf.sku_grade, paf.drop_ship_ind, paf.dotcom_exclusive,
                saf.store_name, saf.district, saf.dma_name, saf.shop_in_shop, saf.combo_store, saf.channel
            FROM pmps_partition  
            INNER JOIN saf USING(store_code)
            INNER JOIN paf USING (l0_name, product_code)
        ),
        constraint_master_partition AS (
            SELECT * FROM inventory_smart.constraint_master  WHERE (l0_name::varchar = any('{"551_DIAMOND __ia_char_13 BRIDAL"}'::varchar[]))
        ),
        filtered_constraint_master_partition AS (
            SELECT 
                pmps.*, COALESCE(c.updated_by, c.created_by) AS user_code,
                TO_CHAR(COALESCE(c.updated_at, c.created_at) AT TIME ZONE 'EST', 'YYYY-MM-DD HH24:MI:SS') AS updated_at,
                                jsonb_build_array(
                                        jsonb_build_object(
                                                'wos', c.wos::TEXT,
                                                'min_store', c.min_stock::TEXT,
                                                'max_store', c.max_stock::TEXT,
                                                'min_store_sum', c.min_stock::TEXT,
                                                'max_store_sum', c.max_stock::TEXT
                        ) 
                                ) AS stores
            FROM constraint_master_partition c
            JOIN product_master_filters_data pmps USING(product_code, store_code)
            WHERE c.mapping_code IS NOT NULL
        ),
        constraint_data AS (
            SELECT 
                pmps.product_code, pmps.mapping_code, pmps.store_code, pmps.district, pmps.product_channel_name,
                pmps.l0_name, pmps.l1_name, pmps.l2_name, pmps.article, pmps.product_description, pmps.article_status_tag,
                pmps.store_name, pmps.channel, pmps.planning_ownership, pmps.dma_name AS dma, pmps.combo_store AS combo_store_flag,
                pmps.shop_in_shop, pmps.store_pack_size, pmps.metal_color, pmps.metal_type, pmps.merchandise_brand,
                pmps.merchandise_category, pmps.sku_grade, pmps.drop_ship_ind, pmps.dotcom_exclusive, asg.grade AS store_grade,
                CASE 
                    WHEN asg.grade = 'AAA' THEN 1 
                                        WHEN asg.grade = 'AA' THEN 2
                    WHEN asg.grade = 'A' THEN 3 
                                        WHEN asg.grade = 'B' THEN 4
                    WHEN asg.grade = 'C' THEN 5 
                                        WHEN asg.grade = 'D' THEN 6
                    ELSE 11
                END AS store_grade_priority,
                pmps.stores, pmps.user_code, pmps.updated_at
            FROM filtered_constraint_master_partition pmps
            LEFT JOIN inventory_smart.article_store_grade asg USING (store_code, article)
            ORDER BY article ASC, product_code ASC, store_code ASC
        ),
        constraint_data_limit_and_query AS (
            SELECT * FROM constraint_data WHERE TRUE  LIMIT 10 OFFSET 0
        ),
        final AS (
            SELECT cd.*, name AS updated_by FROM constraint_data_limit_and_query cd
            LEFT JOIN global.user_master um USING (user_code)
        )
        SELECT * FROM final;
    "
PL/pgSQL function inventory_smart.constraints_store_list(refcursor,jsonb,jsonb,jsonb,jsonb) line 116 at OPEN
 
Traceback: Traceback (most recent call last):
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/common/inferring_router.py", line 78, in custom_route_handler
    response = await original_route_handler(request)
               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/fastapi/routing.py", line 301, in app
    raw_response = await run_endpoint_function(
                   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/fastapi/routing.py", line 212, in run_endpoint_function
    return await dependant.call(**values)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/common/inferring_router.py", line 271, in wrapper
    return await func(request=request, *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/common/inferring_router.py", line 193, in handle_request
    return await func(request=request, *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/rahulmishra/Desktop/mtp-inventorysmart-backend/backend/inventory_smart/controller/constraints.py", line 96, in constraints_store_list_custom
    ) = await constraints_service.constraints_store_list_with_custom_filters(input_data, request.state.tenant)
        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/rahulmishra/Desktop/mtp-inventorysmart-backend/backend/inventory_smart/service/constraints.py", line 204, in constraints_store_list_with_custom_filters
    all_dc_name, query_result, table_config = await asyncio.gather(
                                              ^^^^^^^^^^^^^^^^^^^^^
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/ddtrace/contrib/internal/asyncio/patch.py", line 56, in traced_coro
    return await coro
           ^^^^^^^^^^
  File "/Users/rahulmishra/Desktop/mtp-inventorysmart-backend/backend/inventory_smart/data/constraints.py", line 87, in constraints_store_list_custom_filters
    result= await execute_store_procedure(
            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/database/utils.py", line 608, in execute_store_procedure
    await cursor.callproc(procedure_name, input_args)
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/aiopg/connection.py", line 465, in callproc
    await self._conn._poll(waiter, timeout)
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/aiopg/connection.py", line 881, in _poll
    await asyncio.wait_for(self._waiter, timeout)
  File "/Users/rahulmishra/.pyenv/versions/3.12.1/lib/python3.12/asyncio/tasks.py", line 520, in wait_for
    return await fut
           ^^^^^^^^^
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/aiopg/connection.py", line 788, in _ready
    state = self._conn.poll()
            ^^^^^^^^^^^^^^^^^
psycopg2.errors.InsufficientPrivilege: permission denied for materialized view ph_master
CONTEXT:  SQL statement "
        WITH paf AS (SELECT *, article AS product_code FROM inventory_smart.ph_master ph  WHERE (l0_name::varchar = any('{"551_DIAMOND __ia_char_13 BRIDAL"}'::varchar[])) AND (product_channel_name::varchar = any('{"BANTER"}'::varchar[]))),
        saf AS (SELECT * FROM global.store_attributes_filter saf  WHERE (active::bool = 'true'::bool) AND (channel::varchar = any('{"BANTER"}'::varchar[])) AND NOT(channel::varchar = any('{"WHS", "ECOMM", "W", "DC", "Other", "Main DC", "ZALES.COM", "PEOPLES DC", "BANTER Main DC", "PEOPLES Main DC", "BANTER.COM", "BANTER DC", "PEOPLES.COM", "KAY.COM", "JARED.COM", "KAY OUTLET.COM", "KAY JARED DC", "KAY JARED Main DC", "KAY JARED W", "K/J", "K__ia_char_03J", "ZPB"}'::varchar[])) AND (is_deleted::bool = 'false'::bool)),
        pmps_partition AS (
            SELECT * FROM global.product_mapping_product_store  WHERE (l0_name::varchar = any('{"551_DIAMOND __ia_char_13 BRIDAL"}'::varchar[]))
        ),
        product_master_filters_data AS (
            SELECT 
                pmps_partition.product_code, pmps_partition.mapping_code, pmps_partition.store_code,
                paf.article_status_tag, paf.l0_name, paf.l1_name, paf.l2_name, paf.product_channel_name,
                paf.article, paf.store_pack_size, paf.product_description, paf.planning_ownership,
                paf.merchandise_category, paf.merchandise_brand, paf.metal_color, paf.metal_type,
                paf.sku_grade, paf.drop_ship_ind, paf.dotcom_exclusive,
                saf.store_name, saf.district, saf.dma_name, saf.shop_in_shop, saf.combo_store, saf.channel
            FROM pmps_partition  
            INNER JOIN saf USING(store_code)
            INNER JOIN paf USING (l0_name, product_code)
        ),
        constraint_master_partition AS (
            SELECT * FROM inventory_smart.constraint_master  WHERE (l0_name::varchar = any('{"551_DIAMOND __ia_char_13 BRIDAL"}'::varchar[]))
        ),
        filtered_constraint_master_partition AS (
            SELECT 
                pmps.*, COALESCE(c.updated_by, c.created_by) AS user_code,
                TO_CHAR(COALESCE(c.updated_at, c.created_at) AT TIME ZONE 'EST', 'YYYY-MM-DD HH24:MI:SS') AS updated_at,
                                jsonb_build_array(
                                        jsonb_build_object(
                                                'wos', c.wos::TEXT,
                                                'min_store', c.min_stock::TEXT,
                                                'max_store', c.max_stock::TEXT,
                                                'min_store_sum', c.min_stock::TEXT,
                                                'max_store_sum', c.max_stock::TEXT
                        ) 
                                ) AS stores
            FROM constraint_master_partition c
            JOIN product_master_filters_data pmps USING(product_code, store_code)
            WHERE c.mapping_code IS NOT NULL
        ),
        constraint_data AS (
            SELECT 
                pmps.product_code, pmps.mapping_code, pmps.store_code, pmps.district, pmps.product_channel_name,
                pmps.l0_name, pmps.l1_name, pmps.l2_name, pmps.article, pmps.product_description, pmps.article_status_tag,
                pmps.store_name, pmps.channel, pmps.planning_ownership, pmps.dma_name AS dma, pmps.combo_store AS combo_store_flag,
                pmps.shop_in_shop, pmps.store_pack_size, pmps.metal_color, pmps.metal_type, pmps.merchandise_brand,
                pmps.merchandise_category, pmps.sku_grade, pmps.drop_ship_ind, pmps.dotcom_exclusive, asg.grade AS store_grade,
                CASE 
                    WHEN asg.grade = 'AAA' THEN 1 
                                        WHEN asg.grade = 'AA' THEN 2
                    WHEN asg.grade = 'A' THEN 3 
                                        WHEN asg.grade = 'B' THEN 4
                    WHEN asg.grade = 'C' THEN 5 
                                        WHEN asg.grade = 'D' THEN 6
                    ELSE 11
                END AS store_grade_priority,
                pmps.stores, pmps.user_code, pmps.updated_at
            FROM filtered_constraint_master_partition pmps
            LEFT JOIN inventory_smart.article_store_grade asg USING (store_code, article)
            ORDER BY article ASC, product_code ASC, store_code ASC
        ),
        constraint_data_limit_and_query AS (
            SELECT * FROM constraint_data WHERE TRUE  LIMIT 10 OFFSET 0
        ),
        final AS (
            SELECT cd.*, name AS updated_by FROM constraint_data_limit_and_query cd
            LEFT JOIN global.user_master um USING (user_code)
        )
        SELECT * FROM final;
    "
PL/pgSQL function inventory_smart.constraints_store_list(refcursor,jsonb,jsonb,jsonb,jsonb) line 116 at OPEN


Payload: {
    "filters": [
        {
            "filter_name": "Sub Sku Division Name",
            "filter_id": "product_channel_name",
            "filter_type": "cascaded",
            "dimension": "product",
            "display_type": "dropdown",
            "check_configuration": [
                {
                    "checkedRows": [
                        "BANTER"
                    ]
                }
            ],
            "values": [
                "BANTER"
            ],
            "attribute_name": "product_channel_name",
            "operator": "in"
        },
        {
            "filter_name": "Department",
            "filter_id": "l0_name",
            "filter_type": "cascaded",
            "dimension": "product",
            "display_type": "dropdown",
            "check_configuration": [
                {
                    "checkedRows": [
                        "551_DIAMOND __ia_char_13 BRIDAL"
                    ]
                }
            ],
            "values": [
                "551_DIAMOND __ia_char_13 BRIDAL"
            ],
            "attribute_name": "l0_name",
            "operator": "in"
        },
        {
            "filter_name": "Channel",
            "filter_id": "channel",
            "filter_type": "cascaded",
            "dimension": "store",
            "display_type": "dropdown",
            "check_configuration": [
                {
                    "checkedRows": [
                        "BANTER"
                    ]
                }
            ],
            "values": [
                "BANTER"
            ],
            "attribute_name": "channel",
            "operator": "in"
        },
        {
            "attribute_name": "channel",
            "operator": "not in",
            "values": [
                "WHS",
                "ECOMM",
                "W",
                "DC",
                "Other",
                "Main DC",
                "ZALES.COM",
                "PEOPLES DC",
                "BANTER Main DC",
                "PEOPLES Main DC",
                "BANTER.COM",
                "BANTER DC",
                "PEOPLES.COM",
                "KAY.COM",
                "JARED.COM",
                "KAY OUTLET.COM",
                "KAY JARED DC",
                "KAY JARED Main DC",
                "KAY JARED W",
                "K/J",
                "K__ia_char_03J",
                "ZPB"
            ],
            "filter_type": "cascaded",
            "dimension": "store",
            "system_filter": true
        }
    ],
    "meta": {
        "search": [],
        "range": [],
        "sort": [],
        "limit": {
            "limit": 10,
            "page": 1
        }
    },
    "popupLink": null
}
ddtracer_context {'trace_id': '68ff1ab3000000003f617f28b56c4876', 'span_id': '9534006831910642991', 'service': 'fastapi', 'version': '', 'env': ''}
INFO:     127.0.0.1:58139 - "POST /api/v2/inventory-smart/constraints/store-search-custom HTTP/1.1" 500 Internal Server Error
Logs http post request response status True and message OK
ERROR:platform-logging:Logs http post request response status True and message OK
LocalFileLogger is not available, skipping file log.
WARNING:platform-logging:LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.
WARNING:platform-logging:LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.
WARNING:platform-logging:LocalFileLogger is not available, skipping file log.
[LOCAL DEBUG] Executing parameterized query...
2025-10-27 12:39:57,649 LOCAL ERROR [mtp-core-LOCAL] [logger.py:185] - Exception getting key from redis : Redis Flag is set to 'False' in environ variable | transaction.id=None trace.id=None span.id=None
ERROR:mtp-core-LOCAL:Exception getting key from redis : Redis Flag is set to 'False' in environ variable
ddtracer_context {'trace_id': '0', 'span_id': '0', 'service': 'uvicorn', 'version': '', 'env': ''}
[LOCAL DEBUG] Query executed successfully
[LOCAL DEBUG] Fetching all results...
[LOCAL DEBUG] Fetched 1 rows
[LOCAL DEBUG] execute_parameterized_query() - COMPLETED
================================================================================


================================================================================
[LOCAL DEBUG] execute_parameterized_query() - STARTING
[LOCAL DEBUG] Tenant ID: localhost
[LOCAL DEBUG] Query: 
        SELECT view_id
        FROM global.default_user_table_view_mapping
        WHERE user_code = %(user_code)s AND tc_code = %(tc_code)s
    
[LOCAL DEBUG] Parameters: {'user_code': 251, 'tc_code': 152}
[LOCAL DEBUG] Return type: dict
[LOCAL DEBUG] Fetch all: True
[LOCAL DEBUG] Timeout: 200
================================================================================
[LOCAL DEBUG] Using RealDictCursor for return type: dict
[LOCAL DEBUG] Executing parameterized query...
2025-10-27 12:39:57,942 LOCAL ERROR [mtp-core-LOCAL] [logger.py:185] - Exception getting key from redis : Redis Flag is set to 'False' in environ variable | transaction.id=None trace.id=None span.id=None
ERROR:mtp-core-LOCAL:Exception getting key from redis : Redis Flag is set to 'False' in environ variable
ddtracer_context {'trace_id': '0', 'span_id': '0', 'service': 'uvicorn', 'version': '', 'env': ''}
2025-10-27 12:39:57,942 LOCAL ERROR [mtp-core-LOCAL] [logger.py:185] - Exception getting key from redis : Redis Flag is set to 'False' in environ variable | transaction.id=None trace.id=None span.id=None
ERROR:mtp-core-LOCAL:Exception getting key from redis : Redis Flag is set to 'False' in environ variable
ddtracer_context {'trace_id': '0', 'span_id': '0', 'service': 'uvicorn', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.
WARNING:platform-logging:LocalFileLogger is not available, skipping file log.
[LOCAL DEBUG] Query executed successfully
[LOCAL DEBUG] Fetching all results...
[LOCAL DEBUG] Fetched 0 rows
[LOCAL DEBUG] execute_parameterized_query() - COMPLETED
================================================================================


================================================================================
[LOCAL DEBUG] execute_parameterized_query() - STARTING
[LOCAL DEBUG] Tenant ID: localhost
[LOCAL DEBUG] Query: 
        SELECT *
        FROM global.table_config_views
         WHERE tc_code=%(tc_code)s AND view_type = 'global' AND is_default = true and is_deleted=false;
    
[LOCAL DEBUG] Parameters: {'tc_code': 152}
[LOCAL DEBUG] Return type: dict
[LOCAL DEBUG] Fetch all: True
[LOCAL DEBUG] Timeout: 200
================================================================================
[LOCAL DEBUG] Using RealDictCursor for return type: dict
[LOCAL DEBUG] Executing parameterized query...
2025-10-27 12:39:58,233 LOCAL ERROR [mtp-core-LOCAL] [logger.py:185] - Exception getting key from redis : Redis Flag is set to 'False' in environ variable | transaction.id=None trace.id=None span.id=None
ERROR:mtp-core-LOCAL:Exception getting key from redis : Redis Flag is set to 'False' in environ variable
ddtracer_context {'trace_id': '0', 'span_id': '0', 'service': 'uvicorn', 'version': '', 'env': ''}
2025-10-27 12:39:58,233 LOCAL ERROR [mtp-core-LOCAL] [logger.py:185] - Exception getting key from redis : Redis Flag is set to 'False' in environ variable | transaction.id=None trace.id=None span.id=None
ERROR:mtp-core-LOCAL:Exception getting key from redis : Redis Flag is set to 'False' in environ variable
ddtracer_context {'trace_id': '0', 'span_id': '0', 'service': 'uvicorn', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.
WARNING:platform-logging:LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.
WARNING:platform-logging:LocalFileLogger is not available, skipping file log.
[LOCAL DEBUG] Query executed successfully
[LOCAL DEBUG] Fetching all results...
[LOCAL DEBUG] Fetched 0 rows
[LOCAL DEBUG] execute_parameterized_query() - COMPLETED
================================================================================


================================================================================
[LOCAL DEBUG] execute_query() - STARTING
[LOCAL DEBUG] Tenant: localhost
[LOCAL DEBUG] Query: SELECT tc.tc_code,user_code, preference from global.table_configurations tc INNER JOIN global.user_preference_table_config uc ON tc.tc_code = uc.tc_code WHERE uc.user_code =251 and tc.name='inventorysmart_constraints_store_list';
[LOCAL DEBUG] Return type: dataframe
[LOCAL DEBUG] Using existing connection: False
[LOCAL DEBUG] Timeout: 200
[LOCAL DEBUG] Cursor factory: RealDictCursor
================================================================================
[LOCAL DEBUG] Executing query...
2025-10-27 12:39:58,545 LOCAL ERROR [mtp-core-LOCAL] [logger.py:185] - Exception getting key from redis : Redis Flag is set to 'False' in environ variable | transaction.id=None trace.id=None span.id=None
ERROR:mtp-core-LOCAL:Exception getting key from redis : Redis Flag is set to 'False' in environ variable
ddtracer_context {'trace_id': '0', 'span_id': '0', 'service': 'uvicorn', 'version': '', 'env': ''}
2025-10-27 12:39:58,546 LOCAL ERROR [mtp-core-LOCAL] [logger.py:185] - Exception getting key from redis : Redis Flag is set to 'False' in environ variable | transaction.id=None trace.id=None span.id=None
ERROR:mtp-core-LOCAL:Exception getting key from redis : Redis Flag is set to 'False' in environ variable
ddtracer_context {'trace_id': '0', 'span_id': '0', 'service': 'uvicorn', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.
WARNING:platform-logging:LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.
WARNING:platform-logging:LocalFileLogger is not available, skipping file log.
[LOCAL DEBUG] Query executed successfully
[LOCAL DEBUG] Fetched 1 rows
[LOCAL DEBUG] Column names: ['tc_code', 'user_code', 'preference']
[LOCAL DEBUG] Dataframe shape: (1, 3)
[LOCAL DEBUG] execute_query() - COMPLETED
================================================================================


================================================================================
[LOCAL DEBUG] execute_parameterized_query() - STARTING
[LOCAL DEBUG] Tenant ID: localhost
[LOCAL DEBUG] Query: 
        select
                tcm.*
        from
            (
            select
                tc_code
            from
                global.table_configurations
            where
                name = %(table_name)s
        ) tc
        join
        "global".table_configurations_mapping tcm 
        on
            tc.tc_code = tcm.tc_code
        order by
            tcm.order_of_display asc;
    
[LOCAL DEBUG] Parameters: {'columns': 'tcm.*', 'table_name': 'inventorysmart_constraints_store_list'}
[LOCAL DEBUG] Return type: dataframe
[LOCAL DEBUG] Fetch all: True
[LOCAL DEBUG] Timeout: 200
================================================================================
[LOCAL DEBUG] Using RealDictCursor for return type: dataframe
[LOCAL DEBUG] Executing parameterized query...
2025-10-27 12:39:58,843 LOCAL ERROR [mtp-core-LOCAL] [logger.py:185] - Exception getting key from redis : Redis Flag is set to 'False' in environ variable | transaction.id=None trace.id=None span.id=None
ERROR:mtp-core-LOCAL:Exception getting key from redis : Redis Flag is set to 'False' in environ variable
ddtracer_context {'trace_id': '0', 'span_id': '0', 'service': 'uvicorn', 'version': '', 'env': ''}
2025-10-27 12:39:58,844 LOCAL ERROR [mtp-core-LOCAL] [logger.py:185] - Exception getting key from redis : Redis Flag is set to 'False' in environ variable | transaction.id=None trace.id=None span.id=None
ERROR:mtp-core-LOCAL:Exception getting key from redis : Redis Flag is set to 'False' in environ variable
ddtracer_context {'trace_id': '0', 'span_id': '0', 'service': 'uvicorn', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.
WARNING:platform-logging:LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.
WARNING:platform-logging:LocalFileLogger is not available, skipping file log.
[LOCAL DEBUG] Query executed successfully
[LOCAL DEBUG] Fetching all results...
[LOCAL DEBUG] Fetched 28 rows
[LOCAL DEBUG] Converting result to DataFrame
[LOCAL DEBUG] DataFrame shape: (28, 23)
[LOCAL DEBUG] execute_parameterized_query() - COMPLETED
================================================================================

2025-10-27 12:39:59,149 LOCAL ERROR [mtp-core-LOCAL] [logger.py:185] - Exception getting key from redis : Redis Flag is set to 'False' in environ variable | transaction.id=None trace.id=None span.id=None
ERROR:mtp-core-LOCAL:Exception getting key from redis : Redis Flag is set to 'False' in environ variable
ddtracer_context {'trace_id': '0', 'span_id': '0', 'service': 'uvicorn', 'version': '', 'env': ''}
/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/core_utils/utils/table.py:371: FutureWarning: Downcasting object dtype arrays on .fillna, .ffill, .bfill is deprecated and will change in a future version. Call result.infer_objects(copy=False) instead. To opt-in to the future behavior, set `pd.set_option('future.no_silent_downcasting', True)`
  results["child_tc_mapping_code"] = results["child_tc_mapping_code"].fillna(0)
LocalFileLogger is not available, skipping file log.
WARNING:platform-logging:LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.
WARNING:platform-logging:LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.
WARNING:platform-logging:LocalFileLogger is not available, skipping file log.
Error uploading (ddog_prof_Exporter_send failed: client error (Connect): tcp connect error: Connection refused (os error 61): Connection refused (os error 61))
Error uploading (ddog_prof_Exporter_send failed: client error (Connect): tcp connect error: Connection refused (os error 61): Connection refused (os error 61))
Error uploading (ddog_prof_Exporter_send failed: client error (Connect): tcp connect error: Connection refused (os error 61): Connection refused (os error 61))

```

##### The Database findings : 

##### Repos to look at : 
###### mtp-database : 
```
/Users/rahulmishra/Desktop/mtp-database
```
- All the stored procedure which are being called in the API is stored here inside the folder of functions 
- Configurations are stored here in the form of csv and then the data which 

###### inventory backed : 
```
/Users/rahulmishra/Desktop/mtp-inventorysmart-backend/backend
```
- Inventory backend code and API is present in the repo 
- There is one utils file which is installed from the toml file : This utils file is for the execution and everything related to database query and formation , you can check this as well : 
	```path title:utils-path
	/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-D0Rf8yfp-py3.12/lib/python3.12/site-packages/database/utils.py
	```

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




