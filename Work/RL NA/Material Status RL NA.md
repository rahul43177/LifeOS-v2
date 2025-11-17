### The SP using : 
```sql
select * from global.product_status_list ('{"is_deleted": [{"type": "list", "operator": "in", "values": [false]}]}', '{"l0_name": [{"type": "list", "operator": "in", "values": ["33-MENS APPAREL"]}], "l1_name": [{"type": "list", "operator": "in", "values": ["33-M CLOTHING"]}], "brand": [], "color": [], "size": [], "l4_name": [], "article": [], "style_color_id": [], "l3_name": [], "l2_name": [], "supersede_flag": []}', '{"search": [], "sort": [{"column": "product_code", "order": "asc"}], "range": [], "limit": {"limit": 10, "page": 1, "offset": 0}, "query_type": "AND", "download_rows_limit_check": false}', '{"l0_name": [{"type": "list", "operator": "in", "values": ["33-MENS APPAREL"]}], "attribute_name": [{"type": "list", "operator": "in", "values": ["status"]}]}')

--output of the query : 
ffdf l0_name
{channel}
{l0_name,l1_name,l2_name}
here
size
_attr_cols {size}
after loop<NULL>
here
brand
_attr_cols {size,brand}
after loop<NULL>
here
color
_attr_cols {size,brand,color}
after loop<NULL>
here
article
_attr_cols {size,brand,color,article}
after loop<NULL>
here
l0_name
_attr_cols {size,brand,color,article,l0_name}
after loop1
here
l1_name
_attr_cols {size,brand,color,article,l0_name,l1_name}
after loop1
here
l2_name
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name}
after loop0
here
l3_name
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name,l3_name}
after loop0
here
l4_name
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name,l3_name,l4_name}
after loop0
here
is_deleted
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name,l3_name,l4_name,is_deleted}
after loop1
here
product_name
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name,l3_name,l4_name,is_deleted,product_name}
after loop0
here
style_color_id
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name,l3_name,l4_name,is_deleted,product_name,style_color_id}
after loop0
here
supersede_flag
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name,l3_name,l4_name,is_deleted,product_name,style_color_id,supersede_flag}
after loop0
here
product_description
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name,l3_name,l4_name,is_deleted,product_name,style_color_id,supersede_flag,product_description}
after loop0
here
reference_product_codes
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name,l3_name,l4_name,is_deleted,product_name,style_color_id,supersede_flag,product_description,reference_product_codes}
after loop0
here
replacement_product_codes
_attr_cols {size,brand,color,article,l0_name,l1_name,l2_name,l3_name,l4_name,is_deleted,product_name,style_color_id,supersede_flag,product_description,reference_product_codes,replacement_product_codes}
after loop0
 combination <NULL>
{channel}
{l0_name,l1_name,l2_name}
_query_pa SELECT size, brand, color, article, l0_name, l1_name, l2_name, l3_name, l4_name, is_deleted, product_name, style_color_id, supersede_flag, product_description, reference_product_codes, replacement_product_codes, product_code FROM "global".product_attributes_filter  WHERE (l0_name::varchar = any('{"33-MENS APPAREL"}'::varchar[])) AND (l1_name::varchar = any('{"33-M CLOTHING"}'::varchar[])) AND (is_deleted::varchar = any('{false}'::varchar[]))s
 ORDER BY product_code asc nulls last , LIMIT 10 OFFSET 0,
 WHERE (l0_name::varchar = any('{"33-MENS APPAREL"}'::varchar[])) AND (attribute_name::varchar = any('{"status"}'::varchar[]))
{'size',X.size,'brand',X.brand,'color',X.color,'article',X.article,'l0_name',X.l0_name,'l1_name',X.l1_name,'l2_name',X.l2_name,'l3_name',X.l3_name,'l4_name',X.l4_name,'is_deleted',X.is_deleted,'style_color_id',X.style_color_id,'supersede_flag',X.supersede_flag,'aggregation_code',X.article}
SELECT size, brand, color, article, l0_name, l1_name, l2_name, l3_name, l4_name, is_deleted, product_name, style_color_id, supersede_flag, product_description, reference_product_codes, replacement_product_codes, product_code FROM "global".product_attributes_filter  WHERE (l0_name::varchar = any('{"33-MENS APPAREL"}'::varchar[])) AND (l1_name::varchar = any('{"33-M CLOTHING"}'::varchar[])) AND (is_deleted::varchar = any('{false}'::varchar[]))
 with cte as  (SELECT size, brand, color, article, l0_name, l1_name, l2_name, l3_name, l4_name, is_deleted, product_name, style_color_id, supersede_flag, product_description, reference_product_codes, replacement_product_codes, product_code FROM "global".product_attributes_filter  WHERE (l0_name::varchar = any('{"33-MENS APPAREL"}'::varchar[])) AND (l1_name::varchar = any('{"33-M CLOTHING"}'::varchar[])) AND (is_deleted::varchar = any('{false}'::varchar[]))) 
							select
		  					   X.product_code,
		  					   X.product_name,
		  					   X.replacement_product_codes as replacement_product_codes, 
		  					   X.reference_product_codes as reference_product_codes,
		  					   json_build_object('size' ,X.size ,'brand' ,X.brand ,'color' ,X.color ,'article' ,X.article ,'l0_name' ,X.l0_name ,'l1_name' ,X.l1_name ,'l2_name' ,X.l2_name ,'l3_name' ,X.l3_name ,'l4_name' ,X.l4_name ,'is_deleted' ,X.is_deleted ,'style_color_id' ,X.style_color_id ,'supersede_flag' ,X.supersede_flag ,'aggregation_code' ,X.article),
		  					   b.status_obj as status_obj,
		  					   X.product_description,
							   b.updated_by,
							   b.change_time
		  					FROM cte X 
							join (select json_agg(jsonb_build_object('status_start_time', concat(start_time)::varchar, 'status_end_time', concat(end_time)::varchar, 'status', attribute_value , 'time_attr_id', product_time_attr_id) ORDER BY start_time) status_obj, product_code, max(um.name) as updated_by, max(pg_xact_commit_timestamp(pta.xmin)) as change_time from 
						                      	"global".product_time_attributes pta left join "global".user_master um on pta.updated_by = um.user_code  WHERE (l0_name::varchar = any('{"33-MENS APPAREL"}'::varchar[])) AND (attribute_name::varchar = any('{"status"}'::varchar[]))
						                      	group by product_code)b using(product_code)  ORDER BY product_code asc nulls last  LIMIT 10 OFFSET 0

						                      	
						                      	
-- The SP definition : 
						                      	
```

### formatter 
changed 

### Checking the changes 
1. API response 
2. Formatter - MM/DD/YYYY
3. 