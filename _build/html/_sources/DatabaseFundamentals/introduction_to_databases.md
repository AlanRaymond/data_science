# Introduction to databases

A database is a collection of information that reflects some aspect of a real world system. Like a real world system, the information is meaningful.

Information has meaning (logical sets of possible values, values have explicit units, and related by real world phenomena).

WHen analysing a problem, it is useful to work within a defined scope, and so databases will be built for a specific purpose with an implicit scope. When working with a database, it should be understood that there will be inherent limitations to the applications of the data within.

A database system is a set of tools that enable the user to effectively manage the database.
To manage a database we need to:
* Create the framework: define constraints and create the database;
* Store/populate the framework with data, and;
* Extract information (query) to answer targetted questions.

A database is distinguished over a file system in its ability to be queried effectively. Storing data does not provide value if it cannot be accessed.

## Databasing for a cause
Different businesses will have different requirements 
* A retail business needs to store sales transactional data stored in real-time and fast. A delay in reading/writing could lead to inconsistent information in the database.
* A database that stores medical information needs to ensure that the privacy of the data is protected. Database management systems provide the ability to set user restrictions.
* In applications where the amount of 

## Benefits of a database approach
Databases make data storage and organisation easy and efficient.

Helps control data redundancy. 


## Database technologies

## Relational database models

### Definitions
Relation: 
Relationship: 
Primary Key: Most efficient set of attributes that can uniquely identify a tuple (entry) in a relation. Denoted by underline.
Foreign Key: An attribute's value for a relation. Foreign keys establish a relationship between two or more relations (tables).
Entity Integrity Constraint: For an entity to exist, it must be identifiable (primary key is not NULL) and unique (no duplicate of primary key).
Referential Integrity Constraint: There must be consistency between tuples of two relations joined by a relationship (foreign key must be valid).

THere are three strategies to preserve referential integrity as relations are ammended.
RESTRICTED: If loss of integrity will occur if table is ammended, the ammendment is rejected.
CASCADE: Ammending a relation will also ammend all relations referenced through relationships (i.e. deleting an entry in one table will deleted entries in another if a foreign key was used).
NULLIFIES: Foreign key is set to NULL in all matching references, and then the target is then updated.

![Data Integrity Task](images/data_integrity_task.png)

1. What entity integrity constraints exist in the data?
* Student relation, George Washington does not have a 'Student ID'.
* Lecturer relation, 'Lecturer ID' Q234 is not unique.
* Student relation, Chen Ying appears twice in the relation, and has two different 'Student ID's. This is not a constraint, but it does not preserve data integrity.

2. What referential integrity constraints exist in the data?
* Subject relation, foreign key 'P534' in Lecture ID does not exist in the Lecturer relation.
* Enrolment relation, foreign key 'CDE-7' in Student ID does not exist in the Student relation.

3. Assume the subject BUA5FMA is no longer offered. What will the relation tables look like if the preservation effect is 'cascade'?

