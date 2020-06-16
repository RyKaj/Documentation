###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Database](https://github.com/RyKaj/Documentation/tree/master/Database/README.md) |
------------


# Database : MySQL Learning Materials


## Syntax Legend

## DataTypes

**Summary** *:* in this tutorial, you will learn about  **MySQL data
types **and how to use them effectively in designing database in MySQL.

A database table contains multiple columns with specific data types such
as numeric or string. MySQL provides more data types other than just
numeric or string. Each data type in MySQL can be determined by the
following characteristics:

  - The kind of values it represents.
  - The space that takes up and whether the values is a fixed-length or variable length.
  - The values of the data type can be indexed or not.
  - How MySQL compares the values of a specific data type.

<https://sp.mysqltutorial.org/wp-content/uploads/0211/03/MySQL-Data-Types.jpg>

### MySQL numeric data types

In MySQL, you can find all SQL standard numeric types including exact
number data type and approximate numeric data types including integer,
fixed-point and floating point. In addition, MySQL also has
[`BIT`](https://www.mysqltutorial.org/mysql-bit/)  data type for storing
bit values. Numeric types can be signed or unsigned except for the `BIT`
type.

The following table shows the summary of numeric types in MySQL:

<table>
	<thead>
		<tr>
			<th>Numeric Types</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>
				<a href="https://www.mysqltutorial.org/mysql-int/">TINYINT</a>
			</td>
			<td>A very small integer</td>
		</tr>
		<tr>
			<td>
				<a href="https://www.mysqltutorial.org/mysql-int/">SMALLINT</a>
			</td>
			<td>A small integer</td>
		</tr>
		<tr>
			<td>
				<a href="https://www.mysqltutorial.org/mysql-int/">MEDIUMINT</a>
			</td>
			<td>A medium-sized integer</td>
		</tr>
		<tr>
			<td>
				<a href="https://www.mysqltutorial.org/mysql-int/">INT</a>
			</td>
			<td>A standard integer</td>
		</tr>
		<tr>
			<td>
				<a href="https://www.mysqltutorial.org/mysql-int/">BIGINT</a>
			</td>
			<td>A large integer</td>
		</tr>
		<tr>
			<td>
				<a href="https://www.mysqltutorial.org/mysql-decimal/">DECIMAL</a>
			</td>
			<td>A fixed-point number</td>
		</tr>
		<tr>
			<td>FLOAT</td>
			<td>A single-precision floating point number</td>
		</tr>
		<tr>
			<td>DOUBLE</td>
			<td>A double-precision floating point number</td>
		</tr>
		<tr>
			<td>
				<a href="https://www.mysqltutorial.org/mysql-bit/">BIT</a>
			</td>
			<td>A bit field</td>
		</tr>
	</tbody>
</table>

### MySQL Boolean data type

MySQL does not have the built-in [`BOOLEAN`](https://www.mysqltutorial.org/mysql-boolean/) or [`BOOL`](https://www.mysqltutorial.org/mysql-boolean/) data type. To
represent Boolean values, MySQL uses the smallest integer type which is `TINYINT(1)`. In other words,  `BOOLEAN` and `BOOL` are synonyms for `TINYINT(1).`

### MySQL String data types

In MySQL, a string can hold anything from plain text to binary data such as images or files. Strings can be compared and searched based on pattern matching by 
using the [`LIKE`](https://www.mysqltutorial.org/mysql-like/) operator,  [regular expression](https://www.mysqltutorial.org/mysql-regular-expression-regexp.aspx "MySQL Regular Expression"),
and [full-text search](https://www.mysqltutorial.org/mysql-full-text-search.aspx).

The following table shows the string data types in MySQL:

<table>
	<thead>
		<tr>
			<th>String Types</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>
				<a href="https://www.mysqltutorial.org/mysql-char-data-type/">
					CHAR
				</a>
			</td>
			<td>A fixed-length nonbinary (character) string</td>
		</tr>
		<tr>
			<td>
				<a href="https://www.mysqltutorial.org/mysql-varchar/">
					VARCHAR
				</a>
			</td>
			<td>A variable-length non-binary string</td>
		</tr>
		<tr>
			<td>
				BINARY
			</td>
			<td>A fixed-length binary string</td>
		</tr>
		<tr>
			<td>
				VARBINARY
			</td>
			<td>A variable-length binary string</td>
		</tr>
		<tr>
			<td>
				TINYBLOB
			</td>
			<td>A very small BLOB (binary large object)</td>
		</tr>
		<tr>
			<td>
				BLOB
			</td>
			<td>A small BLOB</td>
		</tr>
		<tr>
			<td>
				MEDIUMBLOB
			</td>
			<td>A medium-sized BLOB</td>
		</tr>
		<tr>
			<td>
				LONGBLOB
			</td>
			<td>A large BLOB</td>
		</tr>
		<tr>
			<td>
				<a href="https://www.mysqltutorial.org/mysql-text/">
					TINYTEXT
				</a>
			</td>
			<td>A very small non-binary string</td>
		</tr>
		<tr>
			<td>
				<a href="https://www.mysqltutorial.org/mysql-text/">
					TEXT
				</a>
			</td>
			<td>A small non-binary string</td>
		</tr>
		<tr>
			<td>
				<a href="https://www.mysqltutorial.org/mysql-text/">
					MEDIUMTEXT
				</a>
			</td>
			<td>A medium-sized non-binary string</td>
		</tr>
		<tr>
			<td>
				<a href="https://www.mysqltutorial.org/mysql-text/">
					LONGTEXT
				</a>
			</td>
			<td>A large non-binary string</td>
		</tr>
		<tr>
			<td>
				<a href="https://www.mysqltutorial.org/mysql-enum/">
					ENUM
				</a>
			</td>
			<td>An enumeration; each column value may be assigned one enumeration member</td>
		</tr>
		<tr>
			<td>
				SET
			</td>
			<td>
				A set; each column value may be assigned zero or more SET members
			</td>
		</tr>
	</tbody>
</table>



### MySQL date and time data types

MySQL provides types for date and time as well as the combination of date and time. In addition, MySQL supports 
[timestamp](https://www.mysqltutorial.org/mysql-timestamp.aspx "MySQL Timestamp")
data type for tracking the changes in a row of a table. If you just want to store the year without date and month, you can use the `YEAR` data type.

The following table illustrates the MySQL date and time data types:

<table>
	<thead>
		<tr>
			<th>Date and Time Types</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>
				<a href="https://www.mysqltutorial.org/mysql-date/">
					DATE
				</a>
			</td>
			<td>A date value in 
				CCYY-MM-DD format
			</td>
		</tr>
		<tr>
			<td>
				TIME
			</td>
			<td>A time value in 
				hh:mm:ss format
			</td>
		</tr>
		<tr>
			<td>
				DATETIME
			</td>
			<td>A date and time value in 
				CCYY-MM-DD hh:mm:ssformat
			</td>
		</tr>
		<tr>
			<td>
				TIMESTAMP
			</td>
			<td>A timestamp value in 
				CCYY-MM-DD hh:mm:ss format
			</td>
		</tr>
		<tr>
			<td>
				YEAR
			</td>
			<td>A year value in 
				CCYY or 
				YYformat
			</td>
		</tr>
	</tbody>
</table>


### MySQL spatial data types

MySQL supports many spatial data types that contain various kinds of geometrical and geographical values as shown in the following table:

<table>
	<thead>
		<tr>
			<th>Spatial Data Types</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>
				GEOMETRY
			</td>
			<td>A spatial value of any type</td>
		</tr>
		<tr>
			<td>
				POINT
			</td>
			<td>A point (a pair of X-Y coordinates)</td>
		</tr>
		<tr>
			<td>
				LINESTRING
			</td>
			<td>A curve (one or more 
				POINTvalues)
			</td>
		</tr>
		<tr>
			<td>
				POLYGON
			</td>
			<td>A polygon</td>
		</tr>
		<tr>
			<td>
				GEOMETRYCOLLECTION
			</td>
			<td>A collection of 
				GEOMETRYvalues
			</td>
		</tr>
		<tr>
			<td>
				MULTILINESTRING
			</td>
			<td>A collection of 
				LINESTRINGvalues
			</td>
		</tr>
		<tr>
			<td>
				MULTIPOINT
			</td>
			<td>A collection of 
				POINTvalues
			</td>
		</tr>
		<tr>
			<td>
				MULTIPOLYGON
			</td>
			<td>A collection of 
				POLYGONvalues
			</td>
		</tr>
	</tbody>
</table>

### JSON data type

MySQL supported a native `JSON` data type since version 5.7.8 that allows you to store and manage JSON documents more efficiently. The
native JSON data type provides automatic validation of JSON documents and optimal storage format.

### Query Statement

#### SELECT Clause

The `SELECT` statement allows you to read data from one or more tables.

##### Syntax

> 
> 
> ``` 
> SELECT
>      [ALL | DISTINCT | DISTINCTROW ]
>      [HIGH_PRIORITY]
>      [STRAIGHT_JOIN]
>      [SQL_SMALL_RESULT] [SQL_BIG_RESULT] [SQL_BUFFER_RESULT]
>      [SQL_NO_CACHE] [SQL_CALC_FOUND_ROWS]
>      select_expr [, select_expr] ...
>      [into_option]
>      [FROM table_references
>         [PARTITION partition_list]]
> [LIMIT {[offset,] row_count | row_count OFFSET offset}]
> 
> into_option: {
>       INTO OUTFILE 'file_name'
>       [CHARACTER SET charset_name]
>       export_options
>    | INTO DUMPFILE 'file_name'
>    | INTO var_name [, var_name] ...
> }
>
> ```

#### UPDATE Clause

The `UPDATE` statement modifies existing data in a table. You can also use the `UPDATE` statement change values in one or more columns of a
single row or multiple rows.

  

#### Single-table syntax:

> 
> ``` 
> UPDATE [LOW_PRIORITY] [IGNORE] table_reference
> SET assignment_list
> [WHERE where_condition]
> [ORDER BY ...]
> [LIMIT row_count]
> 
> assignment:
>    col_name = value
> 
> assignment_list:
>    assignment [, assignment] ...
>
> ```

#### Multiple-table syntax:

> 
> 
> ``` 
> UPDATE [LOW_PRIORITY] [IGNORE] table_references
> SET assignment_list
> [WHERE where_condition]
>
> ```

### DELETE Clause

To delete data from a table, you use the MySQL `DELETE` statement. 

#### Syntax

> 
> 
> ``` 
> DELETE [LOW_PRIORITY] [QUICK] [IGNORE] FROM tbl_name [[AS] tbl_alias]
>     [PARTITION (partition_name [, partition_name] ...)]
>     [WHERE where_condition]
>     [ORDER BY ...]
>     [LIMIT row_count]
>
> ```

### INSERT Clause

The `INSERT` statement allows you to insert one or more rows into a
table. 

#### Syntax

> 
> 
> ``` 
> INSERT [LOW_PRIORITY | DELAYED | HIGH_PRIORITY] [IGNORE]
>      [INTO] tbl_name
>      [PARTITION (partition_name [, partition_name] ...)]
>      [(col_name [, col_name] ...)]
>      { {VALUES | VALUE} (value_list) [, (value_list)] ...
>        |
>        VALUES row_constructor_list
>      }
>      [AS row_alias[(col_alias [, col_alias] ...)]]
>      [ON DUPLICATE KEY UPDATE assignment_list]
> 
> INSERT [LOW_PRIORITY | DELAYED | HIGH_PRIORITY] [IGNORE]
>      [INTO] tbl_name
>      [PARTITION (partition_name [, partition_name] ...)]
>      [AS row_alias[(col_alias [, col_alias] ...)]]
>      SET assignment_list
>      [ON DUPLICATE KEY UPDATE assignment_list]
> 
> INSERT [LOW_PRIORITY | HIGH_PRIORITY] [IGNORE]
>     [INTO] tbl_name
>     [PARTITION (partition_name [, partition_name] ...)]
>     [(col_name [, col_name] ...)]
>     [AS row_alias[(col_alias [, col_alias] ...)]]
>     {SELECT ... | TABLE table_name}
>     [ON DUPLICATE KEY UPDATE assignment_list]
> 
> value:
>      {expr | DEFAULT}
> 
> value_list:
>      value [, value] ...
> 
> row_constructor_list:
>      ROW(value_list)[, ROW(value_list)][, ...]
> 
> assignment:
>      col_name = [row_alias.]value
> 
> assignment_list:
>      assignment [, assignment] ...
>
> ```

### WHERE Clause

The `WHERE` clause allows you to specify a search condition for the rows
returned by a query.

#### Syntax

> 
> 
> ``` 
> [WHERE where_condition]
>
> ```

### GROUP BY Clause

The `GROUP BY` clause groups a set of rows into a set of summary rows by
values of columns or expressions. The `GROUP BY` clause returns one row
for each group. In other words, it reduces the number of rows in the
result set.

#### Syntax

> 
> 
> ``` 
> [GROUP BY {col_name | expr | position}, ... [WITH ROLLUP]]
>
> ```

### HAVING Clause

The   `HAVING` clause is used in the `  SELECT  ` statement to specify
filter conditions for a group of rows or aggregates.

#### Syntax

> 
> 
> ``` 
> [HAVING where_condition]
> ```

#### ORDER BY Clause

#### Syntax

> 
> 
> ``` 
> [ORDER BY {col_name | expr | position}
> [ASC | DESC], ... [WITH ROLLUP]]
> ```

### BETWEEN

The `BETWEEN` operator is a logical operator that allows you to specify
whether a value in a range or not.

#### Syntax

> ``` 
> expr [NOT] BETWEEN begin_expr AND end_expr;
> ```

## Intermediate

### Variables

#### User-Defined Variables

To create a user-defined variable, you use the format  `@variable_name`, where the  `variable_name` consists of alphanumeric characters. The
maximum length of the user-defined variable is 64 characters.  The user-defined variables are not case-sensitive. It means that the 
`@id` and  `@ID` are the same.  You can assign the user-defined variable to a certain data types such as 
[integer](https://www.mysqltutorial.org/mysql-int/), floating point,  [decimal](https://www.mysqltutorial.org/mysql-decimal/), string or 
[NULL](https://www.mysqltutorial.org/mysql-null/). A user-defined variable defined by one client is not visible by other clients. In other
words, an user-defined variable is session-specific.

**Note**: that the user-defined variables are the MySQL-specific extension to SQL standard. They may not be available in other database systems.

### Variable Assignment

There are two ways to assign a value to a user-defined variable. The first way is to use the  `SET` statement as follows:

> ``` 
> SET @variable_name := value;
> ```

You can use either := or = as the assignment operator in the SET statement. For example, the statement assigns number 100 to the variable @counter.

> ``` 
> SET @counter := 100;
> ```

The second way to assign a value to a variable is to use the  [SELECT statement](https://www.mysqltutorial.org/mysql-select-statement-query-data.aspx).
In this case, you must use the := assignment operator because, within the SELECT statement, MySQL treats the = operator as the equal operator.

> ``` 
> SELECT @variable_name := value;
> ```

### Variable Examples

The following statement gets the most expensive product in the `products` table and assigns the price to the user-defined variable @msrp:

> ``` 
> SELECT @msrp:=MAX(msrp)
> FROM  products;
> ```

The following statement uses the @msrp variable to query the information of the most expensive product.

> ``` 
> SELECT productCode, productName, productLine, msrp
> FROM products
> WHERE msrp = @msrp;
> ```

Sometimes, you want to insert a row into a table, get the last insert id, and use it for inserting data into another table. In this case, you
can use the user-defined variable to store the most recent id generated by an 
[AUTO\_INCREMENT ](https://www.mysqltutorial.org/mysql-sequence/)column as follows.

> ``` 
> SELECT @id:=LAST_INSERT_ID();
> ```

A user-defined variable can hold a single value only. If the SELECT statement returns multiple values, the variable will take the value of
the last row in the result.

> ``` 
> SELECT  @buyPrice:=buyprice
> FROM    products
> WHERE   buyprice > 95
> ORDER BY buyprice;
> ```

## Advanced

### Functions

#### Create

> ``` 
> CREATE 
>     [DEFINER = user]
>     FUNCTION function_name ([func_parameter[,...]])
>     RETURNS type
>     [characteristic ...] routine_body
> 
> proc_parameter:
>     [ IN | OUT | INOUT ] param_name type
> 
> func_parameter:
>     param_name type
> 
> type:
>     Any valid MySQL data type
> 
> characteristic:
>     COMMENT 'string'
>     | LANGUAGE SQL
>     | [NOT] DETERMINISTIC
>     | { CONTAINS SQL | NO SQL | READS SQL DATA | MODIFIES SQL DATA }
>     | SQL SECURITY { DEFINER | INVOKER }
> 
> routine_body:
>     Valid SQL routine statement>
> ```

#### Alter

> ``` 
> ALTER FUNCTION func_name [characteristic ...]
>     characteristic:
>     COMMENT 'string'
>     | LANGUAGE SQL
>     | { CONTAINS SQL | NO SQL | READS SQL DATA | MODIFIES SQL DATA }
>     | SQL SECURITY { DEFINER | INVOKER }
> ```

#### Drop / Existing Check

> ``` 
> DROP FUNCTION [IF EXISTS] function_name;
> ```

### Stored Procedure

### Create

> ``` 
> CREATE 
>     [DEFINER = user]
>     PROCEDURE procedure_name ([func_parameter[,...]])
>     RETURNS type
>     [characteristic ...] routine_body
> 
> proc_parameter:
>      [ IN | OUT | INOUT ] param_name type
> 
> func_parameter:
>      param_name type
> 
> type:
>      Any valid MySQL data type
> 
> characteristic:
>      COMMENT 'string'
>      | LANGUAGE SQL
>      | [NOT] DETERMINISTIC
>      | { CONTAINS SQL | NO SQL | READS SQL DATA | MODIFIES SQL DATA }
>      | SQL SECURITY { DEFINER | INVOKER }
> routine_body:
>     Valid SQL routine statement
> ```

### Alter

> ``` 
> ALTER PROCEDURE proc_name [characteristic ...]
>      characteristic:
>      COMMENT 'string'
>      | LANGUAGE SQL
>      | { CONTAINS SQL | NO SQL | READS SQL DATA | MODIFIES SQL DATA }
>      | SQL SECURITY { DEFINER | INVOKER }
> ```

### Rename

### Drop / Existing Check

> ``` 
> DROP PROCEDURE [IF EXISTS] Procedure_name;
> ```

### Views

#### Create

> ``` 
> CREATE
>      [OR REPLACE]
>      [ALGORITHM = { | MERGE | TEMPTABLE}]
>      [DEFINER = user]
>      [SQL SECURITY { DEFINER | INVOKER }]
>      VIEW view_name [(column_list)]
>      AS select_statement
>      [WITH [CASCADED | LOCAL] CHECK OPTION]
> ```

#### Alter

> ``` 
> ALTER
>      [ALGORITHM = { | MERGE | TEMPTABLE}]
>      [DEFINER = user]
>      [SQL SECURITY { DEFINER | INVOKER }]
>      VIEW view_name [(column_list)]
>      AS select_statement
>     [WITH [CASCADED | LOCAL] CHECK OPTION]
> ```

#### Drop / Existing Check

> ``` 
> DROP VIEW [IF EXISTS] 
>      view_name [, view_name] ... 
>      [RESTRICT | CASCADE]
> ```

### Triggers

#### Create

> ``` 
> CREATE
>      [DEFINER = user]
>      TRIGGER trigger_name
>      trigger_time trigger_event
>      ON tbl_name FOR EACH ROW
>      [trigger_order]
> trigger_body
> trigger_time: { BEFORE | AFTER }
> trigger_event: { INSERT | UPDATE | DELETE }
> trigger_order: { FOLLOWS | PRECEDES } other_trigger_name
> ```

### Alter

### Rename

### Drop / Existing Check

> DROP TRIGGER [IF EXISTS] [schema_name.]trigger_name

### Constraints

#### Primary Key

#### Foreign Key

### Arithmetic Operators

### Arithmetic

<table>
	<thead>
		<tr>
			<th>Name</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/arithmetic-functions.html#operator_mod">
					%, 
					MOD
				</a>
			</td>
			<td>Modulo operator</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/arithmetic-functions.html#operator_times">
					*
				</a>
			</td>
			<td>Multiplication operator</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/arithmetic-functions.html#operator_plus">
					+
				</a>
			</td>
			<td>Addition operator</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/arithmetic-functions.html#operator_minus">
					-
				</a>
			</td>
			<td>Minus operator</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/arithmetic-functions.html#operator_unary-minus">
					-
				</a>
			</td>
			<td>Change the sign of the argument</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/arithmetic-functions.html#operator_divide">
					/
				</a>
			</td>
			<td>Division operator</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/arithmetic-functions.html#operator_div">
					DIV
				</a>
			</td>
			<td>Integer division</td>
		</tr>
	</tbody>
</table>


### Mathematical Functions

<table>
	<thead>
		<tr>
			<th>Name</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_abs">
					ABS()
				</a>
			</td>
			<td>Return the absolute value</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_acos">
					ACOS()
				</a>
			</td>
			<td>Return the arc cosine</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_asin">
					ASIN()
				</a>
			</td>
			<td>Return the arc sine</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_atan">
					ATAN()
				</a>
			</td>
			<td>Return the arc tangent</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_atan2">
					ATAN2(), 
					ATAN()
				</a>
			</td>
			<td>Return the arc tangent of the two arguments</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_ceil">
					CEIL()
				</a>
			</td>
			<td>Return the smallest integer value not less than the argument</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_ceiling">
					CEILING()
				</a>
			</td>
			<td>Return the smallest integer value not less than the argument</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_conv">
					CONV()
				</a>
			</td>
			<td>Convert numbers between different number bases</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_cos">
					COS()
				</a>
			</td>
			<td>Return the cosine</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_cot">
					COT()
				</a>
			</td>
			<td>Return the cotangent</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_crc32">
					CRC32()
				</a>
			</td>
			<td>Compute a cyclic redundancy check value</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_degrees">
					DEGREES()
				</a>
			</td>
			<td>Convert radians to degrees</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_exp">
					EXP()
				</a>
			</td>
			<td>Raise to the power of</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_floor">
					FLOOR()
				</a>
			</td>
			<td>Return the largest integer value not greater than the argument</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_ln">
					LN()
				</a>
			</td>
			<td>Return the natural logarithm of the argument</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_log">
					LOG()
				</a>
			</td>
			<td>Return the natural logarithm of the first argument</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_log10">
					LOG10()
				</a>
			</td>
			<td>Return the base-10 logarithm of the argument</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_log2">
					LOG2()
				</a>
			</td>
			<td>Return the base-2 logarithm of the argument</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_mod">
					MOD()
				</a>
			</td>
			<td>Return the remainder</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_pi">
					PI()
				</a>
			</td>
			<td>Return the value of pi</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_pow">
					POW()
				</a>
			</td>
			<td>Return the argument raised to the specified power</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_power">
					POWER()
				</a>
			</td>
			<td>Return the argument raised to the specified power</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_radians">
					RADIANS()
				</a>
			</td>
			<td>Return argument converted to radians</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_rand">
					RAND()
				</a>
			</td>
			<td>Return a random floating-point value</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_round">
					ROUND()
				</a>
			</td>
			<td>Round the argument</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_sign">
					SIGN()
				</a>
			</td>
			<td>Return the sign of the argument</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_sin">
					SIN()
				</a>
			</td>
			<td>Return the sine of the argument</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_sqrt">
					SQRT()
				</a>
			</td>
			<td>Return the square root of the argument</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_tan">
					TAN()
				</a>
			</td>
			<td>Return the tangent of the argument</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_truncate">
					TRUNCATE()
				</a>
			</td>
			<td>Truncate to specified number of decimal places</td>
		</tr>
	</tbody>
</table>

### Bitwise Operator

<table>
	<thead>
		<tr>
			<th>Name</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/bit-functions.html#operator_bitwise-and">
					&amp;
				</a>
			</td>
			<td>Bitwise AND</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/bit-functions.html#operator_right-shift">
					&gt;&gt;
				</a>
			</td>
			<td>Right shift</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/bit-functions.html#operator_left-shift">
					&lt;&lt;
				</a>
			</td>
			<td>Left shift</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/bit-functions.html#operator_bitwise-xor">
					^
				</a>
			</td>
			<td>Bitwise XOR</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/bit-functions.html#function_bit-count">
					BIT_COUNT()
				</a>
			</td>
			<td>Return the number of bits that are set</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/bit-functions.html#operator_bitwise-or">
					\|
				</a>
			</td>
			<td>Bitwise OR</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/bit-functions.html#operator_bitwise-invert">
					~
				</a>
			</td>
			<td>Bitwise inversion</td>
		</tr>
	</tbody>
</table>

### Comparision Operator

<table>
	<thead>
		<tr>
			<th>Name</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#operator_greater-than">
					&gt;
				</a>
			</td>
			<td>Greater than operator</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#operator_greater-than-or-equal">
					&gt;=
				</a>
			</td>
			<td>Greater than or equal operator</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#operator_less-than">
					&lt;
				</a>
			</td>
			<td>Less than operator</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#operator_not-equal">
					&lt;&gt;, 
					!=
				</a>
			</td>
			<td>Not equal operator</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#operator_less-than-or-equal">
					&lt;=
				</a>
			</td>
			<td>Less than or equal operator</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#operator_equal-to">
					&lt;=&gt;
				</a>
			</td>
			<td>NULL-safe equal to operator</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#operator_equal">
					=
				</a>
			</td>
			<td>Equal operator</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#operator_between">
					BETWEEN ... AND ...
				</a>
			</td>
			<td>Whether a value is within a range of values</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#function_coalesce">
					COALESCE()
				</a>
			</td>
			<td>Return the first non-NULL argument</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#function_greatest">
					GREATEST()
				</a>
			</td>
			<td>Return the largest argument</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#operator_in">
					IN()
				</a>
			</td>
			<td>Whether a value is within a set of values</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#function_interval">
					INTERVAL()
				</a>
			</td>
			<td>Return the index of the argument that is less than the first argument</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#operator_is">
					IS
				</a>
			</td>
			<td>Test a value against a boolean</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#operator_is-not">
					IS NOT
				</a>
			</td>
			<td>Test a value against a boolean</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#operator_is-not-null">
					IS NOT NULL
				</a>
			</td>
			<td>NOT NULL value test</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#operator_is-null">
					IS NULL
				</a>
			</td>
			<td>NULL value test</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#function_isnull">
					ISNULL()
				</a>
			</td>
			<td>Test whether the argument is NULL</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#function_least">
					LEAST()
				</a>
			</td>
			<td>Return the smallest argument</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/string-comparison-functions.html#operator_like">
					LIKE
				</a>
			</td>
			<td>Simple pattern matching</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#operator_not-between">
					NOT BETWEEN ... AND ...
				</a>
			</td>
			<td>Whether a value is not within a range of values</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/comparison-operators.html#operator_not-in">
					NOT IN()
				</a>
			</td>
			<td>Whether a value is not within a set of values</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/string-comparison-functions.html#operator_not-like">
					NOT LIKE
				</a>
			</td>
			<td>Negation of simple pattern matching</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/string-comparison-functions.html#function_strcmp">
					STRCMP()
				</a>
			</td>
			<td>Compare two strings</td>
		</tr>
	</tbody>
</table>


### Compound Operator

### JSON Function Reference

<table>
	<thead>
		<tr>
			<th>Name</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-search-functions.html#operator_json-column-path">
					-&gt;
				</a>
			</td>
			<td>Return value from JSON column after evaluating path; equivalent to JSON_EXTRACT().</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-search-functions.html#operator_json-inline-path">
					-&gt;&gt;
				</a>
			</td>
			<td>Return value from JSON column after evaluating path and unquoting the result; equivalent to JSON_UNQUOTE(JSON_EXTRACT()).</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-creation-functions.html#function_json-array">
					JSON_ARRAY()
				</a>
			</td>
			<td>Create JSON array</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-modification-functions.html#function_json-array-append">
					JSON_ARRAY_APPEND()
				</a>
			</td>
			<td>Append data to JSON document</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-modification-functions.html#function_json-array-insert">
					JSON_ARRAY_INSERT()
				</a>
			</td>
			<td>Insert into JSON array</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-search-functions.html#function_json-contains">
					JSON_CONTAINS()
				</a>
			</td>
			<td>Whether JSON document contains specific object at path</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-search-functions.html#function_json-contains-path">
					JSON_CONTAINS_PATH()
				</a>
			</td>
			<td>Whether JSON document contains any data at path</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-attribute-functions.html#function_json-depth">
					JSON_DEPTH()
				</a>
			</td>
			<td>Maximum depth of JSON document</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-search-functions.html#function_json-extract">
					JSON_EXTRACT()
				</a>
			</td>
			<td>Return data from JSON document</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-modification-functions.html#function_json-insert">
					JSON_INSERT()
				</a>
			</td>
			<td>Insert data into JSON document</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-search-functions.html#function_json-keys">
					JSON_KEYS()
				</a>
			</td>
			<td>Array of keys from JSON document</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-attribute-functions.html#function_json-length">
					JSON_LENGTH()
				</a>
			</td>
			<td>Number of elements in JSON document</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-modification-functions.html#function_json-merge">
					JSON_MERGE()
				</a> (deprecated)
			</td>
			<td>Merge JSON documents, preserving duplicate keys. Deprecated synonym for JSON_MERGE_PRESERVE()</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-modification-functions.html#function_json-merge-patch">
					JSON_MERGE_PATCH()
				</a>
			</td>
			<td>Merge JSON documents, replacing values of duplicate keys</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-modification-functions.html#function_json-merge-preserve">
					JSON_MERGE_PRESERVE()
				</a>
			</td>
			<td>Merge JSON documents, preserving duplicate keys</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-creation-functions.html#function_json-object">
					JSON_OBJECT()
				</a>
			</td>
			<td>Create JSON object</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-search-functions.html#function_json-overlaps">
					JSON_OVERLAPS()
				</a> (introduced 8.0.17)
			</td>
			<td>Compares two JSON documents, returns TRUE (1) if these have any key-value pairs or array elements in common, otherwise FALSE (0)</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-utility-functions.html#function_json-pretty">
					JSON_PRETTY()
				</a>
			</td>
			<td>Print a JSON document in human-readable format</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-creation-functions.html#function_json-quote">
					JSON_QUOTE()
				</a>
			</td>
			<td>Quote JSON document</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-modification-functions.html#function_json-remove">
					JSON_REMOVE()
				</a>
			</td>
			<td>Remove data from JSON document</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-modification-functions.html#function_json-replace">
					JSON_REPLACE()
				</a>
			</td>
			<td>Replace values in JSON document</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-validation-functions.html#function_json-schema-valid">
					JSON_SCHEMA_VALID()
				</a> (introduced 8.0.17)
			</td>
			<td>Validate JSON document against JSON schema; returns TRUE/1 if document validates against schema, or FALSE/0 if it does not</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-validation-functions.html#function_json-schema-validation-report">
					JSON_SCHEMA_VALIDATION_REPORT()
				</a> (introduced 8.0.17)
			</td>
			<td>Validate JSON document against JSON schema; returns report in JSON format on outcome on validation including success or failure and reasons for failure</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-search-functions.html#function_json-search">
					JSON_SEARCH()
				</a>
			</td>
			<td>Path to value within JSON document</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-modification-functions.html#function_json-set">
					JSON_SET()
				</a>
			</td>
			<td>Insert data into JSON document</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-utility-functions.html#function_json-storage-free">
					JSON_STORAGE_FREE()
				</a>
			</td>
			<td>Freed space within binary representation of JSON column value following partial update</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-utility-functions.html#function_json-storage-size">
					JSON_STORAGE_SIZE()
				</a>
			</td>
			<td>Space used for storage of binary representation of a JSON document</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-table-functions.html#function_json-table">
					JSON_TABLE()
				</a>
			</td>
			<td>Return data from a JSON expression as a relational table</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-attribute-functions.html#function_json-type">
					JSON_TYPE()
				</a>
			</td>
			<td>Type of JSON value</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-modification-functions.html#function_json-unquote">
					JSON_UNQUOTE()
				</a>
			</td>
			<td>Unquote JSON value</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-attribute-functions.html#function_json-valid">
					JSON_VALID()
				</a>
			</td>
			<td>Whether JSON value is valid</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/json-search-functions.html#operator_member-of">
					MEMBER OF()
				</a> (introduced 8.0.17)
			</td>
			<td>Returns true (1) if first operand matches any element of JSON array passed as second operand, otherwise returns false (0)</td>
		</tr>
	</tbody>
</table>



### Logical Operator

<table>
	<thead>
		<tr>
			<th>Name</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/logical-operators.html#operator_and">
					AND, 
					&amp;&amp;
				</a>
			</td>
			<td>Logical AND</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/logical-operators.html#operator_not">
					NOT, 
					!
				</a>
			</td>
			<td>Negates value</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/logical-operators.html#operator_or">
					OR, 
					\|\|
				</a>
			</td>
			<td>Logical OR</td>
		</tr>
		<tr>
			<td>
				<a href="https://dev.mysql.com/doc/refman/8.0/en/logical-operators.html#operator_xor">
					XOR
				</a>
			</td>
			<td>Logical XOR</td>
		</tr>
	</tbody>
</table>

## Expert

### Condition Handling

#### DECLARE ... CONDITION Statement

> ``` 
> DECLARE condition_name CONDITION FOR condition_value
>      condition_value: {
>      mysql_error_code
>      | SQLSTATE [VALUE] sqlstate_value
> }
> ```

#### DECLARE ... HANDLER Statement

> ``` 
> DECLARE handler_action HANDLER
>      FOR condition_value [, condition_value] ...
>      statement
> 
> handler_action: {
>      CONTINUE
>      | EXIT
>      | UNDO
> }
> 
> condition_value: {
>      mysql_error_code
>      | SQLSTATE [VALUE] sqlstate_value
>      | condition_name
>      | SQLWARNING
>      | NOT FOUND
>      | SQLEXCEPTION
> }
> ```

#### GET DIAGNOSTICS Statement

> 
> ``` 
> GET [CURRENT | STACKED] DIAGNOSTICS
> {
>      statement_information_item
>      [, statement_information_item] ...
>    | CONDITION condition_number
>      condition_information_item
>      [, condition_information_item] ...
> }
> 
> statement_information_item:
>      target = statement_information_item_name
> 
> condition_information_item:
>      target = condition_information_item_name
> 
> statement_information_item_name:
>      NUMBER
>      | ROW_COUNT
> 
> condition_information_item_name: {
>      CLASS_ORIGIN
>      | SUBCLASS_ORIGIN
>      | RETURNED_SQLSTATE
>      | MESSAGE_TEXT
>      | MYSQL_ERRNO
>      | CONSTRAINT_CATALOG
>      | CONSTRAINT_SCHEMA
>      | CONSTRAINT_NAME
>      | CATALOG_NAME
>      | SCHEMA_NAME
>      | TABLE_NAME
>      | COLUMN_NAME
>      | CURSOR_NAME
> }
> 
> condition_number, target:
>
> ```

#### RESIGNAL Statement

> ``` 
> RESIGNAL [condition_value]
>      [SET signal_information_item
>      [, signal_information_item] ...]
> 
> condition_value: {
>      SQLSTATE [VALUE] sqlstate_value
>      | condition_name
> }
> 
> signal_information_item:
>      condition_information_item_name = simple_value_specification
> 
> condition_information_item_name: {
>      CLASS_ORIGIN
>      | SUBCLASS_ORIGIN
>      | MESSAGE_TEXT
>      | MYSQL_ERRNO
>      | CONSTRAINT_CATALOG
>      | CONSTRAINT_SCHEMA
>      | CONSTRAINT_NAME
>      | CATALOG_NAME
>      | SCHEMA_NAME
>      | TABLE_NAME
>      | COLUMN_NAME
>     | CURSOR_NAME
> }
> 
> condition_name, simple_value_specification:
>
> ```

#### SIGNAL Statement

> 
> 
> ``` 
> SIGNAL condition_value
>     [SET signal_information_item
>     [, signal_information_item] ...]
> 
> condition_value: {
>     SQLSTATE [VALUE] sqlstate_value
>     | condition_name
> }
> 
> signal_information_item:
>     condition_information_item_name = simple_value_specification
> 
> condition_information_item_name: {
>     CLASS_ORIGIN
>     | SUBCLASS_ORIGIN
>     | MESSAGE_TEXT
>     | MYSQL_ERRNO
>     | CONSTRAINT_CATALOG
>     | CONSTRAINT_SCHEMA
>     | CONSTRAINT_NAME
>     | CATALOG_NAME
>     | SCHEMA_NAME
>     | TABLE_NAME
>     | COLUMN_NAME
>     | CURSOR_NAME
> }
> 
> interval:
>      quantity {YEAR | QUARTER | MONTH | DAY | HOUR | MINUTE | WEEK | SECOND | YEAR_MONTH | DAY_HOUR | DAY_MINUTE | DAY_SECOND | HOUR_MINUTE | HOUR_SECOND | MINUTE_SECOND }
>
> DROP EVENT [IF EXISTS] event_name
>
> ```

#### Privileges

The EVENT privilege governs the creation, modification, and deletion of events. This privilege can be bestowed using GRANT . For example, this
GRANT statement confers the EVENT privilege for the schema named myschema on the user jon@ghidora:

> ``` 
> GRANT EVENT ON myschema.* TO jon@ghidora;
> ```

(We assume that this user account already exists, and that we wish for it to remain unchanged otherwise.) To grant this same user the
[`EVENT`](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_event)
privilege on all schemas, use the following statement:

> ``` 
> GRANT EVENT ON *.* TO jon@ghidora;
> ```

The EVENT privilege has global or schema-level scope. Therefore, trying to grant it on a single table results in an error as shown:

> ``` 
> mysql> GRANT EVENT ON myschema.mytable TO jon@ghidora; ERROR 1144 (42000): Illegal GRANT/REVOKE command; please consult the manual to see which privileges can be used
> ```

## MySQL Shell

### SQL Syntax

  - <https://dev.mysql.com/doc/mysql-shell/8.0/en/mysql-shell-commands.html>
  - <https://docs.oracle.com/cd/E19078-01/mysql/mysql-refman-5.0/sql-syntax.html#show>

### MySQLCheck

  - <https://dev.mysql.com/doc/refman/8.0/en/mysqlcheck.html>
  - <https://mariadb.com/kb/en/mysqlcheck/>

References

  - [Mysql Tutorial - mysql data
	types](https://www.mysqltutorial.org/mysql-data-types.aspx)
  - [Dev.mysql - data
	types](https://dev.mysql.com/doc/refman/8.0/en/data-types.html)

