# MYSQL CONCEPTS AND EXAMPLES

## Introduction

This is a single page combined brief and basic topics of MySQL.

## Table of Contents

1. [Getting Started](#getting-started)
2. [Data Manipulation](#data-manipulation)
3. [Managing Databases](#managing-databases)
4. [Managing Tables](#managing-tables)
5. [Mysql Constraints](#mysql-constraints)
6. [Mysql Datatypes](#mysql-datatypes)
7. [Mysql Globalization](#mysql-globalization)
8. [Advanced Mysql Concepts](#advanced-mysql-concepts)

## Getting Started

Use any of your sample database or get from open-source database like employees in MySQL. Follow installation procedure from official website.

Consider, this notes primarily made for educational purpose only. For practical and real-time implementation may vary. Consider double check with official [MySQL](https://www.mysql.com/) website and consult with experts opinion. 

## Data Manipulation

1. SELECT:

Explanation: SELECT is used to retrieve data from one or more columns of one or more tables in a database.

Syntax:

```sql
SELECT
    *
FROM
    table_name;
```

Example: 

```sql
SELECT
    *
FROM
    departments;
```

Results:

| dept_no | dept_name           |
|---------|---------------------|
| d009    | Customer Service    |
| d005    | Development         |
| d002    | Finance             |
| d003    | Human Resources     |
| d001    | Marketing           |
| d004    | Production          |
| d006    | Quality Management  |
| d008    | Research            |
| d007    | Sales               |

2. SELECT DISTINCT:

Explanation: SELECT DISTINCT is used to retrieve unique values from a column in the result set.

Syntax:

```sql
SELECT DISTINCT
    column_name
FROM
    table_name;
```

Example: 

```sql
SELECT DISTINCT
    title
FROM
    titles;
```

Result:

| title              |
|--------------------|
| Senior Engineer    |
| Staff              |
| Engineer           |
| Senior Staff       |
| Assistant Engineer |
| Technique Leader   |
| Manager            |

3. LIMIT:

Explanation: LIMIT is used to limit the number of rows returned in a result set.

Syntax:
 
```sql
SELECT
    *
FROM
    table_name
LIMIT number_of_limit;
```

Example:

```sql
SELECT
    *
FROM
    employees
LIMIT 10;
```

Result:

| emp_no | birth_date | first_name | last_name | gender | hire_date |
|--------|------------|------------|-----------|--------|-----------|
| 10001  | 1953-09-02 | Georgi     | Facello   | M      | 1986-06-26|
| 10002  | 1964-06-02 | Bezalel    | Simmel    | F      | 1985-11-21|
| 10003  | 1959-12-03 | Parto      | Bamford   | M      | 1986-08-28|
| 10004  | 1954-05-01 | Chirstian  | Koblick   | M      | 1986-12-01|
| 10005  | 1955-01-21 | Kyoichi    | Maliniak  | M      | 1989-09-12|
| 10006  | 1953-04-20 | Anneke     | Preusig   | F      | 1989-06-02|
| 10007  | 1957-05-23 | Tzvetan    | Zielinski | F      | 1989-02-10|
| 10008  | 1958-02-19 | Saniya     | Kalloufi  | M      | 1994-09-15|
| 10009  | 1952-04-19 | Sumant     | Peac      | F      | 1985-02-18|
| 10010  | 1963-06-01 | Duangkaew  | Piveteau  | F      | 1989-08-24|

4. ORDER BY:

Explanation: ORDER BY is used to sort the result set in ascending or descending order based on one or more columns.

Syntax:

```sql
SELECT
    column_name
FROM
    table_name
ORDER BY
    column_name
DESC;
```

Example: 

```sql
SELECT
    salary
FROM
    salaries
ORDER BY
    salary
DESC;
```

Result:

| salary  |
|---------|
| 158220  |
| 157821  |
| 156286  |
| 155709  |
| 155513  |
| 155377  |
| 155190  |
| 154888  |

5. GROUP BY:

Explanation: GROUP BY is used to group rows based on one or more columns, usually used with aggregate functions like SUM, COUNT, etc.

Syntax:

```sql
SELECT
    column_name,
    COUNT(*) AS total_column
FROM
    table_name
GROUP BY
    column_name;
```

Example: 

```sql
SELECT
    title,
    COUNT(*) AS total_title
FROM
    titles
GROUP BY
    title;
```

Result:

| title             | total_title |
|-------------------|-------------|
| Assistant Engineer| 15128       |
| Engineer          | 115003      |
| Manager           | 24          |
| Senior Engineer   | 97750       |
| Senior Staff      | 92853       |
| Staff             | 107391      |
| Technique Leader  | 15159       |

6. HAVING:

Explanation: HAVING is used to filter groups based on specified conditions in a GROUP BY query.

Syntax:

```sql
SELECT
    column_name,
    COUNT(*) AS total_column
FROM
    table_name
GROUP BY
    column_name
HAVING
    COUNT(*) < number_of_column;
```

Example: 

```sql
SELECT
    title,
    COUNT(*) AS total_titles
FROM
    titles
GROUP BY
    title
HAVING
    COUNT(*) < 20000;
```

Result:

| title             | total_titles |
|-------------------|--------------|
| Assistant Engineer| 15128        |
| Manager           | 24           |
| Technique Leader  | 15159        |	

7. ROLLUP:

Explanation: ROLLUP is used to generate subtotals and grand totals in a GROUP BY query.

Syntax:

```sql
SELECT
    column_name1,
    column_name2,
    COUNT(*) AS total_column
FROM
    table_name
GROUP BY
    column_name1,
    column_name2 WITH ROLLUP
LIMIT number_of_limit;
```

Example: 

```sql
SELECT
    birth_date,
    gender,
    COUNT(*) AS total_employee
FROM
    employees
GROUP BY
    birth_date,
    gender WITH ROLLUP
LIMIT 25;
```

Result:

| birth_date | gender | total_employee |
|------------|--------|----------------|
| 1952-02-01 | M      | 6              |
| 1952-02-01 | NULL   | 6              |
| 1952-02-02 | M      | 48             |
| 1952-02-02 | F      | 22             |
| 1952-02-02 | NULL   | 70             |
| 1952-02-03 | M      | 40             |
| 1952-02-03 | F      | 23             |
| 1952-02-03 | NULL   | 63             |
| 1952-02-04 | M      | 42             |
| 1952-02-04 | F      | 28             |
| 1952-02-04 | NULL   | 70             |
| 1952-02-05 | M      | 35             |
| 1952-02-05 | F      | 23             |
| 1952-02-05 | NULL   | 58             |
| 1952-02-06 | M      | 44             |
| 1952-02-06 | F      | 28             |
| 1952-02-06 | NULL   | 72             |
| 1952-02-07 | M      | 33             |
| 1952-02-07 | F      | 23             |
| 1952-02-07 | NULL   | 56             |
| 1952-02-08 | M      | 32             |
| 1952-02-08 | F      | 29             |
| 1952-02-08 | NULL   | 61             |
| 1952-02-09 | M      | 45             |
| 1952-02-09 | F      | 33             |

8. WHERE:

Explanation: WHERE is used to filter rows based on specified conditions.

Syntax:

```sql
SELECT
    column_name1
FROM
    table_name
WHERE
    column_name2 = specific_value;
```

Example: 

```sql
SELECT
    emp_no
FROM
    employees
WHERE
    hire_date = '2000-01-01';
```

Result:

| emp_no |
|--------|
| 108201 |

9. AND:

Explanation: AND is used to combine multiple conditions in a WHERE clause.

Syntax:

```sql
SELECT
    column_name1
FROM
    table_name
WHERE
    column_name2 = specific_value AND column_name3 = another_specific_value;
```

Example: 

```sql
SELECT
    emp_no
FROM
    employees
WHERE
    hire_date = '1990-01-01' AND gender = 'M';
```

Result:

| emp_no |
|--------|
| 18199  |
| 21865  |
| 24751  |
| 28869  |
| 39204  |
| 44808  |
| 49447  |
| 50654  |

10. OR:

Explanation: OR is used to combine multiple conditions in a WHERE clause, where at least one condition must be true.

Syntax:

```sql
SELECT
    column_name1,
    column_name2,
    column_name3
FROM
    table_name
WHERE
    column_name2 = specific_value OR column_name3 = another_specific_value;
```

Example: 

```sql
SELECT
    emp_no,
    birth_date,
    hire_date
FROM
    employees
WHERE
    birth_date = '1990-01-01' OR hire_date = '1990-01-01';
```

Result:

| emp_no | birth_date  | hire_date   |
|--------|-------------|-------------|
| 18199  | 1953-02-25  | 1990-01-01  |
| 18873  | 1961-03-05  | 1990-01-01  |
| 21865  | 1964-10-24  | 1990-01-01  |
| 24751  | 1953-01-24  | 1990-01-01  |
| 28869  | 1961-01-08  | 1990-01-01  |
| 33268  | 1958-08-27  | 1990-01-01  |
| 34515  | 1964-04-12  | 1990-01-01  |
| 39204  | 1956-03-08  | 1990-01-01  |
| 44480  | 1952-06-13  | 1990-01-01  |

11. IN:

Explanation: IN is used to specify multiple possible values for a column in a WHERE clause.

Syntax:

```sql
SELECT
    column_name1,
    column_name2
FROM
    table_name
WHERE
    column_name2 IN (specific_value, another_specific_value, ...);
```

Example: 

```sql
SELECT
    emp_no,
    dept_no
FROM
    dept_manager
WHERE
    dept_no IN('d001', 'd002');
```

Result:

| emp_no | dept_no |
|--------|---------|
| 110022 | d001    |
| 110039 | d001    |
| 110085 | d002    |
| 110114 | d002    |

12. BETWEEN:

Explanation: BETWEEN is used to select values within a range in a WHERE clause.

Syntax:

```sql
SELECT
    column_name1,
    column_name2
FROM
    table_name
WHERE
    column_name2 BETWEEN start_value AND end_value;
```

Example: 

```sql
SELECT
    emp_no,
    hire_date
FROM
    employees
WHERE
    hire_date BETWEEN '1985-01-01' AND '1990-01-01';
```

Result:

| emp_no | hire_date   |
|--------|-------------|
| 10001  | 1986-06-26  |
| 10002  | 1985-11-21  |
| 10003  | 1986-08-28  |
| 10004  | 1986-12-01  |
| 10005  | 1989-09-12  |
| 10006  | 1989-06-02  |
| 10007  | 1989-02-10  |
| 10009  | 1985-02-18  |
| 10010  | 1989-08-24  |
| 10013  | 1985-10-20  |

13. LIKE:

Explanation: LIKE is used to search for a specified pattern in a column in a WHERE clause.

Syntax:

```sql
SELECT
    column_name1,
    column_name2
FROM
    table_name
WHERE
    column_name2 LIKE 'starting_with%';
```

Example: 

```sql
SELECT
    emp_no,
    first_name
FROM
    employees
WHERE
    first_name LIKE 'Jo%';
```

Result:

| emp_no | first_name |
|--------|------------|
| 10194  | Josyula    |
| 10439  | Jolita     |
| 10471  | Jouko      |
| 10556  | JoAnna     |
| 10660  | Jouko      |
| 10751  | Jordanka   |
| 11004  | JoAnna     |
| 11017  | Jovan      |
| 11097  | Jovan      |
| 11201  | Jouko      |
| 11282  | Josyula    |
| 11286  | Joydip     |
| 11387  | Jordanka   |
| 11391  | Jouko      |
| 11421  | Josyula    |
| 11638  | JoAnne     |
| 11697  | JoAnne     |
| 12047  | Jordanka   |
| 12196  | JoAnne     |
| 12418  | Jongsuk    |
| 12486  | Joydip     |
| 12494  | JoAnna     |
| 12599  | Jouni      |
| 12673  | Jouni      |
| 12911  | Jordanka   |	

14. IS NULL:

Explanation: IS NULL is used to check if a column value is NULL in a WHERE clause.

Syntax:

```sql
SELECT
    column_name1
FROM
    table_name
WHERE
    column_name2 IS NULL;
```

Example: 

```sql
SELECT
    emp_no
FROM
    salaries
WHERE
    salary IS NULL;
```

Result:

| emp_no |
|--------|
| 10001  |
| 10002  |
| 10003  |

15. Table & Column Aliases:

Explanation: Aliases are used to provide a temporary name for a table or column in a query.

Syntax:

```sql
SELECT
    t.column_name1 AS name1
FROM
    table_name t
WHERE
    t.column_name2 = specific_value;
```

Example: 

```sql
SELECT
    a.emp_no AS employee_number
FROM
    employees a
WHERE
    a.gender = 'M';
```

Result:

| employee_number |
|----------------|
| 10001          |
| 10003          |
| 10004          |
| 10005          |
| 10008          |
| 10012          |
| 10013          |
| 10014          |
| 10015          |
| 10016          |

16. Joins:

Explanation: Joins are used to combine rows from two or more tables based on related columns.

Syntax:

```sql
SELECT
    t.column_name1 AS employee_number,
    u.column_name2 AS employee_position
FROM
    table_name1 t
JOIN table_name2 u ON
    t.column_name1 = u.column_name1
WHERE
    t.column_name2 = specific_value;
```

Example: 

```sql
SELECT
    a.emp_no AS employee_number,
    b.title AS employee_position
FROM
    employees a
JOIN titles b ON
    a.emp_no = b.emp_no
WHERE
    a.gender = 'M';
```

Result:

| employee_number | employee_position   |
|----------------|---------------------|
| 10001          | Senior Engineer     |
| 10003          | Senior Engineer     |
| 10004          | Engineer            |
| 10004          | Senior Engineer     |
| 10005          | Senior Staff        |
| 10005          | Staff               |
| 10008          | Assistant Engineer  |
| 10012          | Engineer            |
| 10012          | Senior Engineer     |
| 10013          | Senior Staff        |
| 10014          | Engineer            |

17. INNER JOIN:

Explanation: INNER JOIN returns rows that have matching values in both tables involved in the join.

Syntax:

```sql
SELECT
    t.column_name1,
    u.column_name1
FROM
    table_name1 t
INNER JOIN table_name2 u ON
    t.column_name1 = u.column_name1;
```

Example: 

```sql
SELECT
    a.dept_no,
    b.dept_name
FROM
    dept_emp a
INNER JOIN departments b ON
    a.dept_no = b.dept_no;
```

Result:

| dept_no | dept_name         |
|---------|-------------------|
| d009    | Customer Service  |
| d009    | Customer Service  |
| d009    | Customer Service  |
| d009    | Customer Service  |
| d009    | Customer Service  |
| d009    | Customer Service  |
| d009    | Customer Service  |
| d009    | Customer Service  |

18. LEFT JOIN:

Explanation: LEFT JOIN returns all rows from the left table and the matched rows from the right table. If no match is found, NULL values are returned.

Syntax:

```sql
SELECT
    t.column_name1,
    u.column_name2
FROM
    table_name1 t
LEFT JOIN table_name2 u ON
    t.column_name1 = u.column_name1;
```

Example: 

```sql
SELECT
    a.emp_no,
    b.hire_date
FROM
    dept_manager a
LEFT JOIN employees b ON
    a.emp_no = b.emp_no;
```

Result:

| emp_no | hire_date  |
|--------|------------|
| 110022 | 1985-01-01 |
| 110039 | 1986-04-12 |
| 110085 | 1985-01-01 |
| 110114 | 1985-01-14 |
| 110183 | 1985-01-01 |
| 110228 | 1985-08-04 |
| 110303 | 1985-01-01 |
| 110344 | 1985-11-22 |
| 110386 | 1988-10-14 |

19. RIGHT JOIN:

Explanation: RIGHT JOIN returns all rows from the right table and the matched rows from the left table. If no match is found, NULL values are returned.

Syntax:

```sql
SELECT
    t.column_name1,
    u.column_name1
FROM
    table_name1 t
RIGHT JOIN table_name2 u ON
    a.column_name1 = b.column_name1;
```

Example: 

```sql
SELECT
    a.emp_no,
    b.dept_no
FROM
    employees a
RIGHT JOIN dept_emp b ON
    a.emp_no = b.emp_no;
```

Result:

| emp_no | dept_no |
|--------|---------|
| 10001  | d005    |
| 10002  | d007    |
| 10003  | d004    |
| 10004  | d004    |
| 10005  | d003    |
| 10006  | d005    |
| 10007  | d008    |
| 10008  | d005    |
| 10009  | d006    |
| 10010  | d004    |

20. Self Join:

Explanation: Self Join is used to join a table with itself, treating it as two separate tables.

Syntax:

```sql
SELECT
    t.column_name1,
    t.column_name2,
    u.column_name3,
    ...
FROM
    table_name1 t
JOIN table_name1 u ON
    t.column_name2 = u.column_name3;
```

Example: 

```sql
SELECT
    a.dept_no,
    a.from_date,
    b.emp_no,
    b.dept_no,
    b.to_date
FROM
    dept_emp a
JOIN dept_emp b ON
    a.from_date = b.to_date;
```

Result:

| dept_no | from_date  | emp_no | dept_no | to_date    |
|---------|------------|--------|---------|------------|
| d005    | 2000-07-31 | 10008  | d005    | 2000-07-31 |
| d005    | 2000-07-31 | 10008  | d005    | 2000-07-31 |
| d006    | 2000-06-26 | 10010  | d004    | 2000-06-26 |
| d009    | 2000-06-26 | 10010  | d004    | 2000-06-26 |
| d004    | 1996-11-09 | 10011  | d009    | 1996-11-09 |
| d004    | 1996-11-09 | 10011  | d009    | 1996-11-09 |
| d007    | 1996-11-09 | 10011  | d009    | 1996-11-09 |
| d005    | 1996-11-09 | 10011  | d009    | 1996-11-09 |
| d005    | 1996-11-09 | 10011  | d009    | 1996-11-09 |
| d001    | 1993-08-22 | 10015  | d008    | 1993-08-22 |

21. CROSS JOIN:

Explanation: CROSS JOIN returns the Cartesian product of the two tables involved in the join, resulting in all possible combinations of rows.

Syntax:

```sql
SELECT
    t.column_name1
    u.column_name2,
    ...
FROM
    table_name1 t
CROSS JOIN table_name2 u;
```

Example: 

```sql
SELECT
    a.dept_name,
    b.title
FROM
    departments a
CROSS JOIN titles b;
```

Result:

| dept_name         | title            |
|-------------------|------------------|
| Customer Service  | Senior Engineer  |
| Development       | Senior Engineer  |
| Finance           | Senior Engineer  |
| Human Resources   | Senior Engineer  |
| Marketing         | Senior Engineer  |
| Production        | Senior Engineer  |
| Quality Management| Senior Engineer  |
| Research          | Senior Engineer  |
| Sales             | Senior Engineer  |
| Customer Service  | Staff            |

22. Derived Tables:

Explanation: Derived Tables are temporary tables created within a query, used to simplify complex queries or calculations.

Syntax:

```sql
SELECT
    dt.column_name1,
    dt.name
FROM
    (
    SELECT
        column_name1,
        COUNT(column_name2) AS name
    FROM
        table_name
    GROUP BY
        column_name1
) AS dt;
```

Example: 

```sql
SELECT
    dt.emp_no,
    dt.salary_appraisal
FROM
    (
    SELECT
        emp_no,
        COUNT(salary) AS salary_appraisal
    FROM
        salaries
    GROUP BY
        emp_no
) AS dt;
```

Result:

| emp_no | salary_appraisal |
|--------|-----------------|
| 10001  | 17              |
| 10002  | 6               |
| 10003  | 7               |
| 10004  | 16              |
| 10005  | 13              |
| 10006  | 12              |
| 10007  | 14              |
| 10008  | 3               |
| 10009  | 18              |

23. EXISTS:

Explanation: EXISTS is used to check if a subquery returns any rows, and returns true if at least one row exists.

Syntax:

```sql
SELECT
    column_name1
FROM
    table_name1
WHERE
    EXISTS(
    SELECT
        *
    FROM
        table_name2
    WHERE
        table_name1.column_name2 = table_name2.column_name1
);
```

Example: 

```sql
SELECT
    first_name
FROM
    employees
WHERE
    EXISTS(
    SELECT
        *
    FROM
        dept_manager
    WHERE
        employees.emp_no = dept_manager.dept_no
);
```

Result:

first_name

24. UNION:

Explanation: UNION is used to combine result sets of two or more SELECT statements into a single result set.

Syntax:

```sql
SELECT
    table_name1.column_name1
FROM
    table_name1
UNION
SELECT
    table_name2.column_name1
FROM
    table_name2;
```

Example: 

```sql
SELECT
    departments.dept_name
FROM
    departments
UNION
SELECT
    titles.title
FROM
    titles;
```

Result:

| dept_name         |
|-------------------|
| Customer Service  |
| Development       |
| Finance           |
| Human Resources   |
| Marketing         |
| Production        |
| Quality Management|

25. INSERT:

Explanation: INSERT is used to insert new rows into a table.

Syntax:

```sql
INSERT INTO table_name1(column_name1, column_name2, ...)
VALUES(specific_value1, specific_value2, ...);
```

Example: 

```sql
INSERT INTO departments(dept_no, dept_name)
VALUES('d010', 'Software Developement');
```

Result:

```bash
1 row inserted. (Query took 0.0320 seconds.)
```

26. Insert Multiple Rows:

Explanation: Insert Multiple Rows is used to insert multiple rows into a table in a single INSERT statement.

Syntax:

```sql
INSERT INTO table_name1(column_name1, column_name2, ...)
VALUES(specific_value1, specific_value2, ...),(specific_value1, specific_value2, ...);
```

Example: 

```sql
INSERT INTO departments(dept_no, dept_name)
VALUES('d010', 'Software Developement'),('d011', 'Software Testing');
```

Result:

```bash
2 rows inserted. (Query took 0.0350 seconds.)
```

27. INSERT INTO SELECT:

Explanation: INSERT INTO SELECT is used to insert rows into a table by selecting data from another table.

Syntax:

```sql
INSERT INTO table_name1(column_name1, column_name2, ...)
SELECT
    column_name1,
    column_name2,
    ...
FROM
    table_name1
GROUP BY
    column_name1
LIMIT number_of_limit;
```

Example: 

```sql
INSERT INTO salary_appraisal(emp_no, appraisal)
SELECT
    emp_no,
    COUNT(salary)
FROM
    salaries
GROUP BY
    emp_no
LIMIT 3;
```

Result:

```bash
3 rows inserted. (Query took 0.1550 seconds.)
```

28. Insert On Duplicate Key Update:

Explanation: Insert On Duplicate Key Update is used to insert new rows into a table, and if a duplicate key is found, update the existing row.

Syntax:

```sql
INSERT INTO table_name1(column_name1, column_name2, ...)
VALUES(specific_value1, specific_value2, ...)
ON DUPLICATE KEY
UPDATE
    column_name1 = VALUES(column_name1), 
    column_name2 = VALUES(column_name2);
```

Example: 

```sql
INSERT INTO salary_appraisal(emp_no, appraisal)
VALUES('100010', '10')
ON DUPLICATE KEY
UPDATE
    emp_no = VALUES(emp_no), 
	appraisal = VALUES(appraisal);
```

Result:

```bash
1 row inserted. (Query took 0.0660 seconds.)
```

29. INSERT IGNORE:

Explanation: INSERT IGNORE is used to insert new rows into a table, ignoring any duplicate key errors.

Syntax:

```sql
INSERT IGNORE
INTO table_name1(column_name1, column_name2, ...)
VALUES(specific_value1, specific_value2, ...);
```

Example: 

```sql
INSERT IGNORE
INTO salary_appraisal(emp_no, appraisal)
VALUES('100010', '10');
```

Result:

```bash
1 row inserted. (Query took 0.0880 seconds.)
```

30. UPDATE:

Explanation: UPDATE is used to modify existing rows in a table.

Syntax:

```sql
UPDATE
    table_name1
SET
    column_name1 = specific_value1
WHERE
    column_name2 = specific_value2;
```

Example: 

```sql
UPDATE
    salary_appraisal
SET
    appraisal = '8'
WHERE
    emp_no = '10003';
```

Result:

```bash
1 row affected. (Query took 0.0600 seconds.)
```

31. UPDATE JOIN:

Explanation: UPDATE JOIN is used to update rows in a table based on a join with another table.

Syntax:

```sql
UPDATE
    table_name1 t
JOIN table_name2 u ON
    t.column_name1 = u.column_name2
SET
    t.column_name2 = u.column_name3;
```

Example: 

```sql
UPDATE
    salary_appraisal a
JOIN dept_emp b ON
    a.emp_no = b.emp_no
SET
    a.dept_no = b.dept_no;
```

Result:

```bash
5 rows affected. (Query took 0.0660 seconds.)
```

32. DELETE:

Explanation: DELETE is used to delete existing rows from a table.

Syntax:

```sql
DELETE
FROM
    table_name1
WHERE
    column_name1 = specific_value1;
```

Example: 

```sql
DELETE
FROM
    salary_appraisal
WHERE
    emp_no = '100010';
```

Result:

```bash
2 rows affected. (Query took 0.0910 seconds.)
```

33. DELETE JOIN:

Explanation: DELETE JOIN is used to delete rows from a table based on a join with another table.

Syntax:

```sql
DELETE
    table_name1
FROM
    table_name1
JOIN table_name2 ON table_name1.column_name1 = table_name2.column_name2;
```

Example: 

```sql
DELETE
    salary_appraisal
FROM
    salary_appraisal
JOIN employees ON salary_appraisal.emp_no = employees.emp_no;
```

Result:

```bash
3 rows affected. (Query took 0.0950 seconds.)
```

34. REPLACE:

Explanation: REPLACE is used to insert new rows into a table, and if a duplicate key is found, delete the existing row and insert the new row.

Syntax:

```sql
REPLACE
INTO table_name1(column_name1, column_name2, ...)
VALUES(specific_value1, specific_value2, ...);
```

Example: 

```sql
REPLACE
INTO salary_appraisal(emp_no, appraisal, dept_no)
VALUES('10005', '14', 'd003');
```

Result:

```bash
1 row affected. (Query took 0.0410 seconds.)
```

## Managing Database:

1. Select a Database:

Explanation: SELECT DATABASE is used to select a specific database to work with.

Syntax: 

```bash 
USE database_name
```

Syntax: 

```bash 
USE test
```

2. Create Databases:

Explanation: CREATE DATABASE is used to create a new database.

Syntax: 

```sql
CREATE DATABASE database_name;
```

Example: 

```sql
CREATE DATABASE test;
```

For more information related to this category refer [Here](create-database.md)

3. Drop Databases:

Explanation: DROP DATABASE is used to delete an existing database.

Example: 

```sql
DROP DATABASE database_name;
```

Example: 

```sql
DROP DATABASE test;
```

For more information related to this category refer [Here](drop-database.md)

## Managing Tables:

1. MySQL Storage Engines:

Explanation: MySQL supports multiple storage engines for managing tables.

Example: 

```bash
SHOW ENGINES
```

Result:

| Engine              | Support | Comment                                               | Transactions | XA  | Savepoints |
|---------------------|---------|-------------------------------------------------------|--------------|-----|------------|
| CSV                 | YES     | Stores tables as CSV files                            | NO           | NO  | NO         |
| MRG_MyISAM          | YES     | Collection of identical MyISAM tables                 | NO           | NO  | NO         |
| MEMORY              | YES     | Hash based, stored in memory, useful for temporary... | NO           | NO  | NO         |
| Aria                | YES     | Crash-safe tables with MyISAM heritage. Used for i... | NO           | NO  | NO         |
| MyISAM              | YES     | Non-transactional engine with good performance and... | NO           | NO  | NO         |
| SEQUENCE            | YES     | Generated tables filled with sequential values        | YES          | NO  | YES        |
| InnoDB              | DEFAULT | Supports transactions, row-level locking, foreign ... | YES          | YES | YES        |
| PERFORMANCE_SCHEMA  | YES     | Performance Schema                                    | NO           | NO  | NO         |

2. Create Tables:

Explanation: CREATE TABLE is used to create a new table in a database.

Syntax: 

```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    ...
);
```

For more information related to this category refer [Here](docs/create-tables.md)

3. AUTO_INCREMENT:

Explanation: AUTO_INCREMENT is used to automatically generate unique values for a column.

Syntax: 

```sql
CREATE TABLE table_name (
    id INT AUTO_INCREMENT PRIMARY KEY,
    column1 datatype,
    column2 datatype,
    ...
);
```

4. Rename Tables:

Explanation: RENAME TABLE is used to rename an existing table.

Syntax: 

```sql
RENAME TABLE old_table_name TO new_table_name;
```

Example: 

```sql
RENAME TABLE users TO employees;
```

5. Alter Tables:

Explanation: ALTER TABLE is used to modify an existing table's structure.

Syntax: 

```sql
ALTER TABLE table_name
    ADD column_name datatype,
    MODIFY column_name datatype,
    DROP column_name;
```

For more information related to this category refer [Here](docs/alter-tables.md)

6. Drop Columns:

Explanation: ALTER TABLE with DROP COLUMN is used to remove a column from an existing table.

Syntax: 

```sql
ALTER TABLE table_name DROP COLUMN column_name;
```

Example: 

```sql
ALTER TABLE employees DROP COLUMN experience;
```

7. Add Columns:

Explanation: ALTER TABLE with ADD COLUMN is used to add a new column to an existing table.

Syntax: 

```sql
ALTER TABLE table_name ADD COLUMN column_name datatype;
```

Example: 

```sql
ALTER TABLE employees ADD COLUMN experience INT;
```

8. Drop Tables:

Explanation: DROP TABLE is used to delete an existing table from the database.

Syntax: 

```sql
DROP TABLE table_name;
```

Example: 

```sql
DROP TABLE employees;
```

9. Temporary Tables:

Explanation: Temporary tables are created and used for storing temporary data.

Syntax: 

```sql
CREATE TEMPORARY TABLE temp_table_name (
    column1 datatype,
    column2 datatype,
    ...
);
```

10. Truncate Tables:

Explanation: TRUNCATE TABLE is used to delete all rows from an existing table.

Syntax: 

```sql
TRUNCATE TABLE table_name;
```

Example: 

```sql
TRUNCATE TABLE employees;
```

11. Generated Columns:

Explanation: Generated columns are computed columns whose values are automatically calculated.

Syntax: 

```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    generated_column_name datatype AS (expression) VIRTUAL,
    ...
);
```

## Mysql Constraints:

1. Primary Key:

Explanation: Primary key is used to uniquely identify each record in a table.

Syntax: 

```sql
CREATE TABLE table_name (
    id INT PRIMARY KEY,
    column1 datatype,
    column2 datatype,
    ...
);
```

2. Foreign Key:

Explanation: Foreign key is used to establish a relationship between two tables based on a column.

Syntax: 

```sql
CREATE TABLE table_name1 (
    id INT PRIMARY KEY,
    column1 datatype,
    column2 datatype,
    ...
);
```

```sql
CREATE TABLE table_name2 (
    id INT,
    column3 datatype,
    column4 datatype,
    FOREIGN KEY (id) REFERENCES table_name1(id)
);
```

3. Disable Foreign Key Checks:

Explanation: FOREIGN_KEY_CHECKS system variable is used to enable or disable foreign key checks.

Example: 

```sql
SET FOREIGN_KEY_CHECKS = 0;
-- Perform actions that would violate foreign key constraints
SET FOREIGN_KEY_CHECKS = 1;
```

4. UNIQUE Constraint:

Explanation: UNIQUE constraint ensures that values in a column or a group of columns are unique.

Syntax: 

```sql
CREATE TABLE table_name (
    id INT,
    column1 datatype,
    column2 datatype,
    UNIQUE (id)
);
```

5. NOT NULL Constraint:

Explanation: NOT NULL constraint ensures that a column cannot have NULL values.

Syntax: 

```sql
CREATE TABLE table_name (
    id INT,
    column1 datatype NOT NULL,
    column2 datatype,
    ...
);
```

6. DEFAULT Constraint:

Explanation: DEFAULT constraint sets a default value for a column if no value is provided.

Syntax: 

```sql
CREATE TABLE table_name (
    id INT,
    column1 datatype DEFAULT default_value,
    column2 datatype,
    ...
);
```

7. CHECK Constraint:

Explanation: CHECK constraint is used to enforce a condition on the values in a column.

Syntax: 

```sql
CREATE TABLE table_name (
    id INT,
    column1 datatype,
    column2 datatype,
    column3 datatype CHECK (column3 > 0),
    ...
);
```

## Mysql Datatypes

1. BIT:

Explanation: BIT data type is used to store bit-field values.

Syntax: 

```sql
column_name BIT(n);
```

2. BOOLEAN:

Explanation: BOOLEAN data type is used to store true/false values.

Syntax: 

```sql 
column_name BOOLEAN;
```

3. CHAR:

Explanation: CHAR data type is used to store fixed-length character strings.

Syntax:  

```sql
column_name CHAR(n);
```

4. DATE:

Explanation: DATE data type is used to store a date value.

Syntax:  

```sql
column_name DATE;
```

5. DATETIME:

Explanation: DATETIME data type is used to store a date and time value.

Syntax: 

```sql
column_name DATETIME;
```

6. DECIMAL:

Explanation: DECIMAL data type is used to store exact numeric values with a specified precision and scale.

Syntax: 

```sql
column_name DECIMAL(precision, scale);
```

7. ENUM:

Explanation: ENUM data type is used to store one value from a predefined list of values.

Syntax:  

```sql
column_name ENUM('value1', 'value2', ...);
```

8. INT:

Explanation: INT data type is used to store whole numbers.

Syntax: 

```sql
column_name INT;
```

9. JSON:

Explanation: JSON data type is used to store JSON (JavaScript Object Notation) documents.

Syntax:  

```sql
column_name JSON;
```

10. TIME:

Explanation: TIME data type is used to store a time value.

Syntax:  

```sql
column_name TIME;
```

11. TIMESTAMP:

Explanation: TIMESTAMP data type is used to store a timestamp value.

Syntax: 

```sql
column_name TIMESTAMP;
```

12. VARCHAR:

Explanation: VARCHAR data type is used to store variable-length character strings.

Syntax: 

```sql
column_name VARCHAR(n);
```

## Mysql Globalization:

1. MySQL Character Set:

Explanation: MySQL character set is used to define the encoding for storing textual data.

Syntax: 

```sql
ALTER TABLE table_name CONVERT TO CHARACTER SET charset_name;
```

2. MySQL Collation:

Explanation: MySQL collation is used to define the comparison rules for string data based on a specific character set.

Syntax:  

```sql
ALTER TABLE table_name CONVERT TO CHARACTER SET charset_name COLLATE collation_name;
```

## Advanced Mysql Concepts

1. Stored Procedures:

Explanation: Stored procedures are pre-written SQL statements that are stored in the database and can be executed later.

Syntax:  

```sql
CREATE PROCEDURE procedure_name()
BEGIN
    -- SQL statements here
END;
```

2. Triggers:

Explanation: Triggers are database objects that automatically execute in response to specific events, such as insert, update, or delete operations on a table.

Syntax:  

```sql
CREATE TRIGGER trigger_name
AFTER INSERT ON table_name
FOR EACH ROW
BEGIN
    -- SQL statements here
END;
```

3. Views:

Explanation: Views are virtual tables that are derived from the result of a query and can be used like regular tables.

Syntax:  

```sql
CREATE VIEW view_name AS
SELECT column1, column2
FROM table_name
WHERE condition;
```

4. Indexes:

Explanation: Indexes are data structures that improve the speed of data retrieval operations on database tables.

Syntax:  

```sql
CREATE INDEX index_name
ON table_name (column1, column2);
```

5. Administration:

Explanation: Administration refers to the tasks involved in managing and maintaining a MySQL database, such as user management, backup and restore, and performance tuning. 

- User Management: 

Syntax: 

```sql 
CREATE USER username@hostname IDENTIFIED BY 'password';
```

- Backup: 

Syntax: 

```bash
mysqldump -u username -p database_name > backup.sql
``` 

- Restore: 

Syntax: 

```bash
mysql -u username -p database_name < backup.sql
```

- Performance Tuning: Analyzing query performance, optimizing database schema, etc.

---
[&#8682; To Top](#mysql-concepts-and-examples)

[&#8962; Goto Home Page](../README.md)