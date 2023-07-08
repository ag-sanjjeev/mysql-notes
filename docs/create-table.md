Explanation:

The CREATE TABLE statement is used to create a new table in a database. It defines the structure of the table by specifying the column names, data types, constraints, and other attributes.

Syntax:

```sql
CREATE TABLE [IF NOT EXISTS] table_name (
    column1 datatype constraint,
    column2 datatype constraint,
    ...
    [additional_constraints]
);
```

Parameters:
- IF NOT EXISTS (optional): This keyword is used to avoid an error if the table already exists. If specified, the CREATE TABLE statement will not produce an error if the specified table already exists.

- table_name: The name of the table to be created.

- column1, column2, ...: The names of the columns in the table.

- datatype: The data type of the corresponding column.

- constraint (optional): Constraints define rules for the data in a table column, such as whether it can be NULL or have unique values. Constraints include PRIMARY KEY, FOREIGN KEY, UNIQUE, NOT NULL, and more.

- [additional_constraints] - (optional): Additional constraints can be specified after defining the columns.

Examples:

1. Create a basic table with two columns:

```sql
CREATE TABLE customers (
    id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL
);
```


This statement will create a table named "customers" with two columns - "id" of INT data type as the primary key, and "name" of VARCHAR(50) data type that cannot be NULL.

2. Create a table with multiple columns and constraints:

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE,
    department_id INT,
    FOREIGN KEY (department_id) REFERENCES departments(id)
);
```

This statement will create a table named "employees" with several columns, including a primary key, NOT NULL constraints on the "first_name" and "last_name" columns, a UNIQUE constraint on the "email" column, and a FOREIGN KEY constraint on the "department_id" column referencing the "id" column of the "departments" table.

3. Create a table with IF NOT EXISTS option:

```sql
CREATE TABLE IF NOT EXISTS products (
    id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL
);
```

This statement will create a table named "products" only if it does not already exist. If the table already exists, the statement will not produce an error and will not create a new table.

Note: The examples provided are basic illustrations of the CREATE TABLE statement. There are many more options and constraints available for creating tables in MySQL. Make sure to refer to the MySQL documentation for more detailed information and examples.