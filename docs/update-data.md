1. UPDATE:

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

2. UPDATE JOIN:

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

3. Updating data based on a subquery:
   
```sql
   UPDATE table_name SET column_name = (SELECT new_value FROM other_table WHERE condition) WHERE condition;
```

Example:
   
```sql
   UPDATE employees SET salary = (SELECT AVG(salary) FROM other_table) WHERE department = 'Finance';
```   
Result: 

The "salary" column will be updated to the average salary from the "other_table" for all rows where "department" is 'Finance'.

4. Updating data using a case statement:
   
```sql
   UPDATE table_name SET column_name = CASE WHEN condition THEN value1 ELSE value2 END WHERE condition;
```  
Example:
   
```sql
   UPDATE employees SET salary = CASE WHEN experience > 5 THEN salary * 1.1 ELSE salary * 1.05 END;
```   
Result: 

The "salary" column will be updated to 10% higher for employees with more than 5 years of experience, and 5% higher for others.
