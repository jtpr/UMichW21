# COMP - L12 Databases Example 2

Import this table into SQLite using python:

| ID  | Dog Breed | Weight | Speed |
| --- | --------- | ------ | ----- |
| 1   | Chihuahua | 5      | 8     |
| 2   | Corgi     | 15     | 6     |
| 3   | Greyhound | 65     | 12    | 


```python
import sqlite3 as sql # Bring in SQL3

conn = sql.connect('Dogs.db') # Create dogs datable
```


```python
cursor = conn.cursor()
cursor.execute('DROP TABLE IF EXISTS DOGS')
```




    <sqlite3.Cursor at 0x1e91d762490>




```python
cursor.execute('''
    CREATE TABLE DOGS (          
    ID int primary key,
    DOG_BREED char(50),
    WEIGHT real,
    SPEED real)''')
```




    <sqlite3.Cursor at 0x1e91d762490>



Add data into the table according to the given table


```python
cursor.execute("INSERT INTO DOGS (ID, DOG_BREED, WEIGHT, SPEED) \
      VALUES (1, 'Chihuahua', 5.0, 8.0)")
cursor.execute("INSERT INTO DOGS (ID, DOG_BREED, WEIGHT, SPEED) \
      VALUES (2, 'Corgi', 15.0, 6.0)")
cursor.execute("INSERT INTO DOGS (ID, DOG_BREED, WEIGHT, SPEED) \
      VALUES (3, 'Greyhound', 65.0, 12.0)")

conn.commit() # Save changes
```

I can then print out my database:


```python
cursor = conn.execute("SELECT ID, DOG_BREED, WEIGHT, SPEED from DOGS")

for row in cursor:
    print("ID = ", row[0])
    print("DOG BREED = ", row[1])
    print("WEIGHT = ", row[2])
    print("SPEED = ", row[3], "\n")
```

    ID =  1
    DOG BREED =  Chihuahua
    WEIGHT =  5.0
    SPEED =  8.0 
    
    ID =  2
    DOG BREED =  Corgi
    WEIGHT =  15.0
    SPEED =  6.0 
    
    ID =  3
    DOG BREED =  Greyhound
    WEIGHT =  65.0
    SPEED =  12.0 
    
    

Now, delete row 1, add row 4 and change the speed of the greyhound to 15.5:

| ID  | Dog Breed | Weight | Speed |
| --- | --------- | ------ | ----- |
| 2   | Corgi     | 15     | 6     |
| 3   | Greyhound | 65     | 15.5  | 
| 4   | Lab       | 75     | 9     |


```python
# Delete the chihuahua row

conn.execute("DELETE from DOGS where ID = 1;")
conn.commit()

# Add in row 4
cursor.execute("INSERT INTO DOGS (ID, DOG_BREED, WEIGHT, SPEED) \
      VALUES (4, 'Lab', 75.0, 9.0)")
conn.commit()

# Change the speed of the greyhound
conn.execute("UPDATE DOGS set SPEED = '15.5' where ID = 15.5")
conn.commit()

cursor = conn.execute("SELECT ID, DOG_BREED, WEIGHT, SPEED from DOGS")
# Print resulting data:
for row in cursor:
    print("ID = ", row[0])
    print("DOG BREED = ", row[1])
    print("WEIGHT = ", row[2])
    print("SPEED = ", row[3], "\n")
```

    ID =  2
    DOG BREED =  Corgi
    WEIGHT =  15.0
    SPEED =  6.0 
    
    ID =  3
    DOG BREED =  Greyhound
    WEIGHT =  65.0
    SPEED =  12.0 
    
    ID =  4
    DOG BREED =  Lab
    WEIGHT =  75.0
    SPEED =  9.0 
    
    
![[COMP - L12 Database Example 2.ipynb]]