Explanation:

The ALTER TABLE statement is used to modify an existing table in a database. It allows you to add, modify, or delete columns, change data types, add or remove constraints, and perform other table-level modifications.

Syntax:

```sql
ALTER TABLE table_name
    [alter_specification]
    [alter_specification]
    ...
```

Parameters:
- table_name: The name of the table to be altered.

- alter_specification: The alteration specification defines the modification to be made to the table. It can include multiple alteration statements separated by commas.

Alteration Statements:
1. ADD COLUMN:

```sql
ALTER TABLE table_name
    ADD COLUMN column_name datatype [constraint];
```

This statement adds a new column to the table.

Example:

```sql
ALTER TABLE customers
    ADD COLUMN age INT;
```

This statement adds a column named "age" with the INT datatype to the "customers" table.

2. MODIFY COLUMN:

```sql
ALTER TABLE table_name
    MODIFY COLUMN column_name datatype [constraint];
```

This statement modifies the datatype or constraints of an existing column.

Example:

```sql
ALTER TABLE customers
    MODIFY COLUMN age TINYINT NOT NULL;
```

This statement modifies the "age" column in the "customers" table to have the TINYINT datatype and be NOT NULL.

3. DROP COLUMN:

```sql
ALTER TABLE table_name
    DROP COLUMN column_name;
```

This statement removes an existing column from the table.

Example:

```sql
ALTER TABLE customers
    DROP COLUMN age;
```

This statement removes the "age" column from the "customers" table.

4. ADD CONSTRAINT:

```sql
ALTER TABLE table_name
    ADD CONSTRAINT constraint_name constraint_type (column_name);
```

This statement adds a constraint to the table, such as a primary key, foreign key, or unique constraint.

Example:

```sql
ALTER TABLE orders
    ADD CONSTRAINT fk_customer_id FOREIGN KEY (customer_id) REFERENCES customers(id);
```

This statement adds a foreign key constraint named "fk_customer_id" to the "orders" table, referencing the "id" column in the "customers" table.

Note: The examples provided are basic illustrations of the ALTER TABLE statement. There are many more alteration options available for modifying tables in MySQL. Make sure to refer to the MySQL documentation for more detailed information and examples.