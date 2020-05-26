Infrastructure Architecture - Database SQL Architect
==================================================
 
History
-------

In the 'Computing Dark Ages', we used flat record layouts, or arrays;
all data saved to tape or large disk drives for subsequent
retrieval. However, in 1958,  [J. W. Young and H. K.
Kent](https://en.wikipedia.org/wiki/Data_model#cite_ref-10)
described modeling information systems as " *a precise and abstract way
of specifying the informational and time characteristics of a data
processing problem* ". Soon after in 1959, 
[CODASYL](http://purl.umn.edu/40644 "Visit http://purl.umn.edu/40644 (click to open in a new window)")
or the ' *Conference/Committee on Data Systems Languages* ', a
consortium, was formed by the  [Charles Babbage
Institute](https://en.wikipedia.org/wiki/Charles_Babbage_Institute "Visit https://en.wikipedia.org/wiki/Charles_Babbage_Institute (click to open in a new window)")
at the University of Minnesota which led to standard programming
languages like COBOL and the ' [*Integrated Data
Store*](https://en.wikipedia.org/wiki/Integrated_Data_Store "Visit https://en.wikipedia.org/wiki/Integrated_Data_Store (click to open in a new window)")
' (IDS); an early database technology designed in the 1960's at
GE/Honeywell by  [Charles
Bachman](https://en.wikipedia.org/wiki/Charles_Bachman "Visit https://en.wikipedia.org/wiki/Charles_Bachman (click to open in a new window)")
. IDS proved difficult to use, so it evolved to become the '
[*Integrated Database Management
System*](https://en.wikipedia.org/wiki/IDMS "Visit https://en.wikipedia.org/wiki/IDMS (click to open in a new window)")
' (IDMS) developed at  [B. F.
Goodrich](https://en.wikipedia.org/wiki/Goodrich_Corporation "Visit https://en.wikipedia.org/wiki/Goodrich_Corporation (click to open in a new window)")
(a US aerospace company at the time, and yes the tire company we know
today), marketed by Cullinane Database Systems (now owned by Computer
Associates). These two data modeling methodologies called the '
*Hierarchal Data Model* ' and the ' *Network Data Model* ' respectively,
were both very common across mainframe computing for the next 50 years.
You may still find them in use today. Wow!

In the late 1960's, while working at IBM,  [E. F.
Codd](https://en.wikipedia.org/wiki/Edgar_F._Codd "Visit https://en.wikipedia.org/wiki/Edgar_F._Codd (click to open in a new window)") in
collaboration with  [C. J.
Date](https://en.wikipedia.org/wiki/Christopher_J._Date "Visit https://en.wikipedia.org/wiki/Christopher_J._Date (click to open in a new window)") (author
of ' [An Introduction to Database
Systems](https://www.amazon.com/Introduction-Database-Systems-8th/dp/0321197844 "Visit https://www.amazon.com/Introduction-Database-Systems-8th/dp/0321197844 (click to open in a new window)")'),
mapped Codd's innovative data modeling theories resulting in the '
[*Relational Model of Data for Large Shared Data
Banks*](http://www.idc-online.com/technical_references/pdfs/information_technology/A_Relational_Model_of_Data_for_Large_Shared_Data_Banks.pdf "Visit http://www.idc-online.com/technical_references/pdfs/information_technology/A_Relational_Model_of_Data_for_Large_Shared_Data_Banks.pdf (click to open in a new window)")
' publication in 1970. Codd's campaign to ensure vendors implemented the
methodology properly published his famous  [*'Twelve Rules of the
Relational
Model*](http://computing.derby.ac.uk/c/codds-twelve-rules/ "Visit http://computing.derby.ac.uk/c/codds-twelve-rules/ (click to open in a new window)")
' in 1985. Actually, thirteen rules numbered zero to twelve; Codd was
clearly a computer geek of his day. The Relational Model also introduced
the concept of ' *Normalization*' with the definition of the ' [*Five
Normal
Forms*](http://www.bkent.net/Doc/simple5.htm "Visit http://www.bkent.net/Doc/simple5.htm (click to open in a new window)")
'. Many of us talk about '3NF' or the ' *three ^rd^ Normal Form* ', but
do you know how to define it? Read up on these two links and find out if
you really know what you think you know. There will be a quiz at the
end! Not ...

The next significant data modeling methodology arrived in 1996, proposed
by  [Ralph
Kimball](https://en.wikipedia.org/wiki/Ralph_Kimball "Visit https://en.wikipedia.org/wiki/Ralph_Kimball (click to open in a new window)") (
*retired*), in his groundbreaking book co-authored by Margy Ross, '
[*The Data Warehouse Toolkit: The Complete Guide to Dimensional
Modeling*](http://www.kimballgroup.com/data-warehouse-business-intelligence-resources/books/data-warehouse-dw-toolkit/ "Visit http://www.kimballgroup.com/data-warehouse-business-intelligence-resources/books/data-warehouse-dw-toolkit/ (click to open in a new window)")
'. Kimball's widely adopted ' [*Star
Schema*](https://en.wikipedia.org/wiki/Star_schema "Visit https://en.wikipedia.org/wiki/Star_schema (click to open in a new window)")
' data model applied concepts introduced in the data warehouse paradigm
first proposed in the 1970's by  [W. H. (Bill)
Inmon](https://en.wikipedia.org/wiki/Bill_Inmon "Visit https://en.wikipedia.org/wiki/Bill_Inmon (click to open in a new window)") (named
in 2007 by Computerworld as one of the ten most influencial people of
the first 40 years in computing). Inmon's ' [*Building the Data
Warehouse*](http://fit.hcmute.edu.vn/Resources/Docs/SubDomain/fit/ThayTuan/DataWH/Bulding%20the%20Data%20Warehouse%204%20Edition.pdf)
', published in 1991 has become the defacto standard for all data
warehouse computing. While there has been some history of disagreement
between Inmon and Kimball over the proper approach to data warehouse
implementation, Margy Ross, of the Kimball Group in her article '
[*Differences of
Opinion*](http://www.kimballgroup.com/2004/03/differences-of-opinion/ "Visit http://www.kimballgroup.com/2004/03/differences-of-opinion/ (click to open in a new window)")
' presents a fair and balanced explanation for your worthy
consideration.

Recently a new data modeling methodology has emerged as a strong
contender.  [The Data
Vault](https://en.wikipedia.org/wiki/Data_vault_modeling "Visit https://en.wikipedia.org/wiki/Data_vault_modeling (click to open in a new window)")!
Its author and inventor,  [Dan
Linsdedt](http://danlinstedt.com/ "Visit http://danlinstedt.com/ (click to open in a new window)"),
first conceived the Data Vault in 1990 and released a publication to the
public domain in 2001. The Data Vault model resolves many competing
Inmon and Kimball arguments, incorporating historical lineage of data,
and offering a highly adaptable, auditable, and expandable paradigm. A
critical improvement (IMHO); I invite you to read my blog on ' [What is
\"The Data Vault\" and why do we need
it?](https://www.talend.com/blog/2015/03/27/what-is-the-data-vault-and-why-do-we-need-it/). Linstedt's
Data Vault proved invaluable on several significant DOD, NSA, and
Corporate projects. In 2013, Linsdedt released  [Data Vault
2.0](http://learndatavault.com/ "Visit http://learndatavault.com/ (click to open in a new window)") addressing
Big Data, NoSQL, unstructured, semi-structured data integration coupled
with SDLC best practices on how to use it. Perfect timing, I'd say. So
here we are ...

![](https://www.talend.com/wp-content/uploads/280px-Relational_Model_svg-1.png){.confluence-embedded-image
.wp-image-28612 .alignleft .confluence-external-resource
.confluence-content-image-border height="250"}
![](https://www.talend.com/wp-content/uploads/the-data-vault-2.jpg){.confluence-embedded-image
.alignleft .wp-image-28619 .size-full .confluence-external-resource
.confluence-content-image-border width="352" height="250"}
![](https://www.talend.com/wp-content/uploads/dim1-1.jpg){.confluence-embedded-image
.wp-image-28613 .alignright .confluence-external-resource
.confluence-content-image-border height="250"}
![](https://www.talend.com/wp-content/uploads/320px-Network_Model_svg-1.png){.confluence-embedded-image
.size-full .wp-image-28610 .alignright .confluence-external-resource
.confluence-content-image-border height="250"}

A Data Model Summary
--------------------

A quick summary of the different data modeling methodologies
historically include:

-   **Flat Model** --- *single, two-dimensional array of data elements*
-   **Hierarchical Model** --- *records containing fields and sets
    defining a parent/child hierarchy*
-   **Network Model** --- *similar to hierarchical model allowing
    one-to-many relationships using a junction 'link' table mapping*
-   **Relational Model** --- *collection of predicates over finite set
    of predicate variables defined with constraints on the possible
    values and combination of values*
-   **Star Schema Model** --- *normalized fact and dimension tables
    removing low cardinality attributes for data aggregations*
-   **Data Vault Model** --- *records long term historical data from
    multiple data sources using hub, satellite, and link tables*

Database Development Life Cycle - DDLC
--------------------------------------

Today's dialogue seems to focus entirely on complexity and sheer volume
of data. Important, sure, but again I'd like to remind you that the Data
Model should be an important part of the discussion. As requirements
evolve, the schema (a Data Model) must follow along --- or even lead the
way; regardless, it needs to be managed. Therefore, I submit to you, the
Database Development Life Cycle!

For every environment (like DEV/TEST/PROD) where data is involved,
developers need to accommodate and adapt code to its inevitable
structural mutation. Similar to the Software Development Life Cycle
(SDLC), a database should embrace appropriate Data Model Design and Best
Practices. Of the many Data Models that I have designed, clear precepts
have emerged which include:

-   **Adaptability** --- *creating schemas that withstand enhancement or
    correction*
-   **Expandability** --- *creating schemas that grow beyond
    expectations*
-   **Fundamentality** --- *creating schemas that deliver on features
    and functionality*
-   **Portability** ---  *creating schemas that can be hosted on
    disparate systems*
-   **Exploitation** ---  *creating schemas that maximize
    a host technology*
-   **Efficient Storage** --- *creating optimized schema disk footprint*
-   **High Performance** --- *creating optimized schemas that excel*

These design precepts incorporate the essence of any chosen modeling
methodology, some in contradiction with others. In my experience
regardless of these dichotomies, a data model has just three stages of
life --- cradle to grave:

-   **A Fresh INSTALL** --- *based upon the current version of the
    schema*
-   **Apply an UPGRADE** --- *drop/create/alter dB objects upgrading one
    version to the next*
-   **Data MIIGRATION** ---  *where a disruptive 'upgrade' occurs (like
    splitting tables or platform)*

Designing the Data Model can be a labor of love entailing both the
tedious attention to detail tempered with the creative abstraction of
ambiguity. Personally drawn to challenging schemas, I look for cracks
and crevices to correct, which often present themselves in various
ways. For example:

-   **χ Composite Primary Keys** *avoid them, rarely effective or
    appropriate; there are some exceptions depending upon the data
    model*
-   **χ Bad Primary Keys** *usually datetime and/or strings (except a
    GUID or Hash) are inappropriate*
-   **χ Bad Indexing** *either too few or too many*
-   **χ Column Datatypes** *when you only need an Integer don't use a
    Long (or Big Integer), especially on a primary key*
-   **χ Storage Allocation** *inconsiderate of data size and growth
    potential*
-   **χ Circular References** *where a table A has a relationship with
    table B, table B has a relationship with table C, and table C has a
    relationship with table A --- this is simply bad design (IMHO)*

Let us consider then a database design best practice: The design and
release process of a data model. I believe that when crafting a data
model one should follow a prescribed process similar to this:

![](https://www.talend.com/wp-content/uploads/DDLC_DBdesignflow-3.png){.confluence-embedded-image
.size-full .wp-image-28615 .aligncenter .confluence-external-resource
.confluence-content-image-border height="150"}

Self-explanatory to most perhaps, yet let me emphasize the importance of
adopting this process. While schema changes are inevitable, getting a
solid data model early in any software development project is essential.
Undoubtedly minimizing the impact to application code is desirable for
delivering successful software projects. Schema changes can be an
expensive proposition so understanding the database life cycle and its
role becomes very important. Versioning your database model is
critical. Use graphical diagrams to illustrate the designs. Create a '
*Data Dictionary*' or ' *Glossary*' and track lineage for historical
changes. It is a higher discipline; but it works!

Data Modeling Methodologies
---------------------------

Understanding the history of the Data Model and the best process under
which to design them is only the starting point. As a Database Architect
for both  [Transactional
(OLTP)](https://en.wikipedia.org/wiki/Online_transaction_processing "Visit https://en.wikipedia.org/wiki/Online_transaction_processing (click to open in a new window)") and 
[Analytical
(OLAP)](https://en.wikipedia.org/wiki/Online_analytical_processing "Visit https://en.wikipedia.org/wiki/Online_analytical_processing (click to open in a new window)") models,
I have discovered that the first three steps illustrated above represent
about 80% of the work. So let us consider that next.

Sometimes Data Models are easy, usually due to simplicity and/or small
stature. Data Models can also be very hard, usually due to complexity,
diversity, and/or sheer size and shape of the data and the many places
throughout the Enterprise where it is used. I believe we should
understand as early as possible the full extent of what and where data
is, how it is affected by, or affects the applications and systems using
it, and why it is there in the first place. Getting your head around who
needs what and how to deliver it is the challenge. Mapping it out to
ensure a solid Data Model is the goal. Choosing the right data modeling
methodology is paramount.

Business Value of a Data Model
------------------------------

Talend ETL/ELT jobs are written to read and write data. We do this
ostensibly to deliver value to the business. Why then do we need a Data
Model? What purpose does it serve? Can't we simply process it and be
done? From a technical perspective, we rely on the data model to provide
a structure upon which we manipulate data flow. The life cycle of a Data
Model directly impacts job design, performance, and scalability. And
this is just the tip of the iceberg, technically. The business
perspective is perhaps more abstract. Foremost the Data Model validates
the business requirements. It provides a critical definition for systems
integration and the structural control of data used by the business,
thus ensuring various functional and/or operational tenets. I submit
that the business becomes wholly inefficient without a Data Model.

Patterns
--------

### Basic Table Types

These patterns describe the kinds of things that you store in tables.
Each pattern is characterized by the relative number of columns and
rows, and whether it stores either information about permanent things or
interactions between permanent things.

These patterns were described in the entry on  [A Sane Approach to
Primary
Keys](http://database-programmer.blogspot.com/2008/01/database-skills-sane-approach-to.html).

 {.table-wrap}
+-------------+-------------+-------------+-----------+-------------+
| Pattern     | Relative    | Relative    | Type      | Notes       |
| Name        | Column      | Row Count   |           |             |
|             | Count       |             |           |             |
+=============+=============+=============+===========+=============+
| [Reference  | Small       | Small       | Permanent | Use         |
| ](http://da |             |             |           | si          |
| tabase-prog |             |             |           | ngle-column |
| rammer.blog |             |             |           | character   |
| spot.com/20 |             |             |           | primary     |
| 08/01/datab |             |             |           | key.        |
| ase-skills- |             |             |           |             |
| sane-approa |             |             |           |             |
| ch-to.html# |             |             |           |             |
| rule1){.ext |             |             |           |             |
| ernal-link} |             |             |           |             |
+-------------+-------------+-------------+-----------+-------------+
| [Small      | Small       | Small       | Permanent | Use         |
| Master      |             |             |           | si          |
| ](http://da |             |             |           | ngle-column |
| tabase-prog |             |             |           | character   |
| rammer.blog |             |             |           | primary     |
| spot.com/20 |             |             |           | key.        |
| 08/01/datab |             |             |           |             |
| ase-skills- |             |             |           |             |
| sane-approa |             |             |           |             |
| ch-to.html# |             |             |           |             |
| rule2){.ext |             |             |           |             |
| ernal-link} |             |             |           |             |
+-------------+-------------+-------------+-----------+-------------+
| [Large      | Large       | Large       | Permanent | Use integer |
| Master      |             |             |           | au          |
| ](http://da |             |             |           | to-assigned |
| tabase-prog |             |             |           | primary key |
| rammer.blog |             |             |           |             |
| spot.com/20 |             |             |           |             |
| 08/01/datab |             |             |           |             |
| ase-skills- |             |             |           |             |
| sane-approa |             |             |           |             |
| ch-to.html# |             |             |           |             |
| rule3){.ext |             |             |           |             |
| ernal-link} |             |             |           |             |
+-------------+-------------+-------------+-----------+-------------+
| [T          | n/a         | n/a         | Transient | Describes   |
| ransactions |             |             |           | i           |
| ](http://da |             |             |           | nteractions |
| tabase-prog |             |             |           | between     |
| rammer.blog |             |             |           | things,     |
| spot.com/20 |             |             |           | like a      |
| 08/01/datab |             |             |           | customer    |
| ase-skills- |             |             |           | purchase of |
| sane-approa |             |             |           | an item or  |
| ch-to.html# |             |             |           | a           |
| rule4){.ext |             |             |           | student\'s  |
| ernal-link} |             |             |           | enrollment  |
|             |             |             |           | in a class. |
|             |             |             |           | Use integer |
|             |             |             |           | au          |
|             |             |             |           | to-assigned |
|             |             |             |           | primary key |
+-------------+-------------+-------------+-----------+-------------+
| [Cross      | n/a         | n/a         | Permanent | Describes   |
| Reference   |             |             |           | re          |
| ](http://da |             |             |           | lationships |
| tabase-prog |             |             |           | between     |
| rammer.blog |             |             |           | master      |
| spot.com/20 |             |             |           | entries,    |
| 08/01/datab |             |             |           | such as an  |
| ase-skills- |             |             |           | item\'s     |
| sane-approa |             |             |           | price group |
| ch-to.html# |             |             |           | or a        |
| rule5){.ext |             |             |           | teacher\'s  |
| ernal-link} |             |             |           | department. |
|             |             |             |           | Use         |
|             |             |             |           | m           |
|             |             |             |           | ulti-column |
|             |             |             |           | primary     |
|             |             |             |           | keys.       |
|             |             |             |           |             |
|             |             |             |           | \           |
+-------------+-------------+-------------+-----------+-------------+


### Expanded Table Types

The  [Limited Transaction
Pattern](http://database-programmer.blogspot.com/2008/01/table-design-pattern-limited.html) occurs
when restrictions on allowed transactions require one or more additional
unique constraints on a transaction table.

The  [Impermanent Primary
Key](http://database-programmer.blogspot.com/2008/02/primary-key-that-wasnt.html) pattern
occurs when a value that is a good choice for a natural key will change
from time to time. For this pattern we use a pair of tables to track the
entity.

### Foreign Key Patterns

There are  [two fundamental kinds of foreign
key](http://database-programmer.blogspot.com/2008/07/different-foreign-keys-for-different.html),
which correspond to the \"master table\" and \"transaction tables\"
types.

[The cross-reference validation
pattern](http://database-programmer.blogspot.com/2008/01/table-design-patterns-cross-reference.html) occurs
when an entry must be validated against some previously defined
relationship between master items.

### Different Foreign Keys for Different Tables

A foreign key can be used to implement table design patterns that span
multiple tables. By choosing how a foreign key handles a DELETE attempt
on the parent table, you can structure your table designs to follow two
standard patterns.

Welcome to the Database Programmer blog. This series of essays is for
anybody who wants to learn about databases on their own terms. There is
a complete  [Table of
Contents](http://database-programmer.blogspot.com/2007/12/database-skills-complete-contents.html),
as well as a summary of  [Table Design
Patterns](http://database-programmer.blogspot.com/2008/01/table-design-patterns.html).
There is a new essay in this spot each Monday morning.

#### A Simple Example of Two Foreign Keys

Picture a basic shopping cart, with its two basic tables of CART and
CART\_LINES (or ORDERS and ORDER\_LINES if you are more old-fashioned).
The table CUSTOMERS is also in there as a parent to CARTS. Our three
tables look something like this:

       
                        CUSTOMERS
                            |
                            |
                            /|\
                            CART  Cart is child of customers
                            |
                            |
                            /|\
                        CART_LINES  Lines is child of Cart
                    

There are two foreign keys here. CART has a foreign key to CUSTOMERS,
and CART\_LINES has a foreign key to CART, but the two foreign keys
should behave very differently.

Table Types and Table Design Patterns {#DatabaseSQLArchitect-TableTypesandTableDesignPatterns}
-------------------------------------

In  [A Sane Approach To Choosing Primary
Keys](http://database-programmer.blogspot.com/2008/01/database-skills-sane-approach-to.html) we
saw that table design begins with identifying the basic kinds of tables:
Reference and Small Master Tables, Large Master Tables, Transactions,
and Cross-References. Just as we picked different kinds of primary keys
for the different tables, so will we pick different kinds of foreign
keys between these tables.

Deleting a Customer {#DatabaseSQLArchitect-DeletingaCustomer}
-------------------

Imagine you have a customer who has made 10 orders in 2 years. A system
administrator, who is allowed to basically do anything, goes into your
admin screens, looks up the customer, and clicks \[DELETE\]. What should
happen?

The near-universal answer is that the user should be denied the action.
An error should come back that says \"That customer has orders, cannot
delete.\" We want it this way because we never want to delete any parent
row and \"orphan\" the child rows. Database programmers know from long
experience that if you allow the DELETE, your queries will give
incorrect results, or you will work extremely hard with lots of weird
LEFT JOINS and UNIONS trying to get them to come back correctly.

This is not an issue of \"flexibility\", where a more robust system
would allow the deletion. This is a basic question of record-keeping. If
the customer has orders on file then the customer must be kept on file.
Enforcing this rule keeps code clean and simple, and trying to avoid
this rule in the name of \"flexibility\" just makes heaps of work for
everybody.

Going further, the administrator in question, who supposedly can do
anything, may not violate the rule. An administrator is simply somebody
who can do anything  *that would not produce bad data*. Administrators
should not be given the ability to violate  *the basic structure of the
data*, they simply have full rights to do anything  *within the
structure of the data*.

#### The DELETE RESTRICT Foreign Key

The behavior we want here is called DELETE RESTRICT. On most database
servers this is the default behavior for a foreign key. It means that
you cannot delete a parent table row if there are matching rows in the
child table.

The DELETE RESTRICT pattern is almost universally used when the child
table is a transaction table and the parent table is a master table or
reference table.

The syntax looks something like this:

                        -- Most database servers implement DELETE RESTRICT
                        -- by default, so this syntax:
                        Create table CART (
                            customer integer REFERENCES customers
                           ,order    integer.....
                        )

                        -- ...is the same as this explicit syntax:
                        Create table CART (
                            customer integer REFERENCES customers
                                             ON DELETE RESTRICT 
                           ,order    integer.....
                        )
                    

#### Deleting An Order and DELETE CASCADE

Now let us say a staff member is on the phone with a customer, enters an
order, enters five lines, and then the customers says \"forget it\" and
the user needs to delete the entire order from the CART.

In this case the user wants to go delete the order, and he expects the
computer  *to also delete the lines*. This makes perfect sense, why keep
the lines if we don\'t want the order?

It may seem strange that in the case of deleting a customer it makes
perfect sense to stop the user, but when deleting an order it makes
perfect sense to delete the lines as well.

The difference is that an entry in the CART table is a transaction
entry. When a user deletes a transaction they almost always want to
automatically delete all of the relevant rows from all child tables as
well. The two rules basically are:

-   The user cannot delete a master entry that has transactions.
-   Deleting a transaction means deleting the entire transaction.

NOTE: By \"transaction\" here I mean financial transaction or other
interaction between master elements. I do not mean a database
transaction.

The syntax for DELETE CASCADE looks something like this:

                        -- if the user deletes a row from CART,
                        -- do them the favor of deleting all of the
                        -- lines as well
                        Create table CART_LINES (
                            order   integer REFERENCES CART
                                            ON DELETE CASCADE
                           ,order_line integer....
                        )
                    

#### Conclusion: Different Tables Types, Different Foreign Key Types

I have said many times in these essays that the foreign key is the only
meaningful way to connect data in different tables. This week we have
seen that the kind of foreign key you choose depends on what kind of
tables you are connecting together. Children of master tables generally
get DELETE RESTRICT, and children of transaction tables generally get
DELETE CASCADE.

### Impermanent Primary Key / Cross-Reference Validation

#### The Example: A School Class Schedule

In this series we are using the example of an application that manages a
school of a few dozen faculty and few hundred or perhaps a couple
thousand students. Each year the school administration must make up the
actual class assignments for each teacher, including what classroom and
period each class will be taught in. Then students must be assigned into
the classes.

There are five rules that must be followed:

1.  A teacher must be qualified in advance for each course they teach.
2.  No two classes can be given in the same classroom in the same
    period.
3.  No teacher can be in two places at once, a teacher can only teach
    one class in one period.
4.  No student can be in two places at once, so no student can be in
    more than one class in the same period.
5.  A student cannot take the same class again after passing the class
    once.

All five rules can be handled with some smart table design and  *we will
not need any application code*.

Next week we will look at rules 2 - 4, and the week after that we will
tackle rule 5. This week we look at Rule 1.

#### Rule One and The Cross Reference Validation Pattern

When a user gives us their requirements, they will not express them as
as computer programs or table designs. The user will express his needs
in his own terms, expecting us to translate those terms into tables and
programs. So our job is to translate Rule 1 into one or more tables with
proper primary and foreign keys.

When we look at rule one we see that it splits into two requirements:

-   Subrule A: There must exist of a list of what course a teacher is
    qualified to teach.
-   Subrule B: All actual course assignments must match to the list of
    allowed (or qualified) classes.

When I see these two requirements together I automatically think
\"validate against a cross reference.\" I call this the \"Cross
Reference Validation\" pattern. It is different from a simple foreign
key validation. Let\'s go through it and see why.

We can start start at subrule B, because it is easy to recognize. Any
time some entry in a table must match an entry in another table, that
means a foreign key.

Now we want to work out what the parent table looks like. Is it a simple
master table with a one-column character key? Is it a transaction table?
We answer this buy drilling deeper into Subrule A:

-   Assumption 1: There is a list of teachers
-   Assumption 2: There is a list of courses
-   Assumption 3: There will be a list of teachers and courses together.

So the parent table must be a  *cross reference* because each entry will
list a teacher and a course. It should go without saying that we will
have a table of tgeachers and another table of courses, so the table of
qualifications must be a cross reference between these two.

Here is a picture of the Cross Reference Validation pattern:

      
                        CLASSROOM |  PERIOD    | COURSE   | TEACHER  | STUDENT  | ASSIGN_ID
                        ----------+------------+----------+----------+----------+-----------   
                          XXX     |   XXXX     |   XX     |  XXX     |   XXX    |   1
                          XXX     |   XXXX     |   XX     |  XXX     |   XXX    |   2  
                          XXX     |   XXXX     |   XX     |  XXX     |   XXX    |   3 
                          XXX     |   XXXX     |   XX     |  XXX     |   XXX    |   4  
                        ----------+------------+----------+----------+----------+-----------
                                                    |          |
                                                    |          |
                               Use A foreign        |          |
                               key to make sure     |          |
                               teacher is qualified |          |
                               for each course      |          |
                                                 COURSE     | TEACHER
                                                 -----------+--------
                                                   XXX      | XXXX
                                                   XXX      | XXXX
                    

Here is the SQL to create these tables. I have left out anything not
directly related to our Cross Reference Validation pattern:

                        -- Create the bottom table: allowed courses by teacher
                        CREATE TABLE courses_x_teachers (
                           teacher char(10) 
                          ,course  char(10)
                          ,foreign key (teacher) references teachers(teacher)
                          ,foreign key (courses) references courses(course)
                          ,primary key (teacher,course)
                        );

                        -- Create the main table (assumes we have already created
                        -- teh TEACHERS table, the CLASSROOMS table and so forth
                        CREATE TABLE enrollment (
                           classroom char(5)
                          ,period    char(5)
                          ,course    char(10)
                          ,teacher   char(10)
                          ,student   int 
                          -- this is a trx table, so use an integer ID for pk
                          ,assign_id int IDENTITY
                          ,primary key (assign_id)
                          -- The cross reference validation pattern needs a foreign key
                          ,foreign key                    (teacher,course) 
                           references courses_x_teachers  (teacher,course)
                    

#### Another Comment On Integer Keys

In last week\'s essay we saw that  [the rule of thumb for
cross-references](http://database-programmer.blogspot.com/2008/01/database-skills-sane-approach-to.html#rule5) is
to use a multi-column primary key and not to use an integer key. It
should be obvious now why we do that. If we used an integer key, then it
could not help us!

The tables as described above completely satisfy the business
requirement: no entry is allowed if the teacher is not approved for that
course. But an integer key provides no such value, it is useless. If you
use an integer key for the cross-reference table, then you are 
*required to write extra program code to \"chase\" the key out to the
cross-reference and make sure the values for teacher and course match
what you have in the child table.*

#### Foreign Keys and Performance

One time I was giving a presentation and somebody in the audience said
they had been told not to use foreign keys because they reduced
performance. To me this was like saying don\'t put gas in your car
because it weighs down the car and reduces mileage. The question was
such a shock and so unexpected that I had no decent answer.

Since that time I have discovered that this kind of nonsense is actually
prevelant these days. Such advice may make sense in cases where the data
structure is trivial (at most 7-10 tables) and the presentation is
paramount, but in any serious application such advice is ridiculous.
Here is the real scoop.

Somehow, some way, your code must ensure that every class assignment
made in the above example is valid. This means that the check for
teacher-course validity must be made. If you do not perform this check
then your software is structurally unsound and you will have bad data,
with no way to stop it and you will always be patching live systems in
crisis mode.

So because you must make the checks, we can ask, which is better, to
make the checks in program code or using the declarative constraints in
the table definition? This is easy to answer. Without the foreign key,
our program must make one round trip to the server to make the check,
and then a second round trip to do the insert. But if you use foreign
keys you only have to make one round trip. Since the overhead of making
a trip to the server is often more than the time spent executing on the
server, the foreign key solution will often perform twice as well as the
application code solution.

In short, if you\'re worried about performance, use foreign keys, not
application code.

#### Architecture Note: Server-Side Errors {#DatabaseSQLArchitect-ArchitectureNote:Server-SideErrors}

Many programmers are taught not to use foreign keys and so they are not
used to the idea that the database server will throw errors. Once you
start using the database for all that it is worth, you will depend more
and more on the errors it throws, so you want to make sure your
framework can read them and report them to the user the same way it
reports your application-generated errors.

#### Conclusion: Learn to Recognize Foreign Keys {#DatabaseSQLArchitect-Conclusion:LearntoRecognizeForeignKeys}

User requirements will never be expressed as program code or table
design, but we can recognize common patterns in them. One of those
patterns is the Cross Reference Validation pattern, which we implement
with a foreign key into a cross reference table. This and other patterns
will stand out if we examine user requirements with an aim to
identifying:

-   Lists of things you are keeping track of. These go into master
    tables, like courses and teachers.
-   Relationships between those master items, like a list of
    teacher-course qualifications.
-   Restrictions on how things can interact, so that a teacher must be
    qualified to teach courses means there will be a foreign key somehow
    into that teacher-course cross reference from some other table.

Next week we will examine Rules 2-4 and find out more about how unique
constraints and their associated patterns can reduce the amount of code
in our applications.

### Secure Patterns

Some table patterns depend upon security as a basic part of their
definition. Different combinations of SELECT, INSERT, UPDATE, and DELETE
permissions can replace complex application logic with zero-code
server-implemented solutions.

### Denormalization Patterns

Many seasoned database programmers denormalize their databases for a
variety of reasons. Like all database activities, these also follow
patterns. In the post  [Denormalization
Patterns](http://database-programmer.blogspot.com/2008/04/denormalization-patterns.html),
we see three distinct patterns:

### FETECH Pattern

Consider a shopping cart that has a column \"sku\" and another column
\"price.\" Most programmers lay out these tables and write some code
that copies the price from the ITEMS table to the ORDER\_LINES table. I
call this pattern the \"FETCH\" because the price is FETCHed from the
ITEMS table and written into the ORDER\_LINES table.

Most programmers code up FETCH operations all over the place and do not
ever realize they are denormalizing. I think this pattern is just so
natural that most of us never think about it. If you examine your
database applications you will likely see that you are doing this all
over the place.

In order to get this pattern to operate correctly, your framework must
make sure at very least that the SKU is not null when an INSERT is made
to ORDER\_LINES, and that the price is copied during the INSERT. You can
maintain correctness by not allowing users to change the SKU on this
table, if they change their minds they must delete a line and enter a
new one. Or, you can make your framework a little more flexible and
execute the FETCH again if the SKU changes on an UPDATE.

#### Is FETCH Really Denormalizing?

Die-hard relational theorists will tell you not to copy price from the
items table. You are supposed to leave it where it belongs and use JOINs
to pick up the price when it is needed. There are three arguments
against this sort of purity.

The first practical argument is that it is horribly difficult to deal
with complex calculations this way. It is far easier to copy the price
when the line goes in, so you never have to \"go looking\" for it again.

The second practical argument is that performance tanks if you follow
the die-hard relational approach. If you have to look in 6 tables every
time somebody refreshes their cart you will have a much slower program
than one that only has to look in one table.

But the third argument is more theoretical, and it is this: the FETCH 
*is not really denormalizing*. The idea is that when the customer makes
an order your store has entered in an agreement to sell something at a
particular price. That price is stored on the order and is now a fact
about that order. It is not redundant because you are not storing the
SKU\'s generic price, you are only storing the price that that customer
is going to pay on this order. If the price changes 5 minutes after the
customer places the order, they will expect to get the price as it was
when they put it in the cart, and so you are actually doing the right
thing by writing it to the order.

### Aggregations

The FETCH that was described above is all about copying a value from a
parent table to a child table. The opposite pattern occurs when you roll
up values from children to parents. These are usually done as totals
(SUMS), counts, averages, minimums, and maximums.

Looking at the ORDER\_LINES again, if a customer has 3 items in their
cart, it is perfectly natural to most programmers to put a column
\"PRODUCT\_TOTAL\" onto their ORDERS table that holds the sum of all of
the lines. This is called an aggregation, because the result in the
parent table is always some operation performed on the aggregation of
all of the child rows.

Aggregrations are always denormalizing because they are values that
could be derived from other values. To be specific, an aggregration
violates third normal form because it introduces a non-key dependency -
a value that is dependent not on the key but on values from a completely
different table!

In order to make sure this value is always correct, the framework must
always update the total on the parent table when  *any line in the child
table changes*. If your framework can do that successfully, your
aggregations will always be correct.

### Extend

The first two patterns we saw dealt with foreign keys. The first
pattern, the FETCH, involves values travelling \"downward\" on a foreign
key from parent to child. The second pattern involves values travelling
\"upward\" on a foreign key from child to parent. The third and final
denormalizing pattern involves calculated values within a row.

The example at the beginning of this essay was the column
EXTENDED\_PRICE, which holds the value of PRICE \* QTY. This is an
EXTEND operation, because it extends a row by adding a new redundant
value. This is denormalizing because it violates third normal form, it
introduces a value that is not dependent on any candidate key.

If you want to makes sure your EXTENDs are always correct then you need
a framework that will always update the calculation when either of its
dependent values changes.

### Dependency Tracking

In describing the three denormalizing patterns above, I have explained
what you need to make sure each one is performed successfully. There is
a final requirement to keeping all of this correct, which is that the
operations must be performed in the proper order.

Considering the shopping cart again, in particular the ORDER\_LINES
table, these three operations must occur in this order:

1.  The PRICE is FETCHed
2.  The EXTENDED\_PRICE is calculated as an EXTEND
3.  The ORDERS table\'s PRODUCT\_TOTAL value is adjusted.

Your framework must have a reasonable way to make sure that the
operations are performed in the correct order, or they will not give the
correct result. As a rule of thumb, in most systems the FETCHes come
first, followed by the EXTENDs, and then the aggregations.

Meta-data can be a big help here. When I first contemplated these
patterns about four years ago, it occurred to me that they could all be
stored as formulas in the basic description of the database, and that a
code generator would sequence them for me and generate the code, so that
the operations would always occur in the correct order. I wrote the
basic system in the fall of 2004 and have found it to work extremely
well ever since. In my personal opinion, this is the only way to
reliably handle these patterns.

### Resolutions

Welcome to the Database Programmer! Every Monday morning this blog
contains a new essay. This blog is for people who want to learn the
practical realities of databases. Topics range from simple to advanced.

The main theme of these essays is that your applications will be leaner,
faster, and easier to write and maintain if you understand how databases
work.

#### Basic Description and Example {#DatabaseSQLArchitect-BasicDescriptionandExample}

A resolution pattern occurs when you need a value and there is more than
one place where it might be. As an example, consider the case of a
computer services shop that provides complete IT services, including
programming. In their billing system, they have a simple table that
lists the rates for their various activities.

                        ACTIVITY  | RATE
                        ----------+-------
                        ITGENERAL | 100
                        PROJMGT   | 200
                        SOFTWARE  | 150
                    

This is simple enough, but now suppose that you have a particular
employee that you bill out at \$175.00/hour for software development.
This makes the picture a little more complicated. But suppose that it
gets more complicated, suppose that you enter into an arrangement with a
particular customer to do volume software development for them for
\$135.00. And just to make it interesting, suppose you have a very
specific arrangement with a particular customer to provide the services
of a particular employee for \$185.00 for project management.

With this many possible billing arrangements, your super-simple
invoicing program is suddenly not so simple. On any particular invoice
line, you must  ***resolve***  the actual hourly billing rate out of
several possibilities. Because you must resolve the value, this pattern
is called a resolution.

#### Precise Description of the Resolution Pattern {#DatabaseSQLArchitect-PreciseDescriptionoftheResolutionPattern}

A resolution pattern has these characteristics:

-   The goal of a resolution is to find a particular value. In our
    example this is a billing rate.
-   Resolutions examine multiple possible values and pick the first
    match according to precedence.
-   Precedence usually begins with the most specific and falls back to
    the most general. In our example the most specific possible rate is
    defined for a customer-activity-employee, while the most general is
    the default rate for an activity.

Resolutions are not always easy to recognize. Mostly this is because
customers do not tell you \"we have a resolution.\" Instead they tell
you they have a billing rate. The explanation of the special overrides
for employees comes in a different conversation, and perhaps to a
different member of your team. Then later comes the explanation of the
other overrides. The resolution only becomes apparent when the various
requirements are all sorted out and put next to each other. Then
somebody says, \"Hey, there are four different formulas for the billing
rate!\" Then you know you have a resolution.

#### The Table Design {#DatabaseSQLArchitect-TheTableDesign}

A resolution requires one table for each possible level of detail where
a value might be supplied. In our example there will be a table for:

-   Rates by activity-customer-employee
-   Rates by activity-customer
-   Rates by activity-employee
-   Final default values by activity

These table only contain values when they are relevant. The table of
activity-customer does not contain a row for every possible combination
of activities and customers, it only contains a row when there has been
some agreement to provide an activity to a specific customer for a
special rate.

Here are the tables:

                        ACTIVITY | CUSTOMER | RATE
                        ---------+----------+------
                        PROJMGT  | PRAXIS   |  225
                        SOFTWARE | PRAXIS   |  235


                        ACTIVITY | EMPLOYEE | RATE
                        ---------+----------+------
                        PROJMGT  | SRUSSEL  |  225


                        ACTIVITY | EMPLOYEE | CUSTOMER | RATE
                        ---------+----------+----------+------
                        PROJMGT  | HIROKO   | PRAXIS   |  250
                    

#### Resolving In Client Code Will Kill Performance

Now consider that the there is a table somewhere that is used to drive
billing. Maybe the employees themselves record their time in this table,
or maybe some clerical staff member is entering them. Whoever puts them
in, each record has an activity, an employee, and a customer (and of
course hours). You need to write a program that finds the correct
billing rate for each row.

A die-hard code grinder will do all of this in the client. He will write
a query to pull all of the rows from the time entry table. Then he will
loop through these rows. For each line he will query the server for a
the most detailed value, activity-employee-customer. If it is not found
he will do a second query for the next table in line, and so forth. This
will be a performance disaster because his program will be making a huge
number of round trips to the server. If he understood the LEFT JOIN he
would need only one trip to the server.

#### First Stab with A LEFT JOIN

Here is a query that does most of what we need for the resolution:

                      SELECT    ol.activity
                                , ol.employee
                                , ol.customer
                                , aec.rate as aec_rate
                                , ac.rate  as ac_rate
                                , ae.rate  as ae_rate
                                , a.rate
                      FROM  orderlines ol
                            LEFT JOIN act_emp_cust_rates aec ON ol.activity = aec.activity AND ol.customer = aec.customer AND ol.employee = aec.employee
                            LEFT JOIN act_cust_rates ac ON ol.activity = ae.activity AND ol.customer = ae.customer
                            LEFT JOIN act_emp_rates ae ON ol.activity = aec.activity AND ol.employee = aec.employee
                            INNER JOIN activities a ON ol.activity = a.activity  
                      WHERE (....relevant search conditions....)
                    

The LEFT JOIN tells the server to return all matching rows from the
orderlines table, even if there is no match in the various override
tables. The above query will return something like this:

                        ACTIVITY | EMPLOYEE | CUSTOMER | AEC_RATE | AC_RATE | AE_RATE | RATE
                        ---------+----------+----------+----------+---------+---------+------
                        PROJMGT  | HIROKO   | PRAXIS   |      250 |  null   |  null   |  200
                        PROJMGT  | NIRGAL   | PRAXIS   |     null |   225   |  null   |  200
                        SOFTWARE | SRUSSEL  | PRAXIS   |     null |   235   |  null   |  150
                        PROJMGT  | SRUSSEL  | GE       |     null |  null   |   225   |  200
                        PROJMGT  | SRUSSEL  | NASA     |     null |  null   |   225   |  200
                        SOFTWARE | HIROKO   | PRAXIS   |     null |   235   |  null   |  150
                        SOFTWARE | HIROKO   | GE       |     null |  null   |  null   |  150
                    

#### The Final Form of the Query

The first form of the query returns all four possible rates, and the
effect of a LEFT JOIN is to have a NULL value where there was no match
on the right side.

We can do better than this and return the actual rate by using a
COALESCE function. A COALESCE allows us to list two or more values, and
the function returns the first one that is not null. This lets us return
the actual resolved value from the server:

                        SELECT  ol.activity
                                ,ol.employee,ol.customer
                                , COALESCE(aec.rate,ac.rate,ae.rate,a.rate) as rate
                        FROM    orderlines ol
                                LEFT JOIN act_emp_cust_rates aec ON ol.activity = aec.activity AND ol.customer = aec.customer AND ol.employee = aec.employee
                                LEFT JOIN act_cust_rates ac ON ol.activity = ae.activity AND ol.customer = ae.customer
                                LEFT JOIN act_emp_rates ae ON ol.activity = aec.activity AND ol.employee = aec.employee
                                INNER JOIN activities a ON ol.activity = a.activity  
                        WHERE   (....relevant search conditions....)
                    

\...which gives us the complete answer:

                        ACTIVITY | EMPLOYEE | CUSTOMER | RATE 
                        ---------+----------+----------+------
                        PROJMGT  | HIROKO   | PRAXIS   |  250 
                        PROJMGT  | NIRGAL   | PRAXIS   |  225 
                        SOFTWARE | SRUSSEL  | PRAXIS   |  235 
                        PROJMGT  | SRUSSEL  | GE       |  225 
                        PROJMGT  | SRUSSEL  | NASA     |  225 
                        SOFTWARE | HIROKO   | PRAXIS   |  235 
                        SOFTWARE | HIROKO   | GE       |  150 
                    

Tenancy Patterns
----------------

### Single-tenant app with single-tenant Database

#### Application level isolation

In this model, the whole application is installed repeatedly, once for
each tenant. Each instance of the app is a standalone instance, so it
never interacts with any other standalone instance. Each instance of the
app has only one tenant, and therefore needs only one database. The
tenant has the database all to itself.

![Design of standalone app with exactly one single-tenant
database.](https://docs.microsoft.com/en-us/azure/sql-database/media/saas-tenancy-app-design-patterns/saas-standalone-app-single-tenant-database-11.png){.confluence-embedded-image
.confluence-external-resource .confluence-content-image-border
height="250"}

Each app instance is installed in a separate Azure resource group. The
resource group can belong to a subscription that is owned by either the
software vendor or the tenant. In either case, the vendor can manage the
software for the tenant. Each application instance is configured to
connect to its corresponding database.

Each tenant database is deployed as a single database. This model
provides the greatest database isolation. But the isolation requires
that sufficient resources be allocated to each database to handle its
peak loads. Here it matters that elastic pools cannot be used for
databases deployed in different resource groups or to different
subscriptions. This limitation makes this standalone single-tenant app
model the most expensive solution from an overall database cost
perspective.

#### Vendor management

The vendor can access all the databases in all the standalone app
instances, even if the app instances are installed in different tenant
subscriptions. The access is achieved via SQL connections. This
cross-instance access can enable the vendor to centralize schema
management and cross-database query for reporting or analytics purposes.
If this kind of centralized management is desired, a catalog must be
deployed that maps tenant identifiers to database URIs. Azure SQL
Database provides a sharding library that is used together with a SQL
database to provide a catalog. The sharding library is formally named
the  [Elastic Database Client
Library](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-database-client-library).

### Multi-tenant app with database-per-tenant

This next pattern uses a multi-tenant application with many databases,
all being single-tenant databases. A new database is provisioned for
each new tenant. The application tier is scaled  *up* vertically by
adding more resources per node. Or the app is scaled  *out* horizontally
by adding more nodes. The scaling is based on workload, and is
independent of the number or scale of the individual databases.

![Design of multi-tenant app with
database-per-tenant.](https://docs.microsoft.com/en-us/azure/sql-database/media/saas-tenancy-app-design-patterns/saas-multi-tenant-app-database-per-tenant-13.png){.confluence-embedded-image
.confluence-external-resource}

#### Customize for a tenant

Like the standalone app pattern, the use of single-tenant databases
gives strong tenant isolation. In any app whose model specifies only
single-tenant databases, the schema for any one given database can be
customized and optimized for its tenant. This customization does not
affect other tenants in the app. Perhaps a tenant might need data beyond
the basic data fields that all tenants need. Further, the extra data
field might need an index.

With database-per-tenant, customizing the schema for one or more
individual tenants is straightforward to achieve. The application vendor
must design procedures to carefully manage schema customizations at
scale.

#### Elastic pools

When databases are deployed in the same resource group, they can be
grouped into elastic pools. The pools provide a cost-effective way of
sharing resources across many databases. This pool option is cheaper
than requiring each database to be large enough to accommodate the usage
peaks that it experiences. Even though pooled databases share access to
resources they can still achieve a high degree of performance isolation.

![Design of multi-tenant app with database-per-tenant, using elastic
pool.](https://docs.microsoft.com/en-us/azure/sql-database/media/saas-tenancy-app-design-patterns/saas-multi-tenant-app-database-per-tenant-pool-15.png){.confluence-embedded-image
.confluence-external-resource}

Azure SQL Database provides the tools necessary to configure, monitor,
and manage the sharing. Both pool-level and database-level performance
metrics are available in the Azure portal, and through Azure Monitor
logs. The metrics can give great insights into both aggregate and
tenant-specific performance. Individual databases can be moved between
pools to provide reserved resources to a specific tenant. These tools
enable you to ensure good performance in a cost effective manner.

#### Operations scale for database-per-tenant

The Azure SQL Database platform has many management features designed to
manage large numbers of databases at scale, such as well over 100,000
databases. These features make the database-per-tenant pattern
plausible.

For example, suppose a system has a 1000-tenant database as its only one
database. The database might have 20 indexes. If the system converts to
having 1000 single-tenant databases, the quantity of indexes rises to
20,000. In SQL Database as part of  [Automatic
tuning](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-automatic-tuning),
the automatic indexing features are enabled by default. Automatic
indexing manages for you all 20,000 indexes and their ongoing create and
drop optimizations. These automated actions occur within an individual
database, and they are not coordinated or restricted by similar actions
in other databases. Automatic indexing treats indexes differently in a
busy database than in a less busy database. This type of index
management customization would be impractical at the database-per-tenant
scale if this huge management task had to be done manually.

Other management features that scale well include the following:

-   Built-in backups.
-   High availability.
-   On-disk encryption.
-   Performance telemetry.

#### Automation

The management operations can be scripted and offered through a 
[devops](https://www.visualstudio.com/devops/) model.
The operations can even be automated and exposed in the application.

For example, you could automate the recovery of a single tenant to an
earlier point in time. The recovery only needs to restore the one
single-tenant database that stores the tenant. This restore has no
impact on other tenants, which confirms that management operations are
at the finely granular level of each individual tenant.

### Multi-tenant app with multi-tenant databases

Another available pattern is to store many tenants in a multi-tenant
database. The application instance can have any number of multi-tenant
databases. The schema of a multi-tenant database must have one or more
tenant identifier columns so that the data from any given tenant can be
selectively retrieved. Further, the schema might require a few tables or
columns that are used by only a subset of tenants. However, static code
and reference data is stored only once and is shared by all tenants.

Tenant isolation is sacrificed {#DatabaseSQLArchitect-Tenantisolationissacrificed}
------------------------------

*Data:*  A multi-tenant database necessarily sacrifices tenant
isolation. The data of multiple tenants is stored together in one
database. During development, ensure that queries never expose data from
more than one tenant. SQL Database supports  [row-level
security](https://docs.microsoft.com/sql/relational-databases/security/row-level-security),
which can enforce that data returned from a query be scoped to a single
tenant.

*Processing:*  A multi-tenant database shares compute and storage
resources across all its tenants. The database as a whole can be
monitored to ensure it is performing acceptably. However, the Azure
system has no built-in way to monitor or manage the use of these
resources by an individual tenant. Therefore, the multi-tenant database
carries an increased risk of encountering noisy neighbors, where the
workload of one overactive tenant impacts the performance experience of
other tenants in the same database. Additional application-level
monitoring could monitor tenant-level performance.

Lower cost {#DatabaseSQLArchitect-Lowercost}
----------

In general, multi-tenant databases have the lowest per-tenant cost.
Resource costs for a single database are lower than for an equivalently
sized elastic pool. In addition, for scenarios where tenants need only
limited storage, potentially millions of tenants could be stored in a
single database. No elastic pool can contain millions of databases.
However, a solution containing 1000 databases per pool, with 1000 pools,
could reach the scale of millions at the risk of becoming unwieldy to
manage.

Two variations of a multi-tenant database model are discussed in what
follows, with the sharded multi-tenant model being the most flexible and
scalable.

### Multi-tenant app with a single multi-tenant database

The simplest multi-tenant database pattern uses a single database to
host data for all tenants. As more tenants are added, the database is
scaled up with more storage and compute resources. This scale up might
be all that is needed, although there is always an ultimate scale limit.
However, long before that limit is reached the database becomes unwieldy
to manage.

Management operations that are focused on individual tenants are more
complex to implement in a multi-tenant database. And at scale these
operations might become unacceptably slow. One example is a
point-in-time restore of the data for just one tenant.

### Multi-tenant app with sharded multi-tenant databases

Most SaaS applications access the data of only one tenant at a time.
This access pattern allows tenant data to be distributed across multiple
databases or shards, where all the data for any one tenant is contained
in one shard. Combined with a multi-tenant database pattern, a sharded
model allows almost limitless scale.

![Design of multi-tenant app with sharded multi-tenant
databases.](https://docs.microsoft.com/en-us/azure/sql-database/media/saas-tenancy-app-design-patterns/saas-multi-tenant-app-sharded-multi-tenant-databases-17.png){.confluence-embedded-image
.confluence-external-resource .confluence-content-image-border
height="250"}

#### Manage shards {#DatabaseSQLArchitect-Manageshards}

Sharding adds complexity both to the design and operational management.
A catalog is required in which to maintain the mapping between tenants
and databases. In addition, management procedures are required to manage
the shards and the tenant population. For example, procedures must be
designed to add and remove shards, and to move tenant data between
shards. One way to scale is to by adding a new shard and populating it
with new tenants. At other times you might split a densely populated
shard into two less-densely populated shards. After several tenants have
been moved or discontinued, you might merge sparsely populated shards
together. The merge would result in more cost-efficient resource
utilization. Tenants might also be moved between shards to balance
workloads.

SQL Database provides a split/merge tool that works in conjunction with
the sharding library and the catalog database. The provided app can
split and merge shards, and it can move tenant data between shards. The
app also maintains the catalog during these operations, marking affected
tenants as offline prior to moving them. After the move, the app updates
the catalog again with the new mapping, and marking the tenant as back
online.

#### Smaller databases more easily managed {#DatabaseSQLArchitect-Smallerdatabasesmoreeasilymanaged}

By distributing tenants across multiple databases, the sharded
multi-tenant solution results in smaller databases that are more easily
managed. For example, restoring a specific tenant to a prior point in
time now involves restoring a single smaller database from a backup,
rather than a larger database that contains all tenants. The database
size, and number of tenants per database, can be chosen to balance the
workload and the management efforts.

#### Tenant identifier in the schema {#DatabaseSQLArchitect-Tenantidentifierintheschema}

Depending on the sharding approach used, additional constraints may be
imposed on the database schema. The SQL Database split/merge application
requires that the schema includes the sharding key, which typically is
the tenant identifier. The tenant identifier is the leading element in
the primary key of all sharded tables. The tenant identifier enables the
split/merge application to quickly locate and move data associated with
a specific tenant.

#### Elastic pool for shards {#DatabaseSQLArchitect-Elasticpoolforshards}

Sharded multi-tenant databases can be placed in elastic pools. In
general, having many single-tenant databases in a pool is as cost
efficient as having many tenants in a few multi-tenant databases.
Multi-tenant databases are advantageous when there are a large number of
relatively inactive tenants.

### Hybrid sharded multi-tenant database model

In the hybrid model, all databases have the tenant identifier in their
schema. The databases are all capable of storing more than one tenant,
and the databases can be sharded. So in the schema sense, they are all
multi-tenant databases. Yet in practice some of these databases contain
only one tenant. Regardless, the quantity of tenants stored in a given
database has no effect on the database schema.

#### Move tenants around

At any time, you can move a particular tenant to its own multi-tenant
database. And at any time, you can change your mind and move the tenant
back to a database that contains multiple tenants. You can also assign a
tenant to new single-tenant database when you provision the new
database.

The hybrid model shines when there are large differences between the
resource needs of identifiable groups of tenants. For example, suppose
that tenants participating in a free trial are not guaranteed the same
high level of performance that subscribing tenants are. The policy might
be for tenants in the free trial phase to be stored in a multi-tenant
database that is shared among all the free trial tenants. When a free
trial tenant subscribes to the basic service tier, the tenant can be
moved to another multi-tenant database that might have fewer tenants. A
subscriber that pays for the premium service tier could be moved to its
own new single-tenant database.

Pools {#DatabaseSQLArchitect-Pools}
-----

In this hybrid model, the single-tenant databases for subscriber tenants
can be placed in resource pools to reduce database costs per tenant.
This is also done in the database-per-tenant model.

### Tenancy models compared

The following table summarizes the differences between the main tenancy
models.

 {.table-wrap}
  ---------------------------------------------------------------------------
  Measurement       Standalone app    Database-per-tenant   Sharded
                                                            multi-tenant
  ----------------- ----------------- --------------------- -----------------
  Scale             Medium\           Very high\            Unlimited\
                    1-100s            1-100,000s            1-1,000,000s

  Tenant isolation  Very high         High                  Low; except for
                                                            any single tenant
                                                            (that is alone in
                                                            an MT db).

  Database cost per High; is sized    Low; pools used.      Lowest, for small
  tenant            for peaks.                              tenants in MT
                                                            DBs.

  Performance       Per-tenant only   Aggregate +           Aggregate;
  monitoring and                      per-tenant            although is
  management                                                per-tenant only
                                                            for singles.

  Development       Low               Low                   Medium; due to
  complexity                                                sharding.

  Operational       Low-High.         Low-Medium. Patterns  Low-High.
  complexity        Individually      address complexity at Individual tenant
                    simple, complex   scale.                management is
                    at scale.                               complex.
  ---------------------------------------------------------------------------


AntiPattern
-----------

### Common Lookup Tables

![843-Fig1.jpg](https://www.red-gate.com/simple-talk/wp-content/uploads/imported/843-Fig1.jpg){.confluence-embedded-image
.confluence-external-resource .confluence-content-image-border
height="250"}

Figure 1

A few years back, Don Peterson wrote an article for  [SQL Server
Central](http://www.sqlservercentral.com/) that detailed
a common practice of creating a single lookup table for various types of
data usually called as code table or an "allowed value table" (AVT). 
These tables tend to be massive and have a pile of unrelated data. 
 Appropriately enough, Don called these tables Massively Unified
Code-Key (MUCK) tables  [(Peterson,
2006)](https://www.red-gate.com/simple-talk/sql/database-administration/five-simple-database-design-errors-you-should-avoid/#peterson) Though
many others have written about it over the years, this name seems to
capture most effectively the clumsiness associated with such a
structure.

In many cases, the data in these tables are  VARCHAR(n) though the real
data type of these values can be anything ranging from  **INTEGER** to 
**DATETIME**.  They are mostly represented in  three columns that may
take some form of the sample table (Figure 1):

The justification here is that each entity in the example here has a
similar set of attributes and therefore it is okay to cram it to a
single table. After all, it results in fewer  tables, keep the database
simpler, right?

During the design process, the database designer may come across several
small tables (in the example, these are tables that represent distinct
types of entities such as 'status of orders', 'priority of financial
assets', 'location codes', 'type of warehouses' etc.).

![843-Fig2.jpg](https://www.red-gate.com/simple-talk/wp-content/uploads/imported/843-Fig2.jpg){.confluence-embedded-image
.confluence-external-resource .confluence-content-image-border
width="259" height="124"}
![843-Fig3.jpg](https://www.red-gate.com/simple-talk/wp-content/uploads/imported/843-Fig3.jpg){.confluence-embedded-image
.confluence-external-resource .confluence-content-image-border
width="314" height="188"}
![843-Fig4.jpg](https://www.red-gate.com/simple-talk/wp-content/uploads/imported/843-Fig4.jpg){.confluence-embedded-image
.confluence-external-resource .confluence-content-image-border
width="285" height="124"}
![843-Fig5.jpg](https://www.red-gate.com/simple-talk/wp-content/uploads/imported/843-Fig5.jpg){.confluence-embedded-image
.confluence-external-resource .confluence-content-image-border
width="253" height="146"}

Figures 2-5

 He then decides to combine them all because of the similarity of their
columns. He assumes that he is eliminating redundant tables and
simplifying the database; he will have fewer tables, he'll save space,
improve efficiency etc. People also assume that it reduces the
complexity of the SQL required, because a single routine/stored
procedure can be written to access any type of data.

So what is wrong with it?

-   Firstly, you lose the means to ensure accurate data; constraints. By
    combining different entities into a single table, you have no
    declarative means to restrain values of a certain category. There is
    no easy way to enforce simple foreign key constraints without adding
    the  **categoryid** in all the referencing keys.
-   Secondly, you are forced to represent every data type as a string
    with this type of  generic lookup table. Such intermingling of
    different types can be a problem, because check constraints cannot
    be imposed without major code-hacking . In the example we've given,
    if the discount code is CHAR(3) and  **location\_nbr** is INT(4),
    what should the data type of the  'code' column be in the Common
    Lookup table?
-   Thirdly, you commit yourself to rigidity and subsequent complexity.
    You might be tempted to ask, how can such an apparently simple and
    flexible design be rigid? Well, considering our example of a common
    lookup table scheme, just imagine that the 'LocationCode' table 
    includes another column which might be 'region'. What about the
    consequences of adding a status to the 'DiscountType' table? Just in
    order to change a single category,  you'll have to consider making
    way for all the rows in the table regardless of whether the new
    column is applicable to them or not.  What about complexity? Often
    the idea of using common lookup tables come from the idea of
    generalizing entities where by a single table represents a "thing"
    -- pretty much anything.\
    Contrast this with the fundamental rule that a well-designed table
    represents a set of facts about entities or relationships of the
    same kind. The problem with generalizing entities is that a table
    becomes a pile of unrelated rows: Consequently, you then lose
    precision of meaning,  followed by confusion and, often, unwanted
    complexity.  \
    The main goal of a DBMS is to enforce the rules that govern how the
    data is represented and   manipulated. Make sure you do not confuse
    the terms "generalize", "reuse" etc. in the  context of database
    design to the extent where you have no control over what is being
    designed.
-   Fourthly and finally, you are faced with the physical implementation
    issues.  While logical design is considered to be totally separate
    from physical implementation, in commercial DBMS products like SQL
    Server, physical implementations can be influenced by logical
    design, and vice-versa. In large enterprises, such common lookup
    tables can grow to hundreds of thousands of rows and require heavy
    physical database tuning. Locking and concurrency issues with such
    large tables will also have to be controlled. The internal
    representation of a particular set of row in physical storage can be
    a determining factor in how efficient the values can be accessed and
    manipulated by SQL queries.

As a general recommendation, always use separate tables for each logical
entity, identifying the appropriate columns with correct types,
constraints and references. It is better to write simple routines and
procedures to access and manipulate the data in the tables without
aiming for "dynamic code".

Common lookup tables have no place in sensible database design, whether
used as a short-term makeshift fix or as a long-term viable solution.
While application-enforced integrity is sometimes favored by developers,
it remains true that the DBMS must still be the centralized enforcer of
all integrity. Because the foremost goal in a given database design is
to preserve data integrity and logical correctness,  common lookup
tables are one of the worst kind of mistakes that one can make..

### Check Constraint conundrum

Check Constraints serve several purposes, but cause trouble to designers
in two ways:

-   They miss declaring appropriate check constraints when it is
    necessary.
-   They are unaware when to use a column level constraints rather than
    a table with a foreign key constraint.

Constraints in SQL Server can serve many different purposes, including
support for domain constraints, column constraints and, to some extent,
table constraints. A primary purpose of a database is to preserve data
integrity, and well-defined constraints provide an excellent means to
control what values are allowed in a column.

So then, should you ever avoid using a check constraint? Well, let's
consider the cases where a referencing table (a table with a foreign
key) can be used to restrain the column with a specific set of values.

![843-Fig6.jpg](https://www.red-gate.com/simple-talk/wp-content/uploads/imported/843-Fig6.jpg){.confluence-embedded-image
.confluence-external-resource .confluence-content-image-border
height="250"}

Figure 6

Here the values for  **ins\_code** in the  **PolicyHolders** table can
be restricted in two ways. One way would involve the use of  a lookup
table that holds the allowed values for  **ins\_code**. An alternative
is to have a check constraint on the  **PolicyHolders** table along the
lines of:

        CHECK ( ins_code IN ( 'IC' , 'FS' , 'MC' , 'PPO' , 'POS' , 'HMO' ) )
                    

So what is the rule of thumb in choosing the right approach? Old hands
in database design look for three specific criteria to govern their
choice  between a check constraint or a separate table that has a
 foreign key constraint.

1.  If the list of values changes over a period of time, you must use a
    separate table with a foreign key constraint rather than a check
    constraint.
2.  If the list of values is larger than 15 or 20, you should consider a
    separate table.
3.  If the list of values is shared or reusable, at least used three or
    more times in the same database, then you have a very strong case to
    use a separate table.

Note that database design is a mix of art and science and therefore it
involves tradeoffs. An experienced designer can make a  trade-off, based
on an informed judgment of the specific requirements.

#### Entity-Attribute-Value Table

Ideally a table represents a set of entities, each of which has a set of
attributes represented as columns. Sometimes, designers can get caught
up in the world of alternative programming "paradigms" and might try to
implement  them. One such model is called Entity-Attribute-Value ( or in
some contexts as object-attribute-model), which is a nickname for a
table that has three columns, one for the type of entity it is supposed
to represent, another for a parameter or attribute or property of that
entity and a third one for the actual value of that property.

Consider the following example of a table that records data about
employees:

![843-Fig7.jpg](https://www.red-gate.com/simple-talk/wp-content/uploads/imported/843-Fig7.jpg){.confluence-embedded-image
.confluence-external-resource .confluence-content-image-border
width="383" height="145"}

Fig 7

Now, the EAV approach shuffles up the data, in order to  represent the
attributes as values in one column and the corresponding values of those
attributes in another column:

![843-Fig8.jpg](https://www.red-gate.com/simple-talk/wp-content/uploads/imported/843-Fig8.jpg){.confluence-embedded-image
.confluence-external-resource .confluence-content-image-border
width="291" height="251"}

Fig 8

Taking this to the extreme, there is no need for additional tables ---
all data can be crammed into a single table! The credit to this
invention goes to so called "clinical database" designers who decided
that when various data elements are unknown, partially known or sparse
it is best to use EAV  [(Nadkarni,
2002).](https://www.red-gate.com/simple-talk/sql/database-administration/five-simple-database-design-errors-you-should-avoid/#nadkarni) The
problem is that many newcomers get seduced into applying this approach
in SQL databases and the results are usually chaos. In fact, many people
assume that it is a good thing that they do not know the nature of data!

So what are the benefits that are touted for EAV? Well, there are none.
Since EAV tables will contain any kind of data, we have to PIVOT the
data to a tabular representation, with appropriate columns, in order to
make it useful. In many cases, there is middleware or client-side
software that does this behind the scenes, thereby providing the
illusion to the user that they are dealing with well-designed data.

EAV models have a host of problems.

-   Firstly, the massive amount of data is, in itself, essentially
    unmanageable.
-   Secondly, there is no possible way to define the necessary
    constraints --- any potential check constraints will have to include
    extensive hard-coding for appropriate attribute names. Since a
    single column holds all possible values, the datatype is usually
    VARCHAR(n).  
-   Thirdly, don't even think about having any useful foreign keys.
-   Finally,  there is the complexity and awkwardness of queries. Some
    folks consider it a benefit to be able to  jam a variety of data
    into a single table when necessary --- they call it "scalable". In
    reality, since EAV mixes up data with metadata, it is lot more
    difficult to manipulate data even for simple requirements. Consider
    a simple query to retrieve the employees who are born after 1950. In
    the traditional model, you'd have:

```{=html}
<!-- -->
```
            SELECT  first_name , last_name
            FROM    Employees
            WHERE   date_of_birth > '12/31/1950' ;
                    

In a EAV model, here is one way to write a comparable query :

            SELECT  MAX ( CASE emp_property WHEN 'first_name' THEN value END  ) 'first_name'
                    , MAX ( CASE emp_property WHEN 'last_name' THEN value END ) 'last_name'
            FROM    EmployeeValues
            WHERE   emp_nbr IN ( 
                    SELECT  emp_nbr
                    FROM    EmployeeValues
                    WHERE   emp_property = 'date_of_birth'
                            AND CAST ( value AS DATETIME ) > '12/31/1950' )
                            AND emp_property IN ( 'first_name' , 'last_name' )
                    GROUP BY emp_nbr ;  
                            )
                    

Listing 1

For those who are handy at Transact-SQL, go ahead, add a few new columns
with different data types and try out a few queries and see how much fun
it can be!

The solution to the EAV nightmare is simple: Analyze and research the
users' needs and identify the data requirements up-front.  A relational
database maintains the integrity and consistency of data.  It is
virtually impossible to make a case for designing such a database
without well-defined requirements. Period.

#### Application Encroachments into DB design

There are several ways that an application can trespass on the field of
data management. I'll briefly explain a couple of ways and suggest some
guidelines on how to prevent it.

#### Enforcing Integrity via applications

Proponents of application based integrity usually argues that
constraints negatively impact data access. They also assume selectively
applying rules based on the needs of the application is the best route
to take.

Let us look at this in detail. Are there any good statistical
measurements, comparisons and analyses exist to address the performance
difference between the same rules enforced by the DBMS and the
application? How effectively can an application enforce data related
rules? If the same rules are required by multiple applications, can the
duplication of code be avoided? If there is already an integrity
enforcement mechanism within the DBMS, why reinvent the wheel?

The solution is simple.

Rely on nothing else to provide completeness and correctness except the
database itself. By nothing, I mean neither users nor applications
external to the database. While it may be true that current DBMS
products may not succeed in enforcing all possible constraints, it is
not sensible to let the application or user take over that
responsibility.

You may ask why it is bad to rely on the application to enforce
data-integrity? Well, if there is only one application per database,
then it is not really an issue. But usually, databases act as the
central repositories of data and serve several applications. Therefore, 
rules must be enforced across all these applications. These rules may
change as well.

As a general guideline, databases are more than  mere data repositories;
they are the source of rules associated with that data. Declare
integrity constraints in the database where possible, for every rule
that should be enforced. Use stored procedures and triggers only where
declarative integrity enforcement via keys and constraints isn't
possible. Only application-specific rules need to be implemented via the
application.

##### Application Tail wagging the Database Dog: {#DatabaseSQLArchitect-ApplicationTailwaggingtheDatabaseDog:}

There is a growing trend among the developer community to treat the
database as being a mere component of the 'application domain'. Often,
tables are added as needed by the application developer  and then
columns are subsequently slapped in as an afterthought.

This is convenient because it avoids troublesome parts of the design
process such as requirements-gathering.. Experience tells us that, in
most enterprises,  **applications come and go, but databases usually
stand for a long time.**  It therefore makes good sense to make the
effort to develop a good design based on the rules that are specific to
the business segment in context.  [(Teorey,
1994).](https://www.red-gate.com/simple-talk/sql/database-administration/five-simple-database-design-errors-you-should-avoid/#teorey)

#### Misusing Data values as Data Elements {#DatabaseSQLArchitect-MisusingDatavaluesasDataElements}

Let's just clarify something before proceeding further:  a 'data value'
here refers to the value of an attribute of an entity; a 'data element'
refers to an unit of metadata such as a column name or a table name. By
misusing data values as data elements I refer to the practice of
splitting attribute values of a certain entity and representing it
across several columns or tables. Joe Celko calls it exactly that ---
'attribute splitting'  [(Celko,
2005)](https://www.red-gate.com/simple-talk/sql/database-administration/five-simple-database-design-errors-you-should-avoid/celko).

Consider a table that represents the sales figures of some salesmen that
work for a company. Let's assume that the following design is adopted so
as to make it easier to retrieve the data in order to display it:

![843-Fig9.jpg](https://www.red-gate.com/simple-talk/wp-content/uploads/imported/843-Fig9.jpg){.confluence-embedded-image
.confluence-external-resource .confluence-content-image-border
width="460" height="145"}

Figure 9

You'll see here that  a single attribute in the business model, the
'sales amount', is represented as a series of columns. This  makes life
harder for almost everyone using such a scheme.

Now, what would make such design undesirable?

-   The duplication of constraints is going to cause problems. Any
    constraints that apply to monthly sales will have to be defined for
    each individual column.
-   Without altering the table, you cannot add the sales for a new
    month. One poor alternative is to have the columns for all possible
    monthly sales and use NULLs for the months with no sales.
-   And finally, there is the difficulty in expressing relatively simple
    queries, like comparing sales among sales persons or finding the
    best monthly sales. 

By the way, many people consider this to be a violation first normal
form. This is a misunderstanding since there are no multi-valued columns
here  [ (Pascal,
2005).](https://www.red-gate.com/simple-talk/sql/database-administration/five-simple-database-design-errors-you-should-avoid/#pascal) For
a detailed exposition, please refer to the simple-talk article:  [Facts
and Fallacies about First Normal
Form](http://www.simple-talk.com/sql/learn-sql-server/facts-and-fallacies-about-first-normal-form/)

The ideal way to design this table would be something along the lines
of:

![843-Fig10.jpg](https://www.red-gate.com/simple-talk/wp-content/uploads/imported/843-Fig10.jpg){.confluence-embedded-image
.confluence-external-resource .confluence-content-image-border
width="501" height="402"}

Fig 10

Of course you can have a separate table for the sales persons and then
reference it using a foreign key, preferably with a simple surrogate key
such as  **sales\_person\_id** ,  shown above.

If you are stuck with a table that is designed as Fig 9, you can create
a resultset  from the code  in a few different ways:

1\. Use a UNION query:

        SELECT  sales_person , 'jan' AS " month" , jan_sales AS " sales"
        FROM    salesdata
        UNION ALL
        SELECT  sales_person , 'feb' , feb_sales
        FROM    salesdata
        UNION ALL
        SELECT  sales_person , 'mar' , mar_sales
        FROM    salesdata
        UNION ALL
        SELECT  sales_person , 'apr' , apr_sales
        FROM salesdata ;
                    

2\. Use a JOIN to a derived table with the column names:

        SELECT  sales_person
                , m AS 'month' 
                , CASE m WHEN 'jan' THEN jan_sales WHEN'feb'THENfeb_sales WHEN'mar'THENmar_sales WHEN'apr'THENapr_sales END 'sales'
        FROM    salesdata
                CROSSJOIN(
                        SELECT 'jan'
                        UNION
                        SELECT 'feb'
                        UNION
                        SELECT 'mar'
                        UNION
                        SELECT 'apr'
                        ) months (m);

        SELECT sales_person 
                , m AS " month" ,
                CASE m WHEN 'jan' THEN jan_sales WHEN 'feb' THEN feb_sales WHEN 'mar' THEN mar_sales WHEN 'apr' THEN apr_sales ENDA Ssales
        FROM  salesdata
            CROSSJOIN(
                SELECT 'jan'
                UNION
                SELECT 'feb' 
                UNION
                SELECT 'mar' 
                UNION
                SELECT 'apr'
                ) months (m);
                    

3\. Use UNPIVOT:

        SELECT  sales_person 
                , 'month' 
                , sales
        FROM    (
                    SELECT  sales_person 
                            , jan_sales 
                            , feb_sales 
                            , mar_sales 
                            , apr_sales 
                            , may_sales
                    FROM    salesdata 
                ) s 
                ( 
                    sales_person 
                    , jan 
                    , feb 
                    , mar 
                    , apr 
                    , may 
                )
                UNPIVOT
                ( 
                    sales FOR 'month' IN ( jan , feb , mar , apr , may ) ) m ;
                        

As usual, you will have to test against the underlying tables,  and
consider such things as the magnitude of the data and  existing indexes
to  make sure which method is the most efficient .

The other variation of this approach is to split the attributes across
tables, i.e. using data values as part of the table name itself. This is
commonly done by having multiple tables that are similarly structured.
Consider the following set of tables:

![843-Fig12.jpg](https://www.red-gate.com/simple-talk/wp-content/uploads/imported/843-Fig12.jpg){.confluence-embedded-image
.confluence-external-resource .confluence-content-image-border
width="630" height="138"}

Figure 11

Here, the individual values of the attribute 'month' are assigned to
each table. This design shares similar shortcomings such as the
duplication of constraints and the difficulty in expressing simple
queries.  To be useful, the tables will have to be UNION-ed to form a
single table with an additional column representing the month. It would
have been easier to start with a  single base table.

We should be careful not to confuse splitting attributes with the
logical design principle with table partitioning, a data reorganization
process done at the physical level that creates smaller subsets of data
from a large table or index in an attempt manage and access them
efficiently.

Just as a side note, this problem has been discussed heavily by
relational theorists specifically with respect to the limitations it
imposes on view updates. Some have identified it as a direct violation
of the Information Principle (a relational principle that requires the
representation of all data in a database solely as values in a table)
and recommended that  **no two tables in a database should have
overlapped meanings**.   Originally defined as the New Design Principle,
this recommendation for each table to have a single meaning or predicate
is currently known as the Principle of Orthogonal Design in relational
literature  [(Date & McGoveran,
1995)](https://www.red-gate.com/simple-talk/sql/database-administration/five-simple-database-design-errors-you-should-avoid/#date).

References

-   <https://github.com/DovAmir/awesome-design-patterns>
-   <https://docs.microsoft.com/en-us/azure/sql-database/saas-tenancy-app-design-patterns>
-   <https://www.red-gate.com/simple-talk/sql/database-administration/five-simple-database-design-errors-you-should-avoid/>
-   [https://www.talend.com/blog/2017/05/05/data-model-design-best-practices-part-1](https://www.talend.com/blog/2017/05/05/data-model-design-best-practices-part-1/)
-   <https://database-programmer.blogspot.com/2008/07/different-foreign-keys-for-different.html>
-   <https://database-programmer.blogspot.com/2008/01/table-design-patterns-cross-reference.html>
-   <http://www.databaseanswers.org/data_models/>



 



