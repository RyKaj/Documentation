###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Database](https://github.com/RyKaj/Documentation/tree/master/Database/README.md) |
------------

# Database : Postgres Learning Materials

## Syntax

### Comments

#### Single Line

Single-line comments are preceded by two dashes (- - ) and may either be on a line by themselves, or they may follow valid SQL tokens. (The
comments themselves are not considered tokens to PostgreSQL's parser, as any character data following the - - sequence, up to the end of the
line, is treated as whitespace.)

> testdb=# SELECT 'Test' -- This can follow valid SQL tokens,
> testdb-#               -- or be on a line of it own.
> testdb-# AS example;
>  example
> ---------
>  Test
> (1 row)

#### Multi Line

Multiline comments begin with a sequential slash-asterisk (/\* ) sequence, and terminate with a sequential asterisk-slash (\*/ )
sequence. This style of commenting may already be familiar to C programmers, but there is one key difference between PostgreSQL's
interpreter and the C language interpreter: PostgreSQL comments may be *nested* . Therefore, when you create a multiline comment within another
multiline comment, the \*/ used to close the inner comment does not also close the outer comment.
> ``` 
> testdb=# SELECT 'Multi' /* This comment extends across
> testdb*#                 * numerous lines, and can be
> testdb*#                 * /* nested safely */ */
> testdb-# || '-test' AS example;
>   example
> ------------
>  Multi-test
> (1 row)
> ```

### Punctuation Symbols

<table>
	<thead>
		<tr>
			<th>Character</th>
			<th>Definition</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>* (asterisk)</td>
			<td>Used with the SELECT command to query all columns in the table, and with the count() aggregate function to count all rows in a table.</td>
		</tr>
		<tr>
			<td>() (parentheses)</td>
			<td>Used to group expressions, enforce operator precedence, and to make function calls. The use of parentheses is highly subjective to the context in which they are used.</td>
		</tr>
		<tr>
			<td>[] (brackets)</td>
			<td>Used in the selection of specific elements in an array, or in the declaration of an array type (e.g., with the CREATE TABLE command).</td>
		</tr>
		<tr>
			<td>; (semicolon)</td>
			<td>Used to terminate a SQL command. The only place it can be used within a statement is within a string constant or quoted identifier.</td>
		</tr>
		<tr>
			<td>, (comma)</td>
			<td>Some commands use the comma to separate elements within a list.</td>
		</tr>
		<tr>
			<td>. (period)</td>
			<td>Used in floating-point constants (e.g., 3.1415), as well as to reference column names as children of tables (e.g., table_name.column_name).</td>
		</tr>
		<tr>
			<td>: (colon)</td>
			<td>Used to select 
				<em>slices</em> from arrays.
			</td>
		</tr>
	</tbody>
</table>

### DataTypes

<table>
	<thead>
		<tr>
			<td>
				<p>
					<strong>Category</strong>
				</p>
			</td>
			<td>
				<p>
					<strong>Data type</strong>
				</p>
			</td>
			<td>
				<p>
					<strong>Description</strong>
				</p>
			</td>
			<td>
				<p>
					<strong>Standardization</strong>
				</p>
			</td>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td rowspan="3">
				<p>
					<em>Boolean and binary types</em>
				</p>
			</td>
			<td>
				<p>boolean,&nbsp;bool</p>
			</td>
			<td>
				<p>A single true or false value.</p>
			</td>
			<td>
				<p>SQL99</p>
			</td>
		</tr>
		<tr>
			<td>
				<p>bit(
					<em>n</em>&thinsp;)
				</p>
			</td>
			<td>
				<p>An&nbsp;
					<em>n</em>&thinsp;-length bit string (exactly&nbsp;
					<em>n</em>&nbsp;binary bits).
				</p>
			</td>
			<td>
				<p>SQL92</p>
			</td>
		</tr>
		<tr>
			<td>
				<p>bit varying(
					<em>n</em>&thinsp;),&nbsp;varbit(
					<em>n</em>&thinsp;)
				</p>
			</td>
			<td>
				<p>A variable&nbsp;
					<em>n</em>&thinsp;-length bit string (up to&nbsp;
					<em>n</em>&nbsp;binary bits)
				</p>
			</td>
			<td>
				<p>SQL92</p>
			</td>
		</tr>
		<tr>
			<td rowspan="3">
				<p>
					<em>Character types</em>
				</p>
			</td>
			<td>
				<p>character (
					<em>n</em>&thinsp;),&nbsp;char(
					<em>n</em>&thinsp;)
				</p>
			</td>
			<td>
				<p>A fixed&nbsp;
					<em>n</em>&thinsp;-length character string.
				</p>
			</td>
			<td>
				<p>SQL89</p>
			</td>
		</tr>
		<tr>
			<td>
				<p>character varying(
					<em>n</em>&thinsp;),&nbsp;varchar(
					<em>n</em>&thinsp;)
				</p>
			</td>
			<td>
				<p>A variable length character string of up to&nbsp;
					<em>n</em>&nbsp;characters.
				</p>
			</td>
			<td>
				<p>SQL92</p>
			</td>
		</tr>
		<tr>
			<td>
				<p>text</p>
			</td>
			<td>
				<p>A variable length character string, of unlimited length.</p>
			</td>
			<td>
				<p>PostgreSQL-specific</p>
			</td>
		</tr>
		<tr>
			<td rowspan="7">
				<p>
					<em>Numeric types</em>
				</p>
			</td>
			<td>
				<p>smallint,&nbsp;int2</p>
			</td>
			<td>
				<p>A signed 2-byte integer.</p>
			</td>
			<td>
				<p>SQL89</p>
			</td>
		</tr>
		<tr>
			<td>
				<p>integer,&nbsp;int,&nbsp;int4</p>
			</td>
			<td>
				<p>A signed, fixed-precision 4-byte number.</p>
			</td>
			<td>
				<p>SQL92</p>
			</td>
		</tr>
		<tr>
			<td>
				<p>bigint,&nbsp;int8</p>
			</td>
			<td>
				<p>A signed 8-byte integer, up to 18 digits in length.</p>
			</td>
			<td>
				<p>PostgreSQL-specific</p>
			</td>
		</tr>
		<tr>
			<td>
				<p>real,&nbsp;float4</p>
			</td>
			<td>
				<p>A 4-byte floating-point number.</p>
			</td>
			<td>
				<p>SQL89</p>
			</td>
		</tr>
		<tr>
			<td>
				<p>double precision,&nbsp;float8,&nbsp;float</p>
			</td>
			<td>
				<p>An 8-byte floating-point number.</p>
			</td>
			<td>
				<p>SQL89</p>
			</td>
		</tr>
		<tr>
			<td>
				<p>numeric(
					<em>p</em>,
					<em>s</em>&thinsp;),&nbsp;decimal(
					<em>p</em>,
					<em>s</em>&thinsp;)
				</p>
			</td>
			<td>
				<p>An exact numeric type with arbitrary precision&nbsp;
					<em>p</em>, and scale&nbsp;
					<em>s</em>.
				</p>
			</td>
			<td>
				<p>SQL99</p>
			</td>
		</tr>
		<tr>
			<td>
				<p>money</p>
			</td>
			<td>
				<p>A fixed precision, U.S.-style currency.</p>
			</td>
			<td>
				<p>PostgreSQL-specific, deprecated.</p>
			</td>
		</tr>
	</tbody>
</table>

### Boolean Values

<table>
	<thead>
		<tr>
			<th>True</th>
			<th>False</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>true</td>
			<td>false</td>
		</tr>
		<tr>
			<td>'t'</td>
			<td>'f '</td>
		</tr>
		<tr>
			<td>'true'</td>
			<td>'false'</td>
		</tr>
		<tr>
			<td>'y'</td>
			<td>'n'</td>
		</tr>
		<tr>
			<td>'yes'</td>
			<td>'no'</td>
		</tr>
		<tr>
			<td>'1'</td>
			<td>'0'</td>
		</tr>
	</tbody>
</table>


### Character Types

<table>
	<thead>
		<tr>
			<th>Type</th>
			<th>Storage</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>character( 
				<em>n</em> ), char( 
				<em>n</em> )
			</td>
			<td>(4 + 
				<em>n</em> ) bytes
			</td>
			<td>A fixed-length character string, padded with spaces so that it is 
				<em>n</em> characters in length.
			</td>
		</tr>
		<tr>
			<td>character varying( 
				<em>n</em> ), varchar( 
				<em>n</em> )
			</td>
			<td>Up to (4 + 
				<em>n</em> ) bytes
			</td>
			<td>A variable-length character string with a limit of 
				<em>n</em> characters
			</td>
		</tr>
		<tr>
			<td>text</td>
			<td>Variable</td>
			<td>A variable, unlimited-length character string</td>
		</tr>
	</tbody>
</table>

### Numeric Types

PostgreSQL's numeric types are used to represent both integers and decimal floating-point values. From a general perspective, PostgreSQL's
supported numeric types consist of:

  - Two-, four-, and eight-byte integers
  - Four- and eight-byte floating-point numbers
  - Fixed precision decimals

PostgreSQL has support for special types which fall under the family of numeric types, including the deprecated money type, and the special
serial construct.

<table>
	<thead>
		<tr>
			<th>Data type</th>
			<th>Storage</th>
			<th>Range</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>bigint, int8</td>
			<td>8 bytes</td>
			<td>Whole integer values, –9,223,372,036,854,775,807 to +9,223,372,036,854,775,807</td>
		</tr>
		<tr>
			<td>double precision, float8, float</td>
			<td>8 bytes</td>
			<td>Floating-point integer values, 15 significant digits, unlimited size (with limited precision)</td>
		</tr>
		<tr>
			<td>integer, int, int4</td>
			<td>4 bytes</td>
			<td>Whole integer values, –2147483648 to +2147483647</td>
		</tr>
		<tr>
			<td>numeric( 
				<em>p</em>, 
				<em>s</em> ), decimal (
				<em>p</em>, 
				<em>s</em> )
			</td>
			<td>Variable</td>
			<td>Whole or floating point integers defined as 
				<em>p</em> total digits (including digits to the right of the decimal) with 
				<em>s</em> digits to the right of the decimal point
			</td>
		</tr>
		<tr>
			<td>real, float4</td>
			<td>4 bytes</td>
			<td>Floating-point integer values, six significant digits, unlimited size (with limited precision)</td>
		</tr>
		<tr>
			<td>smallint, int2</td>
			<td>2 bytes</td>
			<td>Whole integers, –32768 to +32767</td>
		</tr>
		<tr>
			<td>money</td>
			<td>4 bytes</td>
			<td>Floating-point integer values with a scale of two digits to the right of the decimal, —21474836.48 to +21474836.47</td>
		</tr>
		<tr>
			<td>serial</td>
			<td>4 bytes</td>
			<td>Whole integers, 0 to 2147483647</td>
		</tr>
	</tbody>
</table>


### The Monetary Type

The money type stores U.S.-style currency notation and plain numeric values. As of the writing of this book, the money type is deprecated,
and is discouraged from being actively used. It is only presented here as it is still a functional data type, and may be in use on existing
PostgreSQL systems.

The suggested alternative to the money type is the numeric type, with a scale of 2 to represent coin values, and a precision large enough to
store the largest necessary monetary value (including two digits for the coin precision).


>     booktown=# CREATE TABLE auto_identified (id serial);
>     NOTICE:  CREATE TABLE will create implicit sequence 'auto_identified_id_seq'
>     for SERIAL column 'auto_identified.id'
>     NOTICE:  CREATE TABLE/UNIQUE will create implicit index 'auto_identified_id_key'
>     for table 'auto_identified'
>     CREATE

### The serial type

The serial type is a non-standard but useful shortcut which allows you to easily create an identifier column within a table that contains a
unique value for each row. The serial type literally combines the functionality of a 4-byte integer data type, an index, and a sequence.

#### Using the serial data type

> ``` 
> booktown=# CREATE TABLE auto_identified (id serial);
> NOTICE:  CREATE TABLE will create implicit sequence 'auto_identified_id_seq'
> for SERIAL column 'auto_identified.id'
> NOTICE:  CREATE TABLE/UNIQUE will create implicit index 'auto_identified_id_key'
> for table 'auto_identified'
> CREATE
> ```

#### Accomplishing the same goal manually

> ``` 
> booktown=#  CREATE SEQUENCE auto_identified_id_seq;
> CREATE booktown=# CREATE TABLE auto_identified 
> booktown-# (id integer UNIQUE DEFAULT nextval('auto_identified_id_seq'));
> NOTICE:  CREATE TABLE/UNIQUE will create implicit index 'auto_identified_id_key' for table 'auto_identified'
> CREATE
> ```

### Date and Time Types

Date and time types are a convenient way to store date and time related data in a uniform SQL data structure, without having to worry about the
conventions involved with storage (e.g., if you were to try to store such information in a character data type). PostgreSQL uses Julian dates
for all date and time calculations. Julian date representation is the commonly used January through December calendar that you are most likely
familiar with. By fixing the length of a year at about 365.24 days, Julian dates can correctly calculate any date after 4713 BC, as well as
far into the future.

<table>
	<thead>
		<tr>
			<th>Name</th>
			<th>Storage</th>
			<th>Description</th>
			<th>Range</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>date</td>
			<td>4 bytes</td>
			<td>A calendar date (year, month, and day)</td>
			<td>4713 BC to 32767 AD</td>
		</tr>
		<tr>
			<td>time</td>
			<td>4 bytes</td>
			<td>The time of day only, without time zone information</td>
			<td>00:00:00.00 to 23:59:59.99</td>
		</tr>
		<tr>
			<td>time with time zone</td>
			<td>4 bytes</td>
			<td>The time of day only, including a time zone</td>
			<td>00:00:00.00+12 to 23:59:59.99-12</td>
		</tr>
		<tr>
			<td>timestamp (includes time zone)</td>
			<td>8 bytes</td>
			<td>Both the calendar date and time, with time zone information</td>
			<td>1903 AD to 2037 AD</td>
		</tr>
		<tr>
			<td>interval</td>
			<td>12 bytes</td>
			<td>A general time span interval</td>
			<td>–1780000000 years to 17800000 years</td>
		</tr>
	</tbody>
</table>

### Valid date formats

<table>
	<thead>
		<tr>
			<th>Format Example</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>July 1, 2001</td>
			<td>Named month, day and year</td>
		</tr>
		<tr>
			<td>Sunday July 1, 2001</td>
			<td>Named day, named month, day and year</td>
		</tr>
		<tr>
			<td>July 15, 01 BC</td>
			<td>Named month, day and year before the Common Era</td>
		</tr>
		<tr>
			<td>2001-07-01</td>
			<td>Standard ISO-8601 format: numeric year, month and day</td>
		</tr>
		<tr>
			<td>20010715</td>
			<td>ISO-8601: formatted numerically as complete year, month, day</td>
		</tr>
		<tr>
			<td>010715</td>
			<td>ISO-8601: formatted numerically as 2-digit year, month, day</td>
		</tr>
		<tr>
			<td>7/01/2001</td>
			<td>Non-European (U.S.) format: numeric month, day and year</td>
		</tr>
		<tr>
			<td>1/7/2001</td>
			<td>European format: numeric day, month and year</td>
		</tr>
		<tr>
			<td>2001.182</td>
			<td>Numeric format, with complete year, and sequential day of the year</td>
		</tr>
	</tbody>
</table>

### Month abbreviations

<table>
	<thead>
		<tr>
			<th>Month</th>
			<th>Abbreviation</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>January</td>
			<td>Jan</td>
		</tr>
		<tr>
			<td>February</td>
			<td>Feb</td>
		</tr>
		<tr>
			<td>March</td>
			<td>Mar</td>
		</tr>
		<tr>
			<td>April</td>
			<td>Apr</td>
		</tr>
		<tr>
			<td>May</td>
			<td>May</td>
		</tr>
		<tr>
			<td>June</td>
			<td>Jun</td>
		</tr>
		<tr>
			<td>July</td>
			<td>Jul</td>
		</tr>
		<tr>
			<td>August</td>
			<td>Aug</td>
		</tr>
		<tr>
			<td>September</td>
			<td>Sep, Sept</td>
		</tr>
		<tr>
			<td>October</td>
			<td>Oct</td>
		</tr>
		<tr>
			<td>November</td>
			<td>Nov</td>
		</tr>
		<tr>
			<td>December</td>
			<td>Dec</td>
		</tr>
	</tbody>
</table>


### Day of the week abbreviations

<table>
	<thead>
		<tr>
			<th>Day</th>
			<th>Abbreviation</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>Sunday</td>
			<td>Sun</td>
		</tr>
		<tr>
			<td>Monday</td>
			<td>Mon</td>
		</tr>
		<tr>
			<td>Tuesday</td>
			<td>Tue, Tues</td>
		</tr>
		<tr>
			<td>Wednesday</td>
			<td>Wed, Weds</td>
		</tr>
		<tr>
			<td>Thursday</td>
			<td>Thu, Thur, Thurs</td>
		</tr>
		<tr>
			<td>Friday</td>
			<td>Fri</td>
		</tr>
		<tr>
			<td>Saturday</td>
			<td>Sat</td>
		</tr>
	</tbody>
</table>


### Date output formats

<table>
	<thead>
		<tr>
			<th>General format</th>
			<th>Description</th>
			<th>Example</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>ISO</td>
			<td>ISO-8601 standard</td>
			<td>2001-06-25 12:24:00-07</td>
		</tr>
		<tr>
			<td>SQL</td>
			<td>Traditional SQL style</td>
			<td>06/25/2001 12:24:00.00 PDT</td>
		</tr>
		<tr>
			<td>Postgres</td>
			<td>Original PostgreSQL style</td>
			<td>Mon 25 Jun 12:24:00 2001 PDT</td>
		</tr>
		<tr>
			<td>German</td>
			<td>Regional style for Germany</td>
			<td>25.06.2001 12:24:00.00 PDT</td>
		</tr>
	</tbody>
</table>



### Extended date output formats

<table>
	<thead>
		<tr>
			<th>Month/day format</th>
			<th>Description</th>
			<th>Example</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>European</td>
			<td>day/month/year</td>
			<td>12/07/2001 17:34:50.00 MET</td>
		</tr>
		<tr>
			<td>U.S., or Non-European</td>
			<td>month/day/year</td>
			<td>07/12/2001 17:34:50.0 PST</td>
		</tr>
	</tbody>
</table>

### Time conventions

Time values, like date values, may be entered in to a table in a number of ways.

<table>
	<thead>
		<tr>
			<th>Format example</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>01:24</td>
			<td>ISO-8601, detailed to minutes</td>
		</tr>
		<tr>
			<td>01:24 AM</td>
			<td>Equivalent to 01:24 (the &quot;AM&quot; attached is for readability only, and does not affect the value)</td>
		</tr>
		<tr>
			<td>01:24 PM</td>
			<td>Equivalent to 13:24 (the hour must be less-than or equal to 12 to use &quot;PM&quot;)</td>
		</tr>
		<tr>
			<td>13:24</td>
			<td>24-hour time, equivalent to 01:24 PM</td>
		</tr>
		<tr>
			<td>01:24:11</td>
			<td>ISO-8601, detailed to seconds</td>
		</tr>
		<tr>
			<td>01:24:11.112</td>
			<td>ISO-8601, detailed to microseconds</td>
		</tr>
		<tr>
			<td>012411</td>
			<td>ISO-8601, detailed to seconds, formatted numerically</td>
		</tr>
	</tbody>
</table>


### Valid time zone formats

<table>
	<thead>
		<tr>
			<td>
				<p>
					<strong>Format Example</strong>
				</p>
			</td>
			<td>
				<p>
					<strong>Description</strong>
				</p>
			</td>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>
				<p>01:24:11-7</p>
			</td>
			<td>
				<p>ISO-8601, 7 hours behind GMT</p>
			</td>
		</tr>
		<tr>
			<td>
				<p>01:24:11-07:00</p>
			</td>
			<td>
				<p>ISO-8601, 7 hours, zero minutes behind GMT</p>
			</td>
		</tr>
		<tr>
			<td>
				<p>01:24:11-0700</p>
			</td>
			<td>
				<p>ISO-8601, 7 hours, zero minutes behind GMT</p>
			</td>
		</tr>
		<tr>
			<td>
				<p>01:24:11 PST</p>
			</td>
			<td>
				<p>ISO-8601, Pacific Standard Time (7 hours behind GMT)</p>
			</td>
		</tr>
	</tbody>
</table>



### Timestamps

The PostgreSQL timestamp combines the functionality of the PostgreSQL date and time types into a single data type. The syntax of a timestamp
value consists of a valid date format, followed by at least one whitespace character, and a valid time format. It can be followed
optionally by a time zone value, if specified.

#### Some valid timestamp formats

<table>
	<thead>
		<tr>
			<th>Format example</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>01:24:11-7</td>
			<td>ISO-8601, 7 hours behind GMT</td>
		</tr>
		<tr>
			<td>01:24:11-07:00</td>
			<td>ISO-8601, 7 hours, zero minutes behind GMT</td>
		</tr>
		<tr>
			<td>01:24:11-0700</td>
			<td>ISO-8601, 7 hours, zero minutes behind GMT</td>
		</tr>
		<tr>
			<td>01:24:11 PST</td>
			<td>ISO-8601, Pacific Standard Time (7 hours behind GMT)</td>
		</tr>
	</tbody>
</table>

																																														  |
**Warning**
While PostgreSQL supports the syntax of creating a column or value with the type timestamp without time zone, as of PostgreSQL 7.1.2 
the resultant data type still contains a time zone.



### Intervals

The SQL92 standard specifies a data typed called an *interval* , which represents a fixed span of time. By itself, an interval represents only
a *quantity of time* , and does not begin or end at any set date or time. These intervals can be useful when applied to date and time values to calculate 
a new date or time, either by subtracting or adding the quantity. They can also be handy for quickly determining the precise interval between two date or time values. 
This can be achieved by subtracting date values, time values or timestamps from one another.

### Built-in date and time constants

PostgreSQL supports many special constants for use when referencing dates and times. These constants represent common date/time values, such as *now*, *tomorrow* , 
and *yesterday* .

<table>
	<thead>
		<tr>
			<th>Format Example</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>1980-06-25 11:11-7</td>
			<td>ISO-8601 date format, detailed to minutes, and PST time zone</td>
		</tr>
		<tr>
			<td>25/06/1980 12:24:11.112</td>
			<td>European date format, detailed to microseconds</td>
		</tr>
		<tr>
			<td>06/25/1980 23:11</td>
			<td>U.S. date format, detailed to minutes in 24-hour time</td>
		</tr>
		<tr>
			<td>25.06.1980 23:11:12 PM</td>
			<td>German regional date format, detailed to seconds, and PM attached</td>
		</tr>
	</tbody>
</table>                                                                                                                                  |



### Geometric types

Geometric types in PostgreSQL represent two dimensional spatial objects. These types are not standard SQL data types, and will not be discussed
in depth in this book. [Table 3-24](http://www.faqs.org/docs/ppbook/x2632.htm#GEOMETRICTYPESTABLE)
gives a brief overview of each of the available geometric types.

<table>
	<thead>
		<tr>
			<th>Type Name</th>
			<th>Storage</th>
			<th>Description</th>
			<th>Syntax</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>point</td>
			<td>16 bytes</td>
			<td>A dimensionless object with no properties except for its location, where x and y are floating-point numbers.</td>
			<td>(
				<em>x</em>, 
				<em>y</em> )
			</td>
		</tr>
		<tr>
			<td>lseg</td>
			<td>32 bytes</td>
			<td>Finite line segment. The points specified are the end points of the line segment.</td>
			<td>( (
				<em>x1</em> , 
				<em>y1</em> ), ( 
				<em>x2</em> , 
				<em>y2</em> ) )
			</td>
		</tr>
		<tr>
			<td>box</td>
			<td>32 bytes</td>
			<td>Rectangular box. The points specified are the opposite corners of the box.</td>
			<td>(( 
				<em>x1</em> , 
				<em>y1</em> ), ( 
				<em>x2</em> , 
				<em>y2</em> ))
			</td>
		</tr>
		<tr>
			<td>path</td>
			<td>4 + 32 * 
				<em>n</em> bytes
			</td>
			<td>Closed path (similar to polygon). A connected set of 
				<em>n</em> points.
			</td>
			<td>(( 
				<em>x1</em> , 
				<em>y1</em> ), ...)
			</td>
		</tr>
		<tr>
			<td>path</td>
			<td>4 + 32 * 
				<em>n</em> bytes
			</td>
			<td>Open path. A connected set of 
				<em>n</em> points.
			</td>
			<td>[( 
				<em>x1</em> , 
				<em>y1</em> ), ...]
			</td>
		</tr>
		<tr>
			<td>polygon</td>
			<td>4 + 32 * 
				<em>n</em> bytes
			</td>
			<td>Polygon (similar to closed path), with 
				<em>n</em> end points defining line segments that makes up the boundary of the polygon.
			</td>
			<td>(( 
				<em>x1</em> , 
				<em>y1</em> ), ...)
			</td>
		</tr>
		<tr>
			<td>circle</td>
			<td>24 bytes</td>
			<td>The point ( 
				<em>x</em> , 
				<em>y</em> ) is the center, while 
				<em>r</em> is the radius of the circle.
			</td>
			<td>&lt;( 
				<em>x</em> , 
				<em>y</em> ), 
				<em>r</em> &gt;
			</td>
		</tr>
	</tbody>
</table>

## Arrays

The original relational model specifies that the values represented by columns within a table be an atomic piece of data, object-relational
database systems such as PostgreSQL allow non-atomic values to be used through data structures called *arrays* .

An array is a collection of data values referenced through a single identifier. The array may be a collection of values of a built-in data
type or a user-defined data type, but every value in the array must be of the same type. Arrays can be accessed from a table through subscript
notation via square brackets (e.g., my\_array\[0\]). You can also use an
array constant via curly braces within single quotes (e.g., '{value\_one,value\_two,value\_three}').

### Arrays in tables

When defining an array, the syntax allows for the array to be defined either as fixed-length or variable-length; however as of PostgreSQL
7.1.2, the fixed-length size restriction is not enforced. This means that you may treat the array as having a fixed number of elements at all
times, but it can still be dynamically sized. For example, it is perfectly acceptable for a single column defined as an array to contain
three values in one record, four values in another, and no values in a third.

Additionally, arrays may be defined as being *multi-dimensional*, meaning that each element of the array may actually represent *another
array* , rather than an atomic value. Values that are selected from a multi-dimensional array will consist of nested curly braces in order to
show an array within an array, as follows:

> ``` 
> booktown=# SELECT editions FROM my_notes WHERE title='The Cat in the Hat'; editions
> ---------------------------------------------------------------
>  {{"039480001X","1st Ed, Hard Cover"},{"0394900014","1st Ed"}}
> (1 row)
> ```

### Array constants

In order to actually insert array values into a table column, you need a way to refer to several values as an array in a SQL statement. The
formal syntax of an array constant is a grouping of values, separated by delimiters (commas, for built-in data types), enclosed by curly braces
({}), which are in turn enclosed by single quotes, as follows:

> ``` 
>  '{ value1 , value2 [, ...] }'
> ```

The *values* in this syntax can be any valid PostgreSQL data type. As the entire array is constrained by single quotes, the use of single
quotes *within* an array value must be escaped, just as they must be within a string constant. The use of commas to delimit the values,
however, poses an interesting problem pertaining to the use of character strings which contain commas themselves, as the commas will be
interpreted as delimiters if not within single-quotes. However, as just mentioned, the singles quotes constrain the *array* , not the array's
*values*.

PostgreSQL's method of handling this is to use *double-quotes* to quote string constants where single-quotes would ordinarily be used outside of
an array context, as follows:

> ``` 
>  '{"value1" , "value 2, which contains a comma" }'
> ```

It's vital to remember that arrays *require* the single quotes surrounding the curly braces in order to be interpreted correctly by
PostgreSQL. You can think of array constants as being akin to a special type of string constant, which is interpreted as an array based on where
it is used (e.g., when used to add records to a target column which is of an array data type). This is because unless used in an array context,
a constant of the this format will be interpreted by PostgreSQL as a normal string constant (as it is bound by single quotes) which just
happens to include curly braces.

## Type Coercion

PostgreSQL supports three separate conventions for type coercion (also called *type casting* , or *explicit type casting* ). Type coercion is a
somewhat ugly looking term which refers to a PostgreSQL method for changing a value from one data type to another. In the middle of a SQL
statement, this has the net effect of explicitly creating a constant of an arbitrary type.

Generally any of the following three methods can be used in order to cast the value contained within a string constant to another type:
  - *type* '*value* '
  - '*value* ':: *type*
  - CAST (' *value* ' AS *type* )

In the case of maintained numeric constants that you wish to cast to a character string, you will need to use one of the following syntax forms:

  - *value* :: *type*
  - CAST ( *value* AS *type* )

The *value* in this syntax represents the constant whose data type you wish to modify, and *type* represents the type that you wish to coerce, 
or cast, the value into.

> **Note:** Remember that the money type is deprecated, and therefore
> not easily cast.

Constants are not the only data values that may be coerced to different types. Columns of a data set returned by a SQL query may be cast by
using its identifier in one of the following syntax forms:

  - *identifier* :: *type*
  - CAST ( *identifier* AS *type* )

Bear in mind that not every data type can be coerced into every other data type. For example, there is no meaningful way to convert the
character string *abcd* into a binary bit type. Invalid casting will result in an error from PostgreSQL. Common valid casts are from
character string, date/time type, or a numeric type to text, or character strings to numeric values.

In addition to these type casting conventions, there are some functions that can be called to achieve essentially the same effect as an explicit
cast of any of the previously mentioned forms. These often bear the name of the type itself (such as the text() function), though others are
named more specifically (such as bitfromint4()).

## Tables

### System Columns

PostgreSQL defines a series of *system columns* in all tables, which are normally invisible to the user (e.g., they will not be shown by queries
unless explicitly requested). These columns contain *meta-data* about the content of the table's rows. Many of these contain data that can
help to differentiate between *tuples* (an individual state of a row) when working with transaction blocks.

<table>
	<thead>
		<tr>
			<th>Column</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>oid (object identifier)</td>
			<td>The unique object identifier of a row. PostgreSQL automatically adds this 4-byte number to all rows. It is never re-used within the same table.</td>
		</tr>
		<tr>
			<td>tableoid (table object identifier)</td>
			<td>The oid of the table that contains a row. The name and oid of a table are related by the pg_class system table.</td>
		</tr>
		<tr>
			<td>xmin (transaction minimum)</td>
			<td>The transaction identifier of the inserting transaction of a tuple.</td>
		</tr>
		<tr>
			<td>cmin (command minimum)</td>
			<td>The command identifier, starting at 0, associated with the inserting transaction of a tuple.</td>
		</tr>
		<tr>
			<td>xmax (transaction maximum)</td>
			<td>The transaction identifier of a tuple's deleting transaction. If a tuple is visible (has not been deleted) this is set to zero.</td>
		</tr>
		<tr>
			<td>cmax (command maximum)</td>
			<td>The command identifier associated with the deleting transaction of a tuple. Like xmax, if a tuple is visible, this is set to zero.</td>
		</tr>
		<tr>
			<td>ctid (tuple identifier)</td>
			<td>The identifier which describes the physical location of the tuple within the database. A pair of numbers are represented by the ctid: the block number, and tuple index within that block.</td>
		</tr>
	</tbody>
</table>


### Object Identifiers

As described in the Section called *Understanding Tables*," each database consists of tables, and each table consists of at least one
named column. These tables may contain rows, but do not necessarily at any given time.

One table management concern can be how to distinguish between two rows whose column values are identical. A very useful PostgreSQL feature is
that every row has its own *object identifier* number, or *OID* , which is unique within that table. In other words, no two rows within the same
table will ever have the same OID. This means that even if a table were designed in such a way that two rows might be identical, there is still
a programmatic way to discern between them: via the OID.

Differentiating rows via the OID

> ``` 
> testdb=# SELECT * FROM my_list; 
> todos
> ----------------------------------
>  Correct redundancies in my list.
>  Correct redundancies in my list.
> (2 rows)
> 
> testdb=# SELECT *,oid FROM my_list;
>               todos               |   oid
> ----------------------------------+---------
>  Correct redundancies in my list. | 3391263
>  Correct redundancies in my list. | 3391264
> (2 rows)
> 
> testdb=# DELETE FROM my_list WHERE oid = 3391264;
> DELETE 1
> testdb=# SELECT *,oid FROM my_list;
>               todos               |   oid
> ----------------------------------+---------
>  Correct redundancies in my list. | 3391263
> (1 row
> ```

## Query Statements

### SELECT Clause

#### Syntax

> ``` 
> SELECT [ ALL | DISTINCT [ ON ( expression [, ...] ) ] ]  target [ AS name ] [, ...] 
> [ FROM source [, ...] ] 
>               [ [ NATURAL ] join_type source 
>               [ ON condition | USING ( column_list ) ] ] 
>               [, ...] 
>        [ WHERE condition ] 
>        [ GROUP BY expression [, ...] ] 
>        [ HAVING condition [, ...] ] 
>        [ { UNION | INTERSECT | EXCEPT } [ ALL ] sub-query ] 
>        [ ORDER BY expression 
>               [ ASC | DESC | USING operator ] 
>               [, ...] ] 
>        [ FOR UPDATE [ OF table [, ...] ] ] 
>         [ LIMIT { count | ALL } [ { OFFSET | , } start ] ]
> ```

In this syntax diagram, source may be either a table name or a subselect. The syntax for these general forms is as follows:

> ``` 
> FROM { [ ONLY ] table [ [ AS ] alias [ ( column_alias [, ...] ) ] ] |
> ( query ) [ AS ] alias [ ( column_alias [, ...] ) ] }
> ```

*ALL*  
The ALL keyword may be specified as a noise term to make it clear that all rows should be returned.

*DISTINCT \[ ON ( expression \[, ...\] ) \]*  
The DISTINCT clause specifies a column (or expression) for which to retrieve only one row per unique value of expression.

*target \[ AS name \] \[, ...\]*  
The SELECT targets are usually column names, though they can be constants, identifier, function or general expression. Each target
requested must be separated by commas, and may be named dynamically to name via the AS clause. Supplying the asterisk symbol (\*) as a target
is shorthand for requesting all non-system columns, and may be listed along with other targets.

*FROM source \[, ...\]*  
The FROM clause dictates the source that PostgreSQL will look in for the specified targets. The source, in this case, may be a table name or a
sub-query. You can specify numerous sources, separated by commas. (This is roughly equivalent to a cross join). The syntax for the FROM clause
is described in more detail later in this section.

*\[ NATURAL \] join\_type source \[ ON condition | USING ( column\_list) \]*  
The FROM sources may be joined together via the JOIN clause, which requires a join\_type (e.g., INNER, FULL OUTER, CROSS) and may require a
condition or column\_list to further define the nature of the join, depending on the join\_type.

*WHERE condition*  
The WHERE clause constrains the result set from the SELECT statement to specified criteria, which are defined by condition. Conditions must
return a single Boolean value (true or false), but may consist of several checks combined with logical operators (e.g., with AND, and OR)
to indicate that available rows must meet all supplied conditions to be included in the statement's results.

*GROUP BY expression \[, ...\]*  
The GROUP BY clause aggregates (groups) rows together by the criteria described in expression. This can be as simple as a column name (and
often is) or an arbitrary expression applied to values of the result set.

*HAVING condition \[, ...\]*  
The HAVING clause is similar to the WHERE clause, but checks its conditions on aggregated (grouped) sets instead of atomic rows.

*{ UNION | INTERSECT | EXCEPT } \[ ALL \] sub-query*  
Performs one of three set operations between the SELECT statement and a second query, returning their result sets in uniform column structure
(which must be compatible).

*UNION*  
Returns the set of collected rows.

*INTERSECT*  
Returns the set of rows where the values of the two sets overlap.

*EXCEPT*  
Returns the set of rows which are found in the SELECT statement, but not found in the secondary query.

*ORDER BY expression*  
Sorts the results of the SELECT statement by expression.

*\[ ASC | DESC | USING operator \]*  
Determines whether or not the ORDER BY expression proceeds in ascending order (ASC), or descending order (DESC). An operator may alternatively
be specified with the USING keyword (e.g., \< or \>).

*FOR UPDATE \[ OF table \[, ...\] \]*  
Allows for exclusive locking of the returned rows. When used within a transaction block, FOR UPDATE locks the rows of the specified table
until the transaction is committed. While locked, the rows cannot be updated by other transactions.

*LIMIT { count | ALL }*  
Limits the number of rows returned to a maximum of count, or explicitly allows ALL rows.

*{ OFFSET | , } start*  
Instructs the LIMIT clause at what point to begin limiting the results. For example, a LIMIT with a count set to 100, and an OFFSET clause with
a start value of 50 would return the rows from 50 to 150 (if there are that many results to return).

Terms used in the FROM clause's syntax description are as follows:

- *\[ ONLY \] table*  
The table name specifies what table to use as a source for the SELECT statement. Specifying the ONLY clause causes the rows of any child's table to be omitted from the query.

- *\[ AS \] alias*  
An alias may optionally be assigned to a FROM source, in order to simplify a query (e.g., books might be temporarily referenced with an alias of b). The AS term is considered noise, and is optional.

- *( query ) \[ AS \] alias*  
Any valid SELECT statement may be placed in parentheses as the query. This causes the result set created by the query to be used as a FROM source, as if it had been a static table. This use of a sub-query requires a specified alias.

- *( column\_alias \[, ...\] )*  
The FROM sources which have assigned aliases may also alias columns by specifying arbitrary column aliases. Each column\_alias must be separated by commas, and grouped within parentheses following the FROM source's alias. These aliases must match the order of the defined columns in the table to which it is applied.

### UPDATE Clause

#### Syntax
> 
> ``` 
> UPDATE [ ONLY ] table SET
>        column = expression [, ...]
>        [ FROM source ]
>        [ WHERE condition ]
> ```

The ONLY keyword may be used to indicate that only the table *table*should be updated, and none of its sub-tables. This is only
relevant if *table*is inherited by any other tables. *SET column = expression \[, ...\]*The required SET clause is
followed by an update expression for each column name that needs to have its values modified, separated by commas. This expression is always of
the form *column*= *expression*, where *column* is the name of the column to be updated (which may not be aliased, or dot-notated), and
where *expression* describes the new value to be inserted into the column. *FROM source* The FROM clause is a non-standard PostgreSQL
extension that allows table columns from other data sets to update a column's value. *WHERE condition* The WHERE clause describes the
*condition* upon which a row in *table* will be updated. If unspecified, *all values* in *column* will be modified. This may be used to qualify
sources in the FROM clause, as you would in a SELECT statement.

### DELETE Clause

#### Syntax

> ``` 
> DELETE FROM [ ONLY ] table
> [ WHERE condition ]
> ```

*DELETE FROM \[ ONLY \] table*  
The ONLY keyword may be used to indicate that only the table table should have rows removed from it, and none of its sub-tables. This is
only relevant if table is inherited by any other tables.

*WHERE condition*  
The WHERE clause describes under what condition to delete rows from table. If unspecified, all rows in the table will be deleted.

The WHERE clause is almost always part of a DELETE statement. It specifies which rows in the target table are to be deleted based on its
specified conditions, which may be expressed syntactically in the same form as in the SELECT statement.

### INSERT Clause

#### Syntax

> ``` 
> INSERT INTO table_name [ ( column_name [, ...] ) ] VALUES ( value [, ...] )
> ```

*table\_name*

The INSERT SQL command initiates an insertion of data into the table called table\_name.

*( column\_name \[, ...\] )*

An optional grouped expression which describes the targeted columns for the insertion.

*VALUES*

The SQL clause which instructs PostgreSQL to expect a grouped expression of values to follow.

*( value \[, ...\] )*

The required grouped expression that describes the values to be inserted. There should be one value for each specified column, separated
by commas. These values may be expressions themselves (e.g., an operation between two values), or constants.

### WHERE Clause

### GROUP BY Clause

### HAVING Clause

### ORDER BY Clause

### MATCH Clause

### BETWEEN

### LINE

### EXISTS

### IN

### SOME

### ANY

## Intermediate

### Variables

> ``` 
> DECLARE variable_name [ CONSTANT ] datatype [ NOT NULL ] [ { DEFAULT | := } initial_value ]
> ```

## Advanced

### Functions

#### Create

#### Alter

#### Rename

#### Drop

#### Existing Check

### Stored Procedure

#### Create

#### Alter

#### Rename

#### Drop

#### Existing Check

### Views

#### Create

> ``` 
> CREATE [OR REPLACE] VIEW view_name AS
> SELECT columns
> FROM tables
> [WHERE conditions];
> ```

#### Rename

#### Drop

> DROP VIEW \[IF EXISTS\] view\_name;

#### Existing Check

### Triggers


## Create

> ``` 
> CREATE [ CONSTRAINT ] TRIGGER name { BEFORE | AFTER | INSTEAD OF } { event [ OR ... ] }
>     ON TABLE_NAME
>     [ FROM referenced_table_name ]
>     { NOT DEFERRABLE | [ DEFERRABLE ] { INITIALLY IMMEDIATE | INITIALLY DEFERRED } }
>     [ FOR [ EACH ] { ROW | STATEMENT } ]
>     [ WHEN ( condition ) ]
>     EXECUTE PROCEDURE function_name ( arguments )
>  
> WHERE event can be one OF:
>  
>     INSERT
>     UPDATE [ OF column_name [, ... ] ]
>     DELETE
>     TRUNCATE
> ```

#### Alter

#### Rename

#### Drop

#### Existing Check

### Constraints

#### Primary Key

#### Foreign Key

### Arithmetic Operators

<table>
	<thead>
		<tr>
			<th>Operator</th>
			<th>Usage</th>
			<th>Description</th>
			<th></th>
			<th></th>
			<th></th>
			<th></th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>+</td>
			<td>
				<em>a</em> + 
				<em>b</em>
			</td>
			<td>Addition of numeric quantities 
				<em>a</em> and 
				<em>b</em>
			</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>-</td>
			<td>
				<em>a</em> - 
				<em>b</em>
			</td>
			<td>Subtraction of numeric quantity 
				<em>b</em> from 
				<em>a</em>
			</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>*</td>
			<td>
				<em>a</em> * 
				<em>b</em>
			</td>
			<td>Multiplication of numeric quantities 
				<em>a</em> and 
				<em>b</em>
			</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>/</td>
			<td>
				<em>a</em> / 
				<em>b</em>
			</td>
			<td>Division of numeric quantity 
				<em>a</em> by 
				<em>b</em>
			</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>%</td>
			<td>
				<em>a</em> % 
				<em>b</em>
			</td>
			<td>Modulus, or remainder, from dividing 
				<em>a</em> by 
				<em>b</em>
			</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>^</td>
			<td>
				<em>a</em> ^ 
				<em>b</em>
			</td>
			<td>Exponential operator, the value of 
				<em>a</em> to the power of 
				<em>b</em>
			</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td></td>
			<td>/</td>
			<td></td>
			<td>/ 
				<em>a</em>
			</td>
			<td>Square root of 
				<em>a</em>
			</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td></td>
			<td></td>
			<td>/</td>
			<td></td>
			<td></td>
			<td>/ 
				<em>a</em>
			</td>
			<td>Cube root of 
				<em>a</em>
			</td>
		</tr>
		<tr>
			<td>!</td>
			<td>
				<em>a</em>!
			</td>
			<td>Factorial of 
				<em>a</em>
			</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>!!</td>
			<td>!! 
				<em>a</em>
			</td>
			<td>Factorial prefix, factorial of 
				<em>a</em>, different only in syntactic placement from !
			</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>@</td>
			<td>@ 
				<em>a</em>
			</td>
			<td>Absolute value of 
				<em>a</em>
			</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
		</tr>
	</tbody>
</table>


### Bitwise Operator

<table>
	<thead>
		<tr>
			<th>Operator</th>
			<th>Usage</th>
			<th>Description</th>
			<th></th>
			<th></th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>&amp;</td>
			<td>
				<em>a</em> &amp; 
				<em>b</em>
			</td>
			<td>Binary AND between bit string values of 
				<em>a</em> and 
				<em>b</em> (which may be provided as integers)
			</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td></td>
			<td></td>
			<td>
				<em>a</em>
			</td>
			<td>
				<em>b</em>
			</td>
			<td>Binary OR between bit string values of 
				<em>a</em> and 
				<em>b</em> (which may be provided as integers)
			</td>
		</tr>
		<tr>
			<td>#</td>
			<td>
				<em>a</em> # 
				<em>b</em>
			</td>
			<td>Binary XOR between bit string values of 
				<em>a</em> and 
				<em>b</em> (which may be provided as integers)
			</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>~</td>
			<td>~ 
				<em>b</em>
			</td>
			<td>Binary NOT, returns the inverted bit string of 
				<em>b</em>
			</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>&lt;&lt;</td>
			<td>
				<em>b</em> &lt;&lt; 
				<em>n</em>
			</td>
			<td>Binary shifts 
				<em>b</em> to the left by 
				<em>n</em> bits
			</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>&gt;&gt;</td>
			<td>
				<em>b</em> &gt;&gt; 
				<em>n</em>
			</td>
			<td>Binary shifts 
				<em>b</em> to the right by 
				<em>n</em> bits
			</td>
			<td></td>
			<td></td>
		</tr>
	</tbody>
</table>


### Comparison Operators

<table>
	<thead>
		<tr>
			<th>Operator</th>
			<th>Usage</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>=</td>
			<td>' 
				<em>string</em>' = ' 
				<em>comparison</em>'
			</td>
			<td>A comparison returning true if 
				<em>string</em> matches 
				<em>comparison</em> identically
			</td>
		</tr>
		<tr>
			<td>!=</td>
			<td>' 
				<em>string</em>' != ' 
				<em>comparison</em>'
			</td>
			<td>A comparison returning true if 
				<em>string</em> does not match 
				<em>comparison</em> identically
			</td>
		</tr>
		<tr>
			<td>&lt;&gt;</td>
			<td>' 
				<em>string</em>' &lt;&gt; ' 
				<em>comparison</em>'
			</td>
			<td>Identical to the != operator</td>
		</tr>
		<tr>
			<td>&lt;</td>
			<td>' 
				<em>string</em>' &lt; ' 
				<em>comparison</em>'
			</td>
			<td>A comparison returning true if 
				<em>string</em> should be sorted alphabetically before 
				<em>comparison</em>
			</td>
		</tr>
		<tr>
			<td>&lt;=</td>
			<td>' 
				<em>string</em>' &lt;= ' 
				<em>comparison</em>'
			</td>
			<td>A comparison returning true if 
				<em>string</em> should be sorted alphabetically before 
				<em>comparison</em>, or if the values are identical
			</td>
		</tr>
		<tr>
			<td>&gt;</td>
			<td>' 
				<em>string</em>' &gt; ' 
				<em>comparison</em>'
			</td>
			<td>A comparison returning true if 
				<em>string</em> should be sorted alphabetically after 
				<em>comparison</em>
			</td>
		</tr>
		<tr>
			<td>&gt;=</td>
			<td>' 
				<em>string</em>' &gt;= ' 
				<em>comparison</em>'
			</td>
			<td>A comparison returning true if 
				<em>string</em> should be sorted alphabetically after 
				<em>comparison</em>, or if the values are identical
			</td>
		</tr>
	</tbody>
</table>

### Comparison Operators

<table>
	<thead>
		<tr>
			<th>Operator</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>&lt;</td>
			<td>Less-than, returns true if the value to the left is smaller in quantity than the value to the right</td>
		</tr>
		<tr>
			<td>&gt;</td>
			<td>Greater-than, returns true if the value to the left is greater in quantity than the value to the right</td>
		</tr>
		<tr>
			<td>&lt;=</td>
			<td>Less-than or equal-to, returns true if the value to the left is smaller, or equal to, in quantity than the value to the right</td>
		</tr>
		<tr>
			<td>&gt;=</td>
			<td>Greater-than or equal-to, returns true if the value to the left is greater, or equal to, in quantity than the value to the right</td>
		</tr>
		<tr>
			<td>=</td>
			<td>Equal-to, returns true if the values to the left and right of the operator are equivalent</td>
		</tr>
		<tr>
			<td>&lt; &gt; or !=</td>
			<td>Not-equal, returns true if the values to the left and right of the operator not equivalent</td>
		</tr>
	</tbody>
</table>


### Logical Operator

<table>
	<thead>
		<tr>
			<th>
				<em>a</em>
			</th>
			<th>
				<em>b</em>
			</th>
			<th>
				<em>a</em> AND 
				<em>b</em>
			</th>
			<th>
				<em>a</em> OR 
				<em>b</em>
			</th>
			<th>NOT 
				<em>a</em>
			</th>
			<th>NOT 
				<em>b</em>
			</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>true</td>
			<td>true</td>
			<td>true</td>
			<td>true</td>
			<td>false</td>
			<td>false</td>
		</tr>
		<tr>
			<td>true</td>
			<td>false</td>
			<td>false</td>
			<td>true</td>
			<td>false</td>
			<td>true</td>
		</tr>
		<tr>
			<td>true</td>
			<td>NULL</td>
			<td>NULL</td>
			<td>true</td>
			<td>false</td>
			<td>NULL</td>
		</tr>
		<tr>
			<td>false</td>
			<td>false</td>
			<td>false</td>
			<td>false</td>
			<td>true</td>
			<td>true</td>
		</tr>
		<tr>
			<td>false</td>
			<td>NULL</td>
			<td>false</td>
			<td>NULL</td>
			<td>true</td>
			<td>NULL</td>
		</tr>
		<tr>
			<td>NULL</td>
			<td>NULL</td>
			<td>NULL</td>
			<td>NULL</td>
			<td>NULL</td>
			<td>NULL</td>
		</tr>
	</tbody>
</table>


### Regular Expression Comparision Operator

Regular expression symbols

<table>
	<thead>
		<tr>
			<th>Symbol(s)</th>
			<th>Usage</th>
			<th>Description</th>
			<th></th>
			<th></th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>
				<em>^</em>
			</td>
			<td>
				<em>^  
					<em>expression</em>
				</em>
			</td>
			<td>Matches the beginning ( 
				<em>^</em> ) of the character string
			</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>
				<em>$</em>
			</td>
			<td>
				<em>expression 
					<span class="math">*        | Matches the end ( *</span>
				</em> ) of the character string
			</td>
			<td></td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>
				<em>.</em>
			</td>
			<td>
				<em>.</em>
			</td>
			<td>Matches any single character</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>
				<em>[ ]</em>
			</td>
			<td>
				<em>[  
					<em>abc</em> ]
				</em>
			</td>
			<td>Matches any single character which is between brackets (e.g., 
				<em>a</em> , 
				<em>b</em> , or 
				<em>c</em> )
			</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>
				<em>[^]</em>
			</td>
			<td>
				<em>[^ 
					<em>abc</em> ]
				</em>
			</td>
			<td>Matches any single character not between brackets, following caret (e.g., not 
				<em>a</em> , 
				<em>b</em> , or 
				<em>c)</em>
			</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>
				<em>[-]</em>
			</td>
			<td>
				<em>[  
					<em>a</em>- 
					<em>z</em> ]
				</em>
			</td>
			<td>Matches any character which is between the range of characters between brackets and separated by the dash (e.g., within 
				<em>a</em> through 
				<em>z</em> )
			</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>
				<em>[^-]</em>
			</td>
			<td>
				<em>[^ 
					<em>a</em>- 
					<em>z</em> ]
				</em>
			</td>
			<td>Matches any characters 
				<em>not</em> between the range of characters between brackets and separated by the dash (e.g., not within 
				<em>a</em> through 
				<em>z</em> )
			</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>
				<em>?</em>
			</td>
			<td>
				<em>
					<em>a</em> ?
				</em>
			</td>
			<td>Matches zero or one instances of the character (or regex sequence) preceding it</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>
				<em>*</em>
			</td>
			<td>
				<em>
					<em>a</em> *
				</em>
			</td>
			<td>Matches zero or more instances of the character (or regex sequence) preceding it</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>
				<em>+</em>
			</td>
			<td>
				<em>
					<em>a</em>+
				</em>
			</td>
			<td>Matches one or more instances of the character (or regex sequence) preceding it</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>*</td>
			<td>*</td>
			<td>*
				<em>expr1</em>
			</td>
			<td>
				<em>expr2</em>*
			</td>
			<td>Matches character sequences to the left 
				<em>or</em> right of it (e.g., either 
				<em>expr1</em>, or 
				<em>expr2</em>)
			</td>
		</tr>
		<tr>
			<td>
				<em>( )</em>
			</td>
			<td>
				<em>( 
					<em>expr1</em>)  
					<em>expr2</em>
				</em>
			</td>
			<td>Explicitly groups expressions, to clarify precedence of special character symbols</td>
			<td></td>
			<td></td>
		</tr>
	</tbody>
</table>


Regular expression comparison operators

<table>
	<thead>
		<tr>
			<th>Operator</th>
			<th>Usage</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>~</td>
			<td>' 
				<em>string</em>' ~ ' 
				<em>regex</em>'
			</td>
			<td>A regular expression comparison, yielding true if the expression matches</td>
		</tr>
		<tr>
			<td>!~</td>
			<td>' 
				<em>string</em>' !~ ' 
				<em>regex</em>'
			</td>
			<td>A regular expression comparison, yielding true if the expression 
				<em>does not</em> match
			</td>
		</tr>
		<tr>
			<td>~*</td>
			<td>' 
				<em>string</em>' ~* ' 
				<em>regex</em>'
			</td>
			<td>A case-insensitive regular expression, yielding true if the expression matches</td>
		</tr>
		<tr>
			<td>!~*</td>
			<td>' 
				<em>string</em>' !~* ' 
				<em>regex</em>'
			</td>
			<td>not equal to regular expression, case insensitive</td>
		</tr>
	</tbody>
</table>

### Operator precedence

<table>
	<thead>
		<tr>
			<th>Operator</th>
			<th>Usage</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>::</td>
			<td>value::type</td>
			<td>Explicit typecast</td>
		</tr>
		<tr>
			<td>[ ]</td>
			<td>value[ 
				<em>index</em> ]
			</td>
			<td>Array element index</td>
		</tr>
		<tr>
			<td>.</td>
			<td>table.column</td>
			<td>Table and column name separator</td>
		</tr>
		<tr>
			<td>-</td>
			<td>- 
				<em>value</em>
			</td>
			<td>Unary minus</td>
		</tr>
		<tr>
			<td>^</td>
			<td>
				<em>value</em> ^ 
				<em>power</em>
			</td>
			<td>Exponent</td>
		</tr>
		<tr>
			<td>* / %</td>
			<td>
				<em>value1</em> * 
				<em>value2</em>
			</td>
			<td>Multiplication, division, and modulus</td>
		</tr>
		<tr>
			<td>+ -</td>
			<td>
				<em>value1</em> + 
				<em>value2</em>
			</td>
			<td>Addition and subtraction</td>
		</tr>
		<tr>
			<td>IS</td>
			<td>
				<em>value</em> IS 
				<em>boolean</em>
			</td>
			<td>Compares against true or false</td>
		</tr>
		<tr>
			<td>ISNULL</td>
			<td>
				<em>value</em> ISNULL
			</td>
			<td>Compares against NULL</td>
		</tr>
		<tr>
			<td>IS NOT NULL</td>
			<td>
				<em>value</em> IS NOT NULL
			</td>
			<td>Checks for 
				<em>value</em> inequivalent to NULL
			</td>
		</tr>
		<tr>
			<td>
				<em>Other</em>
			</td>
			<td>
				<em>Variable</em>
			</td>
			<td>Includes all other native and user-defined character operators</td>
		</tr>
		<tr>
			<td>IN</td>
			<td>
				<em>value</em> IN 
				<em>set</em>
			</td>
			<td>Checks for membership of 
				<em>value</em> in 
				<em>set</em>
			</td>
		</tr>
		<tr>
			<td>BETWEEN</td>
			<td>
				<em>value</em> BETWEEN 
				<em>a</em> AND 
				<em>b</em>
			</td>
			<td>Checks for 
				<em>value</em> in range between values 
				<em>a</em> and 
				<em>b</em>
			</td>
		</tr>
		<tr>
			<td>LIKE, ILIKE</td>
			<td>
				<em>string</em> LIKE 
				<em>comparison</em>
			</td>
			<td>Checks for matching pattern 
				<em>comparison</em> in 
				<em>string</em>
			</td>
		</tr>
		<tr>
			<td>&lt; &gt; &lt;= &gt;=</td>
			<td>
				<em>value1</em> &lt; 
				<em>value2</em>
			</td>
			<td>Quantity comparisons for less than, greater than, less than or equal to, and greater than or equal to.</td>
		</tr>
		<tr>
			<td>=</td>
			<td>
				<em>value1</em> = 
				<em>value2</em>
			</td>
			<td>Equality comparison</td>
		</tr>
		<tr>
			<td>NOT</td>
			<td>NOT 
				<em>value</em>
			</td>
			<td>Logical NOT inversion</td>
		</tr>
		<tr>
			<td>AND</td>
			<td>
				<em>value1</em> AND 
				<em>value2</em>
			</td>
			<td>Logical AND conjunction</td>
		</tr>
		<tr>
			<td>OR</td>
			<td>
				<em>value1</em> OR 
				<em>value2</em>
			</td>
			<td>Logical OR conjunction</td>
		</tr>
	</tbody>
</table>

## Expert

### Schedule Jobs

References

  - [Practical PostgreSQL](http://www.faqs.org/docs/ppbook/book1.htm) 
  - [Techonthenet - postgresql](https://www.techonthenet.com/postgresql/index.php)


