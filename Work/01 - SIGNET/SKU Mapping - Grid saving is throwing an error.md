#signetindex
##### The issue description : 
- When we are saving something in-line it is failing -- The API is giving me 400 bad request. 

##### The API which is causing the issue from the network browser , The CURL :
```
curl 'https://signet.test.impactsmartsuite.com/api/v2/product-mapping/product-to-store/inline-save?product_level=product' \
  -H 'accept: */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'application-code: 1' \
  -H 'authorization: eyJhbGciOiJSUzI1NiIsImtpZCI6IjM4MDI5MzRmZTBlZWM0NmE1ZWQwMDA2ZDE0YTFiYWIwMWUzNDUwODMiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJodHRwczovL3NlY3VyZXRva2VuLmdvb2dsZS5jb20vaW1wYWN0c21hcnQiLCJhdWQiOiJpbXBhY3RzbWFydCIsImF1dGhfdGltZSI6MTc1NzkzMTg0NCwidXNlcl9pZCI6IjA2aVNybUJDU0dVS0tNYXBOWHVJZVB2NVlwVjIiLCJzdWIiOiIwNmlTcm1CQ1NHVUtLTWFwTlh1SWVQdjVZcFYyIiwiaWF0IjoxNzYzNTM5NDM2LCJleHAiOjE3NjM1NDMwMzYsImVtYWlsIjoicWFAaW1wYWN0YW5hbHl0aWNzLmNvIiwiZW1haWxfdmVyaWZpZWQiOmZhbHNlLCJmaXJlYmFzZSI6eyJpZGVudGl0aWVzIjp7ImVtYWlsIjpbInFhQGltcGFjdGFuYWx5dGljcy5jbyJdfSwic2lnbl9pbl9wcm92aWRlciI6InBhc3N3b3JkIiwidGVuYW50Ijoic2lnbmV0LWRldi1hZGkxZCJ9fQ.O73WIeZiGLicHQ6RyBuOLcaqKEbMSyJT2-zQSU6-2Kz9TdQceCngVuuSgT8YGIH8F3mzimVSwC09ekPXHVP6nM_-OydGE62WI8Blw6F3XKRkbx-K3KNB_ako6XFu4WUUo5QMUDZ17O5OZTuw_rJE3lzp0YrS45kg7Wq7Xw_zqOAH52lq3eeuTsql2Y0Ou2FYJpO_paA6kXM0JoKj7ADIhb3uld43SWYWGBrqQCTAYgQepG9saXf93Y764WXed4uNKd58W6uRL4iEQIegD1njtxE99_GvQMFRAdy64uebqq0QzPTZrSVvjIWI-r9ZV2TPXgvmO_1hiZTe8MCUs3QCFA' \
  -H 'content-type: application/json' \
  -b 'Path=/; ph_phc_OBW3O5JZTqdyFZPMcGNdW39hiPYwAJgHbRH6xKOzhf3_posthog=%7B%22%24user_state%22%3A%22identified%22%2C%22%24sesid%22%3A%5B1763539433111%2C%22019a9b22-96a3-7da9-9800-3ffde4baf0a6%22%2C1763539326627%5D%2C%22distinct_id%22%3A%7B%22email%22%3A%22rahul.mishra%40impactanalytics.co%22%7D%2C%22%24device_id%22%3A%2201993305-282d-7ae4-81a2-05b3cea313f7%22%2C%22%24client_session_props%22%3A%7B%22sessionId%22%3A%22019a9b22-96a3-7da9-9800-3ffde4baf0a6%22%2C%22props%22%3A%7B%22initialPathName%22%3A%22%2Fhome%22%2C%22referringDomain%22%3A%22%24direct%22%7D%7D%2C%22%24stored_person_properties%22%3A%7B%22email%22%3A%22rahul.mishra%40impactanalytics.co%22%2C%22host%22%3A%22signet.uat.impactsmartsuite.com%22%7D%2C%22%24user_id%22%3A%7B%22email%22%3A%22rahul.mishra%40impactanalytics.co%22%7D%2C%22%24active_feature_flags%22%3A%5B%5D%2C%22%24enabled_feature_flags%22%3A%7B%7D%2C%22%24feature_flag_payloads%22%3A%7B%7D%2C%22%24session_recording_enabled_server_side%22%3Atrue%2C%22%24console_log_recording_enabled_server_side%22%3Atrue%2C%22%24session_recording_recorder_version_server_side%22%3A%22v2%22%2C%22%24autocapture_disabled_server_side%22%3Afalse%7D; ph_phc_jdfaPUcheTjuLkcagCcjqQx4ebTtQLcSiq115zfZQJj_posthog=%7B%22distinct_id%22%3A%7B%22email%22%3A%22qa%40impactanalytics.co%22%7D%2C%22%24sesid%22%3A%5B1763539437882%2C%22019a9b22-a1d6-7616-a8f1-f7da63340e55%22%2C1763539329494%5D%2C%22%24epp%22%3Atrue%2C%22%24initial_person_info%22%3A%7B%22r%22%3A%22%24direct%22%2C%22u%22%3A%22https%3A%2F%2Fsignet-replica.impactsmartsuite.com%2Flogin%22%7D%2C%22%24client_session_props%22%3A%7B%22sessionId%22%3A%22019a9b22-a1d6-7616-a8f1-f7da63340e55%22%2C%22props%22%3A%7B%22initialPathName%22%3A%22%2Finventory-smart%2Fstore-eligibility-grouping%22%2C%22referringDomain%22%3A%22%24direct%22%7D%7D%2C%22%24stored_person_properties%22%3A%7B%22email%22%3A%22qa%40impactanalytics.co%22%2C%22host%22%3A%22signet.test.impactsmartsuite.com%22%7D%2C%22%24user_id%22%3A%7B%22email%22%3A%22qa%40impactanalytics.co%22%7D%2C%22%24had_persisted_distinct_id%22%3Atrue%2C%22%24device_id%22%3A%7B%22email%22%3A%22qa%40impactanalytics.co%22%7D%2C%22%24user_state%22%3A%22identified%22%7D' \
  -H 'object-id: undefined' \
  -H 'origin: https://signet.test.impactsmartsuite.com' \
  -H 'priority: u=1, i' \
  -H 'referer: https://signet.test.impactsmartsuite.com/inventory-smart/configuration' \
  -H 'screen-name: Inventorysmart Configurations' \
  -H 'sec-ch-ua: "Chromium";v="142", "Google Chrome";v="142", "Not_A Brand";v="99"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "macOS"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'time_format: MM-DD-YYYY' \
  -H 'time_zone: US/central' \
  -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/142.0.0.0 Safari/537.36' \
  --data-raw '{"stores":[{"store_code":"D.100","include_unmapped":false,"map":true,"select":["16865230"],"unselect":[],"valid_from":"2025-11-19","valid_to":"2050-12-31"}],"products":["16865230"],"action":"conflict_combine"}'
```

##### The Response in the network tab response / datadog or grafana 
```plain text
{
    "total": null,
    "page": null,
    "count": null,
    "status": false,
    "data": [
        "16865230"
    ],
    "message": "Failed to create store-product mappings.",
    "previous": null,
    "next": null,
    "offset": null,
    "sub_offset": null,
    "download_rows": null
}
```


##### The logs after calling the API in the local : 
```plain text 

==================================================
[DB DEBUG] execute_parameterized_query() STARTED
[DB DEBUG] Tenant: signet
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
2025-11-19 13:47:05,532 LOCAL ERROR [mtp-core-LOCAL] [logger.py:184] - IA-ERROR: Redis connection error (Worker PID: 81240): Error 8 connecting to redis-11871.c18098.us-central1-1.gcp.cloud.rlrcp.com:11871. nodename nor servname provided, or not known. | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '691d7d0100000000b9314b3c37747bc8', 'span_id': '8267299641066860464', 'service': 'fastapi', 'version': '', 'env': ''}
2025-11-19 13:47:05,533 LOCAL WARNING [mtp-core-LOCAL] [logger.py:184] - IA-WARNING: Redis failure #1. Next retry in 60.0 seconds (exponential backoff) | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '691d7d0100000000b9314b3c37747bc8', 'span_id': '8267299641066860464', 'service': 'fastapi', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.
[DB DEBUG] Records fetched: 1
[DB DEBUG] execute_parameterized_query() COMPLETED

Error uploading (ddog_prof_Exporter_send failed: client error (Connect): tcp connect error: Connection refused (os error 61): Connection refused (os error 61))
Index(['products', 'valid_from', 'valid_to', 'store_code'], dtype='object')
  product_code  valid_from    valid_to store_code
0     16865230  2025-11-19  2050-12-31      D.100
Error uploading (ddog_prof_Exporter_send failed: client error (Connect): tcp connect error: Connection refused (os error 61): Connection refused (os error 61))
  product_code  valid_from    valid_to store_code
0     16865230  2025-11-19  2050-12-31      D.100
Error uploading (ddog_prof_Exporter_send failed: client error (Connect): tcp connect error: Connection refused (os error 61): Connection refused (os error 61))
Error uploading (ddog_prof_Exporter_send failed: client error (Connect): tcp connect error: Connection refused (os error 61): Connection refused (os error 61))

============================================================
[DB DEBUG] execute_store_procedure() STARTED
[DB DEBUG] Tenant: signet
[DB DEBUG] Procedure Name: global.fetch_l0_information
[DB DEBUG] Input Parameters: ['{16865230}', 'product']
[DB DEBUG] Cursor Based: False
[DB DEBUG] Fetch Rows Count: False
[DB DEBUG] Min Max Columns: None
[DB DEBUG] Distinct Columns: None
[DB DEBUG] Table Query: None
[DB DEBUG] Timeout: 200
[DB DEBUG] Application: None
[DB DEBUG] Use Secondary DB: False
[DB DEBUG] Additional kwargs: {}
[DB DEBUG] Generated SP Query: global.fetch_l0_information('{16865230}', 'product')
============================================================
failed to send, dropping 1 traces to intake at http://localhost:8126/v0.5/traces after 3 retries [1 skipped]

🔍 [EXECUTABLE SQL FOR DBEAVER]:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
select * from global.fetch_l0_information ('{16865230}', 'product')
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[DB DEBUG] Final result count: 1
[DB DEBUG] Result type: list
[DB DEBUG] execute_store_procedure() COMPLETED
============================================================


==================================================
[DB DEBUG] execute_query() STARTED
[DB DEBUG] Tenant: signet
[DB DEBUG] Return Type: dataframe
[DB DEBUG] Timeout: 1000
[DB DEBUG] Connection provided: False
[DB DEBUG] Application: None
[DB DEBUG] Use Secondary DB: False
[DB DEBUG] Query: select product_code, store_code, validity, mapping_code, l0_name, updated_by, mapping_type from global.product_mapping_product_store where product_code in ('16865230') and store_code in ('D.100') LIMIT 70000 OFFSET 0
==================================================

🔍 [EXECUTABLE SQL FOR DBEAVER - EXECUTE QUERY]:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
select product_code, store_code, validity, mapping_code, l0_name, updated_by, mapping_type from global.product_mapping_product_store where product_code in ('16865230') and store_code in ('D.100') LIMIT 70000 OFFSET 0
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[DB DEBUG] Query executed successfully
[DB DEBUG] DataFrame shape: Empty DataFrame
[DB DEBUG] DataFrame columns: No columns
[DB DEBUG] execute_query() COMPLETED


==================================================
[DB DEBUG] run_query_all() STARTED
[DB DEBUG] Tenant: signet
[DB DEBUG] Query: insert into global.product_mapping_product_store (product_code,store_code,validity,mapping_type,is_active,l0_name,updated_by,updated_at,creation_source_id,current_updation_id) values ( '16865230','D.100','{[2025-11-19, 2050-12-31]}','product_store',True,'551_DIAMOND __ia_char_13 BRIDAL',251,'2025-11-19 08:21:17.395298+00:00',1,1 )on conflict(product_code,store_code,l0_name) do update set product_code=EXCLUDED.product_code,store_code=EXCLUDED.store_code,validity=EXCLUDED.validity,mapping_type=EXCLUDED.mapping_type,is_active=EXCLUDED.is_active,l0_name=EXCLUDED.l0_name,updated_by=EXCLUDED.updated_by,updated_at=EXCLUDED.updated_at,current_updation_id=EXCLUDED.current_updation_id returning mapping_code, 'global.product_mapping_product_store'
[DB DEBUG] Output Format: None
[DB DEBUG] Timeout: 1000
[DB DEBUG] Connection provided: False
[DB DEBUG] Application: None
[DB DEBUG] Use Secondary DB: False
[DB DEBUG] Additional kwargs: {}
==================================================

🔍 [EXECUTABLE SQL FOR DBEAVER - RUN QUERY ALL]:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
insert into global.product_mapping_product_store (product_code,store_code,validity,mapping_type,is_active,l0_name,updated_by,updated_at,creation_source_id,current_updation_id) values ( '16865230','D.100','{[2025-11-19, 2050-12-31]}','product_store',True,'551_DIAMOND __ia_char_13 BRIDAL',251,'2025-11-19 08:21:17.395298+00:00',1,1 )on conflict(product_code,store_code,l0_name) do update set product_code=EXCLUDED.product_code,store_code=EXCLUDED.store_code,validity=EXCLUDED.validity,mapping_type=EXCLUDED.mapping_type,is_active=EXCLUDED.is_active,l0_name=EXCLUDED.l0_name,updated_by=EXCLUDED.updated_by,updated_at=EXCLUDED.updated_at,current_updation_id=EXCLUDED.current_updation_id returning mapping_code, 'global.product_mapping_product_store'
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

2025-11-19 13:51:18,237 LOCAL WARNING [mtp-core-LOCAL] [logger.py:184] - IA-WARNING: Following product codes failed due to respective reason in product to store mapping : {"['16865230']": NotNullViolation('null value in column "mapping_code" of relation "product_mapping_product_store_551_diamond__ia_char_13bridal" violates not-null constraint\nDETAIL:  Failing row contains (null, product_store, 551_DIAMOND __ia_char_13 BRIDAL, 16865230, D.100, t, {[2025-11-19,2051-01-01)}, 251, 0, 2025-11-19 08:21:17.395298+00, 1, 1).\n')} | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '691d7d0100000000b9314b3c37747bc8', 'span_id': '17685692832557518730', 'service': 'fastapi', 'version': '', 'env': ''}
2025-11-19 13:51:18,237 LOCAL INFO [mtp-core-LOCAL] [logger.py:184] - IA-INFO: create_product_store_map_inline_save() - User-qa@impactanalytics.co , Payload-{"action": "conflict_combine", "product_store": [{"store_code": "D.100", "include_unmapped": false, "map": true, "select": ["16865230"], "unselect": [], "valid_from": "2025-11-19", "valid_to": "2050-12-31", "products": ["16865230"]}]}  | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '691d7d0100000000b9314b3c37747bc8', 'span_id': '17685692832557518730', 'service': 'fastapi', 'version': '', 'env': ''}
LocalFileLogger is not available, skipping file log.
LocalFileLogger is not available, skipping file log.
Traceback (most recent call last):
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-zfxLRh0v-py3.12/lib/python3.12/site-packages/google/api_core/grpc_helpers_async.py", line 86, in __await__
    response = yield from self._call.__await__()
               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-zfxLRh0v-py3.12/lib/python3.12/site-packages/grpc/aio/_interceptor.py", line 474, in __await__
    response = yield from call.__await__()
               ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-zfxLRh0v-py3.12/lib/python3.12/site-packages/grpc/aio/_call.py", line 328, in __await__
    raise _create_rpc_error(
grpc.aio._call.AioRpcError: <AioRpcError of RPC that terminated with:
        status = StatusCode.DEADLINE_EXCEEDED
        details = "Deadline Exceeded"
        debug_error_string = "UNKNOWN:Error received from peer  {grpc_status:4, grpc_message:"Deadline Exceeded"}"
>

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-zfxLRh0v-py3.12/lib/python3.12/site-packages/common/cloud_task.py", line 313, in create_http_request_task
    response = await task_queue_client.create_task(
               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-zfxLRh0v-py3.12/lib/python3.12/site-packages/google/cloud/tasks_v2/services/cloud_tasks/async_client.py", line 2096, in create_task
    response = await rpc(
               ^^^^^^^^^^
  File "/Users/rahulmishra/Library/Caches/pypoetry/virtualenvs/backend-zfxLRh0v-py3.12/lib/python3.12/site-packages/google/api_core/grpc_helpers_async.py", line 89, in __await__
    raise exceptions.from_grpc_error(rpc_error) from rpc_error
google.api_core.exceptions.DeadlineExceeded: 504 Deadline Exceeded
INFO:     127.0.0.1:49955 - "POST /api/v2/product-mapping/product-to-store/inline-save?product_level=product HTTP/1.1" 400 Bad Request
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
- Configurations are stored here in the form of csv. 
- The data for each client is seperated by the folder for example right now we are working with the `signet` , so functions and the config for this client is stored in here 
- If some function is not present then it must be taking from the : `/Users/rahulmishra/Desktop/mtp-database/database/schemas/global/functions` -> common for everyone 
- So if we want to make something client specific we can take it from - `/Users/rahulmishra/Desktop/mtp-database/database/schemas/global/functions` and create the function inside the client or tenant folder

- So the backend is mtp (multi-tenant platform) which means single codebase is being used by multiple clients 
##### Note : 
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


---
##### Further links 
[[SKU Mapping - Inline Save Failure Root cause ]]

