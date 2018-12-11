# Hibernate in Java

## What is Hibernate?
Object-relational mapping(ORM). High performance ORM.
* Map java class to database table & vice versa
* Data query & retrival facility
* Generate the SQL query based on the underline DB.
* Relive developer from manual result set handling and object conversion
* Make application portable to all relational db
* Enhance performance by providing different levels of cache: First level and Second level

## Dialect
Each SQL vendor has its own set of supported syntax. This is known as the dialect. In order to generate appropriate SQL query, Hibernate needs to know, for which db query needs to be generated.
Hibernate does it by org.hibernate.dialect.{DIALECT_CLASS}. Like MySQL: org.hibernate.dialect.MySQLDialect

## HQL - Hibernate Query Language
HQL is an abbreviation of Hibernate Query Language. It is SQL inspired language provided by hibernate. A developer can write SQL like queries to work with data objects.
### Java Code Example
```
//criteria
session.createCriteria(User.class).list();

//query
session.createQuery("from User").list();

//sql query
session.createSQLQuery("select count(*) from users").uniqueResult();
```
## Connection Pooking
Hibernate has its own internal connection pooling but it also supports some third-party connection pooling for production use.
* c3p0 connection pool
* Proxool connection pool
* obtaining connections from an application server, using JNDI

## Hibernate Association
What is Hibernate Association: Any Table in DB could be connected to other tables in same or other DB. And these tables could be associated with each other via some keys(Foreign..). That kind of scenario can be handled by the association.

## Hibernate Caching
Caching is one way to improve the performance of the system, as it enables fewer queries going to the database. Querying the database is always a performance impact because it is an I/O operation. And I/O operations are much slower than operations using only the applications memory. There is two type of caching.

* First Level Caching (Entity Cache)
* Second Level Caching (Query Cache)

### Cache providers
* EHCashe
* OSCashe
* Infinispan

### Caching Strategies
* Read Only - configurations
* Read-Write - This strategy is good for entities which are updated by the application
* Nonrestricted Read-Write
* Transactional

### Query Caches
Alternatively, to entities, you can store queries in a cache too. However, this query cache works close together with the second-level cache so it is only a way to attend if you utilize a second-level cache.

To use the query cache requires two additional cache regions: one for the cached query results and one for the timestamps when a table was lastly updated.

Using a query cache is only reasonable if you have queries which run often with the same parameters.
