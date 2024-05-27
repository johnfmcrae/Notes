# Table References and Joins

Use references to establish relationships between tables and joins to query those relationships.

## Keys

Uniquely identify each row in a table with a *primary key*. Add a primary key with,

```sql
ALTER TABLE table_name ADD PRIMARY KEY(column_name);
```

Reference another table using a *foreign key*. Add a foreign key with,

```sql
ALTER TABLE table_name ADD FOREIGN KEY(current_table_column) REFERENCES referenced_table(referenced_column_name);
```

You can also make the new column and refer it to a foreign table in one step,

```sql
ALTER TABLE table_name ADD COLUMN column_name DATATYPE REFERENCES referenced_table_name(referenced_column_name);
```

Enforce a one-to-one relationship between a foreign key and the table it references with,

```sql
ALTER TABLE table_name ADD UNIQUE(column_name);
```

Primary keys must be unique. SQL will enforce uniqueness via the database management system (DBMS). Sometimes, a single column may not de sufficient to enforce uniqueness for a given key. In that case, you can define a **composite** primary key by assigning two or more columns, which will always have a unique combination,

```sql
ALTER TABLE table_name ADD PRIMARY KEY(column_name1, column_name2s);
```

This also means that the DBMS will throw an error if you try to insert a pair of rows that already exist in the table.

## One-to-Many Relationships

Define one-to-many relationships by pointing the children to parent. For example

```sql
CREATE TABLE author (
  id SERIAL PRIMARY KEY,
  name TEXT
)

CREATE TABLE article (
  id SERIAL PRIMARY KEY,
  author_id INT NOT NULL,
  title TEXT NOT NULL,
  content TEXT NOT NULL,
  CONSTRAINT fk_author FOREIGN KEY(author_id) REFERENCES author(id)
)
```

An author can have multiple articles and in my mind, I think of the author as owning different articles. In this case, the articles are what I'm thinking of as the "children" of the author, so the articles should refer to their "parent" author.

## Joins

View the full join of two tables with,

```sql
SELECT columns FROM table_1 FULL JOIN table_2 ON table_1.primary_key_column = table_2.foreign_key_column;
```
