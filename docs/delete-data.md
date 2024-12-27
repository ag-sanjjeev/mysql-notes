# Delete Data:

1. **DELETE:**

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

2. **DELETE JOIN:**

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

3. **Deleting all rows from a table:**

```sql   
DELETE FROM table_name;
```   

Example:
  
```sql
DELETE FROM employees;
```   
Result: 

All rows from the "employees" table will be deleted.

4. **Deleting data using a subquery:**

```sql   
DELETE FROM table_name WHERE column_name IN (SELECT column_name FROM other_table WHERE condition);
```

Example:

```sql   
DELETE FROM employees WHERE emp_id IN (SELECT emp_id FROM terminated_employees);
```   

Result: 

All rows from the "employees" table where the "emp_id" column matches any value from the "terminated_employees" table will be deleted.

---
[&#8682; To Top](#delete-data)

[&#10094; Previous Topic](./update-data.md)

[&#8962; Goto Home Page](../README.md)