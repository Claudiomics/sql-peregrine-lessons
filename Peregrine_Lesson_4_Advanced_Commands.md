# Advanced Commands 

Table of Contents:
1. [Introduction](#introduction)
2. [Timestamps and EXTRACT](#timestamps-and-extract)
3. [Show All](#show-all)
4. [Show Timezone](#show-timezone)
5. [SELECT DATE AND TIME](#select-date-and-time)
6. [EXTRACT()](#extract)
7. [AGE()](#age)
8. [TO CHAR()](#to-char)
9. [Trial Examples](#trial-examples)
10. [Challenges](#challenges)
11. [Maths Functions](#maths-functions)
12. [String Functions](#string-functions)
13. [Sub Queries](#sub-queries)
14. [Self Joins](#self-joins)

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

## Maths Functions

## String Functions

## Sub-Queries 

## Self Joins




