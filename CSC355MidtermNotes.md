#CSC355 Midterm Review Notes

##Database Intro:

1. DB Properties
	* Database:
		* logically related data stored in an organized manner
		* stores data in single repository with 1+ users
	* Stored __Data's__ Properties
		* Persistency --> the data is stored on a stable platform/medium
		* Shared
		* Interrelated --> form a "bigger picture"
	* Data repository structure:
	* __database and DBMS make up *database system*__

2. cost benefit analysis for Database:

	*__costs__:
	    * takes resources(overhead) (time, money, etc) to design, maintain 	    	and	implement a DB
	* __benefits__:
		* Program-data independence
		* Controlled Data redundancy
		* Controls access to data
		* supports 1+ user interfaces
		* querys are more efficiently processed
		* greater DB efficiency allows for faster app dev.

3. database models
	* Old Models:
		* file systems, networks, hierarchical etc --> all had glaring drawbacks
	* Relational Models
	* Newer Models:
		* semi-structured: XML-based collections of data
		* object-relational: add support for structured data types to relational DBs.
		* NoSQL: 
		* newer models have yet to totally replace relational model

4. DBMS components
	* __Query Processor:__ optimizes user queries
	* __Transaction Processor:__ handles request concurrency
	* __File/buffer/storage managers:__ control internal storage of DB,@ schema and related info

##Relational Model:

0. properties of relational model:
	* first model to separate logical structure of data from physical structure
	* tables are linked by shared columns of data
	* Standardized Query Language (SQL) exists
	* data model:
		* Structure   -->  organization
		* Operations  -->  ways data can be interacted with
		* Constraints -->  what constraints are there on data?
	* __Relational Data model:__
		* Operations  -->  Relational algebra/SQL
		* Structure   -->  2d tables with links
		* Constraints -->  Data domains, uniqueness, etc..
	* __Semi-structured Model:__
		* Structure   -->  Nested XML elements
		* Operations  -->  Element traversal, Searching  
		* Constraints -->  Data domains, nesting restrictions

1.  Data stored in 2d __tables__ called __relations__; ea. one has a name

2.  Relations composed of __rows__ of __records--tuples__, is one instance of the data
	that the table is a representation of.

3.  __Attributes__ are the columns of the table.  They represent (display) a property for which each instance (row) has a value.

4.  __Domains:__  data types (Char, varchar, number, etc)
	* each component (value) in a tuple (row) must be a part of the set of values (domain)
		associated with the specific data type
	* example data types:
		* CHARACTER(n)	Character string. Fixed-length n
		* VARCHAR(n) or CHARACTER VARYING(n):	Character string. Variable length. 		Maximum length n
		* BINARY(n)	Binary string. Fixed-length n
		* BOOLEAN	Stores TRUE or FALSE values
		* VARBINARY(n) or BINARY VARYING(n): Binary string. Variable length. Maximum 	length n
		* INTEGER(p)	Integer numerical (no decimal). Precision p
		* SMALLINT	Integer numerical (no decimal). Precision 5
		* INTEGER:	Integer numerical (no decimal). Precision 10
		* BIGINT:	Integer numerical (no decimal). Precision 19


5.  Properties of relations:
	* ea. relation has a unique name (in DB)
	* ea. attribute has a unique name (in relation(Table))
	* ea. entry (row) of relation (table) is either Null or contains single val
		from its attribute's domain
	* record order doesn't matter
	* order of attributes doesn't matter
	* can't have identical records (__rows__) in relation (table)

6.  Schema vs instance:
	* __schema__ (of relation) has name of relation and a list of the attributes
	* ex:
		* EMPLOYEE (ID: integer(3), Name:string(20), Dept:string(12), Salary:number(5.2));
	* __instance:__
		* set of tuples (vals at col, rows) has a value for ea. attribute or NULL
			* constraints enforced by DBMS

		* Instances usually shown as a table, __but the order of the rows in the the table is *not* important__

7.  __Candidate Keys (CK)__
	* (CK) :
		* set of attributes where each tuple in the relation must have a unique set of vals ("key constraints")
		* no subset of the relation can't have this property

	* __Primary Keys:__
		* a candidate key can be chosen as PK of relation
		* PK is underlined in schema
		* PK cannot have any Null values in its tuple (__entity integrity__)

	* __Foreign Keys:__
		* FK link relations (tables) using a shared key 
		* dotted-underline in schema
		* in every tuple (row) foreign ke must have a 
			value that is the value of the PK for some 
			row/tuple in the referenced relation (__referential integrity__)
		* FK pairs ea. tuple with one in the referenced
			table.

10. Domain Constraints:
	* ea. tuple's (row) attributes need to come from
		domain

11. Key constraints:
	* ea. tuple (row) must have unique set of vals in ea.
		candidate key

12. Entity Integrity:
	* no PK can contain a null value

13. Referential Integrity:
	* All FK vals must appear as the val of the PK in some tuple of the 
		table it references

##SQL's DDL:
1. CREATE TABLE:

	 CREATE TABLE GUEST(
	   ID number(5),
	   LastName varchar(40),
	   FirstName varchar(40),
	   Phone number(10),
	   
	   PRIMARY KEY (ID)
	 );
	 
	 CREATE TABLE HOTEL(
	   ID number(5),
	   Name varchar(40),
	   Address varchar(60),
	   City varchar(20),
	   
	   primary key (ID)
	 );
	 
	 CREATE TABLE RESERVATION(
	   GuestID number (5),
	   HotelID number (4),
	   StartDate date,
	   EndDate date,
	   Confirmation varchar (8),
	   
	   primary key (GuestID, HotelID, StartDate),
	   foreign key (GuestID) references guest(ID),
	   foreign key (HotelID) references hotel(ID)
	 );

1. Domains (Numerical, String, Dates):
	
1. CHECK
1. Defining Keys
1. INSERT INTO 
1. DROP TABLE
1. ALTER TABLE
1. UPDATE 
1. DELETE




##SQL Queries:

##SQL Transactions:

>! can't touch this