# Chapter 1: The world of DB Systems

You: Request info from a website 
Database of that website: serving the information you request

Database is empowered by DBMS or DB systems

## 1.1 Evolution of DBMS
### DBMS:
Create and preserve large amount of data over a long period of time
Manage data: update, insert, delete

More specifically, DBMS can:
- allow user to create new DB and specify their schemas using a specialized DDL
- give user the ability to query the data and modify the data using an appropriate language often called a query language or DML
- Support the storage of very large amount of data (terabytes or more) over a long period of time, allowing efficient access to the data for queries and database modifications
- enable durability, the recovery of the DB in the face of failures, errors of many kinds or intentional misuse
- control access to data from many users at once
	* Isolation: without allowing unexpected interactions among users
	* Atomicaity: without actions on the data to be performed partially but not completely


### This book contains: 
- design BD system
- write program in various language associated with a DBMS
- implement a DBMS

### What is DB?
a collection of information over a long period of time

### What is a query?
a database lingo for a question about the data

### Relational DB systems 
Father: Ted codd in 1970

He proposed that DBS should present the user with a view of data organized as table called *relations*. Behind the scenes, there might be a complex data sturcture that allowed rapid responde to a variety of queries. 

Unlike the programmers for earlier DBS, the programmers of a relational DBS would not be concerned with the storage structure.

Queries are written in a very HHL. SQL is the most important query language based on the relational model.

### Add OO features to relational model after 1990

### smaller and smaller systems
#### 'Large computer system' to 'a single disk'
Originally, DBMS's were large, expensive software system running on LARGE COMPUTER because to store a gigabyte of data required a LAGER COMPUTER SYSTEM. Today, hundreds of gigabytes fit on A SINGLE DISK, and it is quite feasible to run a DBMS on a personal computer. Thus, DB SYSTEMS based on relational model have become avilable even for small machines, and they are beginning to appear as a common tool for COMPUTER APPLICATIONS, much as spreadsheets did before them.

#### A collection of XML documents 
Another important trend is the use of documents using XML (eXtensible Modeling Language). Large collections of small documents can serve as a database. The methods of querying and manipulating them are different from those used in relational systems.

### Information Integration and Data Warehouse
#### An old problem 
Join information contained in many related database is troublesome caused by different DBMS or/and different structures for information. What's more, same term/attribute can mean differently (or different terms means the same thing) in different DBMS. To make things worse, the existance of legacy applications using each of these databases makes it almost impossible to scrap them.

#### Solutions:
1. data warehouses: information from many legacy DB is copied periodically, with the appropriate translation, to a central DB.
2. middleware: support an integrated model of the data of the various databases, while translating between this model and the actual models used by each DB.

## 1.2 Overview of a DBMS

### Two Sources of Commands to DBMS:
#### From User: people or programs that request or modify data 
Users or programs uses DML to query or modify the data. The actions are handled by the following 2 separate subsystems.
##### Answering the Query

##### Transaction Processing
Query --> QUERY COMPLIER --> query plan(sequence of actions the DBMS will perform to answer the query) 
      --> EXECUTION ENGINE --> a sequence of requests for small pieces of data (typically records or tuples of a table)
      --> RESOURCE MANAGER (index/file/record manager) that knows about **data files(holding relations), the format and size of records in those file, and index file(help find elements of data files quickly**) --> page commands/disk block commands(that request for data) 
      --> BUFFER MANAGER --> read/write pages
      --> STORAGE MANAGER --> brings appropriate portions of the data from the secondary storage(disk) to the main-memory buffer so that the buffer manager can access it.

The 'page' or 'disk block' is the unit of transfer between buffers and disk 




#### From DB Administrator(DBA): a person (or persons) responsible for the structure or schema of the DB
1. simpler to process
2. DBA decide schema of the DB: 
- relations/tables (*structure of BD*)
- types and domains for attributes(*Constraints*)
3. DBA needs special authoraity to execute *'schema-altering commands(DDL)'*
4. DDL commands are parsed by a *DDL processor* and passed to the *execution engine*, which then goes through the *index/file/record manager* to alter the *'metadata(schema information for the database)'*




