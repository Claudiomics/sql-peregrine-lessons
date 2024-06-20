# Creating Databases and Tables

Table of Contents

1. [Data Types](#data-types)
2. [Primary and Foreign Keys](#primary-and-foreign-keys)
3. [Constraints](#constraints)
4. [CREATE](#create)
5. [INSERT](#insert)
6. [UPDATE](#update)

## Data Types

Bool - T/F
Character - char, varchar, text
Numeric - int, float
Temporal - date, time, timestamp, interval

UUID - Universally unique identifyer
Array - Stores an array of strings, numbers etc.
JSON - file type
Hstore key-value pair
Special types such as network address and geometric data

## Primary and Foreign Keys

A primary key is a column or group of columns used to identify a row uniquely in a table.

Primary and foreign keys typically make good column choices when joining two or more tables together.

When creating tables and defining columns, contraints can be used to define a column as a primary key, or attaching a foreign key relationship to another table.

<img width="265" alt="Screenshot 2024-06-20 at 14 33 51" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/3a6f5c1a-e126-4ccf-a46f-3ff7046c75de">

## Constraints

These are the rules enforced on data columns in a table, and prevent invalid data from being entered in the database. 

This ensures the accuracy and reliability of the data in the database, and are divided into two main categories:

1. Column Constraints
2. Table Constraints

A few common constraints include:

NOT NULL - Ensures column has no nulls.
UNIQUE - Ensures all values in a column are different.

PRIMARY Key - Uniquely identifies each row/record in a database table.
FOREIGN Key - Constrains data based on columns in other tables.

CHECK Constraint - ensures all values in a column satisfy certain conditions.

EXCLUSION Constraint - if any 2 rows are compared on the specified column or expression using the specified operator, not all of these comparisons will return TRUE.

## CREATE

General syntax to create a table:

CREATE TABLE table_name(
  column_name TYPE column_constraint,
  column_name TYPE column_constraint,
  table_constraint table constraint
  )
INHERITS existing_table_name

e.g. 
CREATE TABLE players( 
  player_id SERIAL PRIMARY KEY,
  age SMALLINT NOT NULL
  );

e.g.2. Create a new database and run the following code in a new query window:

CREATE TABLE account(
  user_id SERIAL PRIMARY KEY,
  username VARCHAR(50) NOT NULL,
  password VARCHAR(50) NOT NULL,
  email VARCHAR(250) UNIQUE NOT NULL,
  created_on TIMESTAMP NOT NULL,
  last_login TIMESTAMP
);

<img width="858" alt="Screenshot 2024-06-20 at 13 30 24" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/99d3bfe2-2a02-4705-ba36-1f0f9d2f3050">

CREATE TABLE job(
  job_id SERIAL PRIMARY KEY,
  job_name VARCHAR(200) UNIQUE NOT NULL
);

CREATE TABLE account_job(
  user_id INTEGER REFERENCES account(user_id),
  job_id INTEGER REFERENCES job(job_id),
  hire_date TIMESTAMP
);

<img width="796" alt="Screenshot 2024-06-20 at 13 33 05" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/1ff782e6-1e7a-4f31-896a-b3f4d862fdfe">

## INSERT

Adds rows to a table.

Syntax:
INSERT INTO table(column1, column2, ...)
VALUES
  (value1, value2, ...)
  (value1, value2, ...);

Syntax for adding rows from another table:

INSERT INTO table(column1, column2, ...)
SELECT column1, column2, ...
FROM another table
WEHRE condition;

e.g. 

INSERT INTO account(username, password, email, created_on)
VALUES
  ('Jose','password','jose@email.com', CURRENT_TIMESTAMP);

<img width="1007" alt="Screenshot 2024-06-20 at 13 42 54" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/dbca2a5f-8c37-4c64-998c-40facb547553">

INSERT INTO job(job_name)
VALUES
  ('Astronaut'), ('President');

<img width="339" alt="Screenshot 2024-06-20 at 13 43 35" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/3b4fc8ed-a3a3-4056-a5dd-a040c12ede16">

INSERT INTO account_job(user_id, job_id, hire_date)
VALUES
  (1, 1, CURRENT_TIMESTAMP);

<img width="542" alt="Screenshot 2024-06-20 at 13 45 40" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/fc53d02e-913a-46b3-9074-07dae005c6ea">

## UPDATE

