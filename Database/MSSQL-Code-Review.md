###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Database](https://github.com/RyKaj/Documentation/tree/master/Database/README.md) |
------------

# Database : MSSQL Code Review


## Folder Structure

Configuration of Database project folder structure can found in Git Flow
Process, section Database Project - Folder Structure

### Code Review Process

#### Review Process

1.  Developer will create a feature branch off develop to work off
2.  When the developer creates a Pull Request - 2 level PR
	1.  Development Manager/Team Lead
	2.  DBA's are the default code reviewer

## Code Review Standards

### Document Style Guide

#### Documentation

##### Header


` 
/******************************************************************************
Procedure Name : <Stored Procedure/Function/View>
Version : <>
Process        : <> 
Description    : 
Parameters     : 
Returns        :

*******************************************************************************
 Change History  
*******************************************************************************
 Date:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; By: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Description:  
YYYY-MM-DD &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt; Author Name &gt;  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   &lt; &gt;
 

**********************************************************************************/

### Do's, Dont's, Naming Conversions

#### Naming Conventions

  - Do not use spaces in the name of database objects
  - Do not use SQL keyword as name of database object
  - Do not use prefix stored procedure with `sp`
  - Use consistent and descriptive Identifiers and Names
  - Camel case for all items
  - Keep code succinct and devoid of redundant SQL - such as unnecessary
	quoting or parentheses of WHERE clause that can otherwise be derived
  - Tables name should be plural - ends with`s`
  - Ensure the name is unique and does not exist as a reserved keyword
  - Name patterns  
	  - Store Procedures
		  - \<Function\>\<Action\>\<Store Procedure Name\>
	  - Functions
		  - \<Function\>\<Action\>\<Function Name\>
	  - Views
		  - \<ViewName\>
	  - Triggers
		  - \<TableName\>\_\<Action\>\<Description\>
	  - Indexes  
		  - \<TableName\>\_\<columns separated by name\>
	  - Keys
		  - PK\_\<TableName\>
		  - FK\_\<TableName\_1\>\_\<TableName\_2\>
	  - Database Backups
		  - \<DatabaseName\>\<YYYY\>\<MMM\>\<DD\>.bak
	  - Synonyms
		  - \<DatabaseName\>\_\[SchemeName\]\_\<TableName\>
	  - Tables
		  - Use a collective name or, less ideally, a plural form. For
			example (in order of preference) `staff` and `employees`.
		  - Do not prefix with `tbl` or any other such descriptive
			prefix or Hungarian notation.
		  - Never give a table the same name as one of its columns and
			vice versa.
		  - Avoid, where possible, concatenating two table names
			together to create the name of a relationship table. Rather
			than `cars_mechanics` prefer `services`.
	  - Columns
		  - Always use the singular name.
		  - Where possible avoid simply using `id` as the primary
			identifier for the table.
		  - Do not add a column with the same name as its table and vice
			versa.
		  - Always use lowercase except where it may make sense not to
			such as proper nouns.

#### Do's

  - Use NOCOUNT ON
  - SELECT only the columns you need
  - Always use a column list in your Insert statement - Do not use SELECT \* (Don't use asterisk)
  - Use single quote characters to delimit string
  - Use parentheses to increase readability
  - Use space to in expressions to increase readability
  - Format JOIN operations using indents
  - Optimize queries using the tools provided by IDE
  - Return multiple result sets from one stored procedure to avoid trips from the application server to SQL server
  - Fully qualify table and columns names in JOINs
  - Fully qualify all Stored Procedures and table references
  - Place all DECLARE statements before any other code in procedure - top of the page
  - Check the global variable @@ERROR immediately after executing a data manipulation statement
  - Try to off-load tasks like string manipulations, concatenations, row numbering, case conversion to the middle layer

#### Don'ts

  - Do not use SELECT \*  ( Don't use asterisk ) List all column names individually
  - Never use column number within Order by clause
  - Non-correlated scalar sub query
  - Avoid the use of GOTO command
  - Do not target database in programmatic files (Store Procedures, Views, User Defined Functions, Triggers, etc..) Avoid USE \<dbname\>
  - Avoid unnecessary use of temporary tables
  - Avoid using `<>` as a comparison operator
  - Do not use cursors or applications loops to do Inserts, Deletes, or Updates
  - Do not defined default values for parameters
  - Do not use RECOMPILE option for stored procedure
  - Avoid using CROSS JOIN, if possible

## Performance

<table>
	<tbody>
		<tr>
			<td>&nbsp;</td>
			<td>
				<p>
					<strong>Don't</strong>
				</p>
			</td>
			<td>
				<p>
					<strong>Do</strong>
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<p>Be Careful When Dividing Integers</p>
			</td>
			<td>&nbsp;</td>
			<td>&nbsp;</td>
		</tr>
		<tr>
			<td>&nbsp;</td>
			<td>&nbsp;</td>
			<td>&nbsp;</td>
		</tr>
		<tr>
			<td>&nbsp;</td>
			<td>&nbsp;</td>
			<td>&nbsp;</td>
		</tr>
		<tr>
			<td>&nbsp;</td>
			<td>&nbsp;</td>
			<td>&nbsp;</td>
		</tr>
		<tr>
			<td>&nbsp;</td>
			<td>&nbsp;</td>
			<td>&nbsp;</td>
		</tr>
	</tbody>
</table>




## Best Practices Rules - Code Anlaysis

### Code Anlaysis

#### [**BP001 – Index type is not specified**](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp001) [<kbd>![](https://documentation.red-gate.com/xx/files/36178435/41359847/1/1460466876883/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

The index type (whether it is CLUSTERED or NONCLUSTERED) is not specified explicitly in the CREATE INDEX statement.

*You can only have one clustered index on a table, of course, and this choice has a lot of influence on the performance of queries, so you
should take care to select wisely. The primary key is often, but not only, the correct choice.*

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp001)

#### **[BP002 – ORDER BY clause with constants](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp002)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

Constants are being used in the ORDER BY clause.

*The use of constants in the ORDER BY is deprecated for removal in the future. They make ORDER BY statements more difficult to understand.*

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp002)

#### **[BP003 – SELECT in trigger](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp003)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

One or more SELECT statements were found in a trigger.

*The trigger should never return data to a client. It is possible to place a SELECT statement in a trigger, but it serves no practical,
useful purpose, and can have unexpected effects.*

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp003)

#### **[BP004 – INSERT without column list](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp004)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

The column list for the insert statement is missing.

*The INSERT statement need not have a column list, but omitting it assumes certain columns in a particular order. It likely to cause errors
if the table in to which the inserts will be made is changed, particularly with table variables where insertions are not checked.
Column lists also make code more intelligible.*

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp004)

#### **[BP005 – Asterisk in select list](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp005)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

There is an asterisk instead of a column list in a SELECT statement.

*SELECT \* FROM in IF EXISTS statements are fine, but SELECT \* in other contexts assumes certain columns in a particular order, which may
not last. Also, results should always consist of just the columns you need.*

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp005)

#### **[BP006 – TOP without ORDER BY](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp006)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

TOP is being used in a SELECT statement without a subsequent ORDER BY
clause.

*This is legal in SQL but meaningless because asking for the TOP 10 rows
implies a certain order, and tables have no implicit logical order.*

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp006)

#### **[BP007 – Variable length datatype without explicit length](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp007)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

Variable length datatype is declared without explicit length (VARCHAR, VARBINARY and NVARCHAR).

*A variable length datatype that is declared without an explicit length is a shorthand for specifying a length of 1.*

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp007)

#### **[BP008 – CAST/CONVERT to var types without length](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp008)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

The length of VARCHAR, VARBINARY and NVARCHAR datatype in a CAST or CONVERT clause wasn’t explicitly specified.

*When you convert a datatype to a varchar, you do not have to specify the length. If you don’t do so, SQL Server will use a Varchar length
sufficient to hold the string. It is better to specify the length because SQL Server has no idea what length you may subsequently need.*

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp008)

#### **[BP009 – Avoid var types of length 1 or 2](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp009)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

You have used a Variable length datatype (NVARCHAR , VARCHAR or BINARY) of length 1 or 2.

Very small CHAR and BINARY values are more economically stored than their VAR equivalents. Specify the datatype of  the fixed-length version.  

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp009)

#### **[BP010 – Usage of @@IDENTITY](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp010)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

@@IDENTITY is being used to get the value of the last identity insertion.

*If you have a trigger on the table, the value can sometimes be wrong. The @@IDENTITY function returns the last identity created in the same
session whereas SCOPE\_IDENTITY() function returns the last identity created in the same scope as well. Using SCOPE\_IDENTITY() is safer.*

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp010)

#### **[BP011 – NULL comparison or addition/substring](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp011)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

A comparison or expression is using NULL without explicit provision for a NULL value.

*Any expression or comparison that involves a NULL value will produce a NULL result. Expressions need to use IS \[NOT\] NULL and the
ISNULL/COALESCE function to handle NULL values appropriately.*

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp011)

#### **[BP012 – CASE without ELSE](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp012)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

The CASE statement doesn't specify what happens when all WHEN expressions evaluate to FALSE.

*The ELSE clause can be omitted but unless you use the ELSE clause of the CASE statement, you will find that a NULL is returned if all WHEN
expressions return FALSE. If you really want to do this, make it explicit so the code is easier to understand.*

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp012)

#### **[BP013 – EXECUTE(string) is used](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp013)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

EXECUTE (string) is being used to execute a SQL batch in a string.

*sp\_executesql supports parameter substitution, and generates execution plans that are more likely to be reused by SQL Server.*

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp013)

#### **[BP014 – \[NOT\] NULL option is not specified in CREATE/DECLARE TABLE statement](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp014)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

A column definition has not specified that a column is NULL or NOT NULL.

*Because the default of allowing NULLs can be changed with the database setting ‘ANSI\_NULL\_DFLT\_ON’, you should explicitly define a column as
NULL or NOT NULL for noncomputed columns or, if you use a user-defined data type, that you allow the column to use the default nullability of
the data type. Sparse columns must always allow NULL.* 

*NOTE: This issue is only shown once for each table definition.*

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp014)

#### **[BP015 – Scope of cursor (LOCAL/GLOBAL) is not specified](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp015)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

You have not explicitly defined the scope of a cursor.

*When you define a cursor with the DECLARE CURSOR statement you can, and should, define the scope of the cursor name. GLOBAL means that the
cursor name should be global to the connection. LOCAL specifies that the cursor name is LOCAL to the stored procedure, trigger, or batch
containing the DECLARE CURSOR statement.*

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp015)

#### **[BP016 – Return without result code](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp016)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

You have a stored procedure that does not return a result code.

*When you use the EXECUTE command to execute a stored procedure, or call the stored procedure from an application, an integer is returned that
can be assigned to a variable. It is generally used to communicate the success of the operation.*

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp016)

#### **[BP017 – DELETE statement without WHERE clause](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp017)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

A DELETE statement has omitted that WHERE clause, which would delete the whole table.

*It is very easy to delete an entire table when you mean to delete just one or more rows.*

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp017)

#### **[BP018 – UPDATE statement without WHERE clause](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp018)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

The UPDATE statement has omitted the WHERE clause, which would update every row in the table.

*It is very easy to delete an entire table when you mean to delete just one or more rows. Delete statements should also be in a transaction so
you can check the result before committing.*

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp018)

#### **[BP020 – Column created with option ANSI\_PADDING set to OFF](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp020)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

*Column created with option ANSI\_PADDING set to OFF.*

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp020)

#### **[BP021 –  Table does not have clustered index](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp021)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

Most tables should have a clustered index

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp021)

#### **[BP022 – Money/SmallMoney datatype is used](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp018)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

The MONEY data type confuses the storage of data values with their display, though it clearly suggests, by its name, the sort of data held.
Using the DECIMAL data type is almost always better.

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp022)

#### **[BP023 – Float/real datatype is used](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp023)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

The FLOAT (8 byte) and REAL (4 byte) data types are suitable only for specialist scientific use since they are approximate types with an
enormous range (-1.79E+308 to -2.23E-308, and 2.23E-308 to 1.79E+308, in the case of FLOAT).

Any other use needs to be regarded as suspect, and a FLOAT or REAL used as a key or found in an index needs to be investigated.

The DECIMAL type is an exact data type and has an impressive range from -10^38+1 through 10^38-1. Although it requires more storage than the
FLOAT or REAL types, it is generally a better choice.

[Learn more about this rule](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp023)

#### **[BP024 – sql\_variant datatype is used](https://documentation.red-gate.com/codeanalysis/best-practice-rules/bp024)** [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864471/1/1511184517205/prompt+16.png)](https://documentation.red-gate.com/sp9) [<kbd>![](https://documentation.red-gate.com/codeanalysis/files/44863593/44864472/1/1511184517220/SCG)](https://documentation.red-gate.com/scg/sql-code-analysis-documentation)

The sql\_variant type is not your typical data type. It stores values from a number of different data types and is used internally by SQL
Server. It is hard to imagine a valid use in a relational database. It cannot be returned to an application via ODBC except as binary data, and
it isn’t supported in Microsoft Azure SQL Database.

References

  - [Red Gate  - Code Analysis Best Practice](https://documentation.red-gate.com/codeanalysis/best-practice-rules)
  - [SQL Style Guide](https://www.sqlstyle.guide/)
  - [SQL Authority - sql server coding standards guidelines part 1](https://blog.sqlauthority.com/2008/09/24/sql-server-coding-standards-guidelines-part-2/)
  - [SQL Authority - sql server coding standards guidelines part 2](https://blog.sqlauthority.com/2008/09/24/sql-server-coding-standards-guidelines-part-2/)
