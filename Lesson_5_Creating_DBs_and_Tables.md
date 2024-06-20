# Creating Databases and Tables

Table of Contents

1. [Data Types](#data-types)
2. [Primary and Foreign Keys](#primary-and-foreign-keys)
3. [Constraints](#constraints)
4. [CREATE](#create)
5. [INSERT](#insert)
6. [UPDATE](#update)

## Primary Key

## Primary and Foreign Keys

## Constraints

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

