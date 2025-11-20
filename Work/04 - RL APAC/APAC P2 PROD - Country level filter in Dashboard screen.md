#rlapacindex 

---
Ticket link - https://impactanalytics.atlassian.net/browse/MTP-113491
##### Context and information :
- So there is a screen called -> Decision Dashboard 
- It asks us to apply the filter
	![[../../attachments/APAC P2 PROD - Country level filter in Dashboard screen - filter.png|500]]
- Which looks like the above one -- now in this filter even tho we are passing the country as JAPAN in the filters 
- Right now the filters I am using are -- ![[../../attachments/APAC P2 PROD - Country level filter in Dashboard screen - filters being used.png]]

The flow looks like -> 
Apply filters -> Alerts Table -> Auto Allocation -> Review Recommendations -> The table is having data not filtered on the basis of country -> So we need to make the changes for the country filtered properly 

##### The API for Alerts table 
**CURL**
```
curl 'https://ralph-lauren-apac.uat.impactsmartsuite.com/api/v2/inventory-smart/dashboard/alerts' \
  -H 'accept: */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'application-code: 1' \
  -H 'authorization: eyJhbGciOiJSUzI1NiIsImtpZCI6IjQ1YTZjMGMyYjgwMDcxN2EzNGQ1Y2JiYmYzOWI4NGI2NzYxMjgyNjUiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJodHRwczovL3NlY3VyZXRva2VuLmdvb2dsZS5jb20vcmFscGgtbGF1cmVuLTExMTIyMDI0IiwiYXVkIjoicmFscGgtbGF1cmVuLTExMTIyMDI0IiwiYXV0aF90aW1lIjoxNzU2OTgzMDg2LCJ1c2VyX2lkIjoiTW1GOFU0RWNLR1JjMTRDOHNoWU05azZJMDZ2MiIsInN1YiI6Ik1tRjhVNEVjS0dSYzE0QzhzaFlNOWs2STA2djIiLCJpYXQiOjE3NjM2MTc5MzYsImV4cCI6MTc2MzYyMTUzNiwiZW1haWwiOiJxYUBpbXBhY3RhbmFseXRpY3MuY28iLCJlbWFpbF92ZXJpZmllZCI6ZmFsc2UsImZpcmViYXNlIjp7ImlkZW50aXRpZXMiOnsiZW1haWwiOlsicWFAaW1wYWN0YW5hbHl0aWNzLmNvIl19LCJzaWduX2luX3Byb3ZpZGVyIjoicGFzc3dvcmQiLCJ0ZW5hbnQiOiJybC1hcGFjLXVhdC16ejdkOCJ9fQ.Yli-YCZbGV8AVtVfiC7hXNvHxS1X51XUKeaV7jE_mlC0dJGNy3534rJcTsgLa0ZioCwb7MfC17_IQT-SdgQq4-YeyMFEeL_q-oSZQYQFNnxc6NLymGT-Ow66OABW_U5C2XWtVsRrI1VauSh6BreiYZ9Usn6RAqWOmq7HH7_nZmTm7Wyfy5RmoZaL9Nt4EkOdFBoiCaQ4PyU4VrmCc0S_j3i8GWHV9642BQO2-R7Qb6OeR2dNrE6TrEYmii0ePO9A66bJfWE4DAYK777er7md19HPDN03_tvz-IFPmRIyiERCcA_ZQuVXTz5BJZtYBRhfHAbHz1xggbbpAPwUYFfyNg' \
  -H 'content-type: application/json' \
  -b 'Path=/; ph_phc_OBW3O5JZTqdyFZPMcGNdW39hiPYwAJgHbRH6xKOzhf3_posthog=%7B%22%24user_state%22%3A%22identified%22%2C%22%24sesid%22%3A%5B1763561926766%2C%22019a9c5a-5bac-7361-91f6-2a720a3cd5a0%22%2C1763559758729%5D%2C%22distinct_id%22%3A%7B%22email%22%3A%22rahul.mishra%40impactanalytics.co%22%7D%2C%22%24device_id%22%3A%2201993305-282d-7ae4-81a2-05b3cea313f7%22%2C%22%24client_session_props%22%3A%7B%22sessionId%22%3A%22019a9c5a-5bac-7361-91f6-2a720a3cd5a0%22%2C%22props%22%3A%7B%22initialPathName%22%3A%22%2Finventory-smart%2Fconfiguration%22%2C%22referringDomain%22%3A%22%24direct%22%7D%7D%2C%22%24stored_person_properties%22%3A%7B%22email%22%3A%22rahul.mishra%40impactanalytics.co%22%2C%22host%22%3A%22signet.uat.impactsmartsuite.com%22%7D%2C%22%24user_id%22%3A%7B%22email%22%3A%22rahul.mishra%40impactanalytics.co%22%7D%2C%22%24active_feature_flags%22%3A%5B%5D%2C%22%24enabled_feature_flags%22%3A%7B%7D%2C%22%24feature_flag_payloads%22%3A%7B%7D%2C%22%24session_recording_enabled_server_side%22%3Atrue%2C%22%24console_log_recording_enabled_server_side%22%3Atrue%2C%22%24session_recording_recorder_version_server_side%22%3A%22v2%22%2C%22%24autocapture_disabled_server_side%22%3Afalse%7D; ph_phc_jdfaPUcheTjuLkcagCcjqQx4ebTtQLcSiq115zfZQJj_posthog=%7B%22distinct_id%22%3A%7B%22email%22%3A%22qa%40impactanalytics.co%22%7D%2C%22%24sesid%22%3A%5B1763617938561%2C%22019a9fd2-1258-7cc3-9f77-0ae3969f62e5%22%2C1763617935960%5D%2C%22%24epp%22%3Atrue%2C%22%24initial_person_info%22%3A%7B%22r%22%3A%22%24direct%22%2C%22u%22%3A%22https%3A%2F%2Fsignet-replica.impactsmartsuite.com%2Flogin%22%7D%2C%22%24client_session_props%22%3A%7B%22sessionId%22%3A%22019a9fd2-1258-7cc3-9f77-0ae3969f62e5%22%2C%22props%22%3A%7B%22initialPathName%22%3A%22%2Fhome%22%2C%22referringDomain%22%3A%22%24direct%22%7D%7D%2C%22%24stored_person_properties%22%3A%7B%22email%22%3A%22qa%40impactanalytics.co%22%2C%22host%22%3A%22ralph-lauren-apac.uat.impactsmartsuite.com%22%7D%2C%22%24user_id%22%3A%7B%22email%22%3A%22qa%40impactanalytics.co%22%7D%2C%22%24had_persisted_distinct_id%22%3Atrue%2C%22%24device_id%22%3A%7B%22email%22%3A%22qa%40impactanalytics.co%22%7D%2C%22%24user_state%22%3A%22identified%22%7D' \
  -H 'object-id: undefined' \
  -H 'origin: https://ralph-lauren-apac.uat.impactsmartsuite.com' \
  -H 'priority: u=1, i' \
  -H 'referer: https://ralph-lauren-apac.uat.impactsmartsuite.com/inventory-smart/decision-dashboard' \
  -H 'screen-name: InventoryDashboard' \
  -H 'sec-ch-ua: "Chromium";v="142", "Google Chrome";v="142", "Not_A Brand";v="99"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "macOS"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'time_format: MM-DD-YYYY' \
  -H 'time_zone: Asia/Hong_Kong' \
  -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/142.0.0.0 Safari/537.36' \
  --data-raw '{"product_attributes":[{"filter_type":"cascaded","attribute_name":"l0_name","operator":"in","dimension":"Product","values":["10-MENS APPAREL"]}],"store_attributes":[{"filter_type":"cascaded","attribute_name":"retail_region","operator":"in","dimension":"Store","values":["GCSEA"]},{"filter_type":"cascaded","attribute_name":"channel","operator":"in","dimension":"Store","values":["OUTLET"]},{"filter_type":"cascaded","attribute_name":"s1_name","operator":"in","dimension":"Store","values":["CHINESE MAINLAND"]},{"attribute_name":"channel","operator":"not in","values":["RLE","RLW","CME","CMS","CMW","CMFS","CMCS","ECOM_DONT_USE","RLC","SHARED"],"filter_type":"cascaded","dimension":"store","system_filter":true},{"attribute_name":"dc_flag","operator":"not in","values":["true"],"filter_type":"cascaded","dimension":"store","system_filter":true}]}'
```

So in this API curl -- if you check the payload properly -> 
- We are sending the country as the `attribute_name` of `s1_name` 
If you want the payload to be in proper format again --> 
```json
{
    "product_attributes": [
        {
            "filter_type": "cascaded",
            "attribute_name": "l0_name",
            "operator": "in",
            "dimension": "Product",
            "values": [
                "10-MENS APPAREL"
            ]
        }
    ],
    "store_attributes": [
        {
            "filter_type": "cascaded",
            "attribute_name": "retail_region",
            "operator": "in",
            "dimension": "Store",
            "values": [
                "GCSEA"
            ]
        },
        {
            "filter_type": "cascaded",
            "attribute_name": "channel",
            "operator": "in",
            "dimension": "Store",
            "values": [
                "OUTLET"
            ]
        },
        {
            "filter_type": "cascaded",
            "attribute_name": "s1_name",
            "operator": "in",
            "dimension": "Store",
            "values": [
                "CHINESE MAINLAND"
            ]
        },
        {
            "attribute_name": "channel",
            "operator": "not in",
            "values": [
                "RLE",
                "RLW",
                "CME",
                "CMS",
                "CMW",
                "CMFS",
                "CMCS",
                "ECOM_DONT_USE",
                "RLC",
                "SHARED"
            ],
            "filter_type": "cascaded",
            "dimension": "store",
            "system_filter": true
        },
        {
            "attribute_name": "dc_flag",
            "operator": "not in",
            "values": [
                "true"
            ],
            "filter_type": "cascaded",
            "dimension": "store",
            "system_filter": true
        }
    ]
}
```

So in the `store_attributes`  we are sending the data of country in the attribute_name of s1_name 

Now moving forward to the response from the API : 
The API response is so big and hence I am not able to paste the entire thing : I will just attach the auto allocation part that two I will only include 2 review recommendation part from that : 
```json
{
                "article_count": 76,
                "name": "Auto Allocation",
                "description": "System recommended auto allocations",
                "level": 2,
                "type": {
                    "1": "new_table",
                    "2": "pop_up"
                },
                "new_table_data": [
                    {
                        "plan_code": "9_1_GCSEA_20251119T170008_OUTLET_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR561JACKETPOLORALPHLAUREN20_2",
                        "allocated_total": 1.0,
                        "inv_avai": 13,
                        "skus": [
                            "710835567002"
                        ],
                        "name": "9_1_GCSEA_20251119T170008_OUTLET_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR561JACKETPOLORALPHLAUREN20_2",
                        "status": "Created",
                        "type": "Auto Allocation",
                        "description": null,
                        "created_at": "11-20-2025",
                        "updated_at": "11-19-2025",
                        "created_by": "QA User",
                        "updated_by": null,
                        "packs_allocated_qty": "0",
                        "loose_allocated_qty": "1",
                        "total_allocated_qty_pack": 1.0,
                        "channel": [
                            "OUTLET"
                        ],
                        "retail_region": [
                            "GCSEA"
                        ],
                        "l0_name": [
                            "10-MENS APPAREL"
                        ],
                        "l1_name": [
                            "8-POLO RALPH LAUREN"
                        ],
                        "l2_name": [
                            "43-OUTERWEAR"
                        ],
                        "l3_name": [
                            "26-SPORTSWEAR"
                        ],
                        "color_name": [
                            "BEIGE__ia_char_03KHAKI",
                            "LIGHT__ia_char_03PASTEL BROWN-230"
                        ],
                        "vendor_case_pack": "{\"\"}",
                        "product_description": [
                            "O CITY CHINO WINDBREAKER",
                            "O THORPE ANORAK JACKET"
                        ],
                        "brand": [
                            "POLO RALPH LAUREN"
                        ],
                        "rtl_coordinate_group_desc": [
                            "0-"
                        ],
                        "color": [
                            "250-BEIGE__ia_char_03KHAKI",
                            "230-LIGHT__ia_char_03PASTEL BROWN-230"
                        ],
                        "style": [
                            "MNPOOTW16020588",
                            "MNPOOTW16021353"
                        ],
                        "pop_up_data": [
                            {
                                "channel": [
                                    "OUTLET"
                                ],
                                "plan_code": "9_1_GCSEA_20251119T170008_OUTLET_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR561JACKETPOLORALPHLAUREN20_2",
                                "name": "9_1_GCSEA_20251119T170008_OUTLET_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR561JACKETPOLORALPHLAUREN20_2",
                                "l3_name": "26-SPORTSWEAR",
                                "product_description": "O THORPE ANORAK JACKET",
                                "color_name": "LIGHT__ia_char_03PASTEL BROWN-230",
                                "color": "230-LIGHT__ia_char_03PASTEL BROWN-230",
                                "brand": "POLO RALPH LAUREN",
                                "style_color_id": "MNPOOTW16020588",
                                "l4_name": "561-JACKET",
                                "vendor_case_pack": null,
                                "rtl_coordinate_group_desc": "0-",
                                "style": "MNPOOTW16020588",
                                "l0_name": "10-MENS APPAREL",
                                "l1_name": "8-POLO RALPH LAUREN",
                                "l2_name": "43-OUTERWEAR",
                                "article": "710835567002",
                                "allocated_total": 1.0,
                                "inv_avai": 13,
                                "selected_store_group_names": [
                                    "'NONCN_PRO_MN_PO_PREDICTIVE_710835567002'",
                                    "'JP_PRO_MN_PO_PREDICTIVE_710835567002'"
                                ]
                            }
                        ]
                    },
                    {
                        "plan_code": "9_1_GCSEA_20251119T170008_OUTLET_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2",
                        "allocated_total": 34.0,
                        "inv_avai": 5674,
                        "skus": [
                            "710904969001",
                            "710919213005",
                            "710919213010",
                            "710919213007",
                            "710919213004"
                        ],
                        "name": "9_1_GCSEA_20251119T170008_OUTLET_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2",
                        "status": "Created",
                        "type": "Auto Allocation",
                        "description": null,
                        "created_at": "11-20-2025",
                        "updated_at": "11-19-2025",
                        "created_by": "QA User",
                        "updated_by": null,
                        "packs_allocated_qty": "0",
                        "loose_allocated_qty": "34",
                        "total_allocated_qty_pack": 34.0,
                        "channel": [
                            "OUTLET"
                        ],
                        "retail_region": [
                            "GCSEA"
                        ],
                        "l0_name": [
                            "10-MENS APPAREL"
                        ],
                        "l1_name": [
                            "8-POLO RALPH LAUREN"
                        ],
                        "l2_name": [
                            "58-SWEATER"
                        ],
                        "l3_name": [
                            "26-SPORTSWEAR"
                        ],
                        "color_name": [
                            "GREY",
                            "NATURAL-101",
                            "BLUE",
                            "BLACK"
                        ],
                        "vendor_case_pack": "{\"\"}",
                        "product_description": [
                            "O COTTON ROVING CABLE FZ",
                            "O COMBED COTTON CN SPP",
                            "O COTTON ROVING CABLE HZ SPP",
                            "O ROVING CABLE CN SPP"
                        ],
                        "brand": [
                            "POLO RALPH LAUREN"
                        ],
                        "rtl_coordinate_group_desc": [
                            "0-"
                        ],
                        "color": [
                            "020-GREY",
                            "001-BLACK",
                            "101-NATURAL-101",
                            "400-BLUE"
                        ],
                        "style": [
                            "MNPOSWE16821562",
                            "MNPOSWE16821574",
                            "MNPOSWE16821541",
                            "MNPOSWE16822107",
                            "MNPOSWE16821548",
                            "MNPOSWE16821558",
                            "MNPOSWE16821567",
                            "MNPOSWE16820075",
                            "MNPOSWE16821438",
                            "MNPOSWE16821745",
                            "MNPOSWE16821737"
                        ],
                        "pop_up_data": [
                            {
                                "channel": [
                                    "OUTLET"
                                ],
                                "plan_code": "9_1_GCSEA_20251119T170008_OUTLET_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2",
                                "name": "9_1_GCSEA_20251119T170008_OUTLET_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2",
                                "l3_name": "26-SPORTSWEAR",
                                "product_description": "O COTTON ROVING CABLE FZ",
                                "color_name": "BLUE",
                                "color": "400-BLUE",
                                "brand": "POLO RALPH LAUREN",
                                "style_color_id": "MNPOSWE16821438",
                                "l4_name": "569-LONG SLEEVE",
                                "vendor_case_pack": null,
                                "rtl_coordinate_group_desc": "0-",
                                "style": "MNPOSWE16821438",
                                "l0_name": "10-MENS APPAREL",
                                "l1_name": "8-POLO RALPH LAUREN",
                                "l2_name": "58-SWEATER",
                                "article": "710904969001",
                                "allocated_total": 6.0,
                                "inv_avai": 705,
                                "selected_store_group_names": [
                                    "'JP_PRO_MN_PO_PREDICTIVE_710904969001'",
                                    "'NONCN_PRO_MN_PO_PREDICTIVE_710904969001'"
                                ]
                            },
                            {
                                "channel": [
                                    "OUTLET"
                                ],
                                "plan_code": "9_1_GCSEA_20251119T170008_OUTLET_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2",
                                "name": "9_1_GCSEA_20251119T170008_OUTLET_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2",
                                "l3_name": "26-SPORTSWEAR",
                                "product_description": "O COTTON ROVING CABLE HZ SPP",
                                "color_name": "GREY",
                                "color": "020-GREY",
                                "brand": "POLO RALPH LAUREN",
                                "style_color_id": "MNPOSWE16822107",
                                "l4_name": "569-LONG SLEEVE",
                                "vendor_case_pack": null,
                                "rtl_coordinate_group_desc": "0-",
                                "style": "MNPOSWE16822107",
                                "l0_name": "10-MENS APPAREL",
                                "l1_name": "8-POLO RALPH LAUREN",
                                "l2_name": "58-SWEATER",
                                "article": "710919213005",
                                "allocated_total": 7.0,
                                "inv_avai": 1098,
                                "selected_store_group_names": [
                                    "'NONCN_PRO_MN_PO_PREDICTIVE_710919213005'",
                                    "'JP_PRO_MN_PO_PREDICTIVE_710919213005'"
                                ]
                            },
                            {
                                "channel": [
                                    "OUTLET"
                                ],
                                "plan_code": "9_1_GCSEA_20251119T170008_OUTLET_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2",
                                "name": "9_1_GCSEA_20251119T170008_OUTLET_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2",
                                "l3_name": "26-SPORTSWEAR",
                                "product_description": "O COTTON ROVING CABLE HZ SPP",
                                "color_name": "NATURAL-101",
                                "color": "101-NATURAL-101",
                                "brand": "POLO RALPH LAUREN",
                                "style_color_id": "MNPOSWE16821737",
                                "l4_name": "569-LONG SLEEVE",
                                "vendor_case_pack": null,
                                "rtl_coordinate_group_desc": "0-",
                                "style": "MNPOSWE16821737",
                                "l0_name": "10-MENS APPAREL",
                                "l1_name": "8-POLO RALPH LAUREN",
                                "l2_name": "58-SWEATER",
                                "article": "710919213010",
                                "allocated_total": 7.0,
                                "inv_avai": 698,
                                "selected_store_group_names": [
                                    "'JP_PRO_MN_PO_PREDICTIVE_710919213010'",
                                    "'NONCN_PRO_MN_PO_PREDICTIVE_710919213010'"
                                ]
                            },
                            {
                                "channel": [
                                    "OUTLET"
                                ],
                                "plan_code": "9_1_GCSEA_20251119T170008_OUTLET_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2",
                                "name": "9_1_GCSEA_20251119T170008_OUTLET_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2",
                                "l3_name": "26-SPORTSWEAR",
                                "product_description": "O COTTON ROVING CABLE HZ SPP",
                                "color_name": "NATURAL-101",
                                "color": "101-NATURAL-101",
                                "brand": "POLO RALPH LAUREN",
                                "style_color_id": "MNPOSWE16821567",
                                "l4_name": "569-LONG SLEEVE",
                                "vendor_case_pack": null,
                                "rtl_coordinate_group_desc": "0-",
                                "style": "MNPOSWE16821567",
                                "l0_name": "10-MENS APPAREL",
                                "l1_name": "8-POLO RALPH LAUREN",
                                "l2_name": "58-SWEATER",
                                "article": "710919213007",
                                "allocated_total": 7.0,
                                "inv_avai": 1814,
                                "selected_store_group_names": [
                                    "'NONCN_PRO_MN_PO_PREDICTIVE_710919213007'",
                                    "'JP_PRO_MN_PO_PREDICTIVE_710919213007'"
                                ]
                            },
                            {
                                "channel": [
                                    "OUTLET"
                                ],
                                "plan_code": "9_1_GCSEA_20251119T170008_OUTLET_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2",
                                "name": "9_1_GCSEA_20251119T170008_OUTLET_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2",
                                "l3_name": "26-SPORTSWEAR",
                                "product_description": "O COTTON ROVING CABLE HZ SPP",
                                "color_name": "BLUE",
                                "color": "400-BLUE",
                                "brand": "POLO RALPH LAUREN",
                                "style_color_id": "MNPOSWE16821562",
                                "l4_name": "569-LONG SLEEVE",
                                "vendor_case_pack": null,
                                "rtl_coordinate_group_desc": "0-",
                                "style": "MNPOSWE16821562",
                                "l0_name": "10-MENS APPAREL",
                                "l1_name": "8-POLO RALPH LAUREN",
                                "l2_name": "58-SWEATER",
                                "article": "710919213004",
                                "allocated_total": 7.0,
                                "inv_avai": 1359,
                                "selected_store_group_names": [
                                    "'NONCN_PRO_MN_PO_PREDICTIVE_710919213004'",
                                    "'JP_PRO_MN_PO_PREDICTIVE_710919213004'"
                                ]
                            }
                        ]
                    },
```

So this looks something like this on the UI -- 
![[../../attachments/APAC P2 PROD - Country level filter in Dashboard screen - alerts and review recommendation.png]]
So the Alerts Table -> Auto Allocation -> Click on the Review Recommendation 
It opens a new table called -> Review Recommendation 

Now with context we are done. Let's move on to the things raised by client -> 
##### Issue description 
If you see the review recommendation table 
which looks like this -- 
![[../../attachments/APAC P2 PROD - Country level filter in Dashboard screen - review recommendation table.png]]

So let me take two names from this table : 
1. 9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA13RLPURPLELABEL34KNIT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2
2. 9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA13RLPURPLELABEL41NECKWEAR28FURNISHINGS181BOWTIERLPURPLELABEL20_2

So if you check the above two names  - AUSTRALIA is there in them - which means other country values are also coming in this table 

So this is what we have to fix and for more information related to the SP and the query and the API 

I directly called the API in the local and printed a detailed logs which are : 

```plain text 
[LOCAL DEBUG] execute_query() - STARTING
[LOCAL DEBUG] Tenant: ralph-lauren-apac
[LOCAL DEBUG] Query: 
with saf as (
  select distinct store_code, channel, special_classification from global.store_attributes_filter
)
SELECT 
--COALESCE(SUM(CASE WHEN is_resolved = 1 THEN 1 END), 0) is_resolved, COALESCE(SUM(CASE WHEN is_resolved = 0 THEN 1 END), 0) is_not_resolved,
1  is_not_resolved,
0  is_resolved, 
COUNT(DISTINCT article) article_count, COUNT(CASE WHEN clearance = 1 and dc_flag is not true THEN store_code END) AS store_count
FROM (
    SELECT number_of_allocations is_resolved, article, store_code, clearance, dc_flag
    FROM inventory_smart.alerts_product_store_level
    JOIN saf using (store_code, channel)
    WHERE clearance_alert_flag = 1 
    AND  l0_name in ('10-MENS APPAREL')  AND (( retail_region in ('GCSEA') and channel in ('FULL PRICE') and channel not in ('RLE','RLW','CME','CMS','CMW','CMFS','CMCS','ECOM_DONT_USE','RLC','SHARED') and s1_name in ('CHINESE MAINLAND') ) or ( retail_region in ('GCSEA') and special_classification in ('WHS') )) 
    --GROUP BY 1, 2, 3, 4, 5
) sq

[LOCAL DEBUG] Return type: dataframe
[LOCAL DEBUG] Using existing connection: False
[LOCAL DEBUG] Timeout: 200
[LOCAL DEBUG] Cursor factory: RealDictCursor
================================================================================

================================================================================
[LOCAL DEBUG] execute_query() - STARTING
[LOCAL DEBUG] Tenant: ralph-lauren-apac
[LOCAL DEBUG] Query: 
with saf as (
  select distinct store_code, channel, special_classification from global.store_attributes_filter
)
SELECT 
--COALESCE(SUM(CASE WHEN is_resolved = 1 THEN 1 END), 0) is_resolved, COALESCE(SUM(CASE WHEN is_resolved = 0 THEN 1 END), 0) is_not_resolved,
1  is_not_resolved,
0  is_resolved, 
COUNT(DISTINCT article) article_count, COUNT(CASE WHEN markdown = 1 and dc_flag is not true THEN store_code END) AS store_count
FROM (
    SELECT number_of_allocations is_resolved, article, store_code, markdown, dc_flag
    FROM inventory_smart.alerts_product_store_level
    JOIN saf using (store_code, channel)
    WHERE markdown_alert_flag = 1 
    AND  l0_name in ('10-MENS APPAREL')  AND (( retail_region in ('GCSEA') and channel in ('FULL PRICE') and channel not in ('RLE','RLW','CME','CMS','CMW','CMFS','CMCS','ECOM_DONT_USE','RLC','SHARED') and s1_name in ('CHINESE MAINLAND') ) or ( retail_region in ('GCSEA') and special_classification in ('WHS') )) 
    --GROUP BY 1, 2, 3, 4, 5
) sq

[LOCAL DEBUG] Return type: dataframe
[LOCAL DEBUG] Using existing connection: False
[LOCAL DEBUG] Timeout: 200
[LOCAL DEBUG] Cursor factory: RealDictCursor
================================================================================

================================================================================
[LOCAL DEBUG] execute_query() - STARTING
[LOCAL DEBUG] Tenant: ralph-lauren-apac
[LOCAL DEBUG] Query: 
with saf as (
  select distinct store_code, channel, special_classification from global.store_attributes_filter
)
SELECT 
--COALESCE(SUM(CASE WHEN is_resolved = 1 THEN 1 END), 0) is_resolved, COALESCE(SUM(CASE WHEN is_resolved = 0 THEN 1 END), 0) is_not_resolved,
1  is_not_resolved,
0  is_resolved, 
COUNT(DISTINCT article) article_count, COUNT(CASE WHEN floorset = 1 and dc_flag is not true THEN store_code END) AS store_count
FROM (
    SELECT number_of_allocations is_resolved, article, store_code, floorset, dc_flag
    FROM inventory_smart.alerts_product_store_level
    JOIN saf using (store_code, channel)
    WHERE floorset_alert_flag = 1 
    AND  l0_name in ('10-MENS APPAREL')  AND (( retail_region in ('GCSEA') and channel in ('FULL PRICE') and channel not in ('RLE','RLW','CME','CMS','CMW','CMFS','CMCS','ECOM_DONT_USE','RLC','SHARED') and s1_name in ('CHINESE MAINLAND') ) or ( retail_region in ('GCSEA') and special_classification in ('WHS') )) 
    --GROUP BY 1, 2, 3, 4, 5
) sq

[LOCAL DEBUG] Return type: dataframe
[LOCAL DEBUG] Using existing connection: False
[LOCAL DEBUG] Timeout: 200
[LOCAL DEBUG] Cursor factory: RealDictCursor
================================================================================

================================================================================
[LOCAL DEBUG] execute_query() - STARTING
[LOCAL DEBUG] Tenant: ralph-lauren-apac
[LOCAL DEBUG] Query: select name,attribute_value from global.tenant_attribute_master where application_code = '3' AND name = 'tenant_time_config' 
[LOCAL DEBUG] Return type: dataframe
[LOCAL DEBUG] Using existing connection: False
[LOCAL DEBUG] Timeout: 200
[LOCAL DEBUG] Cursor factory: RealDictCursor
================================================================================

================================================================================
[LOCAL DEBUG] execute_query() - STARTING
[LOCAL DEBUG] Tenant: ralph-lauren-apac
[LOCAL DEBUG] Query: 
with saf as (
  select distinct store_code, channel, special_classification from global.store_attributes_filter
)
SELECT 
--COALESCE(SUM(CASE WHEN is_resolved = 1 THEN 1 END), 0) is_resolved, COALESCE(SUM(CASE WHEN is_resolved = 0 THEN 1 END), 0) is_not_resolved,
1  is_not_resolved,
0  is_resolved, 
COUNT(DISTINCT article) article_count, COUNT(CASE WHEN newlylaunched = 1 and dc_flag is not true THEN store_code END) AS store_count
FROM (
    SELECT number_of_allocations is_resolved, article, store_code, newlylaunched, dc_flag
    FROM inventory_smart.alerts_product_store_level
    JOIN saf using (store_code, channel)
    WHERE newly_launched_alert_flag = 1 
    AND  l0_name in ('10-MENS APPAREL')  AND (( retail_region in ('GCSEA') and channel in ('FULL PRICE') and channel not in ('RLE','RLW','CME','CMS','CMW','CMFS','CMCS','ECOM_DONT_USE','RLC','SHARED') and s1_name in ('CHINESE MAINLAND') ) or ( retail_region in ('GCSEA') and special_classification in ('WHS') )) 
    --GROUP BY 1, 2, 3, 4, 5
) sq

[LOCAL DEBUG] Return type: dataframe
[LOCAL DEBUG] Using existing connection: False
[LOCAL DEBUG] Timeout: 200
[LOCAL DEBUG] Cursor factory: RealDictCursor
================================================================================

================================================================================
[LOCAL DEBUG] execute_query() - STARTING
[LOCAL DEBUG] Tenant: ralph-lauren-apac
[LOCAL DEBUG] Query: select name,attribute_value from global.tenant_attribute_master where application_code = '3' AND name = 'tenant_time_config' 
[LOCAL DEBUG] Return type: dataframe
[LOCAL DEBUG] Using existing connection: False
[LOCAL DEBUG] Timeout: 200
[LOCAL DEBUG] Cursor factory: RealDictCursor
================================================================================

Logs http post request response status True and message OK
ERROR:platform-logging:Logs http post request response status True and message OK
[LOCAL DEBUG] Query executed successfully
[LOCAL DEBUG] Fetched 1 rows
[LOCAL DEBUG] Column names: ['is_not_resolved', 'is_resolved', 'article_count', 'store_count']
[LOCAL DEBUG] Dataframe shape: (1, 4)
[LOCAL DEBUG] execute_query() - COMPLETED
================================================================================

[LOCAL DEBUG] Query executed successfully
[LOCAL DEBUG] Fetched 1 rows
[LOCAL DEBUG] Column names: ['is_not_resolved', 'is_resolved', 'article_count', 'store_count']
[LOCAL DEBUG] Dataframe shape: (1, 4)
[LOCAL DEBUG] execute_query() - COMPLETED
================================================================================
[LOCAL DEBUG] Executing query...
[LOCAL DEBUG] Executing query...
[LOCAL DEBUG] Executing query...
[LOCAL DEBUG] Query executed successfully
[LOCAL DEBUG] Fetched 1 rows
[LOCAL DEBUG] Column names: ['is_not_resolved', 'is_resolved', 'article_count', 'store_count']
[LOCAL DEBUG] Dataframe shape: (1, 4)
[LOCAL DEBUG] execute_query() - COMPLETED
================================================================================

[LOCAL DEBUG] Query executed successfully
[LOCAL DEBUG] Fetched 1 rows
[LOCAL DEBUG] Column names: ['is_not_resolved', 'is_resolved', 'article_count', 'store_count']
[LOCAL DEBUG] Dataframe shape: (1, 4)
[LOCAL DEBUG] execute_query() - COMPLETED
================================================================================

[LOCAL DEBUG] Query executed successfully
[LOCAL DEBUG] Fetched 1 rows
[LOCAL DEBUG] Column names: ['is_not_resolved', 'is_resolved', 'article_count', 'store_count']
[LOCAL DEBUG] Dataframe shape: (1, 4)
[LOCAL DEBUG] execute_query() - COMPLETED
================================================================================

[LOCAL DEBUG] Executing query...
[LOCAL DEBUG] Executing query...
[LOCAL DEBUG] Executing query...
[LOCAL DEBUG] Executing query...
[LOCAL DEBUG] Query executed successfully
[LOCAL DEBUG] Fetched 1 rows
[LOCAL DEBUG] Column names: ['name', 'attribute_value']
[LOCAL DEBUG] Dataframe shape: (1, 2)
[LOCAL DEBUG] execute_query() - COMPLETED
================================================================================


================================================================================
[LOCAL DEBUG] execute_store_procedure() - STARTING
[LOCAL DEBUG] Tenant: ralph-lauren-apac
[LOCAL DEBUG] Procedure Name: inventory_smart.past_plans_list
[LOCAL DEBUG] Input Parameters: ('{"status": [{"type": "list", "operator": "in", "values": [1]}], "type": [{"type": "list", "operator": "in", "values": [2]}]}', '{"l0_name": [{"type": "list", "operator": "in", "values": ["10-MENS APPAREL"]}], "retail_region": [{"type": "list", "operator": "in", "values": ["GCSEA"]}], "channel": [{"type": "list", "operator": "in", "values": ["FULL PRICE"]}, {"type": "list", "operator": "not in", "values": ["RLE", "RLW", "CME", "CMS", "CMW", "CMFS", "CMCS", "ECOM_DONT_USE", "RLC", "SHARED"]}], "s1_name": [{"type": "list", "operator": "in", "values": ["CHINESE MAINLAND"]}], "dc_flag": [{"type": "list", "operator": "not in", "values": ["true"]}], "l3_name": [], "l2_name": [], "brand": [], "rtl_coordinate_group_desc": [], "color_name": [], "color": [], "style_color_id": [], "vendor_case_pack": [], "style": [], "l4_name": [], "l1_name": [], "product_description": [], "article": []}', '{"sort": [{"column": "created_at", "order": "desc"}]}', '2025-11-20', '2025-11-20', False)
[LOCAL DEBUG] Table Query --------> :
 {"sort": [{"column": "created_at", "order": "desc"}]}
[LOCAL DEBUG] Cursor Based: True
[LOCAL DEBUG] Fetch Rows Count: True
[LOCAL DEBUG] Min Max Columns: None
[LOCAL DEBUG] Distinct Columns: None
[LOCAL DEBUG] Timeout: 200
[LOCAL DEBUG] Cursor Factory: RealDictCursor
================================================================================
[LOCAL DEBUG] Starting transaction (BEGIN)
[LOCAL DEBUG] Query executed successfully
[LOCAL DEBUG] Fetched 1 rows
[LOCAL DEBUG] Column names: ['name', 'attribute_value']
[LOCAL DEBUG] Dataframe shape: (1, 2)
[LOCAL DEBUG] execute_query() - COMPLETED
================================================================================

================================================================================
[LOCAL DEBUG] execute_store_procedure() - STARTING
[LOCAL DEBUG] Tenant: ralph-lauren-apac
[LOCAL DEBUG] Procedure Name: inventory_smart.past_plans_list
[LOCAL DEBUG] Input Parameters: ('{"status": [{"type": "list", "operator": "in", "values": [1]}], "type": [{"type": "list", "operator": "in", "values": [7]}]}', '{"l0_name": [{"type": "list", "operator": "in", "values": ["10-MENS APPAREL"]}], "retail_region": [{"type": "list", "operator": "in", "values": ["GCSEA"]}], "channel": [{"type": "list", "operator": "in", "values": ["FULL PRICE"]}, {"type": "list", "operator": "not in", "values": ["RLE", "RLW", "CME", "CMS", "CMW", "CMFS", "CMCS", "ECOM_DONT_USE", "RLC", "SHARED"]}], "s1_name": [{"type": "list", "operator": "in", "values": ["CHINESE MAINLAND"]}], "dc_flag": [{"type": "list", "operator": "not in", "values": ["true"]}], "l3_name": [], "l2_name": [], "brand": [], "rtl_coordinate_group_desc": [], "color_name": [], "color": [], "style_color_id": [], "vendor_case_pack": [], "store_code": [], "style": [], "l4_name": [], "l1_name": [], "product_description": [], "article": []}', '{"sort": [{"column": "created_at", "order": "desc"}]}', '2025-11-20', '2025-11-20', False)
[LOCAL DEBUG] Table Query --------> :
 {"sort": [{"column": "created_at", "order": "desc"}]}
[LOCAL DEBUG] Cursor Based: True
[LOCAL DEBUG] Fetch Rows Count: True
[LOCAL DEBUG] Min Max Columns: None
[LOCAL DEBUG] Distinct Columns: None
[LOCAL DEBUG] Timeout: 200
[LOCAL DEBUG] Cursor Factory: RealDictCursor
================================================================================
[LOCAL DEBUG] Starting transaction (BEGIN)
[LOCAL DEBUG] Query executed successfully
[LOCAL DEBUG] Fetched 1 rows
[LOCAL DEBUG] Column names: ['is_not_resolved', 'is_resolved', 'article_count', 'store_count']
[LOCAL DEBUG] Dataframe shape: (1, 4)
[LOCAL DEBUG] execute_query() - COMPLETED
================================================================================

[LOCAL DEBUG] Query executed successfully
[LOCAL DEBUG] Fetched 1 rows
[LOCAL DEBUG] Column names: ['is_not_resolved', 'is_resolved', 'article_count', 'store_count']
[LOCAL DEBUG] Dataframe shape: (1, 4)
[LOCAL DEBUG] execute_query() - COMPLETED
================================================================================

[LOCAL DEBUG] Cursor-based SP call with cursor_name: 48680156-0cc3-4860-8708-a6cee5d1536b
[LOCAL DEBUG] Final input args: ['48680156-0cc3-4860-8708-a6cee5d1536b', '{"status": [{"type": "list", "operator": "in", "values": [1]}], "type": [{"type": "list", "operator": "in", "values": [2]}]}', '{"l0_name": [{"type": "list", "operator": "in", "values": ["10-MENS APPAREL"]}], "retail_region": [{"type": "list", "operator": "in", "values": ["GCSEA"]}], "channel": [{"type": "list", "operator": "in", "values": ["FULL PRICE"]}, {"type": "list", "operator": "not in", "values": ["RLE", "RLW", "CME", "CMS", "CMW", "CMFS", "CMCS", "ECOM_DONT_USE", "RLC", "SHARED"]}], "s1_name": [{"type": "list", "operator": "in", "values": ["CHINESE MAINLAND"]}], "dc_flag": [{"type": "list", "operator": "not in", "values": ["true"]}], "l3_name": [], "l2_name": [], "brand": [], "rtl_coordinate_group_desc": [], "color_name": [], "color": [], "style_color_id": [], "vendor_case_pack": [], "style": [], "l4_name": [], "l1_name": [], "product_description": [], "article": []}', '{"sort": [{"column": "created_at", "order": "desc"}]}', '2025-11-20', '2025-11-20', False]
[LOCAL DEBUG] Calling stored procedure: inventory_smart.past_plans_list
[LOCAL DEBUG] Generated SQL Query: SELECT inventory_smart.past_plans_list('48680156-0cc3-4860-8708-a6cee5d1536b', '{"status": [{"type": "list", "operator": "in", "values": [1]}], "type": [{"type": "list", "operator": "in", "values": [2]}]}', '{"l0_name": [{"type": "list", "operator": "in", "values": ["10-MENS APPAREL"]}], "retail_region": [{"type": "list", "operator": "in", "values": ["GCSEA"]}], "channel": [{"type": "list", "operator": "in", "values": ["FULL PRICE"]}, {"type": "list", "operator": "not in", "values": ["RLE", "RLW", "CME", "CMS", "CMW", "CMFS", "CMCS", "ECOM_DONT_USE", "RLC", "SHARED"]}], "s1_name": [{"type": "list", "operator": "in", "values": ["CHINESE MAINLAND"]}], "dc_flag": [{"type": "list", "operator": "not in", "values": ["true"]}], "l3_name": [], "l2_name": [], "brand": [], "rtl_coordinate_group_desc": [], "color_name": [], "color": [], "style_color_id": [], "vendor_case_pack": [], "style": [], "l4_name": [], "l1_name": [], "product_description": [], "article": []}', '{"sort": [{"column": "created_at", "order": "desc"}]}', '2025-11-20', '2025-11-20', False);
[LOCAL DEBUG] Cursor-based SP call with cursor_name: e714eab7-9f6c-4f64-9866-d78dbda60a76
[LOCAL DEBUG] Final input args: ['e714eab7-9f6c-4f64-9866-d78dbda60a76', '{"status": [{"type": "list", "operator": "in", "values": [1]}], "type": [{"type": "list", "operator": "in", "values": [7]}]}', '{"l0_name": [{"type": "list", "operator": "in", "values": ["10-MENS APPAREL"]}], "retail_region": [{"type": "list", "operator": "in", "values": ["GCSEA"]}], "channel": [{"type": "list", "operator": "in", "values": ["FULL PRICE"]}, {"type": "list", "operator": "not in", "values": ["RLE", "RLW", "CME", "CMS", "CMW", "CMFS", "CMCS", "ECOM_DONT_USE", "RLC", "SHARED"]}], "s1_name": [{"type": "list", "operator": "in", "values": ["CHINESE MAINLAND"]}], "dc_flag": [{"type": "list", "operator": "not in", "values": ["true"]}], "l3_name": [], "l2_name": [], "brand": [], "rtl_coordinate_group_desc": [], "color_name": [], "color": [], "style_color_id": [], "vendor_case_pack": [], "store_code": [], "style": [], "l4_name": [], "l1_name": [], "product_description": [], "article": []}', '{"sort": [{"column": "created_at", "order": "desc"}]}', '2025-11-20', '2025-11-20', False]
[LOCAL DEBUG] Calling stored procedure: inventory_smart.past_plans_list
[LOCAL DEBUG] Generated SQL Query: SELECT inventory_smart.past_plans_list('e714eab7-9f6c-4f64-9866-d78dbda60a76', '{"status": [{"type": "list", "operator": "in", "values": [1]}], "type": [{"type": "list", "operator": "in", "values": [7]}]}', '{"l0_name": [{"type": "list", "operator": "in", "values": ["10-MENS APPAREL"]}], "retail_region": [{"type": "list", "operator": "in", "values": ["GCSEA"]}], "channel": [{"type": "list", "operator": "in", "values": ["FULL PRICE"]}, {"type": "list", "operator": "not in", "values": ["RLE", "RLW", "CME", "CMS", "CMW", "CMFS", "CMCS", "ECOM_DONT_USE", "RLC", "SHARED"]}], "s1_name": [{"type": "list", "operator": "in", "values": ["CHINESE MAINLAND"]}], "dc_flag": [{"type": "list", "operator": "not in", "values": ["true"]}], "l3_name": [], "l2_name": [], "brand": [], "rtl_coordinate_group_desc": [], "color_name": [], "color": [], "style_color_id": [], "vendor_case_pack": [], "store_code": [], "style": [], "l4_name": [], "l1_name": [], "product_description": [], "article": []}', '{"sort": [{"column": "created_at", "order": "desc"}]}', '2025-11-20', '2025-11-20', False);

[LOCAL DEBUG] Fetching all results from cursor: 48680156-0cc3-4860-8708-a6cee5d1536b
[LOCAL DEBUG] Fetching all results from cursor: e714eab7-9f6c-4f64-9866-d78dbda60a76
[LOCAL DEBUG] Fetched 0 rows from cursor
[LOCAL DEBUG] Closing cursor: e714eab7-9f6c-4f64-9866-d78dbda60a76
[LOCAL DEBUG] Fetched 153 rows from cursor
[LOCAL DEBUG] Closing cursor: 48680156-0cc3-4860-8708-a6cee5d1536b
[LOCAL DEBUG] Executing rows count query: select rows_count from cache.rows_count(current_setting('myvars.cache_table_id'), '{"sort": [{"column": "created_at", "order": "desc"}]}');
[LOCAL DEBUG] Executing rows count query: select rows_count from cache.rows_count(current_setting('myvars.cache_table_id'), '{"sort": [{"column": "created_at", "order": "desc"}]}');
[LOCAL DEBUG] Rows count result: 0
[LOCAL DEBUG] Returning plain results
[LOCAL DEBUG] Ending transaction (END)
[LOCAL DEBUG] Rows count result: 153
[LOCAL DEBUG] Returning results as tuple with table_results
[LOCAL DEBUG] Ending transaction (END)
[LOCAL DEBUG] execute_store_procedure() - COMPLETED SUCCESSFULLY
================================================================================


================================================================================
[LOCAL DEBUG] execute_query() - STARTING
[LOCAL DEBUG] Tenant: ralph-lauren-apac
[LOCAL DEBUG] Query: select name,attribute_value from global.tenant_attribute_master where application_code = '3' AND name = 'tenant_time_config' 
[LOCAL DEBUG] Return type: dataframe
[LOCAL DEBUG] Using existing connection: False
[LOCAL DEBUG] Timeout: 200
[LOCAL DEBUG] Cursor factory: RealDictCursor
================================================================================
[LOCAL DEBUG] Executing query...
[LOCAL DEBUG] execute_store_procedure() - COMPLETED SUCCESSFULLY
================================================================================

================================================================================
[LOCAL DEBUG] execute_query() - STARTING
[LOCAL DEBUG] Tenant: ralph-lauren-apac
[LOCAL DEBUG] Query: select name,attribute_value from global.tenant_attribute_master where application_code = '3' AND name = 'tenant_time_config' 
[LOCAL DEBUG] Return type: dataframe
[LOCAL DEBUG] Using existing connection: False
[LOCAL DEBUG] Timeout: 200
[LOCAL DEBUG] Cursor factory: RealDictCursor
================================================================================
[LOCAL DEBUG] Executing query...
[LOCAL DEBUG] Query executed successfully
[LOCAL DEBUG] Fetched 1 rows
[LOCAL DEBUG] Column names: ['name', 'attribute_value']
[LOCAL DEBUG] Dataframe shape: (1, 2)
[LOCAL DEBUG] execute_query() - COMPLETED
================================================================================

[LOCAL DEBUG] Query executed successfully
[LOCAL DEBUG] Fetched 1 rows
[LOCAL DEBUG] Column names: ['name', 'attribute_value']
[LOCAL DEBUG] Dataframe shape: (1, 2)
[LOCAL DEBUG] execute_query() - COMPLETED
================================================================================


================================================================================
[LOCAL DEBUG] execute_query() - STARTING
[LOCAL DEBUG] Tenant: ralph-lauren-apac
[LOCAL DEBUG] Query: 
with size_level as (
select
  allocation_code as plan_code,
  article,
  selected_store_group_names,
        size_avi,
        dc_code,
        avg(avail_qty::int)::int inv_avai
        from (
                SELECT
            x.allocation_code,
      x.article,
      x.selected_store_group_names,
      x.dc_code,
      unnest(replace(replace(x.inventory_data::jsonb ->> 'packs_allocated'::text, '['::text, '{'::text), ']'::text, '}'::text)::text[]) AS size_avi,
      unnest(replace(replace(x.inventory_data::jsonb ->> 'packs_available_qty'::text, '['::text, '{'::text), ']'::text, '}'::text)::double precision[]) AS avail_qty
      FROM (
        SELECT
                carfs.allocation_code,
          carfs.article,
          carfs.selected_store_group_names,
          js.items AS dc_code,
          js.value AS inventory_data
          FROM inventory_smart.create_allocation_result_flat_gurobi carfs
          CROSS JOIN LATERAL jsonb_each_text(carfs.pack_dc_allocation) js(items, value)
          where allocation_code in ('9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA13RLPURPLELABEL34KNIT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA13RLPURPLELABEL41NECKWEAR28FURNISHINGS181BOWTIERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA13RLPURPLELABEL47SHORT26SPORTSWEAR289ATHLETICRLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA13RLPURPLELABEL75SPORTSHIRT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA15RRL75SPORTSHIRT26SPORTSWEAR569LONGSLEEVERRL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN17DENIM26SPORTSWEAR5215POCKETPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN20DRESSSHIRT28FURNISHINGS577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN34KNIT21VINTAGE414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN34KNIT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN34KNIT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN41NECKWEAR28FURNISHINGS221NECKTIEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN43OUTERWEAR14NONE2518BOMBERPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR540COATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR561JACKETPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN44PANT26SPORTSWEAR289ATHLETICPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN44PANT26SPORTSWEAR89FLATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN44PANT26SPORTSWEAR90PLEATEDPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN47SHORT26SPORTSWEAR89FLATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN54SPORTCOAT27CLOTHING577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN57SUIT27CLOTHING5152PCSUITPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN58SWEATER26SPORTSWEAR320SLEEVELESSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN59SWIM26SPORTSWEAR577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN69TSHIRT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN69TSHIRT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN75SPORTSHIRT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN75SPORTSHIRT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND13RLPURPLELABEL34KNIT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND13RLPURPLELABEL41NECKWEAR28FURNISHINGS181BOWTIERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND13RLPURPLELABEL47SHORT26SPORTSWEAR289ATHLETICRLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND13RLPURPLELABEL75SPORTSHIRT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND15RRL75SPORTSHIRT26SPORTSWEAR569LONGSLEEVERRL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN20DRESSSHIRT28FURNISHINGS577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN34KNIT21VINTAGE414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN34KNIT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN34KNIT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN41NECKWEAR28FURNISHINGS221NECKTIEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN43OUTERWEAR14NONE2518BOMBERPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR540COATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR561JACKETPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN44PANT26SPORTSWEAR289ATHLETICPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN44PANT26SPORTSWEAR90PLEATEDPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN47SHORT26SPORTSWEAR89FLATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN54SPORTCOAT27CLOTHING577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN58SWEATER26SPORTSWEAR320SLEEVELESSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN59SWIM26SPORTSWEAR577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN69TSHIRT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN75SPORTSHIRT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG13RLPURPLELABEL34KNIT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG13RLPURPLELABEL41NECKWEAR28FURNISHINGS181BOWTIERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG13RLPURPLELABEL47SHORT26SPORTSWEAR289ATHLETICRLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG13RLPURPLELABEL75SPORTSHIRT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG15RRL75SPORTSHIRT26SPORTSWEAR569LONGSLEEVERRL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN20DRESSSHIRT28FURNISHINGS577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN34KNIT21VINTAGE414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN34KNIT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN34KNIT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN41NECKWEAR28FURNISHINGS221NECKTIEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN43OUTERWEAR14NONE2518BOMBERPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR540COATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR561JACKETPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN44PANT26SPORTSWEAR289ATHLETICPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN44PANT26SPORTSWEAR90PLEATEDPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN47SHORT26SPORTSWEAR89FLATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN54SPORTCOAT27CLOTHING577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN58SWEATER26SPORTSWEAR320SLEEVELESSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN59SWIM26SPORTSWEAR577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN69TSHIRT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN75SPORTSHIRT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO13RLPURPLELABEL34KNIT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO13RLPURPLELABEL41NECKWEAR28FURNISHINGS181BOWTIERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO13RLPURPLELABEL47SHORT26SPORTSWEAR289ATHLETICRLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO15RRL75SPORTSHIRT26SPORTSWEAR569LONGSLEEVERRL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN20DRESSSHIRT28FURNISHINGS577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN34KNIT21VINTAGE414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN34KNIT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN34KNIT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN41NECKWEAR28FURNISHINGS221NECKTIEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN43OUTERWEAR14NONE2518BOMBERPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR540COATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR561JACKETPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN44PANT26SPORTSWEAR90PLEATEDPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN47SHORT26SPORTSWEAR89FLATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN54SPORTCOAT27CLOTHING577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN58SWEATER26SPORTSWEAR320SLEEVELESSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN75SPORTSHIRT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA13RLPURPLELABEL34KNIT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA13RLPURPLELABEL41NECKWEAR28FURNISHINGS181BOWTIERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA13RLPURPLELABEL47SHORT26SPORTSWEAR289ATHLETICRLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA13RLPURPLELABEL75SPORTSHIRT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA15RRL75SPORTSHIRT26SPORTSWEAR569LONGSLEEVERRL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN20DRESSSHIRT28FURNISHINGS577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN34KNIT21VINTAGE414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN34KNIT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN34KNIT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN41NECKWEAR28FURNISHINGS221NECKTIEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN43OUTERWEAR14NONE2518BOMBERPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR540COATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR561JACKETPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN44PANT26SPORTSWEAR289ATHLETICPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN44PANT26SPORTSWEAR90PLEATEDPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN47SHORT26SPORTSWEAR89FLATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN54SPORTCOAT27CLOTHING577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN58SWEATER26SPORTSWEAR320SLEEVELESSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN69TSHIRT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN75SPORTSHIRT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE13RLPURPLELABEL34KNIT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE13RLPURPLELABEL41NECKWEAR28FURNISHINGS181BOWTIERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE13RLPURPLELABEL47SHORT26SPORTSWEAR289ATHLETICRLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE13RLPURPLELABEL75SPORTSHIRT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE15RRL75SPORTSHIRT26SPORTSWEAR569LONGSLEEVERRL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN20DRESSSHIRT28FURNISHINGS577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN34KNIT21VINTAGE414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN34KNIT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN34KNIT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN41NECKWEAR28FURNISHINGS221NECKTIEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN43OUTERWEAR14NONE2518BOMBERPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR540COATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR561JACKETPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN44PANT26SPORTSWEAR289ATHLETICPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN44PANT26SPORTSWEAR90PLEATEDPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN47SHORT26SPORTSWEAR89FLATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN54SPORTCOAT27CLOTHING577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN58SWEATER26SPORTSWEAR320SLEEVELESSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN59SWIM26SPORTSWEAR577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN69TSHIRT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN75SPORTSHIRT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN13RLPURPLELABEL34KNIT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN13RLPURPLELABEL41NECKWEAR28FURNISHINGS181BOWTIERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN13RLPURPLELABEL47SHORT26SPORTSWEAR289ATHLETICRLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN13RLPURPLELABEL75SPORTSHIRT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN15RRL75SPORTSHIRT26SPORTSWEAR569LONGSLEEVERRL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN20DRESSSHIRT28FURNISHINGS577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN34KNIT21VINTAGE414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN34KNIT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN34KNIT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN41NECKWEAR28FURNISHINGS221NECKTIEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN43OUTERWEAR14NONE2518BOMBERPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR540COATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR561JACKETPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN44PANT26SPORTSWEAR289ATHLETICPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN44PANT26SPORTSWEAR90PLEATEDPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN47SHORT26SPORTSWEAR89FLATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN54SPORTCOAT27CLOTHING577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN58SWEATER26SPORTSWEAR320SLEEVELESSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN59SWIM26SPORTSWEAR577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN69TSHIRT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN75SPORTSHIRT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2') and is_deleted is null and carfs.created_at >= (now()::date - '1 day'::interval) AND carfs.created_at <= (now()::date + '1 day'::interval)
          GROUP BY carfs.allocation_code, carfs.article, carfs.selected_store_group_names, js.items, js.value
        ) x
      )y
    GROUP BY 1,2,3,4,5
)
,allocated as (
  select article, allocation_code as plan_code, sum(allocated_total) allocated_total
  from inventory_smart.create_allocation_result_flat_gurobi
  where allocation_code in ('9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA13RLPURPLELABEL34KNIT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA13RLPURPLELABEL41NECKWEAR28FURNISHINGS181BOWTIERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA13RLPURPLELABEL47SHORT26SPORTSWEAR289ATHLETICRLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA13RLPURPLELABEL75SPORTSHIRT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA15RRL75SPORTSHIRT26SPORTSWEAR569LONGSLEEVERRL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN17DENIM26SPORTSWEAR5215POCKETPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN20DRESSSHIRT28FURNISHINGS577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN34KNIT21VINTAGE414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN34KNIT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN34KNIT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN41NECKWEAR28FURNISHINGS221NECKTIEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN43OUTERWEAR14NONE2518BOMBERPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR540COATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR561JACKETPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN44PANT26SPORTSWEAR289ATHLETICPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN44PANT26SPORTSWEAR89FLATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN44PANT26SPORTSWEAR90PLEATEDPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN47SHORT26SPORTSWEAR89FLATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN54SPORTCOAT27CLOTHING577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN57SUIT27CLOTHING5152PCSUITPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN58SWEATER26SPORTSWEAR320SLEEVELESSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN59SWIM26SPORTSWEAR577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN69TSHIRT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN69TSHIRT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN75SPORTSHIRT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAAUSTRALIA8POLORALPHLAUREN75SPORTSHIRT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND13RLPURPLELABEL34KNIT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND13RLPURPLELABEL41NECKWEAR28FURNISHINGS181BOWTIERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND13RLPURPLELABEL47SHORT26SPORTSWEAR289ATHLETICRLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND13RLPURPLELABEL75SPORTSHIRT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND15RRL75SPORTSHIRT26SPORTSWEAR569LONGSLEEVERRL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN20DRESSSHIRT28FURNISHINGS577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN34KNIT21VINTAGE414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN34KNIT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN34KNIT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN41NECKWEAR28FURNISHINGS221NECKTIEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN43OUTERWEAR14NONE2518BOMBERPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR540COATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR561JACKETPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN44PANT26SPORTSWEAR289ATHLETICPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN44PANT26SPORTSWEAR90PLEATEDPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN47SHORT26SPORTSWEAR89FLATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN54SPORTCOAT27CLOTHING577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN58SWEATER26SPORTSWEAR320SLEEVELESSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN59SWIM26SPORTSWEAR577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN69TSHIRT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEACHINESEMAINLAND8POLORALPHLAUREN75SPORTSHIRT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG13RLPURPLELABEL34KNIT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG13RLPURPLELABEL41NECKWEAR28FURNISHINGS181BOWTIERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG13RLPURPLELABEL47SHORT26SPORTSWEAR289ATHLETICRLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG13RLPURPLELABEL75SPORTSHIRT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG15RRL75SPORTSHIRT26SPORTSWEAR569LONGSLEEVERRL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN20DRESSSHIRT28FURNISHINGS577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN34KNIT21VINTAGE414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN34KNIT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN34KNIT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN41NECKWEAR28FURNISHINGS221NECKTIEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN43OUTERWEAR14NONE2518BOMBERPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR540COATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR561JACKETPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN44PANT26SPORTSWEAR289ATHLETICPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN44PANT26SPORTSWEAR90PLEATEDPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN47SHORT26SPORTSWEAR89FLATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN54SPORTCOAT27CLOTHING577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN58SWEATER26SPORTSWEAR320SLEEVELESSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN59SWIM26SPORTSWEAR577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN69TSHIRT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAHONGKONG8POLORALPHLAUREN75SPORTSHIRT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO13RLPURPLELABEL34KNIT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO13RLPURPLELABEL41NECKWEAR28FURNISHINGS181BOWTIERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO13RLPURPLELABEL47SHORT26SPORTSWEAR289ATHLETICRLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO15RRL75SPORTSHIRT26SPORTSWEAR569LONGSLEEVERRL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN20DRESSSHIRT28FURNISHINGS577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN34KNIT21VINTAGE414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN34KNIT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN34KNIT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN41NECKWEAR28FURNISHINGS221NECKTIEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN43OUTERWEAR14NONE2518BOMBERPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR540COATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR561JACKETPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN44PANT26SPORTSWEAR90PLEATEDPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN47SHORT26SPORTSWEAR89FLATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN54SPORTCOAT27CLOTHING577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN58SWEATER26SPORTSWEAR320SLEEVELESSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMACAO8POLORALPHLAUREN75SPORTSHIRT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA13RLPURPLELABEL34KNIT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA13RLPURPLELABEL41NECKWEAR28FURNISHINGS181BOWTIERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA13RLPURPLELABEL47SHORT26SPORTSWEAR289ATHLETICRLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA13RLPURPLELABEL75SPORTSHIRT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA15RRL75SPORTSHIRT26SPORTSWEAR569LONGSLEEVERRL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN20DRESSSHIRT28FURNISHINGS577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN34KNIT21VINTAGE414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN34KNIT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN34KNIT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN41NECKWEAR28FURNISHINGS221NECKTIEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN43OUTERWEAR14NONE2518BOMBERPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR540COATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR561JACKETPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN44PANT26SPORTSWEAR289ATHLETICPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN44PANT26SPORTSWEAR90PLEATEDPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN47SHORT26SPORTSWEAR89FLATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN54SPORTCOAT27CLOTHING577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN58SWEATER26SPORTSWEAR320SLEEVELESSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN69TSHIRT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEAMALAYSIA8POLORALPHLAUREN75SPORTSHIRT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE13RLPURPLELABEL34KNIT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE13RLPURPLELABEL41NECKWEAR28FURNISHINGS181BOWTIERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE13RLPURPLELABEL47SHORT26SPORTSWEAR289ATHLETICRLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE13RLPURPLELABEL75SPORTSHIRT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE15RRL75SPORTSHIRT26SPORTSWEAR569LONGSLEEVERRL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN20DRESSSHIRT28FURNISHINGS577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN34KNIT21VINTAGE414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN34KNIT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN34KNIT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN41NECKWEAR28FURNISHINGS221NECKTIEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN43OUTERWEAR14NONE2518BOMBERPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR540COATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR561JACKETPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN44PANT26SPORTSWEAR289ATHLETICPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN44PANT26SPORTSWEAR90PLEATEDPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN47SHORT26SPORTSWEAR89FLATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN54SPORTCOAT27CLOTHING577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN58SWEATER26SPORTSWEAR320SLEEVELESSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN59SWIM26SPORTSWEAR577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN69TSHIRT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEASINGAPORE8POLORALPHLAUREN75SPORTSHIRT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN13RLPURPLELABEL34KNIT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN13RLPURPLELABEL41NECKWEAR28FURNISHINGS181BOWTIERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN13RLPURPLELABEL47SHORT26SPORTSWEAR289ATHLETICRLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN13RLPURPLELABEL75SPORTSHIRT26SPORTSWEAR414SHORTSLEEVERLPURPLELABEL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN15RRL75SPORTSHIRT26SPORTSWEAR569LONGSLEEVERRL20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN20DRESSSHIRT28FURNISHINGS577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN34KNIT21VINTAGE414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN34KNIT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN34KNIT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN41NECKWEAR28FURNISHINGS221NECKTIEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN43OUTERWEAR14NONE2518BOMBERPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR540COATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN43OUTERWEAR26SPORTSWEAR561JACKETPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN44PANT26SPORTSWEAR289ATHLETICPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN44PANT26SPORTSWEAR90PLEATEDPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN47SHORT26SPORTSWEAR89FLATPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN54SPORTCOAT27CLOTHING577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN58SWEATER26SPORTSWEAR320SLEEVELESSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN58SWEATER26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN59SWIM26SPORTSWEAR577NOSUBCLASSPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN69TSHIRT26SPORTSWEAR414SHORTSLEEVEPOLORALPHLAUREN20_2','9_1_GCSEA_20251119T170008_FULL_PRICE_10MENSAPPARELGCSEATAIWAN8POLORALPHLAUREN75SPORTSHIRT26SPORTSWEAR569LONGSLEEVEPOLORALPHLAUREN20_2') and is_deleted is NULL and created_at >= (now()::date - '1 day'::interval) AND created_at <= (now()::date + '1 day'::interval)
  group by 1,2)
, available as (
  select article, plan_code, selected_store_group_names, sum(inv_avai)::int as inv_avai
  from size_level group by 1,2,3)
,final_result as (
  select plan_code, article, selected_store_group_names, coalesce(allocated_total,0) allocated_total, coalesce(inv_avai,0) inv_avai
  from available full join allocated using (plan_code, article))
select fr.*, pm.* from final_result fr left join inventory_smart.ph_master pm using (article) where allocated_total > 0

[LOCAL DEBUG] Return type: dataframe
[LOCAL DEBUG] Using existing connection: False
[LOCAL DEBUG] Timeout: 200
[LOCAL DEBUG] Cursor factory: RealDictCursor
================================================================================
[LOCAL DEBUG] Executing query...
[LOCAL DEBUG] Query executed successfully
[LOCAL DEBUG] Fetched 471 rows
[LOCAL DEBUG] Column names: ['plan_code', 'article', 'selected_store_group_names', 'allocated_total', 'inv_avai', 'l0_name', 'l1_name', 'l2_name', 'l3_name', 'l4_name', 'clearance', 'style', 'ph_code', 'article', 'channel', 'color', 'foe_year', 'year', 'season', 'brand', 'color_name', 'rtl_coordinate_group_desc', 'coordinate_cd', 'supersede_flag', 'launch_date', 'article_status_tag', 'product_description', 'model_description', 'style_color_id', 'vendor_case_pack', 'product_code_size_map', 'sizes', 'product_codes', 'pack_configuration']
[LOCAL DEBUG] Dataframe shape: (471, 33)
[LOCAL DEBUG] execute_query() - COMPLETED
================================================================================
INFO:     127.0.0.1:55380 - "POST /api/v2/inventory-smart/dashboard/alerts HTTP/1.1" 200 OK
```


you can find so many things from the logs 

##### Reports to looks at 
###### mtp-database : 
```
/Users/rahulmishra/Desktop/mtp-database
```
- All the stored procedure which are being called in the API is stored here inside the folder of functions 
- Configurations are stored here in the form of csv. 
- The data for each client is seperated by the folder for example right now we are working with the `ralph_lauren_apac` , so functions and the config for this client is stored in here 
- If some function is not present then it must be taking from the : `/Users/rahulmishra/Desktop/mtp-database/database/schemas/global/functions` -> common for everyone 
- So if we want to make something client specific we can take it from - `/Users/rahulmishra/Desktop/mtp-database/database/schemas/global/functions` and create the function inside the client or tenant folder

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


Please help me find where is the exact place I should handle this country filtering , thanks 





---
##### Linked Notes
[[DD Screen - Questions]]
[[DD Screen - Reproducing the issue]]

---
[[DD Screen - Fix]]




