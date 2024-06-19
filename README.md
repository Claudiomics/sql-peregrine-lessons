# SQL Lessons

These are exercises to practice and consolidate my SQL skills, through Peregrine's Data and Analytics training programme.

Set Up
Ensure you have downloaded pgadmin4 and postgresql 16 and created a master password.

Download dvdrentals.tar into a folder on your machine

Name db dvd_rentals:
<img width="713" alt="Screenshot 2024-06-19 at 10 42 01" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/5b82bff5-c8c5-4d41-a37d-7045829af701">

Restore
<img width="348" alt="Screenshot 2024-06-19 at 10 45 16" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/52512edc-4a01-4a2c-939f-110208bb283e">

<img width="104" alt="Screenshot 2024-06-19 at 10 45 37" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/e7b24af9-0d33-4c84-91c0-c01ecfef1af1">

<img width="358" alt="Screenshot 2024-06-19 at 10 46 07" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/7bc23e83-b2b6-4ce4-9a77-d7494a5bf5ba">

<img width="262" alt="Screenshot 2024-06-19 at 10 46 28" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/84159e53-ccdd-47c8-a248-a8751cbf7285">

ERD
<img width="1440" alt="Screenshot 2024-06-19 at 10 47 43" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/4fc19eb6-3db3-4131-8385-613ae05c839b">

Exercise 1:

<img width="807" alt="Screenshot 2024-06-19 at 10 48 13" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/158f1955-9722-4baf-8c44-3ee518144abb">

Query tool
<img width="837" alt="Screenshot 2024-06-19 at 11 26 50" src="https://github.com/Claudiomics/sql-peregrine-lessons/assets/149532217/a3ce60e5-0685-4d7d-aaeb-eee809cbf43e">

fn F5 to run as a keyboard shortcut on mac.

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


