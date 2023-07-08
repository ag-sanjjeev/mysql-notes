Explanation:

The DROP DATABASE statement is used to delete an existing database in MySQL. It permanently removes the entire database and all its associated tables, views, indexes, and data.

Syntax:

```sql
DROP DATABASE [IF EXISTS] database_name;
```

Parameters:

- IF EXISTS (optional): This keyword is used to avoid an error if the database does not exist. If specified, the DROP DATABASE statement will not produce an error if the specified database does not exist.

- database_name: The name of the database to be dropped.

Examples:

1. Drop a database without checking if it exists:

```sql
DROP DATABASE database_name;
```

In this example, replace "database_name" with the actual name of the database you want to drop. For instance:

```sql
DROP DATABASE test;
```

This statement will drop the "test" database.

2. Drop a database with the IF EXISTS option:

```sql
DROP DATABASE IF EXISTS database_name;
```

In this example, the IF EXISTS option is used to prevent an error if the database does not exist. Replace "database_name" with the actual name of the database you want to drop. For instance:

```sql
DROP DATABASE IF EXISTS test;
```

This statement will drop the "test" database if it exists, or do nothing if it does not exist.

Note: Be cautious when using the DROP DATABASE statement as it permanently deletes the database and all its contents. Make sure to double-check the database name before executing the statement to avoid accidental data loss.