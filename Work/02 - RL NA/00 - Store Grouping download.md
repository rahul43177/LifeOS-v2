### Curl : 
```curl
curl --location 'localhost:8085/api/v2/core/group/store/download' \
--header 'accept: */*' \
--header 'accept-language: en-US,en;q=0.9' \
--header 'application-code: 1' \
--header 'authorization: eyJhbGciOiJSUzI1NiIsImtpZCI6IjdlYTA5ZDA1NzI2MmU2M2U2MmZmNzNmMDNlMDRhZDI5ZDg5Zjg5MmEiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJodHRwczovL3NlY3VyZXRva2VuLmdvb2dsZS5jb20vaW1wYWN0c21hcnQiLCJhdWQiOiJpbXBhY3RzbWFydCIsImF1dGhfdGltZSI6MTc2MTU0NTY4MSwidXNlcl9pZCI6ImExclJjVlNpM0ZnbnBFMk42cEtaR29TZXQyczEiLCJzdWIiOiJhMXJSY1ZTaTNGZ25wRTJONnBLWkdvU2V0MnMxIiwiaWF0IjoxNzYxODkzNjQwLCJleHAiOjE3NjE4OTcyNDAsImVtYWlsIjoicWFAaW1wYWN0YW5hbHl0aWNzLmNvIiwiZW1haWxfdmVyaWZpZWQiOmZhbHNlLCJmaXJlYmFzZSI6eyJpZGVudGl0aWVzIjp7ImVtYWlsIjpbInFhQGltcGFjdGFuYWx5dGljcy5jbyJdfSwic2lnbl9pbl9wcm92aWRlciI6InBhc3N3b3JkIiwidGVuYW50IjoicmFscGgtbGF1cmVuLXVzem9xIn19.tlHhHlagxxFA0LOhQqgF_2_nh6zr8-In6yz9Ykonp5yaN0kJOp0RcmbH8HDjwNNSIB0v8io_S1WvgXtaFmctzon1J3tD0jcYQdBcLJvgsb7olyYZbGvGUPXr15NOfSBoVNELHVAxwwWHUq1IpOoubptmldhUhqMPWz56SOZ4KGo_wVdPUgrYXuFFt_11abDshNgsRj3X1ZDu039CYPQ2Dk0YX2Z7f8I1jUAUaKc7GSbPMpNSIO2h2R_F85OrI72i9lNrIzxd-9qIaFPNo0RTzJHYC21G02chMMyCMxwm69zJqpaESDrwLsxRERH-FZb8RywF1ASMZyWuLOFfbCGhPQ' \
--header 'content-type: application/json' \
--header 'object-id: undefined' \
--header 'origin: https://ralph-lauren.test.impactsmartsuite.com' \
--header 'priority: u=1, i' \
--header 'referer: https://ralph-lauren.test.impactsmartsuite.com/inventory-smart/store-eligibility-grouping' \
--header 'screen-name: Inventorysmart Store Eligibility Group' \
--header 'sec-ch-ua: "Google Chrome";v="141", "Not?A_Brand";v="8", "Chromium";v="141"' \
--header 'sec-ch-ua-mobile: ?0' \
--header 'sec-ch-ua-platform: "macOS"' \
--header 'sec-fetch-dest: empty' \
--header 'sec-fetch-mode: cors' \
--header 'sec-fetch-site: same-origin' \
--header 'time_format: MM-DD-YYYY' \
--header 'time_zone: US/eastern' \
--header 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/141.0.0.0 Safari/537.36' \
--header 'Cookie: ph_phc_OBW3O5JZTqdyFZPMcGNdW39hiPYwAJgHbRH6xKOzhf3_posthog=%7B%22%24user_state%22%3A%22identified%22%2C%22%24sesid%22%3A%5B1760774974689%2C%220199f65d-ece1-7cdf-9698-5778833e83fb%22%2C1760774974689%5D%2C%22distinct_id%22%3A%7B%22email%22%3A%22rahul.mishra%40impactanalytics.co%22%7D%2C%22%24device_id%22%3A%2201993305-282d-7ae4-81a2-05b3cea313f7%22%2C%22%24client_session_props%22%3A%7B%22sessionId%22%3A%220199f65d-ece1-7cdf-9698-5778833e83fb%22%2C%22props%22%3A%7B%22initialPathName%22%3A%22%2Finventory-smart%2Fproduct-profile%22%2C%22referringDomain%22%3A%22%24direct%22%7D%7D%2C%22%24stored_person_properties%22%3A%7B%22email%22%3A%22rahul.mishra%40impactanalytics.co%22%2C%22host%22%3A%22signet.uat.impactsmartsuite.com%22%7D%2C%22%24user_id%22%3A%7B%22email%22%3A%22rahul.mishra%40impactanalytics.co%22%7D%2C%22%24active_feature_flags%22%3A%5B%5D%2C%22%24enabled_feature_flags%22%3A%7B%7D%2C%22%24feature_flag_payloads%22%3A%7B%7D%2C%22%24session_recording_enabled_server_side%22%3Atrue%2C%22%24console_log_recording_enabled_server_side%22%3Atrue%2C%22%24session_recording_recorder_version_server_side%22%3A%22v2%22%2C%22%24autocapture_disabled_server_side%22%3Afalse%7D; Path=/; ph_phc_jdfaPUcheTjuLkcagCcjqQx4ebTtQLcSiq115zfZQJj_posthog=%7B%22%24user_state%22%3A%22identified%22%2C%22%24sesid%22%3A%5B1761893641367%2C%22019a38fd-d924-760f-8746-55063d7d479c%22%2C1761892751652%5D%2C%22distinct_id%22%3A%7B%22email%22%3A%22qa%40impactanalytics.co%22%7D%2C%22%24device_id%22%3A%220199f221-5cdc-7402-9c7e-1fe46c158a65%22%2C%22%24stored_person_properties%22%3A%7B%22email%22%3A%22qa%40impactanalytics.co%22%2C%22host%22%3A%22ralph-lauren.test.impactsmartsuite.com%22%7D%2C%22%24client_session_props%22%3A%7B%22sessionId%22%3A%22019a38fd-d924-760f-8746-55063d7d479c%22%2C%22props%22%3A%7B%22initialPathName%22%3A%22%2Fhome%22%2C%22referringDomain%22%3A%22%24direct%22%7D%7D%2C%22%24user_id%22%3A%7B%22email%22%3A%22qa%40impactanalytics.co%22%7D%7D' \
--data '{
    "total_count": 366,
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


### Logs running in the local 
```

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
2025-10-31 12:30:52,392 LOCAL WARNING [mtp-core-LOCAL] [logger.py:184] - IA-WARNING: Skipping Redis check: exponential backoff active. Retry in 6.1 seconds (attempt 2, backoff: 60.0s) | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '69045ea4000000004af632ff518a3459', 'span_id': '6537687400516671694', 'service': 'fastapi', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.

🔍 [EXECUTABLE SQL FOR DBEAVER - PARAMETERIZED]:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

                SELECT user_code FROM global.user_master WHERE lower(email)= 'qa@impactanalytics.co' AND is_deleted = false
            
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[DB DEBUG] Executing parameterized query...
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

2025-10-31 12:30:54,377 LOCAL WARNING [mtp-core-LOCAL] [logger.py:184] - IA-WARNING: Skipping Redis check: exponential backoff active. Retry in 4.1 seconds (attempt 2, backoff: 60.0s) | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '69045ea4000000004af632ff518a3459', 'span_id': '10098534108644253804', 'service': 'fastapi', 'version': '', 'env': ''}
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

2025-10-31 12:30:55,494 LOCAL WARNING [mtp-core-LOCAL] [logger.py:184] - IA-WARNING: Skipping Redis check: exponential backoff active. Retry in 3.0 seconds (attempt 2, backoff: 60.0s) | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '69045ea4000000004af632ff518a3459', 'span_id': '16464807012561486452', 'service': 'fastapi', 'version': '', 'env': ''}
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

2025-10-31 12:30:55,775 LOCAL WARNING [mtp-core-LOCAL] [logger.py:184] - IA-WARNING: Skipping Redis check: exponential backoff active. Retry in 2.7 seconds (attempt 2, backoff: 60.0s) | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '69045ea4000000004af632ff518a3459', 'span_id': '13216213140490739973', 'service': 'fastapi', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.
[DB DEBUG] Query executed successfully
[DB DEBUG] DataFrame shape: (1, 2)
[DB DEBUG] DataFrame columns: ['name', 'attribute_value']
[DB DEBUG] execute_query() COMPLETED


🔍 [EXECUTABLE SQL FOR DBEAVER - GENERATOR CURSOR]:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CALL global.store_group_list_aggregation_download_main ('44bf3c8e-6080-42cf-b9fe-4f96fe334aa0', '{"channel": [{"type": "list", "operator": "in", "values": ["PFS"]}]}', '{}', '{}', '{"search": [], "range": [], "query_type": "AND", "download_rows_limit_check": false}', '["retail_facility_code", "store_name", "country"]')
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

failed to send, dropping 8 traces to intake at http://localhost:8126/v0.5/traces after 3 retries [3 skipped]
2025-10-31 12:31:17,459 LOCAL ERROR [mtp-core-LOCAL] [logger.py:184] - IA-ERROR: Invalid datetime string: None | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '69045ea4000000004af632ff518a3459', 'span_id': '17916133404602918741', 'service': 'fastapi', 'version': '', 'env': ''}
2025-10-31 12:31:17,530 LOCAL ERROR [mtp-core-LOCAL] [logger.py:184] - IA-ERROR: Invalid datetime string: None | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '69045ea4000000004af632ff518a3459', 'span_id': '17916133404602918741', 'service': 'fastapi', 'version': '', 'env': ''}
2025-10-31 12:31:17,530 LOCAL ERROR [mtp-core-LOCAL] [logger.py:184] - IA-ERROR: Invalid datetime string: None | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '69045ea4000000004af632ff518a3459', 'span_id': '17916133404602918741', 'service': 'fastapi', 'version': '', 'env': ''}
2025-10-31 12:31:17,530 LOCAL ERROR [mtp-core-LOCAL] [logger.py:184] - IA-ERROR: Invalid datetime string: None | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '69045ea4000000004af632ff518a3459', 'span_id': '17916133404602918741', 'service': 'fastapi', 'version': '', 'env': ''}
2025-10-31 12:31:17,530 LOCAL ERROR [mtp-core-LOCAL] [logger.py:184] - IA-ERROR: Invalid datetime string: None | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '69045ea4000000004af632ff518a3459', 'span_id': '17916133404602918741', 'service': 'fastapi', 'version': '', 'env': ''}
2025-10-31 12:31:17,530 LOCAL ERROR [mtp-core-LOCAL] [logger.py:184] - IA-ERROR: Invalid datetime string: None | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '69045ea4000000004af632ff518a3459', 'span_id': '17916133404602918741', 'service': 'fastapi', 'version': '', 'env': ''}
2025-10-31 12:31:17,530 LOCAL ERROR [mtp-core-LOCAL] [logger.py:184] - IA-ERROR: Invalid datetime string: None | transaction.id=None trace.id=None span.id=None

IA-ERROR: Invalid datetime string: None | transaction.id=None trace.id=None span.id=None
2025-10-31 12:31:17,531 LOCAL ERROR [mtp-core-LOCAL] [logger.py:184] - IA-ERROR: Invalid datetime string: None | transaction.id=None 
133404602918741', 'service': 'fastapi', 'version': '', 'env': ''}
2025-10-31 12:31:17,531 LOCAL ERROR [mtp-core-LOCAL] [logger.py:184] - IA-ERROR: Invalid datetime string: None | transaction.id=None trace.id=None span.id=None
INFO:     127.0.0.1:56023 - "POST /api/v2/core/group/store/download HTTP/1.1" 200 OK

```


### Downloaded csv 
![[../../attachments/00 - Store Grouping download - store grouping download.png]]
This is how it looks like in the csv 

### Request from client
So here the client team has asked : 
1. Date should be in MM-DD-YYYY format 
2. Timezone should be EDT

### Request from you 
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
- All the stored procedure which are being called in the API is stored here inside the folder of functions , check with .sql files 
- Configurations are stored here in the form of csv and then the data which 
###### Do : 
1. Please go through the codebase and check the SP from the local logs and all 
2. Please find the problematic code for now 
3. Let's change it to work it according to the client requirements 

Thanks 