# Advanced Commands 

Table of Contents:
1. [Introduction](#introduction)
2. [Timestamps and EXTRACT](#timestamps-and-extract)
      1. [Show All](#show-all)
      2. [Show Timezone](#show-timezone)
      3. [SELECT DATE AND TIME](#select-date-and-time)
      4. [EXTRACT()](#extract)
      5. [AGE()](#age)
      6. [TO CHAR()](#to-char)
      7. [Trial Examples](#trial-examples)
      8. [Challenges](#challenges)
11. [Mathematical Operators](#mathematical-operators)
14. [String Functions](#string-functions)
    1. [Trial Examples](#trial-examples)
16. [Sub Queries](#sub-queries)
    1. [Trial Examples](#trial-examples)
18. [Self Joins](#self-joins)
    1. [Trial Example](#trial-example)

## Introduction 

This lesson's objectoves are covering timestamps and EXTRACT, maths functions, string functions, sub-queries and self joins.

Time - Contains only time
Date - Contains only date
Timestamp - Contains date and time 
Timestampz - Contains date, time, and timezone

## Timestamps and EXTRACT

### SHOW ALL

In PostgreSQL 'SHOW ALL' provides a list of all the configuration parameters for the database server along with their current values and descriptions. 

<img width="1023" alt="Screenshot 2024-06-20 at 11 10 22" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/06df511a-5b54-492f-ac2e-28c9ebe6b28d">

### SHOW TIMEZONE

Provides current timezone based on location.

<img width="216" alt="Screenshot 2024-06-20 at 11 12 25" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/83ea5a09-080d-4a36-bb48-fb425d1ed1e0">

### SELECT DATE AND TIME

SELECT NOW();

<img width="281" alt="Screenshot 2024-06-20 at 11 13 19" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/35320685-7dfa-4375-8110-ccb8302f0216">

SELECT TIMEOFDAY();

<img width="304" alt="Screenshot 2024-06-20 at 11 14 13" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/24ea97bf-b692-41d1-a861-aa0c5699a89d">

SELECT CURRENT_TIME;

<img width="263" alt="Screenshot 2024-06-20 at 11 14 39" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/e9141ae8-ba36-40b2-98c2-942b27d48995">


SELECT CURRENT_DATE;

<img width="271" alt="Screenshot 2024-06-20 at 11 15 00" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/04538697-0c34-4be2-8533-5d87f1f75311">

### EXTRACT()

Allows the extraction of a sub-component of a date value
- YEAR
- MONTH
- DAY
- WEEK
- QUARTER

EXTRACT(YEAR FROM date_col);

<img width="390" alt="Screenshot 2024-06-20 at 11 19 12" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/be141466-a63e-4b49-bb5a-9996d32d39f5">

### AGE()

Calculates and returns current age given a timestamp

AGE(date_col)
Returns: 13 years 1 mon 5 days 01:34:13.003423

### TO CHAR()

Converts data types to text, which is useful for timestamp formatting

TO_CHAR(date_col, 'mm-dd-yy'

### Trial Examples

SELECT EXTRACT(YEAR FROM payment_date)
FROM payment;

<img width="378" alt="Screenshot 2024-06-20 at 11 23 53" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/b1771620-dc7d-4b9c-8327-9d602c15edd3">

SELECT EXTRACT(MONTH FROM payment_date) AS pay_month
FROM payment;

<img width="546" alt="Screenshot 2024-06-20 at 11 24 32" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/4db65bf9-6fb5-42a4-a773-252a27b99c61">

SELECT EXTRACT(QUARTER FROM payment_date) AS pay_quarter
FROM payment;

<img width="552" alt="Screenshot 2024-06-20 at 11 25 08" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/1917c787-0fa2-4ecb-b82c-639e63475fc8">

SELECT AGE(payment_date)
FROM payment;

<img width="449" alt="Screenshot 2024-06-20 at 11 25 25" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/7eb8396d-41bf-4001-bdfc-cfc84cdca51e">

SELECT TO_CHAR(payment_date, 'MM/dd/YYYY')
FROM payment;

<img width="436" alt="Screenshot 2024-06-20 at 11 25 45" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/7b5a9bd4-4b79-4462-b6b5-98e039b817a5">

How to change format to European? Change date option to 'dd/MM/YYYY'

### Challenges

1. 

<img width="332" alt="Screenshot 2024-06-20 at 11 26 30" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/3e4db48f-a338-453d-a526-652b5fb580c4">

Inititally tried but it threw an error:

SELECT TO_CHAR(EXTRACT(MONTH FROM payment_date)) as payment_month
FROM payment
GROUP BY payment_month;

<img width="532" alt="Screenshot 2024-06-20 at 11 30 20" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/a12a3a92-c8ef-45bd-8c17-ee4800505076">

Could also be: 

SELECT DISTINCT(TO_CHAR(payment_date,'MONTH'))
FROM payment

2. 

<img width="333" alt="Screenshot 2024-06-20 at 11 31 55" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/1de5ba48-4347-4716-bd16-428e1c5189f3">

First try:

<img width="905" alt="Screenshot 2024-06-20 at 11 39 18" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/65120df1-abfd-4e44-9f34-cb57efbb9579">

Correct try:

<img width="926" alt="Screenshot 2024-06-20 at 11 45 41" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/77a048cb-d048-440a-bff1-96cceb83d027">

Need to use the **dow** keyword when using EXTRACT().
Sunday is the start of the week (index 0) according to PostgreSQL.

Alternative:

<img width="465" alt="Screenshot 2024-06-20 at 11 46 30" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/34a34b2e-0983-47a3-bcb7-d369e889079a">

## Mathematical Operators

SELECT ROUND(rental_rate/replacement_cost,4)*100 AS percent_cost
FROM film;

<img width="635" alt="Screenshot 2024-06-20 at 11 57 12" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/cfa77fb7-c6f8-41f6-95a9-b245b05468f6">

## String Functions

Allow us to edit, combine and alter text data columns.

### Trial Examples

SELECT UPPER(first_name) ||' '|| UPPER(last_name) AS full_name
FROM customer;

<img width="622" alt="Screenshot 2024-06-20 at 11 59 51" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/31b50570-6992-46ee-b093-04bf283b6681">

SELECT (LOWER(LEFT(first_name,1)) || LOWER(last_name) || '@gmail.com')
AS custom_email
FROM customer;

<img width="681" alt="Screenshot 2024-06-20 at 12 02 53" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/f3728a55-1909-4722-86e6-a0481f378375">

## Sub-Queries 

Sub queries allow you to construct complex queries, essentially performing a query on the results of another query. It involves two SELECT statements.

SELECT student, grade
FROM test_scores;

+

SELECT AVG(grade)
FROM test_scores;

=

SELECT student, grase
FROM test_scores
WHERE grade > (SELECT AVG(grade)
FROM test_scores);

The sub query is run first and 'IN' can be used with a subquery to check multiple results.

Subqueries can operate on a separate table:

SELECT student, grade
FROM test_scores
WHERE student IN 
  (SELECT student 
    FROM honor_roll_table);

The EXISTS operator is used to test for existance of rows in a subquery. The typical syntax is as follows:

SELECT column_name
FROM table_name
WHERE EXIXTS
(SELECT column_name 
FROM table_name
WHERE condition);

### Trial Examples

SELECT title, rental_rate
FROM film
WHERE rental_rate > (SELECT AVG(rental_rate)
                      FROM film);

<img width="493" alt="Screenshot 2024-06-20 at 12 14 53" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/47271219-96fc-470b-b085-4b6c50b4d976">

SELECT film_id, title
FROM film
WHERE film_id IN (SELECT inventory.film_id
                  FROM rental
                  INNER JOIN inventory 
                    ON inventory.inventory_id = rental.inventory_id
                    WHERE return_date BETWEEN '2005-05-29' AND '2005-05-30');

<img width="760" alt="Screenshot 2024-06-20 at 12 21 18" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/e8ed08aa-8f4c-4e7c-a1e5-2833e14c4f48">

SELECT first_name, last_name 
FROM customer as c
WHERE EXISTS (SELECT * FROM payment as p
              WHERE p.customer_id = c.customer_id
              AND amount > 11);

<img width="519" alt="Screenshot 2024-06-20 at 12 23 58" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/92fad25f-6d84-4f34-aa47-517e22908263">

## Self Joins

A self-join is a query in which a table is joined to itself, and are useful for comparing values in a column of rows within the same table. 

It can be seen as a join of two copies of the same table.

Syntax:

SELECT tableA.col, tableB.com
FROM table as tableA
JOIN table AS tableB ON 
tableA.some_col = tableB.other_col

### Trial Example

SELECT f1.title, f2.length 
FROM film as f1 
INNER JOIN film AS f2 
ON f1.film_id != f2.film_id
AND f1.length = f2.length;

<img width="340" alt="Screenshot 2024-06-20 at 12 34 08" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/d72a9ee5-f27e-4573-a532-f62494017758">

This query performs a self-join of the 'film' table, comparing the columns 'title' and 'length', using the aliases f1 and f2.
The film table (f1)is joined to film (f2) to return the results (title and length) of an INNER JOIN where the film_id's are not the same, but have the same lengths. There are multiple of the same film because the store carries mutltiple copies of the same film.


