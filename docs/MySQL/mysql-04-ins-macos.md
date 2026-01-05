# MySQL-04: Ins on macOS by Homebrew

This tutorial is written for **beginners** and assumes:

-   You are using **macOS**
-   You prefer **command-line tools**
-   You already have (or are willing to install) **Homebrew**

------

## 1. What Is MySQL?

**MySQL** is a popular **open-source relational database management system (RDBMS)**.
It is widely used for:

-   Web development
-   Backend services
-   Learning SQL and databases
-   Applications using PHP, Python, Java, etc.

------

## 2. Install Homebrew (If Not Installed)

First, check whether Homebrew is installed:

```bash
brew --version
```

If you see a version number, you can skip this section.

Otherwise, install Homebrew:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

After installation, verify:

```bash
brew --version
```

------

## 3. Install MySQL via Homebrew

### 3.1 Update Homebrew

```bash
brew update
```

### 3.2 Install MySQL

```bash
brew install mysql
```

Homebrew will:

-   Download MySQL
-   Install the server and client tools
-   Configure default paths

Check installation:

```bash
mysql --version
```

You should see output like:

```text
mysql  Ver 8.0.xx for macos
```

------

## 4. Start MySQL Server

### Option 1: Start Automatically (Recommended)

```bash
brew services start mysql
```

This starts MySQL **at login**.

### Option 2: Start Manually

```bash
mysql.server start
```

To stop it later:

```bash
mysql.server stop
```

------

## 5. Secure MySQL (Important for Beginners)

Run the built-in security script:

```bash
mysql_secure_installation
```

You will be asked several questions:

Typical beginner-friendly answers:

-   **Set root password?** → `Y`
-   **Password validation plugin?** → `N` (simpler for beginners)
-   **Remove anonymous users?** → `Y`
-   **Disallow root remote login?** → `Y`
-   **Remove test database?** → `Y`
-   **Reload privilege tables?** → `Y`

------

## 6. Log In to MySQL

Log in as `root`:

```bash
mysql -u root -p
```

Enter the password you just set.

If successful, you will see:

```text
mysql>
```

This means **MySQL is running and ready** 🎉

Exit MySQL:

```sql
exit;
```

------

## 7. Common Beginner Commands

### Check MySQL Status

```bash
brew services list
```

### Restart MySQL

```bash
brew services restart mysql
```

### Stop MySQL

```bash
brew services stop mysql
```

------

## 8. Where Are MySQL Files Located? (Good to Know)

| Item           | Location                                   |
| -------------- | ------------------------------------------ |
| MySQL config   | `/opt/homebrew/etc/my.cnf` (Apple Silicon) |
| Data directory | `/opt/homebrew/var/mysql`                  |
| Socket file    | `/tmp/mysql.sock`                          |

*(On Intel Macs, paths may start with `/usr/local/`)*

------

## 9. Uninstall MySQL (If Needed)

```bash
brew uninstall mysql
brew cleanup
```

⚠️ This does **not** remove database data by default.

------

## 10. Next Steps (Recommended)

After installation, you can learn:

-   Basic SQL (`CREATE`, `INSERT`, `SELECT`)
-   Creating databases and users
-   Executing `.sql` files
-   Connecting MySQL with Python / Java / PHP