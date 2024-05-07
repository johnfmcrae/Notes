# PostgreSQL Basics

PostgreSQL is a relational database management system that supports relational (SQL) and non-relational (JSON) data.

## Connecting to and Viewing a Database 

Start PostgreSQL on the command line with the `psql` command.

```bash
$ psql --username=<username> --dbname=<dbname>
```

View the available databases with `\l`.

Connect to a database with `\c`.

```bash
postgres => \c my_database
```

Create a database with `CREATE DATABASE <name>`.

Once connected to a database, create a table with `CREATE TABLE <name>`.

View all tables with `\d`. View table details with `\d <table name>`

## Altering Tables

Create a column using `ALTER TABLE`.

```sql
ALTER TABLE table_name ADD COLUMN column_name DATATYPE;
```

Delete a column with,

```sql
ALTER TABLE table_name DROP COLUMN column_name;
```

## CRUD Operations

### Create

Add rows with `INSERT INTO`

```sql
INSERT INTO table_name(column_1, column_2) VALUES(value1, value2);
```

### Read

To view everything in a table use,

```sql
SELECT * FROM <TableName>
```

### Update

Modify a row with

```sql
UPDATE table_name SET column_name=new_value WHERE condition;
```

### Delete

Remove a row from a table with

```sql
DELETE FROM table_name WHERE condition;
```

## Data Types

See the PostgreSQL [documentation](https://www.postgresql.org/docs/current/datatype.html) for a complete list of data types.

Here are some of the classics:

| Data Type                 | Aliases            | Description                                                        |
|---------------------------|--------------------|--------------------------------------------------------------------|
| boolean                   | bool               | logical Boolean                                                    |
| integer                   | int, int4          | signed four-byte integer                                           |
| numeric [ (p, s) ]        | decimal [ (p, s) ] | decimal number with selectable precision (p) and scale (s)         |
| serial                    | serial4            | auto-incrementing four-byte integer                                |
| character varying [ (n) ] | varchar [ (n) ]    | character string of length n                                       |
| text                      |                    | variable-length character string                                   |
| date                      |                    | calendar date with year, month, and day (accepts multiple formats) |
| money                     |                    | currency amount                                                    |

The *precision* in the numeric type refers to the number of significant figures. *Scale* refers to the number of decimal places.