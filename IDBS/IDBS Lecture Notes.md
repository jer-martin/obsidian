## Welcome!
- <font color="HotPink" style="font-style: italic;">Database systems</font> are software systems for managing large volumes of data
- Industry sector valued at more than US$100 Billion annually
- <font color="HotPink" style="font-style: italic;">Relational database systems</font> still dominate the sector
- Great overview provided on https://db-engines.com/en/
#### Application Examples
- Sales: customer, product, purchase info
- Accounting: Payments, receipts, balances
- Human resources: Salaries, payroll taxes
- Banking and Finance: Customer info, banking transactions
- Universities: Student info, course registrations
- Airlines: Reservations, schedule information
- Telecommunications: Keeping records of calls made, monthly phone bills
- Web based applications on the internet

## Traditional Data Management Using File Systems
- In a time with no database systems....
### Scenario: University Admin
![](../zassets/Pasted%20image%2020240108095426.png)
##### Assumptions
- Both files contain last name, first name, registration number, and address of a student
- Grade data additionally includes the results of oral exams, written exams, seminars, etc
- Class data additionally comprises the taken classes of each student
### *Problems with early data processing...*
- **Redundancy**
	- Repeated occurrence of the same data in different files
	- Waste of internal memory, increased management and processing costs
- **Inconsistency**
	- Lacking logical concordance of file contents
	- Especially caused due to changes
- **Data-Program dependence**
	- Data are directly created and accessed by an application program
	- Changes of the file structure lead to changes of the application program
	- Extensions of the functionality of an application program lead to new requirements of the file structure and to a restructuring of files
- **Inflexibility**
	- Analysis of data and the realization of new applications is problematic
	- Data from several files can be combined with very high costs
### *Advantages of Database systems...*
- **Data independence**
	- Independence of application programs from the details of data representation and data storage (abstract data view)
- **Efficient data access**
	- Multitude of sophisticated techniques for the efficient storage of and efficient access to persistent data 
	- Application of index structures
- **Common data basis**
	- Common data basis for all current and future application programs
- **Concurrent data access**
	- Simultaneous access to the same data by different users
	- Each user gets the impression of locally, exclusively accessing data
	- Concept of *transaction* for the *synchronization* of concurrent data accesses
- **Lacking or controlled redundancy**
	- Avoiding copies of the same data by an integrated view on data
	- Controlled redundancy for improving performance
- **Consistency**
	- Caused by lacking redundancy
	- DBMS must ensure consistency of data for controlled redundancy
- **Integrity**
	- Correctness and completeness of data
	- Formulation of *integrity constraints* or *integrity rules*
	- DBMS checks constraints for each insertion, change, and deletion
- **Data security**
	- Protection of the database against unauthorized access
	- Access control with authentication and encoding as possible protection mechanisms
- **Backup and recovery**
	- Protection against the consequences of system errors
	- Backup: copies on external storage
	- Recovery: automatic reconstruction of the last, up-to-date, and consistent database status with the aid of tapes or disks and a protocol listing the executed changes
- **Posing queries**
	- Traditional data organization: posing queries by an application program, extremely inflexible
	- DBMS: query language, which allows, to pose ad hoc queries by using the keyboard and to get an immediate answer
	- Embedding of queries into database application programs
	- Importance of an efficient query optimization, query processing, and query execution
- **Provision of diversified user interfaces**
	- Query languages for occasional users, programming interfaces for implementers, menu-driven interfaces for naive users, window and graphic oriented user interfaces
	- *Data definition languages, data manipulation languages*
- **Flexibility
	- Change of the database structure without change of existing application programs
	- Different evaluations of data possible in an easy way
- **Faster developments of new applications
	- Use of the powerful functions of a DBMS for new application

## Fundamental Database Terms
### Database
- Integrated and structured repository of large collections of persistent data, which serves for all users of an application area as a common and reliable basis of up-to-date information
- Frequently used synonymous term: <font color="HotPink" style="font-style: italic;">data basis</font>
### Database Management System (DBMS)
- All purpose software system, which supports the user in the definition, construction and manipulation of databases for different applications in an application-neutral and efficient manner
- Set of programs for the management of and access to the data in the DB
- Software level between physical database and user
### Database System (DBS)
- DBS = DBMS + DB
### Data Model
- Mathematical formalism consisting of a notation for describing the data of interest and of a set of operations for manipulating these data
- Description of the structure of a database (data types, relationships, conditions) together with operations for handling and manipulating the data

## Overview of Data Models for Database Systems
<font color="LightBlue" style="font-weight: bold;">A data model offers facilities</font>
	- for the specification of data objects
	- for the specification of the relationship between data
	- for the specification of operations on data objects together with their semantics
<font color="LightBlue" style="font-weight: bold;">Usually, a DBS has at least two data models</font>
	- A <font color="HotPink" style="font-style: italic;">physical data model</font> for the storage-oriented representation of data
	- A <font color="HotPink" style="font-style: italic;">logical data model</font> for the user-oriented representation of data
#### Logical Data Models
- <font color="HotPink" style="font-style: italic;">object-based</font> e.g., the *entity relationship model*, the *object-oriented data model*, the *object-relational data model*
- <font color="HotPink" style="font-style: italic;">record-based</font> e.g., the *object-relational data model*, the *relational data model*, the *network data model*, the *hierarchical data model*
##### Data Abstraction: The Three Level Database Architecture
<font color="LightBlue" style="font-weight: bold;">DBS has several abstraction levels</font>
- <font color="HotPink" style="font-style: italic;">External/view levels</font> describe the part of the DB that is relevant for users
- <font color="HotPink" style="font-style: italic;">Conceptual/logical level</font> gives information about existing data and relationships in the DB
- <font color="HotPink" style="font-style: italic;">Physical internal level</font> describes how data is physically stored on the disk
<font color="Pink" style="font-weight: bold;">Database schema and Database State</font>
- A <font color="HotPink" style="font-style: italic;">schema</font> describes the structure/design of a DB
- A <font color="HotPink" style="font-style: italic;">state</font> describes a concrete instance of a DB
##### Data Independence
<font color="LightBlue" style="font-weight: bold;">Denotes the property that higher levels of the model are not influenced by changes of lower levels</font>
- <font color="HotPink" style="font-weight: bold;">Logical data independence</font>
	- Changes of the conceptual schema (e.g, info about new types of entities) do not have impact on the external schema (e.g. existing app programs)
	- Example: extension of the class data for an additional Boolean value expressing whether the merits required for a master thesis have been performed
- <font color="HotPink" style="font-weight: bold;">Physical data independence</font>
	- Changes of the physical schema (e.g, change of access structure, data structure) do not have an impact on the conceptual schema and thus also not on external schemas but can improve performance
	- Example: the class data, which is stored in an unsorted file, are to be reorganized in a B-tree to enable efficient access by "registration number"

## Database Languages
<font color="Pink" style="font-weight: bold;">Data definition language (DDL)</font>
- Language to manipulate database schema
- (Meta) data for the description of a schema (<font style="color:HotPink">data dictionary</font>, <font style="color:HotPink">system catalog</font>)
- Permits the specification of implementation details
<font color="Pink" style="font-weight: bold;">Data manipulation language (DML)</font>
- <font color="HotPink" style="font-style: italic;">Query language</font> for the retrieval of data objects in a database
- "Actual" data manipulation language for the change of stored data objects, for the insertion of new data, and for the deletion of stored data
- A query, which is formulated by a user with the objects of their external level, is translated into an efficient query, which rests on the objects of the physical level (i.e, on the data stored in the database on the disk)
- In general, realized as a <font color="HotPink" style="font-style: italic;">non-procedural</font> language
	- User specifies *which* data are searched for but *not how* data can be found

## Entity Relationship Model
### Introduction
- <font color="HotPink" style="font-style: italic;">Entity-Relationship Model</font> (E-R Model) for conceptual database design
- Based on the article by Peter P. Chen (1976)
- E-R Model (besides <font color="LightBlue">UML</font>) has great importance in practice
- Two-phase procedure for DB design
	- Phase 1: Requirements analysis and design of an ER model
	- Phase 2: Transformation of the ER model into a concrete logical model
- <font color="Pink" style="font-weight: bold;">Goal</font>:
	- Modeling an interesting part of the "real world" by abstraction so that questions about its *data* and the *relationships between the data* can be answered with the aid of the model
- ER model describes the "real world" with <font color="HotPink" style="font-style: italic;">entities</font> (objects), <font color="HotPink" style="font-style: italic;">attributes</font> (properties), and <font color="HotPink" style="font-style: italic;">relationships</font> (between entities)
### Entity Sets
- <font color="HotPink" style="font-style: italic;">Entities</font> are distinguishable, independent, self-contained, physically or intellectually existing concepts of the mini-world to be modeled
- Similar entities are collected in an <font color="HotPink" style="font-style: italic;">entity set</font>, e.g., the set of all books, the set of all cars, the set of all students, the set of all professors
- An entity is described by a set of pertaining properties (<font color="HotPink" style="font-style: italic;">attributes</font>), e.g., a book has an ISBN, author, publisher...
- The values of an attribute are from <font color="HotPink" style="font-style: italic;">domains</font> or <font color="HotPink" style="font-style: italic;">data types</font> such as *int*, *real*, *string*, e.g., the name of an author is of type *string*
- A *minimal set of attributes* whose values *uniquely* characterize the associated entity among all entities of an entity set is called a <font color="HotPink" style="font-style: italic;">key</font>, e.g. an ISBN number uniquely identifies a book
### Relationship Sets
- A few set-theoretic concepts and notations are needed
	- <font color="HotPink" style="font-style: italic;">Set</font>: A homogenous collection of distinct elements, e.g., set of integers, set of persons
	- <font color="HotPink" style="font-style: italic;">Type</font>: Similar term to "set", more used in CS and programming
	- <font color="HotPink" style="font-style: italic;">Cartesian (Cross) Product operator</font> "$\times$" as an example of a *type constructor*: Let A, B be sets. Then, $A \times B = \{(a,b)\;|\;a\in A ,\; b\in B\}$
	- <font color="HotPink" style="font-style: italic;">Subset</font> predicate "$\subseteq$" : $A \subseteq B \leftrightarrow \forall \; x \in A\;:\;x\in B$
	- <font color="HotPink" style="font-style: italic;">Proper Subset</font> predicate "$\subset$" : $A \subset B \leftrightarrow ((\forall \; x \in A \;:\; x \in B) \;\wedge\; (\exists \;x \in B\;:\;x\notin A)$ 
	- <font color="HotPink" style="font-style: italic;">Relation</font> as any subset of a Cartesian product: Let $A_{1}, A_{2}, ..., A_{n}$ be sets. Let $n \in N$. Then, a relation $R$ is given as $R\subseteq A_{1}\times A_{2}\times ... \times A_{n}$
- In the ER model, a <font color="HotPink" style="font-style: italic;">relationship</font> describes a connection between several entities, e.g., student Smith *attends* lecture CIS4301, teaching assistant Benson *works for* Professor Meyer
- Formally: A <font color="HotPink" style="font-style: italic;">relationship set</font> R between the entity sets $E_{1},..., E_{n}(n\in N)$ is a relation on the Cartesian product of the entity sets i.e., $$R\subseteq E_{1}\times E_{2}\times ... \times E_{n}$$
- Practical examples
	- attends_lecture $\subseteq$ students $\times$ lectures
	- works_for $\subseteq$ TAs $\times$ professors
- Attributes may characterize relationships e.g., *frequency* as an attribute for attends_lecture
- An entity set can occur more than once in a relationship set
- If there is only one entity set $E$ participating in a *binary* relationship $R(E,E)$, each of these entity sets can be assigned <font color="HotPink" style="font-style: italic;">roles</font>, e.g., (first/second lecture = predecessor/successor)$$\texttt{is\_precondition\_{of}}\subseteq\text{lectures}\times\text{lectures}$$
#### Cardinality of Binary Relationship Sets
- Needed later for creating the actual database
- The cardinality decides about the number of tables that are needed to represent the relationship (performance argument)
- Cardinalities distinguished: 1:1, 1:*m*, *m*:1, *m*:*n*
- <font color="HotPink" style="font-style: italic;">1:1-relationship</font> (one-to-one)
	- If for a binary relationship set $R(E_{1},E_{2})$ each entity in $E_{1}$ is associated with <font style="color:red">at most</font> one entity in $E_{2}$, and vice versa

![center](../zassets/Pasted%20image%2020240112101734.png)

- <font color="HotPink" style="font-style: italic;">1:many-relationship</font> 
	- If for a binary relationship set $R(E_{1},E_{2})$ each entity in $E_{1}$ is associated with any number (zero or more) of entities in $E_{2}$, and each entry in $E_{2}$ is associated with at most one entity in $E_{1}$

![center](../zassets/Pasted%20image%2020240112101921.png)

- <font color="HotPink" style="font-style: italic;">many:1-relationship</font> 
	- If for a binary relationship set $R(E_{1},E_{2})$ each entity in $E_{2}$ is associated with any number (zero or more) of entities in $E_{1}$, and each entry in $E_{1}$ is associated with at most one entity in $E_{2}$

![center](../zassets/Pasted%20image%2020240112102031.png)

- <font color="HotPink" style="font-style: italic;">many:many-relationship</font> (m:n)
	- If for a binary relationship set $R(E_1, E_2)$ each entity in $E_1$ is associated with any number (zero or more) of entities in $E_2$, and vice versa

![center](../zassets/Pasted%20image%2020240112102136.png)

