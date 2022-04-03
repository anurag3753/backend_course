#### database
- Collection of related data

#### dbms
- application/program that manages data
- Ex. (mysql, postgresql, mongodb, node4j, dynamodb)

#### Without db
- Suppose you use file to maintain your data.
- search will be slower
- to update record also, you need to open file, you need to search record in file and then you need to close the file. Not an easy task
- After one point of time, file size will become too big. And it is not a scalable solution.

#### DBMS functionalities:
- Define : Type, structure, constraints etc
- Construct : How it is actually stored
- CRUD
- Sharing: Many users can access the data parallely
- It provides us concurrency control by default

#### different types of dbms:
- Based on the way the data is stored:
    - relational,     non-relational
        - non-relational types:
            - key-value(document type),                 graph type data store
            - mongodb, dynamodb(amazon), redis           neo4j
        - relational
            - mysql, postgresql

### relational database
- data is stored in form of tables
Advantages:
    - ACID(Atomicity, Consistency, Isolation, Durability)
    - Better support, huge community
Disadvantages:
    - Scalability Issues
    - Flexible schema is not supported
    - Difficult for querying on graph like data
        - like you need to model graph traversal in a relational dbms

### CAP Theorem (Consistency, Availability, Partition Tolerance)
- It is a concept of distributed systems
- What is a distributed database means ?
    - whenever the data is stored across multiple systems
- CAP Theorem tells that for any distributed system, you can not enforce these 3 properties together.
- consistency means :- data is consistent (ex. At any point of time, the data you have in db1 and data you have db2 will not be same). Even if you have this, then also 3 of them an not be possible together.
- availability :- data is always available. whenever you make a request, you will get the data. there is no downtime
- partition tolerance :- when you divide the data into multiple databases, then also the total system still works. this property is called partition tolerance.

## NoSQL database
- non-relational databases
- key-value type datastore/document type datastore
- Advantages:
    - highly scalable
    - flexible schema, Data is stored in form of objects
    - with graph databases, graph traversals are possible
- Disadvantages:
    - community support
    - no native support for automatic change in schema. (as there is no schema) suppose a fieldname is updated in one record. Ideally you want to update the field name for all records. but there is no such schema constraint hence you do not get this facility natively from nosql dbs
```python
# key-value type data store    (mongodb)
# Key point is fields need not to be same for multiple records. There is no such thing called as schema
{
    name : "anurag",
    class : "XII",
    branch : "cse",
    rollno : "cs10101003"
    cp_rating : "123",
    project : "database project, ai project"
}
{
    name : "arvind",
    class : "XII",
    branch : "electrical",
    rollno : "ec10101003"
    field_work : "five_years",
    labs : "vivado_lab"
}
```
- graph-like datastore (Ex. neo4j)
    - data will be stored in form of graph
    - click on neo4j free sandbox
    - open a sample database (like movies one)
        - both nodes and edges are storing data
        - edge tells the relation b/w 2 nodes . and these are directed edges

- Ex. Design social media db
    - Nodes : Person, Posts
    - Relations:
        - Friends
        - Created (person created post)
        - Like (person likes a post)
        - Comment (person comment on a post)
        - Follows (person follows another person)

### is key-value type database CACHE ?
- cache is also a key-value type datastore
- but, both are different, because purpose of cache is a faster memory. generally a cache is stored in a faster memory than a database.