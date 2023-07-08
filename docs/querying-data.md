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
JOIN table_name2 u ON
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