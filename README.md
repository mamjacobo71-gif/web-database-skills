# Web Database Skills Project

## Overview
This project aims to showcase skills in working with various web databases, specifically PostgreSQL, MySQL, MongoDB, and SQLite. Each section includes Python examples demonstrating CRUD (Create, Read, Update, Delete) operations and basic query optimization techniques.

### PostgreSQL
- **CRUD Operations in Python**:
  ```python
  import psycopg2

  # Connect to PostgreSQL database
  conn = psycopg2.connect(host='localhost', database='mydatabase', user='myuser', password='mypassword')
  cursor = conn.cursor()

  # Create
  cursor.execute("INSERT INTO mytable (column1, column2) VALUES ('value1', 'value2')")

  # Read
  cursor.execute("SELECT * FROM mytable")
  rows = cursor.fetchall()

  # Update
  cursor.execute("UPDATE mytable SET column1='new_value' WHERE column2='value2'")

  # Delete
  cursor.execute("DELETE FROM mytable WHERE column2='value2'")

  conn.commit()
  cursor.close()
  conn.close()
  ```
- **Query Optimization**:
  Use indexes to speed up queries:
  ```sql
  CREATE INDEX idx_column1 ON mytable (column1);
  ```

### MySQL
- **CRUD Operations in Python**:
  ```python
  import mysql.connector

  # Connect to MySQL database
  conn = mysql.connector.connect(
      host='localhost', database='mydatabase', user='myuser', password='mypassword')
  cursor = conn.cursor()

  # Create
  cursor.execute("INSERT INTO mytable (column1, column2) VALUES ('value1', 'value2')")

  # Read
  cursor.execute("SELECT * FROM mytable")
  rows = cursor.fetchall()

  # Update
  cursor.execute("UPDATE mytable SET column1='new_value' WHERE column2='value2'")

  # Delete
  cursor.execute("DELETE FROM mytable WHERE column2='value2'")

  conn.commit()
  cursor.close()
  conn.close()
  ```
- **Query Optimization**:
  Consider using EXPLAIN to analyze query performance:
  ```sql
  EXPLAIN SELECT * FROM mytable WHERE column1='value1';
  ```

### MongoDB
- **CRUD Operations in Python**:
  ```python
  from pymongo import MongoClient

  # Connect to MongoDB database
  client = MongoClient('mongodb://localhost:27017/')
  db = client['mydatabase']

  # Create
  db.mytable.insert_one({'column1': 'value1', 'column2': 'value2'})

  # Read
  rows = db.mytable.find()

  # Update
  db.mytable.update_one({'column2': 'value2'}, {'$set': {'column1': 'new_value'}})

  # Delete
  db.mytable.delete_one({'column2': 'value2'})
  ```
- **Query Optimization**:
  Use indexes for better performance:
  ```python
  db.mytable.create_index([('column1', 1)])
  ```

### SQLite
- **CRUD Operations in Python**:
  ```python
  import sqlite3

  # Connect to SQLite database
  conn = sqlite3.connect('mydatabase.db')
  cursor = conn.cursor()

  # Create
  cursor.execute("INSERT INTO mytable (column1, column2) VALUES ('value1', 'value2')")

  # Read
  cursor.execute("SELECT * FROM mytable")
  rows = cursor.fetchall()

  # Update
  cursor.execute("UPDATE mytable SET column1='new_value' WHERE column2='value2'")

  # Delete
  cursor.execute("DELETE FROM mytable WHERE column2='value2'")

  conn.commit()
  cursor.close()
  conn.close()
  ```
- **Query Optimization**:
  Use the `ANALYZE` command to collect statistics about tables:
  ```sql
  ANALYZE;
  ```

## Conclusion
This project serves as a comprehensive guide for web database skills, illustrating how to implement basic operations and optimize queries effectively across different database systems.