# COMP - Databases

## Tables
- Name: Salaries
- Same type of data in each column
- A header in each column

| Number | Name | Salary | Years in Service |
| ------ | ---- | ------ | ---------------- |
| 1      | Joe  | $50 K  | 1                |
| 2      | Jane | $52 K  | 5                | 

## SQL
- Structured query language
- Standard language for storing, manipulating, and retrieving data
- We can use python with SQLite within Anaconda
 ```SQL
 - SELECT -- Extract data from database
 - UPDATE -- Update data from database
 - DELETE -- delete data 
 - INSERT INTO -- inserts new data into a database
 - CREATE DATABASE -- creates new database
 - ALTER DATABASE -- changes database
 - CREATE/ALTER TABLE -- create and change table
 - DROP TABLE -- delete table
 - CREATE INDEX -- creates index
 - DROP INDEX -- delete index
 ```

Examples
```SQL

SELECT column1, column2, ... FROM table_name;  
SELECT * FROM table_name;  
INSERT INTO table_name (column1, column2, column3, ...) VALUES (value1, value2, value3, ...);  
UPDATE table_name SET column1 = value1, column2 = value2, ...WHERE condition;  
DELETE FROM table_name WHERE condition;

```

- General comments 
	- SQL is not case sensitive
	- But, for formatting, SQL commands should be written in ALL CAPS
	- We don’t need semicolons at the end of SQL statements, but the way we’re using it, it isn’t needed. 

## Cursors
- A database cursor is a mechanism that allows you to move throughout the database. 
- Allows you to process while you traverse

## Linking Python and SQLite
```python
import sqlite3

conn = sqlite3.connect('Weather.db') # Connect to a database called
									 # Weather.db

cursor = conn.cursor() # Create a cursor

# Execute SQL Commands
# this command goes on to create the columns of the database
cursor.execute('''
	CREATE TABLE WEATHER (          
	ID int primary key,
	CITY char(50),
	STATE char(2),
	TEMPERATURE real,
	CONDITION char(50))
	''')

conn.commit() # Save the changes
conn.close()  # Close the database

```

## Example Time!
[[COMP - L12 Database Example 1]]
[[COMP - L12 Database Example 2]]