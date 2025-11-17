#### Initial rough writing 
|                  |                                              |                           |
| ---------------- | -------------------------------------------- | ------------------------- |
| Material Mapping | Product - Store > Mapped stores > Updated at | YYYY-MM-DD and time stamp |
current yyyy 
everywhere -> right now -> `MM / DD / YYYY`  -> NA and APAC  
- NA - EST  -> `US/Eastern`
 - APAC - HKT 
 -
EMEA -> `DD / MM / YYYY` 
- EMEA -utc 

|                  |
| ---------------- |
|                  |
| Material Mapping |
|                  |
| Store Status     |
| Store Mapping    |

- [ ] Cross verify all core screens once 
- [ ] frontend mapping - if hardcoded ? 

Material profile -> Handled in backend by Surya


Format -> 
`Formatter` and `extra` 


#### Bug Description with image of the UI :
The place -> 
Configurations -> Material Mapping -> Product - store -> View Mapped Stores 
- This is how the UI looks like 
- ![[../../attachments/00 - Frontend Date format Material Mapping - mapped store UI.png]]
- Here we have Update at column , which is showing the date like -> YYYY-MM-DD:hh:mm 
- But in the API response and the SP I have changed , and I am sending it like : ` "updated_at": "05/06/2025"`


#### The API which are getting called related to the bug : 
```curl
curl 'https://ralph-lauren.test.impactsmartsuite.com/api/v2/product-mapping/mapped-stores?level=product' \
  -H 'accept: */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'application-code: 1' \
  -H 'authorization: eyJhbGciOiJSUzI1NiIsImtpZCI6IjdlYTA5ZDA1NzI2MmU2M2U2MmZmNzNmMDNlMDRhZDI5ZDg5Zjg5MmEiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJodHRwczovL3NlY3VyZXRva2VuLmdvb2dsZS5jb20vaW1wYWN0c21hcnQiLCJhdWQiOiJpbXBhY3RzbWFydCIsImF1dGhfdGltZSI6MTc2MTU0NTgyMCwidXNlcl9pZCI6ImExclJjVlNpM0ZnbnBFMk42cEtaR29TZXQyczEiLCJzdWIiOiJhMXJSY1ZTaTNGZ25wRTJONnBLWkdvU2V0MnMxIiwiaWF0IjoxNzYxNzI0ODY1LCJleHAiOjE3NjE3Mjg0NjUsImVtYWlsIjoicWFAaW1wYWN0YW5hbHl0aWNzLmNvIiwiZW1haWxfdmVyaWZpZWQiOmZhbHNlLCJmaXJlYmFzZSI6eyJpZGVudGl0aWVzIjp7ImVtYWlsIjpbInFhQGltcGFjdGFuYWx5dGljcy5jbyJdfSwic2lnbl9pbl9wcm92aWRlciI6InBhc3N3b3JkIiwidGVuYW50IjoicmFscGgtbGF1cmVuLXVzem9xIn19.EYNGUJcbrLmBVQ9RUmB9WBbT1vAG4--AF4-dew3H6wP1s9Kkr3h6i9Qk6Jb9AUn-5ppy046cMziG5gnEAEgbNji7YvkdAlj8-XtWkJek1MAxmqYyq2xVPR3my_Zea01Blu9ArfKFO4NhkYbtized11b8CWISm9oA3JoYBGDJPkgMzh78Zyi9NfFd8T-zXJJe8baC7ZOogMGg-8oFs3gz9L8KMCjdVYZ-QIJlu8c5wU0ebrvbC_CfDp1jeiRL0O-iiStkZyFNmmAULd0DE7tNFznA7X9eXyJII-D9DQZ0hXo9PW7i56HTrALtuc4WAQ6OqIxYKsbDeS5QbHVSgc7mFg' \
  -H 'content-type: application/json' \
  -H 'object-id: undefined' \
  -H 'origin: http://localhost:8080' \
  -H 'priority: u=1, i' \
  -H 'referer: http://localhost:8080/' \
  -H 'screen-name: Inventorysmart Configurations' \
  -H 'sec-ch-ua: "Google Chrome";v="141", "Not?A_Brand";v="8", "Chromium";v="141"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "macOS"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: cross-site' \
  -H 'time_format: MM-DD-YYYY' \
  -H 'time_zone: US/eastern' \
  -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/141.0.0.0 Safari/537.36' \
  --data-raw '{"filters":[{"attribute_name":"channel","operator":"not in","values":["RLE","RLW","CME","CMS","CMW","CMFS"],"filter_type":"cascaded","dimension":"store","system_filter":true},{"attribute_name":"dc_flag","operator":"not in","values":["true"],"filter_type":"cascaded","dimension":"store","system_filter":true}],"meta":{"search":[],"range":[],"sort":[],"limit":{"limit":10,"page":1}},"product_codes":["100006097322"]}'
```
#### The  response of the API : 
```
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
            "updated_at": "05/06/2025",
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
            "updated_at": "05/06/2025",
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
            "updated_at": "08/25/2025",
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
            "updated_at": "08/25/2025",
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
            "updated_at": "09/19/2025",
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
            "updated_at": "09/19/2025",
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

#### The repos : 
###### Frontend - 
The path : 
```
/Users/rahulmishra/Desktop/mtp-frontend
```
- We store frontend code in the frontend folder 
- This is a mtp (multi-tenant) which means single codebase is being used by multiple clients 
###### mtp-database : 
```
/Users/rahulmishra/Desktop/mtp-database
```
- All the stored procedure which are being called in the API is stored here inside the folder of functions 
- Configurations are stored here in the form of csv. 


#### Request : 
1. So basically it should show the date format in the form of  `MM / DD / YYYY`  and the timezone should be `US/Eastern` , which I have already changed in the Stored Procedure in the mtp-database but I think in the frontend somewhere have hardcoded this format and hence it is showing in this manner. 
2. Now I want to remove that hard coding and it should show what we are sending in the API response as text 
3. This is mtp (multi-tenant platform) repo which means so many clients uses this same repo and hence if I change something here will affect all other clients , so only change it for the material mapping -> mapped store updated at , and not any other table column. 
4. Please check the codebase properly and go through the flow. 
5. Please try to find out the problematic code which is causing the issue/error 
6. Please try to find out the solid and concrete RCA of the issue. 
7. And a solid resolution of this issue. 

