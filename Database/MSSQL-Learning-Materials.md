###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Database](https://github.com/RyKaj/Documentation/tree/master/Database/README.md) |
------------


# Database : MSSQL Learning Materials

T-SQL (Transact-SQL) is an extension of SQL language. This tutorial covers the fundamental concepts of T-SQL such as its various functions, procedures, 
indexes, and transactions related to the topic.

## Syntax Legend

### Transact-SQL Syntax Conventions (Transact-SQL)

<table>
	<thead>
		<tr class="header">
			<th>Convention</th>
			<th>Used for</th>
		</tr>
	</thead>
	<tbody>
		<tr class="odd">
			<td>UPPERCASE</td>
			<td>Transact-SQL keywords.</td>
		</tr>
		<tr class="even">
			<td>
				<em>italic</em>
			</td>
			<td>User-supplied parameters of Transact-SQL syntax.</td>
		</tr>
		<tr class="odd">
			<td>
				<strong>bold</strong>
			</td>
			<td>Type database names, table names, column names, index names, stored procedures, utilities, data type names, and text exactly as shown.</td>
		</tr>
		<tr class="even">
			<td>underline</td>
			<td>Indicates the default value applied when the clause that contains the underlined value is omitted from the statement.</td>
		</tr>
		<tr class="odd">
			<td>| (vertical bar)</td>
			<td>Separates syntax items enclosed in brackets or braces. You can use only one of the items.</td>
		</tr>
		<tr class="even">
			<td>
				<code>[ ]</code> (brackets)
			</td>
			<td>Optional syntax items. Don't type the brackets.</td>
		</tr>
		<tr class="odd">
			<td>{ } (braces)</td>
			<td>Required syntax items. Don't type the braces.</td>
		</tr>
		<tr class="even">
			<td>[ 
				<strong>,</strong>... 
				<em>n</em>]
			</td>
			<td>Indicates the preceding item can be repeated 
				<em>n</em> number of times. The occurrences are separated by commas.
			</td>
		</tr>
		<tr class="odd">
			<td>[... 
				<em>n</em>]
			</td>
			<td>Indicates the preceding item can be repeated 
				<em>n</em> number of times. The occurrences are separated by blanks.
			</td>
		</tr>
		<tr class="even">
			<td>;</td>
			<td>Transact-SQL statement terminator. Although the semicolon isn't required for most statements in this version of SQL Server, it will be required in a future version.</td>
		</tr>
		<tr class="odd">
			<td>&lt;label&gt; ::=</td>
			<td>The name for a block of syntax. Use this convention to group and label sections of lengthy syntax or a unit of syntax that you can use in more than one location within a statement. Each location in which the block of syntax could be used is indicated with the label enclosed in chevrons: &lt;label&gt;.
				<br />
				<br />
				A set is a collection of expressions, for example &lt;grouping set&gt;; and a list is a collection of sets, for example &lt;composite element list&gt;.
			</td>
		</tr>
	</tbody>
</table>



### Multipart Names

Unless specified otherwise, all Transact-SQL references to the name of a database object can be a four-part name in the following form:
 
>```
>*server\_name*.\[ *database\_name*\].\[ *schema\_name*\]. *object\_name*
>        | *database\_name*.\[ *schema\_name*\]. *object\_name*
>        | *schema\_name*. *object\_name*
>        | *object\_name*
>```

***server\_name***
Specifies a linked server name or remote server name.

***database\_name***
Specifies the name of a SQL Server database when the object resides in a local instance of SQL Server. When the object is in a linked server, 
*database\_name* specifies an OLE DB catalog.

***schema\_name***
Specifies the name of the schema that contains the object if the object is in a SQL Server database. When the object is in a linked server, 
*schema\_name* specifies an OLE DB schema name.

***object\_name***
Refers to the name of the object.

When referencing a specific object, you don't always have to specify the server, database, and schema for the SQL Server Database Engine to identify the object. 
However, if the object can't be found, an error is returned.

## Beginner

### DataTypes

#### Binary

<table>
	<thead>
		<tr>
			<th>DataType</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>binary</td>
			<td>Fixed-length binary data with a maximum length of 8,000 bytes.</td>
		</tr>
		<tr>
			<td>varbinary</td>
			<td>Variable-length binary data with a maximum length of 8,000 bytes.</td>
		</tr>
		<tr>
			<td>varbinary(max)</td>
			<td>Variable-length binary data with a maximum length of 2 
				<sup>31</sup> bytes (Introduced in SQL Server 2005).
			</td>
		</tr>
		<tr>
			<td>image</td>
			<td>Variable-length binary data with a maximum length of 2,147,483,647 bytes.</td>
		</tr>
	</tbody>
</table>


#### Character Strings

<table>
	<thead>
		<tr>
			<th>DataType</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>char</td>
			<td>Fixed-length non-Unicode character data with a maximum length of 8,000 characters.</td>
		</tr>
		<tr>
			<td>varchar</td>
			<td>Variable-length non-Unicode data with a maximum of 8,000 characters.</td>
		</tr>
		<tr>
			<td>varchar(max)</td>
			<td>Variable-length non-Unicode data with a maximum length of 231 characters (Introduced in SQL Server 2005).</td>
		</tr>
		<tr>
			<td>text</td>
			<td>Variable-length non-Unicode data with a maximum length of 2,147,483,647 characters</td>
		</tr>
	</tbody>
</table>

#### Unicode Characters

<table>
	<thead>
		<tr>
			<th>DataType</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>nchar</td>
			<td>Fixed-length Unicode data with a maximum length of 4,000 characters.</td>
		</tr>
		<tr>
			<td>nvarchar</td>
			<td>Variable-length Unicode data with a maximum length of 4,000 characters.</td>
		</tr>
		<tr>
			<td>Nvarchar(max)</td>
			<td>Variable-length Unicode data with a maximum length of 2 
				<sup>30</sup> characters (Introduced in SQL Server 2005).
			</td>
		</tr>
		<tr>
			<td>ntext</td>
			<td>Variable-length Unicode data with a maximum length of 1,073,741,823 characters.</td>
		</tr>
	</tbody>
</table>


#### Data and Time

<table>
	<thead>
		<tr>
			<th>DataType</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>datetime</td>
			<td>Jan 1, 1753 to Dec 31, 9999 (3.33 milliseconds accuracy)</td>
		</tr>
		<tr>
			<td>smalldatetime</td>
			<td>Jan 1, 1900 to Jun 6, 2079 (1 minute accuracy)</td>
		</tr>
		<tr>
			<td>datetimeoffset</td>
			<td>Jan 1, 0001 to Dec 31, 9999  (100 nanoseconds accuracy. Introduced in SQL Server 2008)</td>
		</tr>
		<tr>
			<td>datetime2</td>
			<td>Jan 1, 0001 to Dec 31, 9999 (100 nanoseconds accuracy. Introduced in 
				<strong>SQL Server 2008</strong> )
			</td>
		</tr>
		<tr>
			<td>time</td>
			<td>00:00:00.0000000 to 23:59:59.9999999 (100 nanoseconds accuracy. Introduced in 
				<strong>SQL Server 2008</strong> )
			</td>
		</tr>
	</tbody>
</table>


#### Numerics

<table>
	<thead>
		<tr>
			<th>DataTypes</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>bigint</td>
			<td>-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</td>
		</tr>
		<tr>
			<td>int</td>
			<td>-2,147,483,648 to 2,147,483,647</td>
		</tr>
		<tr>
			<td>smallint</td>
			<td>-32,768 to 32,767</td>
		</tr>
		<tr>
			<td>tinyint</td>
			<td>0 to 255</td>
		</tr>
		<tr>
			<td>bit</td>
			<td>0 or 1</td>
		</tr>
		<tr>
			<td>decimal</td>
			<td>-10
				<sup>38 +1 to 10</sup>38 –1
			</td>
		</tr>
		<tr>
			<td>numeric</td>
			<td>-10
				<sup>38 +1 to 10</sup>38 –1
			</td>
		</tr>
		<tr>
			<td>money</td>
			<td>-922,337,203,685,477.5808 to +922,337,203,685,477.5807</td>
		</tr>
		<tr>
			<td>smallmoney</td>
			<td>+214,748.3647</td>
		</tr>
	</tbody>
</table>

#### Other Data Types

  - **sql\_variant** − Stores values of various SQL Server-supported data types, except text, ntext, and timestamp.
  - **timestamp** − Stores a database-wide unique number that gets updated every time a row gets updated.
  - **uniqueidentifier** − Stores a globally unique identifier (GUID).
  - **xml** − Stores XML data. You can store XML instances in a column or a variable (Introduced in SQL Server 2005).
  - **cursor** − A reference to a cursor.
  - **table** − Stores a result set for later processing.
  - **hierarchyid** − A variable length, system data type used to represent position in a hierarchy (Introduced in SQL Server 2008).

### Query Statements

#### SELECT Clause

SQL Server **SELECT** statement is used to fetch the data from a database table which returns data in the form of result table. 
These result tables are called **result-sets** . Retrieves rows from the database and enables the selection of one or many rows or columns from one or many tables in SQL Server

#### Syntax

Following is the basic syntax of SELECT statement. Where, column1, column2...are the fields of a table whose values you want to fetch.

> ``` 
> SELECT column1, column2, columnN FROM table_name;
> ```


> ``` 
> <SELECT statement> ::=
>     [ WITH { [ XMLNAMESPACES ,] [ <common_table_expression> [,...n] ] } ]  
>     <query_expression>   
>     [ ORDER BY { order_by_expression | column_position [ ASC | DESC ] }   
>   [ ,...n ] ]   
>     [ <FOR Clause>]   
>     [ OPTION ( <query_hint> [ ,...n ] ) ]   
> <query_expression> ::=   
>     { <query_specification> | ( <query_expression> ) }   
>     [  { UNION [ ALL ] | EXCEPT | INTERSECT }  
>         <query_specification> | ( <query_expression> ) [...n ] ]   
> <query_specification> ::=   
> SELECT [ ALL | DISTINCT ]   
>     [TOP ( expression ) [PERCENT] [ WITH TIES ] ]   
>     < select_list >   
>     [ INTO new_table ]   
>     [ FROM { <table_source> } [ ,...n ] ]   
>     [ WHERE <search_condition> ]   
>     [ <GROUP BY> ]   
>     [ HAVING < search_condition > ]  
> ```

#### UPDATE Clause

#### DELETE Clause

#### INSERT Clause

#### WHERE Clause

The MS SQL Server  **WHERE** clause is used to specify a condition while fetching the data from single table or joining with multiple tables. If
the given condition is satisfied, only then it returns a specific value from the table. You will have to use WHERE clause to filter the records
and fetch only necessary records.

Specifies the search condition for the rows returned by the query.

Following is the basic syntax of SELECT statement with WHERE clause

#### GROUP BY Clause

## Syntax

> SELECT column1, column2
> FROM table\_name
> WHERE \[ conditions \]
> GROUP BY column1, column2
> ORDER BY column1, column2

  

> \-- Syntax for SQL Server and Azure SQL Database   
> \-- ISO-Compliant Syntax  
> ``` 
> GROUP BY {
>     column-expression  
>         | ROLLUP ( <group_by_expression> [ ,...n ] )  
>         | CUBE ( <group_by_expression> [ ,...n ] )  
>         | GROUPING SETS ( <grouping_set> [ ,...n ]  )  
>         | () --calculates the grand total
> } [ ,...n ]
> <group_by_expression> ::=  
>         column-expression  
>     | ( column-expression [ ,...n ] )    
>     <grouping_set> ::=  
>         () --calculates the grand total  
>         | <grouping_set_item>  
>         | ( <grouping_set_item> [ ,...n ] )  
>     <grouping_set_item> ::=  
>         <group_by_expression>  
>         | ROLLUP ( <group_by_expression> [ ,...n ] )  
>         | CUBE ( <group_by_expression> [ ,...n ] )  
>     -- For backward compatibility only.
>     -- Non-ISO-Compliant Syntax for SQL Server and Azure SQL Database
> GROUP BY
>     [ ALL ] column-expression [ ,...n ]
> ```

#### HAVING Clause

Specifies a search condition for a group or an aggregate. HAVING can be used only with the SELECT statement. HAVING is typically used with a
GROUP BY clause. When GROUP BY is not used, there is an implicit single, aggregated group.

#### ORDER BY Clause

The MS SQL Server  **ORDER** BY clause is used to sort the data in ascending or descending order, based on one or more columns. Some
database sort query results in ascending order by default. 

Following is the basic syntax of ORDER BY clause.

> ``` 
> -- Syntax for SQL Server and Azure SQL Database
> ORDER BY order_by_expression  
>     [ COLLATE collation_name ]   
>     [ ASC | DESC ]   
>     [ ,...n ]   
> [ <offset_fetch> ]  
> <offset_fetch> ::=  
> {   
>     OFFSET { integer_constant | offset_row_count_expression } { ROW | ROWS }  
>     [  
>       FETCH { FIRST | NEXT } {integer_constant | fetch_row_count_expression } { ROW | ROWS } ONLY  
>     ]  
> }
> ```

#### MATCH Clause

Specifies a search condition for a graph. MATCH can be used only with graph node and edge tables, in the SELECT statement as part of WHERE clause.

> 
> 
> ``` 
> MATCH (<graph_search_pattern>)
> <graph_search_pattern>::=
>   {  
>       <simple_match_pattern>
>     | <arbitrary_length_match_pattern>  
>     | <arbitrary_length_match_last_node_predicate>
>   }
> <simple_match_pattern>::=
>   {
>       LAST_NODE(<node_alias>) | <node_alias>   {
>           { <-( <edge_alias> )- }
>         | { -( <edge_alias> )-> }
>         <node_alias> | LAST(<node_alias>)
>         }
>   }
>   [ { AND } { ( <simple_match_pattern> ) } ]
>   [ ,...n ]
> <node_alias> ::=
>   node_table_name | node_table_alias
> <edge_alias> ::=
>   edge_table_name | edge_table_alias
> <arbitrary_length_match_pattern>  ::=
>   {
>     SHORTEST_PATH(
>       <arbitrary_length_pattern>
>       [ { AND } { <arbitrary_length_pattern> } ]
>       [ ,…n]
>     )
>   }
> <arbitrary_length_match_last_node_predicate> ::=
>   {  LAST_NODE( <node_alias> ) = LAST_NODE( <node_alias> ) }
> <arbitrary_length_pattern> ::=
>     {  LAST_NODE( <node_alias> )   | <node_alias>
>      ( <edge_first_al_pattern> [<edge_first_al_pattern>…,n] )
>      <al_pattern_quantifier>
>   }
>      |  ( {<node_first_al_pattern> [<node_first_al_pattern> …,n] )
>             <al_pattern_quantifier>
>         LAST_NODE( <node_alias> ) | <node_alias>
>  }   
> <edge_first_al_pattern> ::=
>   { (  
>         { -( <edge_alias> )->   }
>       | { <-( <edge_alias> )- }
>       <node_alias>
>       )
>   }
> <node_first_al_pattern> ::=
>   { (
>       <node_alias>
>         { <-( <edge_alias> )- }
>       | { -( <edge_alias> )-> }
>        )
>   }
> <al_pattern_quantifier> ::=
>   {
>         +
>       | { 1 , n }
>   }
> n -  positive integer only.
>                     
> ```

#### BETWEEN

#### LINE

#### EXISTS

#### IN

#### SOME

#### ANY

### Intermediate

#### Variables

A Transact-SQL local variable is an database object that can store a single data value of a specific type. To declare a variable uses the
keyword DECLARE, assign a variable name and a data type.

> ``` 
> DECLARE @MyVariable datatype;
> ```

After a variable is declared, it gets the default NULL value. To assign a value to a variable, use the SET statement.

### Advanced

#### Functions

> ``` 
> DROP PROCEDURE IF EXISTS [<db user>].[<sp name>]
> ``` 					

##### Alter

##### Rename

##### Drop

> ``` 
> DROP PROCEDURE IF EXISTS [<db user>].[<sp name>]
> ```

#### Stored Procedures

##### Create

##### Alter

##### Rename

##### Drop

#### Views

##### Create

##### Alter

##### Rename

##### Drop

#### Triggers

##### Create

##### Alter

##### Rename

##### Drop

#### Constraints

##### Primary Key

##### Foreign Key

#### Arithmetic Operators

<table>
	<thead>
		<tr>
			<th></th>
			<th></th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>+</td>
			<td>Add</td>
		</tr>
		<tr>
			<td>-</td>
			<td>Subtract</td>
		</tr>
		<tr>
			<td>*</td>
			<td>Multiply</td>
		</tr>
		<tr>
			<td>/</td>
			<td>Divide</td>
		</tr>
		<tr>
			<td>%</td>
			<td>Modulo</td>
		</tr>
	</tbody>
</table>


### Bitwise Operators

<table>
	<thead>
		<tr>
			<th></th>
			<th></th>
			<th></th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>&amp;</td>
			<td>Bitwise AND</td>
			<td></td>
		</tr>
		<tr>
			<td></td>
			<td></td>
			<td>Bitwise OR</td>
		</tr>
		<tr>
			<td>^</td>
			<td>Bitwise exclusive OR</td>
			<td></td>
		</tr>
	</tbody>
</table>


### Comparison Operators

<table>
	<thead>
		<tr>
			<th></th>
			<th></th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>=</td>
			<td>Equal to</td>
		</tr>
		<tr>
			<td>&gt;</td>
			<td>Greater than</td>
		</tr>
		<tr>
			<td>&lt;</td>
			<td>Less than</td>
		</tr>
		<tr>
			<td>&gt;=</td>
			<td>Greater than or equal to</td>
		</tr>
		<tr>
			<td>&lt;=</td>
			<td>Less than or equal to</td>
		</tr>
		<tr>
			<td>&lt;&gt;</td>
			<td>Not equal to</td>
		</tr>
	</tbody>
</table>

### Compound Operators

<table>
	<thead>
		<tr>
			<th></th>
			<th></th>
			<th></th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>+=</td>
			<td>Add Equals</td>
			<td></td>
		</tr>
		<tr>
			<td>-=</td>
			<td>Subtract Equals</td>
			<td></td>
		</tr>
		<tr>
			<td>*=</td>
			<td>Multiply Equals</td>
			<td></td>
		</tr>
		<tr>
			<td>/=</td>
			<td>Divide Equals</td>
			<td></td>
		</tr>
		<tr>
			<td>%=</td>
			<td>Modulo Equals</td>
			<td></td>
		</tr>
		<tr>
			<td>&amp;=</td>
			<td>Bitwise AND Equals</td>
			<td></td>
		</tr>
		<tr>
			<td>^-=</td>
			<td>Bitwise Exclusive Equals</td>
			<td></td>
		</tr>
		<tr>
			<td></td>
			<td>*=</td>
			<td>Bitwise OR Equals</td>
		</tr>
	</tbody>
</table>

### Logical Operators

<table>
	<thead>
		<tr>
			<th></th>
			<th></th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>ALL</td>
			<td>TRUE if all of a set of comparisons are TRUE.</td>
		</tr>
		<tr>
			<td>AND</td>
			<td>TRUE if both expressions are TRUE.</td>
		</tr>
		<tr>
			<td>ANY</td>
			<td>TRUE if any one of a set of comparisons are TRUE.</td>
		</tr>
		<tr>
			<td>BETWEEN</td>
			<td>TRUE if the operand is within the range of comparisons.</td>
		</tr>
		<tr>
			<td>EXISTS</td>
			<td>TRUE if a subquery contains any rows.</td>
		</tr>
		<tr>
			<td>IN</td>
			<td>TRUE if the operand is equal to one of a list of expressions.</td>
		</tr>
		<tr>
			<td>LIKE</td>
			<td>TRUE if the operand matches a pattern.</td>
		</tr>
		<tr>
			<td>NOT</td>
			<td>Reverses the value of any other operator.</td>
		</tr>
		<tr>
			<td>OR</td>
			<td>TRUE if either expression is TRUE.</td>
		</tr>
		<tr>
			<td>SOME</td>
			<td>TRUE if some of a set of comparisons are TRUE.</td>
		</tr>
	</tbody>
</table>


## Expert

### Schedule Jobs

References

  - [docs.microsoft.com - transact-sql-syntax-conventions-transact-sql](https://docs.microsoft.com/en-us/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql?view=sql-server-2017)
  - [docs.microsoft - Joins](https://docs.microsoft.com/en-us/sql/relational-databases/performance/joins?view=sql-server-2017)
  - [docs.microsoft - Tutorial writing transact sql statements](https://docs.microsoft.com/en-us/sql/t-sql/tutorial-writing-transact-sql-statements?view=sql-server-2017)
  - [TSQL info](https://www.tsql.info/)
  - [Tutorials Point - TSQ](https://www.tutorialspoint.com/t_sql/index.htm)
  - [docs.microsoft - Tutorial writing transact sql statements](https://docs.microsoft.com/en-us/sql/t-sql/tutorial-writing-transact-sql-statements?view=sql-server-2017)
  - [Search SQL Server - TSQL](https://searchsqlserver.techtarget.com/definition/T-SQL)
  - [SQL Server Central - understanding outer joins in sql](https://www.sqlservercentral.com/articles/understanding-outer-joins-in-sql)
  - [Sisense - sql symbol cheatsheet](https://www.sisense.com/blog/sql-symbol-cheatsheet/)
