# Insert Data:

1. **INSERT:**

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

2. **Insert Multiple Rows:**

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

3. **INSERT INTO SELECT:**

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

4. **Insert On Duplicate Key Update:**

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

5. **INSERT IGNORE:**

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

6. **REPLACE:**

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

---
[&#8682; To Top](#insert-data)

[&#10094; Previous Topic](./drop-table.md) &emsp; [Next Topic &#10095;](./querying-data.md)

[&#8962; Goto Home Page](../README.md)