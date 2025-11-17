##### The issue description : 
Current state 

| Material Mapping | Product - Store > Mapped stores > Updated at | YYYY-MM-DD and time stamp |
| ---------------- | -------------------------------------------- | ------------------------- |
So basically we need to change the Timestamp for the updated at from YYYY-MM-DD to  ->  `MM / DD / YYYY` 
- NA - EST  -> `US/Eastern` timezone also change in the SP 

in material mapping , if we are clicking on the Mapped Store -> Then there comes a column in the table called updated at , that we need to change from to `MM/DD/YYYY` and the timezone also we need to change in the SP to -> `US/Eastern`


##### The API which is causing the issue from the network browser , The CURL :
```
curl 'https://ralph-lauren.test.impactsmartsuite.com/api/v2/product-mapping/mapped-stores?level=product' \
  -H 'accept: */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'application-code: 1' \
  -H 'authorization: eyJhbGciOiJSUzI1NiIsImtpZCI6IjdlYTA5ZDA1NzI2MmU2M2U2MmZmNzNmMDNlMDRhZDI5ZDg5Zjg5MmEiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJodHRwczovL3NlY3VyZXRva2VuLmdvb2dsZS5jb20vaW1wYWN0c21hcnQiLCJhdWQiOiJpbXBhY3RzbWFydCIsImF1dGhfdGltZSI6MTc2MTU0NTY4MSwidXNlcl9pZCI6ImExclJjVlNpM0ZnbnBFMk42cEtaR29TZXQyczEiLCJzdWIiOiJhMXJSY1ZTaTNGZ25wRTJONnBLWkdvU2V0MnMxIiwiaWF0IjoxNzYxNjQ2NzYxLCJleHAiOjE3NjE2NTAzNjEsImVtYWlsIjoicWFAaW1wYWN0YW5hbHl0aWNzLmNvIiwiZW1haWxfdmVyaWZpZWQiOmZhbHNlLCJmaXJlYmFzZSI6eyJpZGVudGl0aWVzIjp7ImVtYWlsIjpbInFhQGltcGFjdGFuYWx5dGljcy5jbyJdfSwic2lnbl9pbl9wcm92aWRlciI6InBhc3N3b3JkIiwidGVuYW50IjoicmFscGgtbGF1cmVuLXVzem9xIn19.oGSD4Qn2Ux4aVkt8lFKYTKq-UKpMmjjUbZWRLTqinKJnUdF2fg_fjFxx3zIADVN39hFyBfeOxUen9GxWe6b3QKNX1O6h2YtDNtaBUbWXckRWIYJicfX1Zbn7B6mpO_X82lB1VH3guP3NkvrDHyY3R_sYwZZNUYYv7lrQfnFkBPSw_PTYrjpbf_IYmf7wALVEoLV0sf2SshV7w3D3mccvXkTH0OtI61GpT1VEnLpQXwdXEqrrPyH1UOgRv5Yi38I3AmfKA5_LjR2wDgwQgB3HcjEl7q8j9ANQqL0VWhHF4Xj_0i5HqLosZ6OEJ9mxMW_GHMJbmWfh08VJzZttrO2rkw' \
  -H 'content-type: application/json' \
  -b 'ph_phc_OBW3O5JZTqdyFZPMcGNdW39hiPYwAJgHbRH6xKOzhf3_posthog=%7B%22%24user_state%22%3A%22identified%22%2C%22%24sesid%22%3A%5B1760774974689%2C%220199f65d-ece1-7cdf-9698-5778833e83fb%22%2C1760774974689%5D%2C%22distinct_id%22%3A%7B%22email%22%3A%22rahul.mishra%40impactanalytics.co%22%7D%2C%22%24device_id%22%3A%2201993305-282d-7ae4-81a2-05b3cea313f7%22%2C%22%24client_session_props%22%3A%7B%22sessionId%22%3A%220199f65d-ece1-7cdf-9698-5778833e83fb%22%2C%22props%22%3A%7B%22initialPathName%22%3A%22%2Finventory-smart%2Fproduct-profile%22%2C%22referringDomain%22%3A%22%24direct%22%7D%7D%2C%22%24stored_person_properties%22%3A%7B%22email%22%3A%22rahul.mishra%40impactanalytics.co%22%2C%22host%22%3A%22signet.uat.impactsmartsuite.com%22%7D%2C%22%24user_id%22%3A%7B%22email%22%3A%22rahul.mishra%40impactanalytics.co%22%7D%2C%22%24active_feature_flags%22%3A%5B%5D%2C%22%24enabled_feature_flags%22%3A%7B%7D%2C%22%24feature_flag_payloads%22%3A%7B%7D%2C%22%24session_recording_enabled_server_side%22%3Atrue%2C%22%24console_log_recording_enabled_server_side%22%3Atrue%2C%22%24session_recording_recorder_version_server_side%22%3A%22v2%22%2C%22%24autocapture_disabled_server_side%22%3Afalse%7D; Path=/; ph_phc_jdfaPUcheTjuLkcagCcjqQx4ebTtQLcSiq115zfZQJj_posthog=%7B%22%24user_state%22%3A%22identified%22%2C%22%24sesid%22%3A%5B1761641500224%2C%22019a29fc-9009-74ee-b00b-592b35d0f27a%22%2C1761641009161%5D%2C%22distinct_id%22%3A%7B%22email%22%3A%22qa%40impactanalytics.co%22%7D%2C%22%24device_id%22%3A%220199f221-5cdc-7402-9c7e-1fe46c158a65%22%2C%22%24stored_person_properties%22%3A%7B%22email%22%3A%22qa%40impactanalytics.co%22%2C%22host%22%3A%22ralph-lauren.test.impactsmartsuite.com%22%7D%2C%22%24client_session_props%22%3A%7B%22sessionId%22%3A%22019a29fc-9009-74ee-b00b-592b35d0f27a%22%2C%22props%22%3A%7B%22initialPathName%22%3A%22%2Fhome%22%2C%22referringDomain%22%3A%22%24direct%22%7D%7D%2C%22%24user_id%22%3A%7B%22email%22%3A%22qa%40impactanalytics.co%22%7D%7D' \
  -H 'object-id: undefined' \
  -H 'origin: https://ralph-lauren.test.impactsmartsuite.com' \
  -H 'priority: u=1, i' \
  -H 'referer: https://ralph-lauren.test.impactsmartsuite.com/inventory-smart/configuration' \
  -H 'screen-name: Inventorysmart Configurations' \
  -H 'sec-ch-ua: "Google Chrome";v="141", "Not?A_Brand";v="8", "Chromium";v="141"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "macOS"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'time_format: MM-DD-YYYY' \
  -H 'time_zone: US/eastern' \
  -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/141.0.0.0 Safari/537.36' \
  --data-raw '{"filters":[{"attribute_name":"channel","operator":"not in","values":["RLE","RLW","CME","CMS","CMW","CMFS"],"filter_type":"cascaded","dimension":"store","system_filter":true},{"attribute_name":"dc_flag","operator":"not in","values":["true"],"filter_type":"cascaded","dimension":"store","system_filter":true}],"meta":{"search":[],"range":[],"sort":[],"limit":{"limit":10,"page":1}},"product_codes":["100006097322"]}'
```

##### The Response in the network tab response / datadog or grafana 
```plain text
{
    "total": 6,
    "page": 1,
    "count": 6,
    "status": true,
    "data": [
        {
            "store_code": "1479300631",
            "store_name": "ALBERNI STREET",
            "active": true,
            "validity": [
                [
                    "2020-02-02",
                    "2099-02-01"
                ]
            ],
            "updated_by": null,
            "updated_at": "2025-05-06T18:47:09.806622Z",
            "created_type": false,
            "updated_type": false,
            "channel": "RLS",
            "dc_flag": false,
            "s1_name": "CANADA",
            "s2_name": "RLS CANADA",
            "retail_facility_code": "08801"
        },
        {
            "store_code": "1479300922",
            "store_name": "JACKSON STREET",
            "active": true,
            "validity": [
                [
                    "2020-02-02",
                    "2099-02-01"
                ]
            ],
            "updated_by": null,
            "updated_at": "2025-05-06T18:47:09.806622Z",
            "created_type": false,
            "updated_type": false,
            "channel": "RLS",
            "dc_flag": false,
            "s1_name": "UNITED STATES OF AMERICA",
            "s2_name": "RL WEST",
            "retail_facility_code": "08070"
        },
        {
            "store_code": "116000002",
            "store_name": "OTTAWA",
            "active": true,
            "validity": [
                [
                    "2022-12-01",
                    "2050-12-31"
                ]
            ],
            "updated_by": "Testtesttest",
            "updated_at": "2025-08-25T06:12:43.875598Z",
            "created_type": false,
            "updated_type": false,
            "channel": "PFS",
            "dc_flag": false,
            "s1_name": "CANADA",
            "s2_name": "NORTH __ia_char_15CANADA__ia_char_16",
            "retail_facility_code": "00355"
        },
        {
            "store_code": "119600002",
            "store_name": "VANCOUVER",
            "active": true,
            "validity": [
                [
                    "2022-12-01",
                    "2050-12-31"
                ]
            ],
            "updated_by": "Testtesttest",
            "updated_at": "2025-08-25T06:12:43.875598Z",
            "created_type": false,
            "updated_type": false,
            "channel": "PFS",
            "dc_flag": false,
            "s1_name": "CANADA",
            "s2_name": "NORTH __ia_char_15CANADA__ia_char_16",
            "retail_facility_code": "00352"
        },
        {
            "store_code": "1479300963",
            "store_name": "LEGACY WEST",
            "active": true,
            "validity": [
                [
                    "2020-02-02",
                    "2099-02-01"
                ]
            ],
            "updated_by": null,
            "updated_at": "2025-09-19T14:39:49.323674Z",
            "created_type": false,
            "updated_type": false,
            "channel": "RLS",
            "dc_flag": false,
            "s1_name": "UNITED STATES OF AMERICA",
            "s2_name": "RL WEST",
            "retail_facility_code": "08032"
        },
        {
            "store_code": "1479311700",
            "store_name": "SOUTHDALE",
            "active": true,
            "validity": [
                [
                    "2020-02-02",
                    "2099-02-01"
                ]
            ],
            "updated_by": null,
            "updated_at": "2025-09-19T14:39:49.323674Z",
            "created_type": false,
            "updated_type": false,
            "channel": "RLS",
            "dc_flag": false,
            "s1_name": "UNITED STATES OF AMERICA",
            "s2_name": "RL WEST",
            "retail_facility_code": "08078"
        }
    ],
    "message": "Successful",
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
2025-10-28 16:21:15,385 LOCAL ERROR [mtp-core-LOCAL] [logger.py:184] - IA-ERROR: Redis connection error (Worker PID: 8450): Error 8 connecting to redis-11871.c18098.us-central1-1.gcp.cloud.rlrcp.com:11871. nodename nor servname provided, or not known. | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '6900a022000000009aef60c74464759a', 'span_id': '101266230561243212', 'service': 'fastapi', 'version': '', 'env': ''}
2025-10-28 16:21:15,386 LOCAL WARNING [mtp-core-LOCAL] [logger.py:184] - IA-WARNING: Redis failure #1. Next retry in 60.0 seconds (exponential backoff) | transaction.id=None trace.id=None span.id=None
ddtracer_context {'trace_id': '6900a022000000009aef60c74464759a', 'span_id': '101266230561243212', 'service': 'fastapi', 'version': '', 'env': ''}
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
[DB DEBUG] Query: 
with access_role as (select role_code, acm.application_code, filters from global.acl_master acm 
join global.user_access_hierarchy_mapping uahm on acm.acl_code=uahm.acl_code 
where  acm.status 
and uahm.user_code= 155
and acm.application_code = 1
),
screen_name as (
select case when count(module_code) > 0 THEN lower('Inventorysmart Configurations')
else lower('All')
end as screen_name
from global.module_master mm join global.screen_master sm on mm.screen_code = sm.screen_code where lower(sm.screen_name) = lower('Inventorysmart Configurations')
and mm.application_code = 1
),
access_hierarchy_table as (select filters, is_superuser from global.module_master mm 
join global.screen_master sm using (screen_code)
join access_role using (application_code) 
join global.role_action_module_mapping ramm using (role_code)
join ( select screen_name.screen_name from screen_name ) sn
on lower(sm.screen_name) = sn.screen_name
and mm.module_code = any(ramm.module_code)
),
filter_data as (select 
case 
        when is_superuser then '[]' 
        else filters
end as filters
from access_hierarchy_table
group by filters, is_superuser)
select * from filter_data group by filters

==================================================

🔍 [EXECUTABLE SQL FOR DBEAVER - EXECUTE QUERY]:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

with access_role as (select role_code, acm.application_code, filters from global.acl_master acm 
join global.user_access_hierarchy_mapping uahm on acm.acl_code=uahm.acl_code 
where  acm.status 
and uahm.user_code= 155
and acm.application_code = 1
),
screen_name as (
select case when count(module_code) > 0 THEN lower('Inventorysmart Configurations')
else lower('All')
end as screen_name
from global.module_master mm join global.screen_master sm on mm.screen_code = sm.screen_code where lower(sm.screen_name) = lower('Inventorysmart Configurations')
and mm.application_code = 1
),
access_hierarchy_table as (select filters, is_superuser from global.module_master mm 
join global.screen_master sm using (screen_code)
join access_role using (application_code) 
join global.role_action_module_mapping ramm using (role_code)
join ( select screen_name.screen_name from screen_name ) sn
on lower(sm.screen_name) = sn.screen_name
and mm.module_code = any(ramm.module_code)
),
filter_data as (select 
case 
        when is_superuser then '[]' 
        else filters
end as filters
from access_hierarchy_table
group by filters, is_superuser)
select * from filter_data group by filters

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[DB DEBUG] Query executed successfully
[DB DEBUG] DataFrame shape: (1, 1)
[DB DEBUG] DataFrame columns: ['filters']
[DB DEBUG] execute_query() COMPLETED

product_store.py:632: get_stores_mapped_to_products ---- 

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
                    tc.name = 'view_mapped_stores_product_mapping' ) tbl_config
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
                    tc.name = 'view_mapped_stores_product_mapping' ) tbl_config
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
[DB DEBUG] Procedure Name: global.product_store_mapping_stores_validity
[DB DEBUG] Input Parameters: ['{100006097322}', '{"active": [{"type": "list", "operator": "in", "values": [true]}]}', '{"channel": [{"type": "list", "operator": "not in", "values": ["RLE", "RLW", "CME", "CMS", "CMW", "CMFS"]}], "dc_flag": [{"type": "list", "operator": "not in", "values": ["true"]}], "s1_name": [], "s2_name": [], "retail_facility_code": []}', '{"search": [], "sort": [], "range": [], "limit": {"limit": 10, "page": 1, "offset": 0}, "query_type": "AND", "download_rows_limit_check": false}']
[DB DEBUG] Cursor Based: False
[DB DEBUG] Fetch Rows Count: False
[DB DEBUG] Min Max Columns: None
[DB DEBUG] Distinct Columns: None
[DB DEBUG] Table Query: None
[DB DEBUG] Timeout: 200
[DB DEBUG] Application: None
[DB DEBUG] Use Secondary DB: False
[DB DEBUG] Additional kwargs: {}
[DB DEBUG] Generated SP Query: global.product_store_mapping_stores_validity('{100006097322}', '{"active": [{"type": "list", "operator": "in", "values": [true]}]}', '{"channel": [{"type": "list", "operator": "not in", "values": ["RLE", "RLW", "CME", "CMS", "CMW", "CMFS"]}], "dc_flag": [{"type": "list", "operator": "not in", "values": ["true"]}], "s1_name": [], "s2_name": [], "retail_facility_code": []}', '{"search": [], "sort": [], "range": [], "limit": {"limit": 10, "page": 1, "offset": 0}, "query_type": "AND", "download_rows_limit_check": false}')
============================================================

==================================================
[DB DEBUG] get_count_of_sp_call_result() STARTED
[DB DEBUG] Tenant: localhost
[DB DEBUG] Tenant Schema ID: global
[DB DEBUG] SP Name: product_store_mapping_stores_validity
[DB DEBUG] Arguments: ('{100006097322}', '{"active": [{"type": "list", "operator": "in", "values": [true]}]}', '{"channel": [{"type": "list", "operator": "not in", "values": ["RLE", "RLW", "CME", "CMS", "CMW", "CMFS"]}], "dc_flag": [{"type": "list", "operator": "not in", "values": ["true"]}], "s1_name": [], "s2_name": [], "retail_facility_code": []}', '{"search": [], "range": [], "query_type": "AND", "download_rows_limit_check": false}')
[DB DEBUG] Cursor Based: False
[DB DEBUG] Application: None
[DB DEBUG] Use Secondary DB: False
[DB DEBUG] Additional kwargs: {}
==================================================

🔍 [EXECUTABLE SQL FOR DBEAVER]:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
select * from global.product_store_mapping_stores_validity ('{100006097322}', '{"active": [{"type": "list", "operator": "in", "values": [true]}]}', '{"channel": [{"type": "list", "operator": "not in", "values": ["RLE", "RLW", "CME", "CMS", "CMW", "CMFS"]}], "dc_flag": [{"type": "list", "operator": "not in", "values": ["true"]}], "s1_name": [], "s2_name": [], "retail_facility_code": []}', '{"search": [], "sort": [], "range": [], "limit": {"limit": 10, "page": 1, "offset": 0}, "query_type": "AND", "download_rows_limit_check": false}')
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[DB DEBUG] Full Procedure Name: global.product_store_mapping_stores_validity
[DB DEBUG] Count result: 6
[DB DEBUG] get_count_of_sp_call_result() COMPLETED
==================================================

[DB DEBUG] Final result count: 6
[DB DEBUG] Result type: list
[DB DEBUG] execute_store_procedure() COMPLETED
============================================================

INFO:     127.0.0.1:51296 - "POST /api/v2/product-mapping/mapped-stores?level=product HTTP/1.1" 200 OK
```

##### The Database findings : 
###### The SP which is getting called found from the local logs : 
```sql

```

###### The Database findings : 
```sql 
🔍 [EXECUTABLE SQL FOR DBEAVER]:

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

select * from global.product_store_mapping_stores_validity ('{100006097322}', '{"active": [{"type": "list", "operator": "in", "values": [true]}]}', '{"channel": [{"type": "list", "operator": "not in", "values": ["RLE", "RLW", "CME", "CMS", "CMW", "CMFS"]}], "dc_flag": [{"type": "list", "operator": "not in", "values": ["true"]}], "s1_name": [], "s2_name": [], "retail_facility_code": []}', '{"search": [], "sort": [], "range": [], "limit": {"limit": 10, "page": 1, "offset": 0}, "query_type": "AND", "download_rows_limit_check": false}')

  

-- Response

store_code|store_name |attributes |active|validity |updated_by |updated_at |created_type|updated_type|

----------+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------+-------------------------+------------+-----------------------------+------------+------------+

1479300631|ALBERNI STREET|{"store_code" : "1479300631", "channel" : "RLS", "dc_flag" : false, "s1_name" : "CANADA", "s2_name" : "RLS CANADA", "retail_facility_code" : "08801"} |true |{[2020-02-02,2099-02-02)}| |2025-05-07 00:17:09.806 +0530|false |false |

1479300922|JACKSON STREET|{"store_code" : "1479300922", "channel" : "RLS", "dc_flag" : false, "s1_name" : "UNITED STATES OF AMERICA", "s2_name" : "RL WEST", "retail_facility_code" : "08070"} |true |{[2020-02-02,2099-02-02)}| |2025-05-07 00:17:09.806 +0530|false |false |

116000002 |OTTAWA |{"store_code" : "116000002", "channel" : "PFS", "dc_flag" : false, "s1_name" : "CANADA", "s2_name" : "NORTH __ia_char_15CANADA__ia_char_16", "retail_facility_code" : "00355"}|true |{[2022-12-01,2051-01-01)}|Testtesttest|2025-08-25 11:42:43.875 +0530|false |false |

119600002 |VANCOUVER |{"store_code" : "119600002", "channel" : "PFS", "dc_flag" : false, "s1_name" : "CANADA", "s2_name" : "NORTH __ia_char_15CANADA__ia_char_16", "retail_facility_code" : "00352"}|true |{[2022-12-01,2051-01-01)}|Testtesttest|2025-08-25 11:42:43.875 +0530|false |false |

1479300963|LEGACY WEST |{"store_code" : "1479300963", "channel" : "RLS", "dc_flag" : false, "s1_name" : "UNITED STATES OF AMERICA", "s2_name" : "RL WEST", "retail_facility_code" : "08032"} |true |{[2020-02-02,2099-02-02)}| |2025-09-19 20:09:49.323 +0530|false |false |

1479311700|SOUTHDALE |{"store_code" : "1479311700", "channel" : "RLS", "dc_flag" : false, "s1_name" : "UNITED STATES OF AMERICA", "s2_name" : "RL WEST", "retail_facility_code" : "08078"} |true |{[2020-02-02,2099-02-02)}| |2025-09-19 20:09:49.323 +0530|false |false |

  

  

  

-- Output query

WHERE (active::bool = any('{true}'::bool[]))

{channel}

{l0_name,l1_name,l2_name}

here

channel

_attr_cols {channel}

after loop1

here

dc_flag

_attr_cols {channel,dc_flag}

after loop1

here

s1_name

_attr_cols {channel,dc_flag,s1_name}

after loop0

here

s2_name

_attr_cols {channel,dc_flag,s1_name,s2_name}

after loop0

here

retail_facility_code

_attr_cols {channel,dc_flag,s1_name,s2_name,retail_facility_code}

after loop0

combination <NULL>

{channel}

{l0_name,l1_name,l2_name}

_query_pa SELECT channel, dc_flag, s1_name, s2_name, retail_facility_code, store_code FROM "global".store_attributes_filter WHERE NOT(channel::varchar = any('{RLE,RLW,CME,CMS,CMW,CMFS}'::varchar[])) AND NOT(dc_flag::bool = any('{true}'::bool[]))s

, LIMIT 10 OFFSET 0,

SELECT X.store_code, X.store_name, json_build_object('store_code' ,X.store_code ,'channel' ,X.channel ,'dc_flag' ,X.dc_flag ,'s1_name' ,X.s1_name ,'s2_name' ,X.s2_name ,'retail_facility_code' ,X.retail_facility_code), X.active, X.validity , X.updated_by, X.updated_at, X.created_type, X.updated_type FROM (select sm.*,

psm.validity, psm.updated_by, psm.updated_at, psm.created_type, psm.updated_type

from (SELECT main.store_name, main.active, attributes.* FROM (SELECT * FROM "global".store_master WHERE (active::bool = any('{true}'::bool[]))) main JOIN (SELECT channel, dc_flag, s1_name, s2_name, retail_facility_code, store_code FROM "global".store_attributes_filter WHERE NOT(channel::varchar = any('{RLE,RLW,CME,CMS,CMW,CMFS}'::varchar[])) AND NOT(dc_flag::bool = any('{true}'::bool[]))) attributes ON main.store_code = attributes.store_code) sm

left join (

select

product_code,

store_code,

validity,

name as updated_by,

pg_xact_commit_timestamp(pmps.xmin) as updated_at,

uc1.updation_value as created_type,

uc2.updation_value as updated_type

from

"global".product_mapping_product_store pmps

left join global.user_master um on pmps.updated_by = um.user_code

left join global.updation_config uc1 on pmps.creation_source_id = uc1.updation_key

left join global.updation_config uc2 on pmps.current_updation_id = uc2.updation_key

where

product_code = any('{100006097322}'::varchar[])) psm

on

sm.store_code = psm.store_code

where psm.validity is not null ) X LIMIT 10 OFFSET 0

  

-- The SP definition

--liquibase formatted sql

--changeset shreyas.sankpal@impactanalytics.co:product_store_mapping_stores_validity_MTP-52725 runOnChange:true stripComments:false splitStatements:false context:MTP-18485-prod labels:mapping_is_upload_feature

--comment: added created type and updated type for mapping is_upload feature

--rollback: SELECT 1

DROP FUNCTION IF EXISTS global.product_store_mapping_stores_validity(input text[], jsonb, jsonb, jsonb);

CREATE OR REPLACE FUNCTION global.product_store_mapping_stores_validity(input text[], jsonb, jsonb, jsonb)

RETURNS TABLE(store_code character varying, store_name character varying, attributes json, active boolean, validity datemultirange, updated_by character varying, updated_at timestamptz, created_type boolean, updated_type boolean)

LANGUAGE plpgsql

AS $function$

declare

_query_sm text := '';

_query_sa text := '';

_query_table_filters text := '';

_query_combine text;

_store_attribute_json_build_column text[] := array['''store_code''', 'X.store_code']::text[];

_key text;

_value text;

begin

for _key, _value in SELECT * FROM jsonb_each_text($3) WHERE value IS NOT NULL loop

continue when _key = 'group';

_store_attribute_json_build_column := array_append(array_append(_store_attribute_json_build_column, ''''||_key||''''),'X.'|| _key ||'');

end loop;

_query_sm := 'SELECT * FROM "global".store_master' || ("global".form_main_table_filters('store_master', $2));

_query_sa := "global".form_attribute_table_filters_v2('store_attributes', 'store_code', $3);

_query_table_filters := "global".form_table_query($4);

_query_combine := 'SELECT X.store_code, X.store_name, json_build_object(' || array_to_string(_store_attribute_json_build_column, ' ,') ||'), X.active, X.validity , X.updated_by, X.updated_at, X.created_type, X.updated_type FROM (select sm.*,

psm.validity, psm.updated_by, psm.updated_at, psm.created_type, psm.updated_type

from (SELECT main.store_name, main.active, attributes.* FROM (' || _query_sm || ') main JOIN (' || _query_sa || ') attributes ON main.store_code = attributes.store_code) sm

left join (

select

product_code,

store_code,

validity,

name as updated_by,

pg_xact_commit_timestamp(pmps.xmin) as updated_at,

uc1.updation_value as created_type,

uc2.updation_value as updated_type

from

"global".product_mapping_product_store pmps

left join global.user_master um on pmps.updated_by = um.user_code

left join global.updation_config uc1 on pmps.creation_source_id = uc1.updation_key

left join global.updation_config uc2 on pmps.current_updation_id = uc2.updation_key

where

product_code = any(''' || $1::varchar || '''::varchar[])) psm

on

sm.store_code = psm.store_code

where psm.validity is not null ) X ' || _query_table_filters;

raise notice '%', _query_combine;

RETURN QUERY execute _query_combine;

end

$function$

;

  

  

THe file path :

/Users/rahulmishra/Desktop/mtp-database/database/ralph_lauren_na/schemas/global/functions/product_store_mapping_stores_validity.sql
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
- I am right now working with `ralph_lauren_na` client. 
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
8. Please help me to implement this new change and thanks. 


--- 
##### Links 
[[Dev Backup]]