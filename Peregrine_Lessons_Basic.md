# Peregrine Lesson 1 - The Basics

This file inlcudes the Questions and Answers from the Lessons provided by Peregrine, using PgAdmin4 and PostgreSQL.

Table of Contents:

1. [Exercises](#exercises)
2. [Review Exercises](#review-exercises)

## Exercises

Exercise 1:

<img width="807" alt="Screenshot 2024-06-19 at 10 48 13" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/158f1955-9722-4baf-8c44-3ee518144abb">

SELECT first_name, last_name, email 
	FROM customer;

<img width="613" alt="Screenshot 2024-06-19 at 11 29 52" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/227f0504-707b-49f6-ad3b-dd4b760d1857">

Execise 2:

<img width="923" alt="Screenshot 2024-06-19 at 11 49 36" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/d5bfaa3a-dd4b-424c-bce6-d8378efaebca">

SELECT * from FILM;

<img width="1056" alt="Screenshot 2024-06-19 at 11 38 43" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/bc7e5557-03eb-4449-8a17-c0730de298cf">

Find the unique ratings:
SELECT DISTINCT rating FROM film;

<img width="387" alt="Screenshot 2024-06-19 at 11 40 18" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/ea618eec-568a-42a7-ab03-95735f2fe269">

Exercise 3:

<img width="925" alt="Screenshot 2024-06-19 at 11 59 23" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/b390a0b7-2599-40b3-80d6-12042af0fcd0">

SELECT email 
	FROM customer
	WHERE first_name = 'Nancy'
	AND last_name = 'Thomas';
<img width="370" alt="Screenshot 2024-06-19 at 12 01 03" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/e526a9af-b9af-4d63-ada4-0144587c7f27">

Exercise 4:

<img width="898" alt="Screenshot 2024-06-19 at 12 01 42" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/494c3fb8-3ea6-4723-abf4-0a4bd4b62556">

SELECT title, description 
	FROM film
	WHERE title = 'Outlaw Hanky';

<img width="806" alt="Screenshot 2024-06-19 at 12 22 41" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/4a744dda-06af-4900-967b-aafd8dabc49f">

Exercise 5:
<img width="932" alt="Screenshot 2024-06-19 at 12 23 06" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/8e800d1d-278d-4810-954c-10a56854fae8">

SELECT address, phone 
	FROM address
	WHERE address = '259 Ipoh Drive';
<img width="376" alt="Screenshot 2024-06-19 at 12 25 42" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/23304def-6524-470d-9012-27b76aa5103a">

Exercise 6:

<img width="883" alt="Screenshot 2024-06-19 at 12 27 42" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/beac724f-3cf9-4337-8252-15716b1c78fe">

SELECT customer_id AS first_10_customers, payment_date
	FROM payment
	ORDER BY payment_date ASC
	LIMIT 10;
<img width="536" alt="Screenshot 2024-06-19 at 12 32 54" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/33d9a818-8c63-449d-b39c-3c057faca7d1">

Exercise 7:

<img width="934" alt="Screenshot 2024-06-19 at 12 36 09" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/a0eba8f3-7454-43db-ae9c-a2e8793a38f0">

SELECT title, description, length AS minutes_long 
	FROM film
	ORDER BY length ASC
	LIMIT 5;

<img width="901" alt="Screenshot 2024-06-19 at 12 35 51" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/a5bb6644-02d0-4a34-adb9-d0d026672e9e">

Excercise 8:

<img width="937" alt="Screenshot 2024-06-19 at 12 36 26" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/522a0433-fbc8-45c2-a716-208d8a617e9a">

SELECT COUNT(title) 
	FROM film
	WHERE length <= 50;

<img width="288" alt="Screenshot 2024-06-19 at 12 38 10" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/89e3d8cc-8b0e-4282-bc5c-aa25b339525b">

## Review Exercises

Review Exercise 1:

<img width="853" alt="Screenshot 2024-06-19 at 12 39 10" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/87af9733-d60f-42fd-be4c-f2ed9f1d33c5">

SELECT COUNT(amount) AS number_of_transactions_greater_than_5_dollars
	FROM payment
	WHERE amount > 5;

<img width="643" alt="Screenshot 2024-06-19 at 12 43 15" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/8fba4f19-ad41-4bf2-97cc-18f29e8f6d24">

Review Exercise 2:

<img width="854" alt="Screenshot 2024-06-19 at 12 43 42" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/0587290d-48ff-4a01-8e97-e3c743440c4f">

SELECT COUNT(first_name) AS number_of_actors_with_first_name_beginning_with_p
	FROM actor
	WHERE first_name LIKE 'P%';

<img width="721" alt="Screenshot 2024-06-19 at 12 45 15" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/55c76233-c897-42c3-b456-d90834a47ce8">

Review Exercise 3:

<img width="831" alt="Screenshot 2024-06-19 at 12 45 50" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/d0688e04-9ab3-4cfb-abef-4c4cb9f86aaf">

SELECT COUNT(DISTINCT district) AS num_of_unique_districts 
	FROM address;

<img width="553" alt="Screenshot 2024-06-19 at 12 48 04" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/ecf67446-9c4b-4496-ac05-7ea925413d95">

Review Exercise 4:

<img width="944" alt="Screenshot 2024-06-19 at 12 48 33" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/c023bdfe-7259-4b94-82e0-caea651ee2c6">

SELECT DISTINCT district AS unique_district_names 
	FROM address;

<img width="479" alt="Screenshot 2024-06-19 at 12 49 13" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/78ed5591-ff6f-493f-95cb-8def7195d712">

Review Exercise 5:

<img width="886" alt="Screenshot 2024-06-19 at 12 49 35" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/9630b5a1-706f-4256-a1a3-86caeb793065">

SELECT title 
FROM film 
WHERE title LIKE '%Truman%';

<img width="322" alt="Screenshot 2024-06-19 at 12 51 58" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/fcb0119d-097e-4cda-a933-004cfe73fb86">

SELECT COUNT(title) 
FROM film 
WHERE title LIKE '%Truman%';

<img width="328" alt="Screenshot 2024-06-19 at 12 52 26" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/4943cc34-42d8-41a5-9409-19bc593c9bcf">
