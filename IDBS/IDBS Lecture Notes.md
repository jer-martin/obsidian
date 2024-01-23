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

### Weak Entity Sets
- Existence dependent (that is, <font color="HotPink" style="font-style: italic;">weak</font>) <font color="HotPink" style="font-style: italic;">entity set</font>
	- Assumption so far: entities exist autonomously and can be uniquely identified within an entity set by their key attributes (<font color="HotPink" style="font-style: italic;">strong entity set</font>)
	- In reality, there are also *weak* entities that do not have sufficient attributes to form a key. These entities are
		- dependent in their existence from one another, superior entity
		- can be uniquely identified only in combination with the key of a superior strong entity
	- But: Examples of weak entity sets are rare and thus difficult to find
	- Superior strong entity set is called <font color="HotPink" style="font-style: italic;">identifying</font> or <font color="HotPink" style="font-style: italic;">owner entity set</font>
	- Graphical notation is double rectangle
- An <font color="HotPink" style="font-style: italic;">Identifying relationship set</font> $R$ associates a *weak entity set* $E_{1}$ with an *identifying entity set* $E_{2}$  such that the key of $E_{1}$ comprises the key of $E_{2}$ and *all* entities of $E_{1}$ are involved in a relationship to an entity in $E_{2}$ (total participation, see below)
	- Relationship from the weak entity set to the superior set has usually an $m:1$ cardinality and more seldom a $1:1$ cardinality
	- Graphical notation is double diamond
- **Example**
![center](../zassets/Pasted%20image%2020240117095725.png)
	The weak entity set *room* has a <font color="HotPink" style="font-style: italic;">total participation</font> (indicated by the double edge) in the identifying relationship set *lies_in*

### Total Participation
- <font color="HotPink" style="font-style: italic;">Total (mandatory) participation</font> of an entity set in a relationship
	- *All* entities of an entity set $E_{1}$ are associated with <font style="color:crimson">at least </font>one or other entity set $E_{2}$ by a relationship set $R$
	- This holds, in particular, for weak entity sets
- **Example**
![center](../zassets/Pasted%20image%2020240117100037.png)

### Min-Max Notation
- More precise characterization and constraint the cardinality of a relationship set by the $\text{(min, max)}$ notation
- For each entity set $E$ participating in a relationship set $R$
	- the value *min* expresses that each entity of $E$ participates in *at least min* relationships in $R$
	- the value *max* expresses that each entity of $E$ participates in *at most max* relationships in $R$
- Special cases
	- min = 0; an entity does not have to be in a relationship (optional)
	- max = \*; an entity may be in a relationship arbitrarily many times

### Multivalued Attributes
- <font color="HotPink" style="font-style: italic;">Optional attribute</font>: Minimal cardinality is equal to 0
- <font color="HotPink" style="font-style: italic;">Simple attribute</font>: Cardinality is equal to 1
- <font color="HotPink" style="font-style: italic;">Prescribed attribute</font>: Minimal cardinality is equal to 1
- <font color="HotPink" style="font-style: italic;">Multivalued attribute</font>: Maximal cardinality is equal to a natural number *n*
- **Example**
![center](../zassets/Pasted%20image%2020240117100844.png)

### Composite Attributes
- Grouping of attributes of the same entity set or relationship set which are closely related
- Hierarchy of closely related attributes
- Antonym: simple attribute
- **Example**
![center](../zassets/Pasted%20image%2020240117101039.png)

### Derived Attributes
- Attributes that can be derived from one or more attributes
- Antonym: <font color="HotPink" style="font-style: italic;">base</font>/<font color="HotPink" style="font-style: italic;">stored attribute</font>
- Graphical representation is dotted ellipse
- **Example**
![center](../zassets/Pasted%20image%2020240117101233.png)
- If used in databases
	- They have to be updated regularly, can be expensive
	- Better to avoid and compute if needed
	- In the example above, *age* can be derived from the difference of *system date* and *birthdate*

### Entity Set vs. Attribute
- Should *address* be an attribute of *person* or its own entity set connected to *person* by a relationship set?
- **Example**
![center](../zassets/Pasted%20image%2020240117101510.png)
- Both ways are feasible but the attribute variant can introduce redundancy if several people live at the same address
- For the entity variant it makes sense to introduce an identifier for entity set *address*
- Similar situation for relationship sets: Employee works in a department for a *single* period
![center](../zassets/Pasted%20image%2020240117101636.png)
- Several values of the descriptive attributes for each instance of this relationship: Employee works in a department for *several* periods
![center](../zassets/Pasted%20image%2020240117101732.png)

## Generalization
- **Objectives**
	- Abstraction at the set level in order to not overwhelm with details but to achieve a more understandable and more concise structuring of entity sets
	- Abstraction at the instance level in order to model similar entities by a common entity set
- Factoring (extracting) properties (attributes, relationships) of similar entity sets (<font color="HotPink" style="font-style: italic;">subclasses, subtypes, categories</font>) to a common <font color="HotPink" style="font-style: italic;">superclass</font> (<font color="HotPink" style="font-style: italic;">supertype</font>)
- Properties that cannot be extracted remain with the respective subclass i.e., the subclass is a <font color="HotPink" style="font-style: italic;">specialization</font> of the superclass
- <font color="crimson" style="font-weight: bold;">Inheritance</font> as the key concept of <font color="crimson" style="font-weight: bold;">generalization</font>: a subclass inherits all properties of its superclass
- Entities of a subclass are implicitly considered as entities of the superclass, therefore the relationship <font style="color:HotPink">is-a</font> (hexagon) is used in the E-R diagrams
- Two special cases of specialization
	- <font color="HotPink" style="font-style: italic;">Disjoint/overlapping specialization</font>: All subclasses of a superclass are pairwise disjoint/overlapping
	- <font color="HotPink" style="font-style: italic;">Total specialization</font>: The superclass does not contain explicit elements, but is only given by the union of its subclasses (antonym: <font color="HotPink" style="font-style: italic;">partial specialization</font>)

## Main Steps for Designing E-R Diagrams in the Small
1. Identify (weak) entity sets
2. Draw (weak) entity sets
3. Identify (key) attributes of (weak) entity sets
4. Draw (key) attributes of (weak) entity sets
5. Identify (identifying) relationship sets
6. Draw (identifying) relationship sets
7. Identify attributes of (identifying) relationship sets
8. Draw attributes of (identifying) relationship sets
9. Insert cardinalities

# Relational Data Model
## Introduction
- Commercial DBMSs such as Oracle, Informix, SQL Server, Sybase, DB2 as well as public domain DBMS such as PostgreSQL and MySQL are based on the relational data model
#### Main reasons for the success of the relational data model
- Flat two-dimensional tables (relations) as the simple underlying data structure
- "Flat" means: No nested complicated structures, that is, attribute fields may *not* contain values such as tables, arrays, lists, trees, etc, but only atomic values
- <font color="HotPink" style="font-style: italic;">Set oriented</font> processing of data in contrast to <font color="HotPink" style="font-style: italic;">record oriented</font> processing prevailing til then
	- Compare to a programming language example: The task is to copy an array A of integers to an array B
	- Usually performed element-wise by a record oriented loop: for (int i = 0; i < n; ++i) B\[i] = A\[i]; // “=” is the assignment operator
	- Desired set-oriented syntax: B = A;
	- Only possible in object-oriented programming languages by overloading the assignment operator
- Simple comprehensibility for even the unskilled user
- Very good performance for standard, alphanumerical database applications
- Existence of a mature, formal theory (in contrast to other data models) in particular with respect to the design of relational databases and with respect to an efficient processing of user queries

## Model Definition
- Given $n$ <font color="HotPink" style="font-style: italic;">domains</font> $D_{1},D_{2},...,D_{n}$
	- The term "domain" is a database term for the term "data type"
	- Examples for domains: data types *integer*, *string\[20]*, *real*, *bool*, *date*,...
	- Domains need not be disjoint, i.e., $D_{i}=D_{j}$ is admissible for $i\ne j$
	- Domains may only contain <font color="HotPink" style="font-style: italic;">atomic</font> values, they must not be structured
- A <font color="HotPink" style="font-style: italic;">relation (instance)</font> $r_{R}$ is defined as a subset of the Cartesian product of $n$ domains: $$r_{R}\subseteq D_{1}\times D_{2} \times ... \times D_{n}, \;\;\; r_{R}\text{ finite}$$
- $r_R$ is an <font color="HotPink" style="font-style: italic;">occurrence (instance)</font> of a pertaining <font color="HotPink" style="font-style: italic;">relation schema</font> $R$ (analogously to the programming language notions of *variable* and *type*)
- An element of the set $r_{R}$ is called a <font color="HotPink" style="font-style: italic;">tuple</font>, a tuple has the <font color="HotPink" style="font-style: italic;">arity</font> or <font color="HotPink" style="font-style: italic;">degree</font> $n$
- Example: Assume domains $D_{1}=\{a,b,c\}, D_{2}=\{0,1\}$
	- Cartesian product: $D_{1}\times D_{2}= \{(a,0),(a,1),(b,0),(b,1),(c,0),(c,1)\}$
	- Examples of instances: $r_{1}=\{(a,0),(b,0),(c,0),(c,1)\},r_{2}=\{(a,0)\},r_{3}=\emptyset$ 
- Number of elements of $D_{1}\times D_{2}:|D_{1}\times D_{2}|=|D_{1}|*|D_{2}|$ where $|A|$ denotes the (finite) cardinality, that is, the number of elements, of a set $A$
- Difference between a relation and a function
	- A <font color="HotPink" style="font-style: italic;">function</font> $f$ between two sets $A$ and $B$ (notation: $f : A\rightarrow B$) is a relation such that each element in $A$ is related (mapped) to exactly one element in $B$
![center](../zassets/Pasted%20image%2020240122094839.png)
- Distinction between the <font color="HotPink" style="font-style: italic;">schema</font> of a relation $R$, which is given by the $n$ domains (data types), and the current <font color="HotPink" style="font-style: italic;">instance</font> of this relation schema, which is given by a subset of the Cartesian product
- Schema analogously to the programming language notion of *type*
- A <font color="HotPink" style="font-style: italic;">relation schema</font> $R$, denoted by $R(A_{1},A_{2},...,A_{n})$ consists of the <font color="HotPink" style="font-style: italic;">relation name</font> $R$ and a list of <font color="HotPink" style="font-style: italic;">attributes</font> $A_{1},A_{2},...,A_{n}$
- Each <font color="HotPink" style="font-style: italic;">attribute</font> $A_{i}$ is the name of a role played by domain $D_{i}$ in the relation schema $R$
	- $D_{i}$ is also the domain (type) of $A_{i}$
	- Notation: $D_{i}=\text{dom}(A_{i})$
- For the schema $R(A_{1},...,A_{n})$ holds: $r_{R}\subseteq \text{dom}(A_{1}:D_{1},...,A_{n}:D_{n})$
- Because we often do *not* make a clear distinction between the meta level (schema) and the instance level (occurrence), we also denote relation instances with the letter $R$
- Representation of a relation as *tables* with *rows* (tuples) and *columns*
	- R is a *table name*, A and N are *attributes* and have the function of *column* names, each horizontal line represents a *row* or tuple
![center](../zassets/Pasted%20image%2020240122095620.png)
- <font color="HotPink" style="font-style: italic;">Database schema</font>: collection of relation schemas (more static character, changes rarely)
- <font color="HotPink" style="font-style: italic;">Database</font>: collection of the current relation instances (more dynamic character, changes more often)
- The definitions so far allow for instances that cannot exist in reality
	- Example: An attribute *age* of type *integer.* Values such as -34 and 18792 are syntactically correct but make no sense semantically
	- Therefore it makes sense to restrict the instances by suitable semantical conditions called <font color="HotPink" style="font-style: italic;">integrity constraints</font>

## Features of Relations
- Difference between a *set* and a *list*
	- Set is *unordered* homogenous collection of values
		- $\{3,9,6,4,1,2\}$
		- Duplicates not possible, sorting is not possible
	- A list is an *ordered* homogenous collection of values
		- $<5,2,1,9,17>$
		- Duplicates are possible, sorting is possible
- A relation is defined as a *set of tuples*
	- Tuples in a relation aren't ordered, order isn't relevant
	- Defining a relation as a list of tuples would allow sorting
	- Note: rows in a table are ordered
- Relations are based on a <font color="HotPink" style="font-style: italic;">set model</font>, relational tables (SQL Tables) are based on a <font color="HotPink" style="font-style: italic;">list model</font>
- A tuple is defined as a *list* of $n$ attribute values
	- Attribute values in a tuple are ordered
	- But the order of attributes and their values is not semantically relevant
	- It is only necessary to maintain the implicit, position based correspondence between attributes and their values: Given the attributes $(A_{1},...,A_{n})$ and the tuple $(v_{1},...,v_{n})$, the value $v_{i}$ corresponds to the attribute $A_{i}$
	- A tuple $t$ could be defined as a *set* of (attribute, attribute value) pairs, that is, $t=\{(A_{1},v_{1}),(A_{2},v_{2}),...,(A_{n},v_{n})\}$ where the $A_{i}$ are attributes and the $v_{i}\in \text{dom}(A_{i})$
- Attribute values in tuples
	- Each attribute value in a tuple is <font color="HotPink" style="font-style: italic;">atomic (indivisible)</font>, that is, no composite or multivalued attributes are allowed <font color="HotPink" style="font-style: italic;">(first normal form)</font>
	- Values of attributes in a tuple can be unknown: use of a special value <font color="HotPink" style="font-style: italic;">null</font> in this case

### Keys
- Analogously to the notion of key in the E-R model
- Due to the set property of relations, there are no two tuples that have the same combination of values for all their attributes
- Let us assume $R(A_{1},A_{2},...,A_{n})$ and let $X \subseteq \{A_{1},A_{2},...,A_{n}\}$ for $t\in r_{R}$ let $t[X]$ be the projection of $t$ to the attributes in $X$. $X$ is called <font color="HotPink" style="font-style: italic;">key</font> if the following two conditions are fulfilled:
	1. <font color="HotPink" style="font-style: italic;">Uniqueness</font>: For all relation instances $r_{R}$ of $R$ holds: $$\vee t_{1},t_{2}\in r_{R}:t_{1}[X]=t_{2}[X]\rightarrow t_{1}[X]\ne t_{2}[X]$$
	2. <font color="HotPink" style="font-style: italic;">Minimality</font>: There is no $Y\subset X$ so that uniqueness is fulfilled
- <font color="HotPink" style="font-style: italic;">Candidate keys</font>: Several possible keys, one of them is selected as the <font color="HotPink" style="font-style: italic;">primary key</font>, the others do not lose their key property and can be used for creating indices on them
- Examples: UFID and SSN are candidate keys for students, ISBN and article numbers are candidate keys for books