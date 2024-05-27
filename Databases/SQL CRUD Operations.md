# CRUD Operations

## Create

Add rows with `INSERT INTO`

```sql
INSERT INTO table_name(column_1, column_2) VALUES(value1, value2);
```

## Read

To view everything in a table use,

```sql
SELECT * FROM <TableName>
```

To view the rows from a specific column

```sql
SELECT columns FROM table_name;
```

You can also add conditions to narrow down your search

```sql
SELECT columns FROM table_name WHERE condition;
```

## Update

Modify a row with

```sql
UPDATE table_name SET column_name=new_value WHERE condition;
```

For example,

```sql
UPDATE courses
SET published_date = '2020-08-01' 
WHERE course_id = 3;
```

## Delete

Remove a row from a table with

```sql
DELETE FROM table_name WHERE condition;
```