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

e.g.2. Create a new database and run the following code:

CREATE TABLE account(
  user_id SERIAL PRIMARY KEY,
  username VARCHAR(50) NOT NULL,
  password VARCHAR(50) NOT NULL,
  email VARCHAR(250) UNIQUE NOT NULL,
  created_on TIMESTAMP NOT NULL,
  last_login TIMESTAMP
);

## INSERT


## UPDATE

