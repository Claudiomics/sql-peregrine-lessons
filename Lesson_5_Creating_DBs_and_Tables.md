# Creating Databases and Tables

Table of Contents

1. [Data Types](#data-types)
2. [Primary and Foreign Keys](#primary-and-foreign-keys)
3. [Constraints](#constraints)
4. [CREATE](#create)
5. [INSERT](#insert)
6. [UPDATE](#update)
7. [DELETE](#delete)
8. [ALTER](#alter)
      1. [Adding Columns](adding-columns)
      2. [Drop](#drop)
9. [Check Contraints](#check-constraints)
10. [Challenge](#challenge)

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

Syntax:
UPDATE table
SET column1 = value1, 
    column2 = value2
WHERE condition;

## DELETE

Removes rows from a table.

DELETE FROM table
WHERE row_id = 1;

Deleting rows based on their presence in another table:

DELETE FROM tableA
USING tableB
WHERE tableA.id = tableB.id

Deleting all rows from the table:

DELETE FROM table;

## ALTER

Changes to a table structure, such as:

- Adding, dropping, renaming a column
- Changing a data type
- Set DEFAULT values for a column
- Add CHECK constraints
- Rename table

Syntax:

ALTER TABLE table_name action;

### Adding Columns 

ALTER TABLE table_name
ADD COLUMN new_col TYPE;

### Drop

ALTER TABLE table_name 
DROP COLUMN col_name;

## Check Constraints 

Alter constraints:

ALTER TABLE table_name 
ALTER COLUMN col_name
ADD CONSTRAINT constraint_name;

Check constraints:

CREATE TABLE example(
  ex_id SERIAL PRIMARY KEY,
  age SMALLINT CHECK(age > 21), 
  parent_age SMALLINT CHECK(parent_age > age));

## Challenge
Present a 2 minute presentation on how you completed the following: You have 1h.

Create a new database called "School" this database should have two tables: teachers and students.
The students table should have columns for student_id, first_name,last_name, homeroom_number, phone,email, and graduation year.

The teachers table should have columns for teacher_id, first_name, last_name, homeroom_number, department, email, and phone.
The constraints are mostly up to you, but your table constraints do have to consider the following:
 We must have a phone number to contact students in case of an emergency.
 We must have ids as the primary key of the tables
Phone numbers and emails must be unique to the individual.
Once you've made the tables, insert a student named Mark Watney (student_id=1) who has a phone number of 777-555-1234 and doesn't have an email. He graduates in 2035 and has 5 as a homeroom number.
Then insert a teacher names Jonas Salk (teacher_id = 1) who as a homeroom number of 5 and is from the Biology department. His contact info is: jsalk@school.org and a phone number of 777-555-4321.
Keep in mind that these insert tasks may affect your constraints!

CREATE TABLES WITH CONSTRAINTS:

CREATE TABLE students(
  student_id SERIAL PRIMARY KEY,
  first_name VARCHAR(50) NOT NULL
  last_name VARCHAR(50) NOT NULL
  homeroom_number INTEGER NOT NULL,
  phone VARCHAR(15) UNIQUE NOT NULL,
  email VARCHAR(200) UNIQUE,
  graduation year INTEGER
  );
  
CREATE TABLE teachers(
    teacher_id SERIAL PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    homeroom_number INTEGER NOT NULL,
    department VARCHAR(100) NOT NULL,
    email VARCHAR(200) UNIQUE,
    phone VARCHAR(15) UNIQUE NOT NULL
);

Add two people: 

Mark Watney (student_id=1) who has a phone number of 777-555-1234 and doesn't have an email. He graduates in 2035 and has 5 as a homeroom number.

INSERT INTO student(student_id, first_name,last_name, homeroom_number, phone,email, graduation year)
VALUES (1, 'Mark', 'Watney', 5, '777-555-1234', null, 2035);

Jonas Salk (teacher_id = 1) who as a homeroom number of 5 and is from the Biology department. His contact info is: jsalk@school.org and a phone number of 777-555-4321.

INSERT INTO teacher(teacher_id, first_name, last_name, homeroom_number, department, email, phone)
VALUES (1, 'Jonas', 'Salk', 5, 'Biology', 'jsalk@school.org', '777-555-4321');

Verify information has been added correctly:

SELECT * FROM students;
SELECT * FROM teachers;
  



