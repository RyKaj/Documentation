###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Database](https://github.com/RyKaj/Documentation/tree/master/Database/README.md) |
------------


# Database : Table Joins


By using joins, you can retrieve data from two or more tables based on logical relationships between the tables. Joins indicate how SQL Server
should use data from one table to select the rows in another table.

A join condition defines the way two tables are related in a query by:
  - Specifying the column from each table to be used for the join. A typical join condition specifies a foreign key from one table and
    its associated key in the other table.
  - Specifying a logical operator (for example, = or \<\>,) to be used in comparing values from the columns.

## Inner Join

Returns rows when there is a match in both tables.  Inner joins can be specified in either the `FROM` or `WHERE` clauses. Outer joins can be
specified in the `FROM` clause only. The join conditions combine with the `WHERE` and `HAVING` search conditions to control the rows that are
selected from the base tables referenced in the `FROM` clause.

## Left Join

Returns all rows from the left table, even if there are no matches in the right table.

## Right Join

Returns all rows from the right table, even if there are no matches in the left table.

## Full Join

Returns rows when there is a match in one of the tables.

## Self Join

This is used to join a table to itself as if the table were two tables, temporarily renaming at least one table in the MS SQL Server statement.

