# MySQL-03: Execute SQL

## 1. What is an SQL file?

An **SQL file** is a plain text file (usually ending with `.sql`) that contains one or more SQL statements, for example:

```sql
CREATE DATABASE demo;
USE demo;

CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50),
    age INT
);

INSERT INTO users (name, age) VALUES ('Alice', 20);
INSERT INTO users (name, age) VALUES ('Bob', 22);
```

You typically use `.sql` files to:

-   Initialize databases
-   Create tables
-   Import data
-   Run batch operations

------

## 2. Prerequisites

Before executing an SQL file, make sure:

1.  **MySQL is installed**
2.  **MySQL server is running**
3.  You know:
    -   MySQL username (e.g. `root`)
    -   MySQL password
4.  You know where your `.sql` file is located

------

## 3. Open MySQL Command Line

### 3.1 Open a terminal

-   **Windows**: Open *Command Prompt* or *PowerShell*
-   **macOS / Linux**: Open *Terminal*

### 3.2 Log in to MySQL

```bash
mysql -u root -p
```

-   Replace `root` with your username if needed
-   Enter your password when prompted

If successful, you will see:

```text
mysql>
```

------

## 4. Method 1 (Recommended): Execute SQL File from the Shell

This is the **most common and safest method**.

### 4.1 Basic syntax

```bash
mysql -u username -p database_name < file.sql
```

### 4.2 Example

Suppose:

-   Username: `root`
-   Database: `demo`
-   SQL file: `init.sql`

```bash
mysql -u root -p demo < init.sql
```

After entering your password, MySQL will execute **all SQL statements in the file**.

✅ No output usually means **success**

------

### 4.3 If the database does NOT exist

If your SQL file already contains:

```sql
CREATE DATABASE demo;
USE demo;
```

Then run:

```bash
mysql -u root -p < init.sql
```

------

## 5. Method 2: Execute SQL File Inside MySQL (`SOURCE`)

You can also run SQL files **after entering MySQL**.

### 5.1 Enter MySQL

```bash
mysql -u root -p
```

### 5.2 Select a database (if needed)

```sql
USE demo;
```

### 5.3 Run the SQL file

```sql
SOURCE /full/path/to/init.sql;
```

⚠️ Notes:

-   Path must be **absolute**
-   **End with semicolon (`;`)**

### Example

```sql
SOURCE /Users/matt/sql/init.sql;
```

------

## 6. Common Path Examples

### macOS / Linux

```text
/home/user/init.sql
/Users/matt/init.sql
```

### Windows

```text
C:/sql/init.sql
```

(Forward slashes work best in MySQL)

------

## 7. Common Errors and Solutions

### ❌ `Access denied for user`

-   Wrong username/password
-   User lacks permission on the database

Fix:

```sql
GRANT ALL PRIVILEGES ON demo.* TO 'user'@'localhost';
FLUSH PRIVILEGES;
```

------

### ❌ `Unknown database`

The database does not exist.

Fix:

```sql
CREATE DATABASE demo;
```

Or run the SQL file **without specifying a database**.

------

### ❌ `ERROR 1064 (42000): You have an error in your SQL syntax`

-   Missing semicolon
-   Typo in SQL statement

Fix:

-   Open the `.sql` file
-   Check the line number mentioned in the error

------

## 8. Verify the Result

After execution, verify with:

```sql
SHOW DATABASES;
USE demo;
SHOW TABLES;
SELECT * FROM users;
```

------

## 9. Best Practices for Beginners

-   Always **backup your database** before running SQL files
-   Test SQL files on a **test database**
-   Use **small SQL files first**
-   Keep SQL files **well-formatted**

------

## 10. Quick Summary

| Task                           | Command                          |
| ------------------------------ | -------------------------------- |
| Execute SQL file (recommended) | `mysql -u root -p db < file.sql` |
| Execute inside MySQL           | `SOURCE /path/file.sql;`         |
| Login to MySQL                 | `mysql -u root -p`               |
| Select database                | `USE db;`                        |

