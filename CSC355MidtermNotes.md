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
1. __CREATE TABLE:__

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
	- Numbers Number(x,y) x = total digits, y = digits to right of dec.
    - String
    	* fixed length, char(x) x = number of characters
    	* variable length, varchar(m) m = max characters
	- Dates:
		* DATE 'yyyy-mm-dd' (all values y, m, and d must be integers) 
1. CHECK:
	* The following SQL creates a CHECK constraint on the "P_Id" column when the "Persons" table is created. The CHECK constraint specifies that the column "P_Id" must only include integers greater than 0.


1. Defining Keys
1. INSERT INTO: populates table
	ex: INSERT INTO TABLENAME VALUES(val1,val2,val3);
	
			INSERT INTO hotel VALUES (00001, 'Ritz Carlton', '160 East Pearson Street at Water Tower Place', 'Chicago' );
			INSERT INTO hotel VALUES (00002, 'Ritz Carlton', '50 Central Park S', 'New York' );
			INSERT INTO hotel VALUES (00003, 'Ritz Carlton', '900 W Olympic Blvd', 'Los Angeles' );
1. DROP TABLE: drops a table from the database
	ex: DROP TABLE TABLENAME	
1. ALTER TABLE:


1. UPDATE:

1. DELETE:

##SQL Queries:

	* SELECT:
	* DISTINCT:
	* AS
	* FROM WHERE:
	* Comparison operators (=, !=, <>, <, <=, >, >=)
	* LIKE and wildcards (_, %):
	* Logical operators (AND, OR, NOT)
	* NULLs
	* ORDER BY
	* ASC/DESC
	* Aggregate functions
		* SUM(), COUNT(), AVG(), etc...
	* GROUP BY
	* HAVING
		* conditional that modifies group by statements
	* Set operations

	* Cartesian product
		* aka cross join
			SELECT table1.column1, table2.column2...
				FROM  table1, table2
	* Equi-join
			SELECT column_list 
			FROM table1, table2....
			WHERE table1.column_name =
			table2.column_name; 
	* Natural join
	* INNER JOIN
	* Inner join vs outer join
	* LEFT OUTER JOIN
	* RIGHT OUTER JOIN
	* FULL OUTER JOIN
	* Subqueries
	* Single-value vs table
	* = vs IN
		* 
	* EXISTS
	* NOT EXISTS
	* ANY

example Queries:

// for each department, print the department and the max salary of a worker in the
// department
		select dept, MAX(salary)
		     from company
		     group by dept;


// list the dept names and total budgets 
// ordered from largest total budget to smallest

		select dept, SUM(salary)
		     from company
		     group by SUM(salary) DESC

// for each student, find total numbers of classes enrolled in and most
// recent year enrolled

		select StudentID, COUNT(CourseID), MAX(year),
		     from enrolled
		     group by StudentID;

		select * from zipcode
		     where not exists (select * from person where zip = zipcode.zip);


-- where zip = zipcode.zip checks all zipcodes in the zipcode table

		select distinct StudentID from ENROLLMENT
		     where SectionID IN (select SectionId from ENROLLMENT where StudentID = '1234567');

		select distinct StudentID from ENROLLMENT
		     where SectionID IN (select SectionId from ENROLLMENT where StudentID =
		          (select StudentID from student
		               where FirstName = 'Paul' and LastName = 'Konrad'));

1. Give the names of all male employees who are directly supervised by Fred Wong.

		select fname, lname from employee where superssn =
		 (select ssn from employee where fname = 'Fred' and lname = 'Wong')
		 and gender = 'M';

2. Give the average salary of all employees in the Development department.

		select avg(salary)
		 from employee inner join department on dno=dnumber
		 where dname = 'Development';

3. Give the names of all employees in department 2 who work at least 10 hours per week on the Reorganization project.

		select fname, lname
			from (employee inner join workson on ssn=essn)
				inner join project on pno=pnumber
			where DNo = 2 and hours >= 10 and pname = 'Reorganization';

4. For each project, give the project name and the total hours (by all employees) spent on that project. (List the projects from the one with the most total hours to the one with the list.)

		select pname, sum(hours)
		 from workson right outer join project on pno=pnumber
		 group by pnumber, pname
		 order by sum(hours) desc;

5. Give the names, department numbers, and SSNs of all employees who do not work on any project.

		select ssn, dno, fname, lname
		 from employee left outer join workson on ssn=essn
		 where essn is null;

6. Give an alphabetical list of only the last names of all employees in department 4 who have at least one daughter.
		
		select distinct lname
		 from employee inner join dependent on ssn=essn
		 where dno = 4 and (relationship in ('Daughter'));
	

7. Give the SSNs of all employees whose supervisor's supervisor (not their direct supervisor) has SSN 888665575, listed in ascending order.
		
		select SSN
		 from employee where superssn in
		 (select ssn from employee where superssn = '888665575')
		 order by SSN;


8. For each department whose average salary is less than $50,000, give the department name and how many employees are in that department.

		select dname, count(ssn)
		 from employee inner join department on dno=dnumber
		 group by dnumber, dname
		 having sum(salary) <= 50000;

##SQL Transactions:

>! can't touch this


* interruptions:
	* tables created from scripts can lose data once connection has been timed out
* concurrency:
	* locking table or rows while one user is accessing them
* transactions:
	* collection of SQL statements
	* statements are executed as unit
	* transaction handler must handle:
		* interruptions --> logging and recovery
		* concurrency   --> concurrency control, Lock tables

* ACID Properties for Databases:
	* Atomicity
		* execute totally or not at all
		* transactions kept local, not immediately applied to DB
		* once transaction done, result "committed" to database
		* partial results can be "rolled back" (by user or system)

	* Consistency
		* satisfy all DB constraints
		* constraints can be "deferred" --> checked on commit
			* deferrable initially deferred (or immediate

	* Isolation
		* execute separately from others
	* Durability
		* once results are committed they are perm. (can't be rolled back)


* COMMIT

* ROLLBACK

* Serializable

* Repeatable read

* Read committed
* Read uncommitted

