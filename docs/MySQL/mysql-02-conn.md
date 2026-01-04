# MySQL-02: Connection

Connecting to MySQL via Terminal 

## 1. Why Use the Terminal to Connect MySQL?

Using the terminal helps you:

-   Understand how MySQL actually works under the hood
-   Manage servers without GUI tools
-   Work on remote servers
-   Debug connection and permission issues

In real-world backend and server environments, **terminal access is the default**.

------

## 2. The `mysql` Client Program

When MySQL is installed, it provides a **command-line client** called:

```bash
mysql
```

This program is used to:

-   Connect to a MySQL server
-   Send SQL statements
-   Receive query results

------

## 3. Basic Connection Command

### 3.1 The Simplest Form (Local Root)

```bash
mysql -u root -p
```

What happens:

-   `-u root` → connect as user `root`
-   `-p` → prompt for password interactively

After entering the password, you will see:

```text
mysql>
```

This means **connection successful**.

------

## 4. Understanding Common Connection Flags ⭐

### 4.1 `-u` / `--user`

```bash
mysql -u username
```

-   Specifies the **MySQL user**
-   MySQL users are **not system users**

Example:

```bash
mysql -u app_user -p
```

------

### 4.2 `-p` / `--password`

```bash
mysql -p
```

-   Prompts for password securely
-   **Recommended** way

❌ Not recommended:

```bash
mysql -u root -proot123
```

Why?

-   Password appears in command history
-   Security risk

------

### 4.3 `-h` / `--host`

```bash
mysql -h hostname
```

Common values:

-   `localhost`
-   `127.0.0.1`
-   Remote IP (e.g., `192.168.1.10`)

Examples:

```bash
mysql -u root -p -h localhost
mysql -u root -p -h 127.0.0.1
```

📌 Difference:

-   `localhost` → uses Unix socket
-   `127.0.0.1` → uses TCP/IP

------

### 4.4 `-P` / `--port` (Capital P)

```bash
mysql -P 3306
```

-   Specifies MySQL port
-   Default: **3306**

Example:

```bash
mysql -u root -p -h 127.0.0.1 -P 3306
```

------

### 4.5 `-D` / `--database`

```bash
mysql -D database_name
```

-   Automatically selects a database after login

Example:

```bash
mysql -u root -p -D test_db
```

Equivalent to:

```sql
USE test_db;
```

------

### 4.6 Combine All Common Flags

```bash
mysql -u root -p -h 127.0.0.1 -P 3306 -D school
```

This is a **standard production-style connection command**.

------

## 5. Connecting to a Remote MySQL Server

```bash
mysql -u app_user -p -h 192.168.10.5 -P 3306
```

Requirements:

1.  MySQL service running
2.  User has remote permission
3.  Firewall allows port 3306

------

## 6. Check Connection Information Inside MySQL

After login:

```sql
SELECT USER();
SELECT DATABASE();
SHOW PROCESSLIST;
```

------

## 7. Using Socket to Connect (Linux / macOS)

```bash
mysql -u root -p --socket=/tmp/mysql.sock
```

Check socket location:

```bash
mysqladmin variables | grep socket
```

------

## 8. Execute SQL Directly from Terminal (Non-Interactive)

### 8.1 Run One SQL Statement

```bash
mysql -u root -p -e "SHOW DATABASES;"
```

### 8.2 Run SQL File

```bash
mysql -u root -p test_db < init.sql
```

Very common for:

-   Initialization
-   Migration
-   Batch operations

------

## 9. Common Connection Errors and Fixes

### 9.1 `Access denied for user`

```text
ERROR 1045 (28000)
```

Possible causes:

-   Wrong password
-   User has no permission
-   Host not allowed

Fix:

```sql
GRANT ALL ON db.* TO 'user'@'%';
FLUSH PRIVILEGES;
```

------

### 9.2 `Can't connect to MySQL server`

```text
ERROR 2003
```

Check:

1.  MySQL service running
2.  Host / port correct
3.  Firewall

------

### 9.3 `Unknown database`

```text
ERROR 1049
```

Fix:

```sql
SHOW DATABASES;
```

------

## 10. MySQL Connection Config File (`.my.cnf`) ⭐

Avoid typing password every time.

```ini
[client]
user=root
password=your_password
host=127.0.0.1
port=3306
```

Location:

-   Linux / macOS: `~/.my.cnf`
-   Permissions:

```bash
chmod 600 ~/.my.cnf
```

Then connect with:

```bash
mysql
```

------

## 11. Exit MySQL Properly

```sql
EXIT;
```

or

```sql
QUIT;
```

Shortcut:

```text
Ctrl + D
```

------

## 12. Best Practices (Teacher’s Advice)

1.  Always use `-p` without password
2.  Avoid using `root` for applications
3.  Learn to read error messages carefully
4.  Practice both local and remote connections
5.  Understand `localhost` vs `127.0.0.1`

------

## 13. Summary

-   `mysql` is the command-line client
-   Core flags: `-u -p -h -P -D`
-   Terminal connection is essential for real systems
-   Config files improve security and efficiency

