## Definition of Relational Database

A relational database is a type of database that organizes data into tables, which are composed of rows and columns. Here, data is stored in a structured manner and relationships between tables are established using keys.

Tables in a relational database represent entities or concepts, and each row in a table represents a specific record. Columns, on the other hand, define the attributes or properties of the record.

The relationships between tables are established through keys. Primary keys uniquely identify each record in a table, while foreign keys establish relationships between tables by referencing the primary key of another table.

## Some of the Most Important SQL commands.

- SELECT: extracts data from a database.
- INSERT: Inserts new records into a table.
- UPDATE: Modifies existing records in a table.
- DELETE: Deletes records from a table based on specified criteria.
- CREATE: Creates a new table, view, or other database object.
- WHERE: Filters rows based on specified conditions.
- ALTER: Modifies a database.
- DROP: Deletes an existing table, view, or other database object.
- JOIN: Combines rows from two or more tables based on a related column between them.
- GROUP BY: Groups rows based on specified columns and applies aggregate functions to each group.
- ORDER BY: Sorts the result set based on specified columns.

## MySQL SELECT Statement

Syntax -

```SQL
SELECT column1, column2, ...
FROM table_name;
```

## MySQL Select Distinct Statement

The <mark>SELECT DISTINCT</mark> statement is used to return only distinct (different) values.

Inside a table, a column often contains many duplicate values; and sometimes you only want to list the different (distinct) values.

Syntax -

```SQL
SELECT DISTINCE column_name
FROM table_name;
```

## MySQL WHERE Statement

Syntax -

```SQL
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

### Operators in the WHERE Clause

| Operator | Description                                      |
| -------- | ------------------------------------------------ |
| =        | Equal                                            |
| >        | Greater Than                                     |
| <        | Less Than                                        |
| >=       | Greater Than or Equal                            |
| <=       | Less Than or Equal                               |
| !=       | Not Equal To                                     |
| BETWEEN  | Between a certain range                          |
| LIKE     | Search for a pattern                             |
| IN       | To specify multiple possible values for a column |

Example of BETWEEN :-

```SQL
SELECT * FROM Products
WHERE Price BETWEEN 50 AND 60;
```

Example of LIKE :-

```SQL
SELECT * FROM Customers
WHERE City LIKE 's%';
```

Example of IN :-

```SQL
SELECT * FROM Customers
WHERE City IN ('Paris','London');
```

<mark>Note: The WHERE clause is not only used in SELECT statements, it is also used in UPDATE, DELETE, etc.!</mark>
