Explanation:

The DROP TABLE statement is used to delete an existing table in a database. It permanently removes the entire table and all its associated data and structures.

Syntax:

```sql
DROP TABLE [IF EXISTS] table_name;
```

Parameters:
- IF EXISTS (optional): This keyword is used to avoid an error if the table does not exist. If specified, the DROP TABLE statement will not produce an error if the specified table does not exist.

- table_name: The name of the table to be dropped.

Examples:

1. Drop a table without checking if it exists:

```sql
DROP TABLE table_name;
```

This statement will drop the specified table. Replace "table_name" with the actual name of the table you want to drop.

Example:

```sql
DROP TABLE customers;
```

This statement will drop the "customers" table.

2. Drop a table with the IF EXISTS option:

```sql
DROP TABLE IF EXISTS table_name;
```

This statement will drop the specified table if it exists, or do nothing if it does not exist. Replace "table_name" with the actual name of the table you want to drop.

Example:

```sql
DROP TABLE IF EXISTS customers;
```

This statement will drop the "customers" table if it exists, or do nothing if it does not exist.

Note: Be cautious when using the DROP TABLE statement as it permanently deletes the table and all its contents. Make sure to double-check the table name before executing the statement to avoid accidental data loss.