## Welcome!
- Database systems are software systems for managing large volumes of data
- Industry sector valued at more than US$100 Billion annually
- *Relational database systems* still dominate the sector
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

