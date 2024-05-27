# Altering Tables

Create a column using `ALTER TABLE`.

```sql
ALTER TABLE table_name ADD COLUMN column_name DATATYPE;
```

Delete a column with,

```sql
ALTER TABLE table_name DROP COLUMN column_name;
```

Rename a column with,

```sql
ALTER TABLE table_name 
RENAME COLUMN column_name TO new_column_name;
```

Enforce non-null columns withm

```sql
CREATE TABLE table_name(
   ...
   column_name data_type NOT NULL,
   ...
);
```

Change the datatype of a column with,

```sql
ALTER TABLE table_name
ALTER COLUMN column_name 
[SET DATA] TYPE new_data_type;
```

For example,

```sql
ALTER TABLE assets 
ALTER COLUMN name TYPE VARCHAR(255);
```
