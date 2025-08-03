# -Apply-filters-to-SQL-queries

Project Overview
This repository contains SQL queries developed to assist in investigating employee login activities and managing department-specific system updates within a large organization. The goal is to identify suspicious login patterns and efficiently retrieve employee information for targeted IT updates.

SQL Query Tasks
1. Retrieve Login Attempts Before 7:00 AM
Query to find login attempts made before 07:00:00 to detect out-of-hours access.

sql
Copy
Edit
SELECT *
FROM log_in_attempts
WHERE CAST(attempt_time AS TIME) < '07:00:00';
2. Retrieve Login Attempts on Specific Dates
Fetch login attempts from May 8 and May 9, 2022, to investigate a suspicious event.

sql
Copy
Edit
SELECT *
FROM log_in_attempts
WHERE login_date IN ('2022-05-08', '2022-05-09');
3. Filter Login Attempts Not Originating from Mexico
Exclude login attempts originating from Mexico (entries starting with 'MEX' or 'MEXICO').

sql
Copy
Edit
SELECT *
FROM log_in_attempts
WHERE country NOT LIKE 'MEX%';
4. Find Marketing Department Employees in East Building Offices
Get all Marketing employees located in offices within the East building (office names like 'East-170', 'East-320').

sql
Copy
Edit
SELECT *
FROM employees
WHERE department = 'Marketing'
  AND office LIKE 'East-%';
5. Retrieve Employees in Finance or Sales Departments
Identify employees who belong to either Finance or Sales departments for targeted updates.

sql
Copy
Edit
SELECT *
FROM employees
WHERE department = 'Finance' OR department = 'Sales';
Alternative:

sql
Copy
Edit
SELECT *
FROM employees
WHERE department IN ('Finance', 'Sales');
6. Find Employees Not in Information Technology Department
List employees who are not part of the Information Technology department, as updates have already been applied there.

sql
Copy
Edit
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';
Alternative:

sql
Copy
Edit
SELECT *
FROM employees
WHERE department <> 'Information Technology';
How to Use
Clone this repository to your local machine.

Use the provided SQL queries directly in your database client to extract and analyze data.

Modify filters as needed to suit other departments, dates, or criteria.
