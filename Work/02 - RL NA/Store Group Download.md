## Requirements : 
We want the updated at and created at to be in the MM-DD-YYYY , instead of current YYYY-MM-DD 
Can you please help me do it , thanks 
## SP called : 
```sql 
SELECT * 
FROM global.store_group_list_aggregation_download_main(
  '33f36527-9113-42ae-ba84-85102a4594a2',
  '{"channel": [{"type": "list", "operator": "in", "values": ["PFS"]}]}',
  '{}',
  '{}',
  '{"search": [], "range": [], "query_type": "AND", "download_rows_limit_check": false}',
  '{retail_facility_code, store_name, country}'
);




--output 
 WHERE (channel::varchar = any('{"PFS"}'::varchar[])) AND (is_deleted::bool = 'false'::bool)
1,3
 ,sgmNew.retail_facility_code AS retail_facility_code, sgmNew.store_name AS store_name, sgmNew.country AS country, ,retail_facility_code, store_name, country, ,retail_facility_code, store_name, country, store_code
,,
 _main_filter_cnt : 1
 _attr_filter_cnt : 3 
 WHERE (active::bool = 'true'::bool)
{channel}
{l0_name,l1_name,l2_name}
 combination <NULL>
{channel}
{l0_name,l1_name,l2_name}
_query_pa SELECT store_code FROM "global".store_attributes_filter s
_filter_con JOIN (SELECT sgm.sg_code FROM (SELECT * FROM global.store_master WHERE (active::bool = 'true'::bool)) x JOIN (SELECT store_code FROM "global".store_attributes_filter ) y on x.store_code = y.store_code join "global".store_groups_mapping sgm ON x.store_code = sgm.store_code group by sgm.sg_code) f ON sg.sg_code = f.sg_code


SELECT * FROM (
				select
				sg.name as name,
				sg.special_classification as special_classification,
				sg.channel,
				sg.created_at,
				sg.updated_at,
				um.name as created_by,
				umup.name as updated_by
				 ,sgmNew.retail_facility_code AS retail_facility_code, sgmNew.store_name AS store_name, sgmNew.country AS country,
				(case
					when sg.extra is not null then sg.extra
					else 'FALSE'
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
					sg.extra->>'is_uploaded' as extra
				from
					"global".store_groups sg  WHERE (channel::varchar = any('{"PFS"}'::varchar[])) AND (is_deleted::bool = 'false'::bool)  ) sg
					left join
						(
						select
							user_code,
							name 
						from
							"global".user_master um 
						where
							(
								um.is_deleted::bool = 'false'::bool
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
								um.is_deleted::bool = 'false'::bool
							)
						)
						umup 
						on sg.updated_by = umup.user_code JOIN (SELECT sgm.sg_code FROM (SELECT * FROM global.store_master WHERE (active::bool = 'true'::bool)) x JOIN (SELECT store_code FROM "global".store_attributes_filter ) y on x.store_code = y.store_code join "global".store_groups_mapping sgm ON x.store_code = sgm.store_code group by sgm.sg_code) f ON sg.sg_code = f.sg_code 
			
					left join
						(
						select
							sg_code,
							channel
							 ,retail_facility_code, store_name, country
						from
							"global".store_groups_mapping 
							join
								(
									select
										channel
										 ,retail_facility_code, store_name, country, store_code 
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
							 ,retail_facility_code, store_name, country
						)
						sgmNew 
						on sg.sg_code = sgmNew.sg_code 
			) X 
			
			
--response 
name       |special_classification|channel|created_at                   |updated_at                   |created_by  |updated_by  |retail_facility_code|store_name                        |country                 |extra|
-----------+----------------------+-------+-----------------------------+-----------------------------+------------+------------+--------------------+----------------------------------+------------------------+-----+
Default PFS|manual                |PFS    |2023-05-19 15:39:20.647 +0530|2024-11-19 14:58:52.490 +0530|Testtesttest|Testtesttest|00001               |LAKE BUENA VISTA                  |UNITED STATES OF AMERICA|FALSE|
Default PFS|manual                |PFS    |2023-05-19 15:39:20.647 +0530|2024-11-19 14:58:52.490 +0530|Testtesttest|Testtesttest|00003               |FREEPORT                          |UNITED STATES OF AMERICA|FALSE|
Default PFS|manual                |PFS    |2023-05-19 15:39:20.647 +0530|2024-11-19 14:58:52.490 +0530|Testtesttest|Testtesttest|00004               |AURORA FARMS                      |UNITED STATES OF AMERICA|FALSE|
Default PFS|manual                |PFS    |2023-05-19 15:39:20.647 +0530|2024-11-19 14:58:52.490 +0530|Testtesttest|Testtesttest|00005               |DEER PARK                         |UNITED STATES OF AMERICA|FALSE|
Default PFS|manual                |PFS    |2023-05-19 15:39:20.647 +0530|2024-11-19 14:58:52.490 +0530|Testtesttest|Testtesttest|00007               |LEESBURG                          |UNITED STATES OF AMERICA|FALSE|
Default PFS|manual                |PFS    |2023-05-19 15:39:20.647 +0530|2024-11-19 14:58:52.490 +0530|Testtesttest|Testtesttest|00009               |MANCHESTER -CLOSED                |UNITED STATES OF AMERICA|FALSE|
Default PFS|manual                |PFS    |2023-05-19 15:39:20.647 +0530|2024-11-19 14:58:52.490 +0530|Testtesttest|Testtesttest|00013               |NEW RIVER                         |UNITED STATES OF AMERICA|FALSE|
Default PFS|manual                |PFS    |2023-05-19 15:39:20.647 +0530|2024-11-19 14:58:52.490 +0530|Testtesttest|Testtesttest|00014               |SAWGRASS MILLS                    |UNITED STATES OF AMERICA|FALSE|

```


## The SP definition : 
Location : 
```
/Users/rahulmishra/Desktop/mtp-database/database/ralph_lauren_na/schemas/global/functions/store_group_list_aggregation_download_main.sql
```



## SP being used : 
![[../../attachments/Store Group Download - sp used.png]]


```
SP name : global.store_group_list_aggregation_download_main
SP Inputs ['{"channel": [{"type": "list", "operator": "in", "values": ["PFS"]}]}', '{}', '{}', '{"search": [], "range": [], "query_type": "AND", "download_rows_limit_check": false}', ['retail_facility_code', 'store_name', 'country']]
```


## questions 
1. Where should we update the `created_at` / `updated_at` timezone and formatting?
   - a) Inside the SQL stored procedure output - Yes inside the SQL Stored procedure whose name from the debugger I got it :  global.store_group_list_aggregation_download_main
   - 
Little more on the formatting , I want the date to be in MM-DD-YYYY and the timezone should be : EDT

## Old query
```sql

--old query 
SELECT *
FROM
  (SELECT x.*,
          sgtg.grade AS store_grade
   FROM 
     (SELECT sg.name AS name,
             sg.special_classification AS special_classification,
             sg.channel,
             sg.created_at,
             sg.updated_at,
             um.name AS created_by,
             umup.name AS updated_by,
             sgmNew.store_code AS store_code,
             sgmNew.store_banner AS store_banner,
             sgmNew.store_name AS store_name,
             sgmNew.combo_store AS combo_store,
             sgmNew.shop_in_shop AS shop_in_shop,
             sgmNew.state AS state,
             sgmNew.city AS city
      FROM
        (SELECT sg_code,
                sg.name,
                sg.special_classification,
                sg.created_at,
                sg.updated_at,
                sg.created_by,
                sg.channel,
                sg.updated_by
         FROM "global".store_groups sg
         WHERE (channel::varchar = any('{"KAY"}'::varchar[]))
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
                store_code,
                store_banner,
                store_name,
                combo_store,
                shop_in_shop,
                state,
                city,
                channel
         FROM "global".store_groups_mapping
         JOIN
           (SELECT store_code,
                   store_banner,
                   store_name,
                   combo_store,
                   shop_in_shop,
                   state,
                   city,
                   channel
            FROM global.store_attributes_filter
            WHERE active) saf USING (store_code)
         WHERE sg_code IS NOT NULL
         GROUP BY sg_code,
                  store_code,
                  store_banner,
                  store_name,
                  combo_store,
                  shop_in_shop,
                  state,
                  city,
                  channel) sgmNew ON sg.sg_code = sgmNew.sg_code) x
   LEFT JOIN "global".store_groups_to_grade sgtg ON x.store_code = sgtg.store_code
   AND x.name = sgtg.name) final_result;		
```

## new optimised query 
```sql 
--- new query (FIXED to match old query order)
WITH
active_stores AS (
    SELECT
        store_code,
        store_banner,
        store_name,
        combo_store,
        shop_in_shop,
        state,
        city,
        channel
    FROM global.store_attributes_filter
    WHERE active = true
),
valid_store_groups AS (
    SELECT
        sg_code,
        name,
        special_classification,
        created_at,
        updated_at,
        created_by,
        updated_by,
        channel
    FROM global.store_groups
    WHERE channel = 'KAY'
      AND is_deleted = false
),
-- Limit store_groups_mapping early by joining only active stores
filtered_mapping AS (
    SELECT  -- REMOVED DISTINCT ON
        sgm.sg_code,
        sgm.store_code,
        saf.store_banner,
        saf.store_name,
        saf.combo_store,
        saf.shop_in_shop,
        saf.state,
        saf.city,
        saf.channel
    FROM global.store_groups_mapping sgm
    JOIN active_stores saf
      ON sgm.store_code = saf.store_code
    WHERE sgm.sg_code IS NOT NULL
    GROUP BY sgm.sg_code,  -- GROUP BY only (like old query)
             sgm.store_code,
             saf.store_banner,
             saf.store_name,
             saf.combo_store,
             saf.shop_in_shop,
             saf.state,
             saf.city,
             saf.channel
),
-- Limit grades to only relevant stores
filtered_grades AS (
    SELECT sgtg.store_code, sgtg.name, sgtg.grade
    FROM global.store_groups_to_grade sgtg
    WHERE EXISTS (
        SELECT 1
        FROM global.store_groups_mapping sgm
        WHERE sgm.store_code = sgtg.store_code
          AND sgm.sg_code IS NOT NULL
    )
),
valid_users AS (
    SELECT user_code, name
    FROM global.user_master
    WHERE is_deleted = false
)
SELECT
    sg.name,
    sg.special_classification,
    sg.channel,
    sg.created_at,
    sg.updated_at,
    u1.name AS created_by,
    u2.name AS updated_by,
    fm.store_code,
    fm.store_banner,
    fm.store_name,
    fm.combo_store,
    fm.shop_in_shop,
    fm.state,
    fm.city,
    fg.grade AS store_grade
FROM valid_store_groups sg
JOIN filtered_mapping fm
  ON sg.sg_code = fm.sg_code
LEFT JOIN filtered_grades fg
  ON fm.store_code = fg.store_code
  AND sg.name = fg.name
LEFT JOIN valid_users u1
  ON sg.created_by = u1.user_code
LEFT JOIN valid_users u2
  ON sg.updated_by = u2.user_code;
--102,433

```
