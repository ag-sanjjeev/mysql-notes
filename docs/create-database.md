# Create a Database

**Explanation:**

The CREATE DATABASE statement is used in MySQL to create a new database. A database is a collection of tables, views, stored procedures, and other database objects.

Syntax: 

```sql
CREATE DATABASE database_name;
```

The `database_name` parameter specifies the name of the new database. It should be a unique identifier and follow naming conventions.

Example: 

1. **Using the CREATE DATABASE statement:**

```sql
CREATE DATABASE test;
```

Result: The "test" database is created successfully.

2. **Using the IF NOT EXISTS clause:**

```sql
CREATE DATABASE IF NOT EXISTS test;
```

Result: If the "test" database does not exist, it will be created. If it already exists, no action will be taken.

3. **Specifying character set and collation:**

```sql
CREATE DATABASE test
  CHARACTER SET utf8mb4
  COLLATE utf8mb4_general_ci;
```

Result: The "test" database is created with the specified character set (utf8mb4) and collation (utf8mb4_general_ci).

In MySQL, the CHARACTER SET and COLLATE keywords are used to specify the character set and collation for a database or table.

1. **CHARACTER SET:**
The CHARACTER SET keyword is used to define the character set for a database or table. A character set is a set of characters that can be used in a database or table. It determines the encoding used to store and retrieve character data.

In the example provided:

```sql
CHARACTER SET utf8mb4
```

The "utf8mb4" character set is specified. It is a Unicode character set that supports a wide range of characters, including emojis and special symbols.

2. **COLLATE:**
The COLLATE keyword is used to define the collation for a database or table. Collation determines the rules for comparing and sorting character data. It affects operations such as string comparison, sorting, and indexing.

In the example provided:

```sql
COLLATE utf8mb4_general_ci
```

The "utf8mb4_general_ci" collation is specified. It is a case-insensitive collation that uses the Unicode character set (utf8mb4). The "ci" stands for case-insensitive, meaning that string comparisons will ignore case differences.

By specifying the CHARACTER SET and COLLATE keywords, you ensure that the database or table is created with the appropriate character set and collation settings. This is important for correctly storing, retrieving, and manipulating character data in MySQL.

3. **Creating a database with a different name:**

```sql
CREATE DATABASE mydatabase;
```

Result: The "mydatabase" database is created successfully.

Note: The user executing the CREATE DATABASE statement should have appropriate privileges to create databases.

---
[&#8682; To Top](#create-a-database)

[&#10094; Previous Topic](./connecting-to-mysql.md) &emsp; [Next Topic &#10095;](./drop-database.md)

[&#8962; Goto Home Page](../README.md)