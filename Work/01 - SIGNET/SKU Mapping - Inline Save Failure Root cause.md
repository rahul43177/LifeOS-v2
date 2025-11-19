# 🎯 ROOT CAUSE CONFIRMED!

Perfect! The database query results clearly show the issue. Let me break down what's happening:

---

## 📊 Key Findings from Query Results

### TEST Database (BROKEN) ❌

**Query 1 (Parent Table):**
mapping_code | default_value: (EMPTY) | is_not_null: true

**Query 2 (Partition):**
mapping_code | default_value: (EMPTY) | is_not_null: true

**Query 4 (All Partitions):**
ALL partitions show: mapping_code_default: (EMPTY)

---

### UAT Database (WORKING) ✅

**Query 1 (Parent Table):**
mapping_code | default_value: nextval('global.product_mapping_product_store_mapping_code_seq'::regclass) | is_not_null: true

**Query 2 (Partition):**
mapping_code | default_value: nextval('global.product_mapping_product_store_mapping_code_seq'::regclass) | is_not_null: true

**Query 4 (All Partitions):**
ALL partitions show: mapping_code_default: nextval('global.product_mapping_product_store_mapping_code_seq'::regclass)

---

## 🔴 THE EXACT PROBLEM

In TEST environment:

* The parent table global.product_mapping_product_store is missing the sequence default on mapping_code
* ALL partition tables are missing the sequence default
* The column is NOT NULL but has NO DEFAULT VALUE
* When INSERT tries to omit mapping_code, it gets NULL → NOT NULL violation

In UAT environment:

* Both parent and ALL partitions have the proper sequence default: nextval('global.product_mapping_product_store_mapping_code_seq'::regclass)
* When INSERT omits mapping_code, PostgreSQL auto-generates it from the sequence

---

## 📋 WHAT TO TELL THE DATA TEAM

### Issue Summary

The TEST database for signet tenant is missing sequence defaults on the mapping_code column for the global.product_mapping_product_store table
and ALL its partitions. This causes inline-save to fail for ALL products/SKUs, not just specific ones.

---

### Comparison: TEST vs UAT

| Aspect                            | TEST (Broken)           | UAT (Working)      |
| --------------------------------- | ----------------------- | ------------------ |
| Parent table mapping_code default | MISSING                 | nextval('..._seq') |
| Partition mapping_code default    | MISSING                 | nextval('..._seq') |
| ALL partitions affected           | YES - ALL 67 partitions | All have sequence  |
| Insert behavior                   | NULL → Error            | Auto-generated     |

---

### Files/Areas Affected

* Table: global.product_mapping_product_store (parent + all 67 partitions)
* Schema File: `/Users/rahulmishra/Desktop/mtp-database/database/schemas/global/tables/product_mapping_product_store.sql`
* Likely Cause: TEST database was rebuilt/restored from a schema dump that didn't preserve the SERIAL sequence defaults, OR a migration was applied incorrectly

---

## 🔧 THE FIX FOR DATA TEAM

### Step 1: Fix the Parent Table

```sql
-- Add sequence default to parent table
ALTER TABLE global.product_mapping_product_store
ALTER COLUMN mapping_code SET DEFAULT nextval('global.product_mapping_product_store_mapping_code_seq'::regclass);
```

---

### Step 2: Fix ALL Partition Tables

```sql
-- Fix all partitions at once using a DO block
DO $$
DECLARE
    partition_rec RECORD;
BEGIN
    FOR partition_rec IN
        SELECT c.relname AS partition_name
        FROM pg_class c
        JOIN pg_inherits i ON i.inhrelid = c.oid
        WHERE i.inhparent = 'global.product_mapping_product_store'::regclass
    LOOP
        EXECUTE format(
            'ALTER TABLE global.%I ALTER COLUMN mapping_code SET DEFAULT
nextval(''global.product_mapping_product_store_mapping_code_seq''::regclass)',
            partition_rec.partition_name
        );
        RAISE NOTICE 'Fixed partition: %', partition_rec.partition_name;
    END LOOP;
END $$;
```

---

### Step 3: Verify the Fix

```sql
-- Verify parent table
SELECT
    pg_get_expr(d.adbin, d.adrelid) AS mapping_code_default
FROM pg_attribute a
LEFT JOIN pg_attrdef d ON a.attrelid = d.adrelid AND a.attnum = d.adnum
WHERE a.attrelid = 'global.product_mapping_product_store'::regclass
    AND a.attname = 'mapping_code';
-- Should return: nextval('global.product_mapping_product_store_mapping_code_seq'::regclass)
```

```sql
-- Verify all partitions have the default
SELECT
    c.relname AS partition_name,
    CASE
        WHEN pg_get_expr(d.adbin, d.adrelid) IS NOT NULL THEN 'HAS DEFAULT'
        ELSE 'MISSING DEFAULT'
    END AS status
FROM pg_class c
JOIN pg_inherits i ON i.inhrelid = c.oid
LEFT JOIN pg_attribute a ON a.attrelid = c.oid AND a.attname = 'mapping_code'
LEFT JOIN pg_attrdef d ON d.adrelid = c.oid AND d.adnum = a.attnum
WHERE i.inhparent = 'global.product_mapping_product_store'::regclass
ORDER BY c.relname;
-- All should show 'HAS DEFAULT'
```

---

## 🔍 ROOT CAUSE ANALYSIS

Most likely scenarios:

1. Schema Restore Issue: TEST database was restored from a SQL dump where the SERIAL defaults weren't properly captured
2. Migration Mismatch: A migration ran in UAT that added the defaults, but wasn't applied to TEST
3. Table Recreation: The table was dropped and recreated in TEST without properly setting up SERIAL column defaults
4. ALTER TABLE Command: Someone ran an ALTER TABLE in TEST that removed the defaults

### When did this break?

Since you mentioned "it worked before - recent regression", check:

* Recent database restores/refreshes in TEST environment
* Recent migrations applied only to UAT but not TEST
* Any manual schema changes in the last few weeks

---

## ✅ NEXT STEPS

1. Data Team: Apply the fix SQL (Step 1 & 2 above) to TEST database
2. Verification: Run Step 3 queries to confirm all partitions are fixed
3. Test: Retry the inline-save API in TEST environment
4. Root Cause: Investigate why TEST and UAT schemas diverged
5. Prevention: Ensure future schema changes are applied consistently across environments

---

## 📄 Summary for Ticket/JIRA

**Title:** TEST Database Missing Sequence Defaults on product_mapping_product_store Table

**Description:**
The mapping_code column in global.product_mapping_product_store and all its partition tables in the TEST database is missing the sequence
default value. This causes all inline-save operations to fail with a NOT NULL violation. UAT has the proper sequence defaults configured. Need
to align TEST schema with UAT.

**Impact:** ALL product-to-store inline-save operations fail in TEST environment for signet tenant

**Priority:** HIGH - Blocking all inline-save testing

**Fix:** Run ALTER TABLE commands to add sequence defaults to parent and all partition tables (SQL provided above)

---

Would you like me to convert this into an **Obsidian callout-style note**, or generate a **clean PDF**, or **add frontmatter metadata** (tags, date, project key)?
