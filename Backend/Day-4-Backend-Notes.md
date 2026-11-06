**What is an Entity?**
Entity is a Java class that represents a table in a database.

For example, imagine our MySQL database has a table called movies.
id	title
1	Interstellar
2	Inception
3	Oppenheimer

*We need a Java class that represents this table. That class is called a Movie Entity.*

In simple words:
- Database table → movies
- Java class → Movie
- Table row → One Movie object
- Table column → Entity field

**What are JPA and Hibernate?**
These three terms are important:
- JPA: A Java specification that defines how Java objects should be mapped to database tables.
- Hibernate: A popular implementation of JPA. It performs the actual database operations.
- Spring Data JPA: Makes database operations easier by providing repository interfaces.
Think of it this way:

JPA = Rules
Hibernate = Worker that follows those rules
Spring Data JPA = Convenient tools that make working with the database easier


*Entity vs DTO*
DTO                                                  	Entity
Transfers data	                                        Represents database data
Used for API requests/responses	                        Used for database mapping
Doesn't directly represent a table	                    Maps to a database table
Example: MovieRequest	                                Example: Movie

