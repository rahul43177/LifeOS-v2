## Issue
- So clients have reported some issues in the download for the store group 
- So the download data for the csv is generated through the postgresql query 
- So my lead has given me a optimised query for it. 

## Request from the lead 
My lead has askend me to check weather : 
1. Both the queries are giving the same data or not ? 
2. If the order of the columns are correct or not ? 
He gave a tip saying , please use `order by` or `group by` so that you can validate 

## old query 
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
--- new query  
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
    SELECT DISTINCT ON (sgm.sg_code, sgm.store_code)
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
    ORDER BY sgm.sg_code, sgm.store_code
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

```



1. Can you please help me with the adding group by and all , then I will run the data and check weather both the queries are giving the same data or not 
2. I will also check weather the column orders are correct or not ?
3. Basically we want to check weather some join is wrong or not , or if we pointed to some other table or column in the optimised new query 

Please help me by analysing it in depth, thanks .