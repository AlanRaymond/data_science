# ER Modelling
What, and how many, tables do we require for the use case?
How do we establish the relationships between tables?

AN entity is represented by a name in a rectangular box. An entity is usually an object or event in the real world, i.e. an employee.
Each entity has a set of attributes that describe it. Each attribute is represented by an oval. Each attribute has a set of legal values.
THere are different types of attributes:
simple/atomic: only one value alllowed
composite: consisting 
multivalued: denoted by double oval.
derived: calculated or derived from another attribute i.e. age derived from a date of birth and current date


Relationships are an association between entities.
degrees of relationships denote the number of entities participating in a relationship

cardinality: The number of entity instances in a relationship instance. THere are three times in binary relationships (degree 2): 1:1, 1:N, M:N.
Types of participation:
Total - existence is totally dependent on another entity.
Partial - entity can exist without further context.

relationships can have attributes. THis only makes sense when the cardinality is M:N. Otherwise, it may make more sense to add this relationship attribute to one of the entities.

weak entity: entity exists conditionally on the existence of one or more other entities. Primary key is partially or totally derived from the owner entity. Denoted by a double lines rectangular/diamond. Use of a cascade.
If in doubt, design the entity as a strong entity.

## steps to draw an ER diagram
* Identify entities in the required system and represent them graphically by a rectangle.
* Search for relationships between the entities and represent them graphically by a diamond.
* Identify constrants on relationships (all relationships).
    * for cardinality, use 1, N or M, and (min,max).
    * for participation, total is shown as double line, partial with a single line.
* Identify all attributes and underline primary keys.


## steps to design relational database (top-down)
Step 1: Regular Entities
Step 2: Weak Entities
Step 3: 1-to-1 relationships
Step 4: 1-to-N relationships
    Foreign key goes in the table with the many relationship - removes ambiguity
Step 5: N-to-N relationships
    A relation is created for the relationship with keys to join the two tables logically
Step 6: Multivalued attributes
    For each multivalued attribute, create a new relation and key it to the original entity
Step 7: N-ary (N>2) relationships
    Similar to Step 5
Step 8: Final table list

Example
![Real Estate Agency E-R diagram](/images/database_design_realestateagency.png)

Step1:
MAINTENANCE(maintenanceID, date, type, cost)
OWNER(ownerID, ownerName, ownerAddress)
PROPERTY(buildingID, address, value)
ACCOUNT(ACReceiptID, dateofPayment, typeofAccount, amountPaid)
TENANT(tenantID, firstName, familyName, address, phoneNumber)

Step2: No weak entities

Step3: No 1-to-1 relationships

Step4:
MAINTENANCE(maintenanceID, date, type, cost, propertyID)
OWNER(ownerID, ownerName, ownerAddress)
PROPERTY(buildingID, address, value, ownerID)
ACCOUNT(ACReceiptID, dateofPayment, typeofAccount, amountPaid, tenantID, propertyID)
TENANT(tenantID, firstName, familyName, address, phoneNumber)

Step5:
MAINTENANCE(maintenanceID, date, type, cost, propertyID)
OWNER(ownerID, ownerName, ownerAddress)
PROPERTY(buildingID, address, value, ownerID)
ACCOUNT(ACReceiptID, dateofPayment, typeofAccount, amountPaid, tenantID, propertyID)
TENANT(tenantID, firstName, familyName, address, phoneNumber)
RENT(tenantID, propertyID)

Step6: No mulitvalued attributes

Step7: No N-ary relationships

Step8:
MAINTENANCE(maintenanceID, date, type, cost, propertyID)
OWNER(ownerID, ownerName, ownerAddress)
PROPERTY(buildingID, address, value, ownerID)
ACCOUNT(ACReceiptID, dateofPayment, typeofAccount, amountPaid, tenantID, propertyID)
TENANT(tenantID, firstName, familyName, address, phoneNumber)
RENT(tenantID, propertyID)


# EER Modelling
Enhanced Entity Relationship modelling includes all the modelling concepts in ER, with some additional concepts:
* Subclass/Superclass entities
* Specialisation/generalisation relationships
* Union types (categories) relationships