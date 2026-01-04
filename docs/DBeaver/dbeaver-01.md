# DBeaver-01: Introduction

_A universal database tool for learning and daily work_

---

## 1. What is DBeaver?

**DBeaver** is a **free, open-source database management tool** that lets you:

- Connect to many databases using one interface
    
- Browse tables and data visually
    
- Write and execute SQL
    
- Import / export data
    
- Manage schemas, users, and metadata
    

### Supported databases (partial list)

- MySQL / MariaDB
    
- PostgreSQL
    
- SQLite
    
- Oracle
    
- SQL Server
    
- Redis
    
- MongoDB (read-oriented)
    
- H2 / DuckDB
    

👉 Think of DBeaver as **“VS Code for databases”**.

---

## 2. Download & Install

### Official website

[https://dbeaver.io](https://dbeaver.io/)

### Editions

- **DBeaver Community (Free)** ✅ recommended for beginners
    
- DBeaver Enterprise (Paid)
    

### Installation

- **macOS**: `.dmg`
    
- **Windows**: `.exe`
    
- **Linux**: `.deb`, `.rpm`, or AppImage
    

After installation, open DBeaver → you’ll see a **workspace** similar to an IDE.

---

## 3. DBeaver Interface Overview

When you open DBeaver, you’ll mainly see:

### 3.1 Main Panels

|Area|Name|Purpose|
|---|---|---|
|Left|**Database Navigator**|Connections, databases, tables|
|Center|**Editor Area**|SQL editor, data viewer|
|Bottom|**Output / Logs**|Query results, execution info|
|Top|**Toolbar**|Connect, SQL, commit, export|

---

## 4. Create Your First Database Connection

### Step 1: Open connection wizard

- Click **“New Database Connection”** (plug icon 🔌)
    
- Or: `Database` → `New Database Connection`
    

### Step 2: Choose database type

Example:

- Choose **MySQL**
    
- Click **Next**
    

### Step 3: Fill connection info

|Field|Example|
|---|---|
|Host|`localhost`|
|Port|`3306`|
|Database|`test`|
|Username|`root`|
|Password|******|

📌 First time?  
DBeaver will prompt you to **download JDBC driver** → click **Download**.

### Step 4: Test connection

- Click **Test Connection**
    
- Success → **Finish**
    

Your database now appears in **Database Navigator** 🎉

---

## 5. Browsing Database Objects

Expand nodes in the **Database Navigator**:

```
connection
 └── database
     ├── Schemas
     │   └── public
     │       ├── Tables
     │       ├── Views
     │       └── Indexes
```

### Common actions

- Double-click a **table** → opens data viewer
    
- Right-click → **View metadata**
    
- Right-click → **Generate SQL**
    

---

## 6. Viewing and Editing Table Data

### Open table data

- Right-click table → **View Data** → **All Rows**
    
- Or double-click the table
    

### Data Editor features

- Filter rows
    
- Sort columns
    
- Inline edit cells
    
- Add / delete rows
    

### Save changes

- Click **Save (Ctrl / Cmd + S)**
    
- Or enable **Auto-commit**
    

⚠️ If auto-commit is off, changes are NOT saved until committed.

---

## 7. Writing and Running SQL

### Open SQL Editor

- Right-click database → **SQL Editor** → **New SQL Script**
    
- Or shortcut: `Ctrl / Cmd + ]`
    

### Example SQL

```sql
SELECT *
FROM users
WHERE age > 18;
```

### Execute

|Action|Shortcut|
|---|---|
|Execute current statement|`Ctrl / Cmd + Enter`|
|Execute script|`Alt + X`|

Results appear in the **bottom panel**.

---

## 8. Transactions & Auto-Commit (Important!)

### Auto-commit ON (default for beginners)

- Each SQL runs immediately
    
- No rollback possible
    

### Auto-commit OFF

- You must manually:
    
    - **Commit**
        
    - or **Rollback**
        

Toolbar buttons:

- ✅ Commit
    
- ❌ Rollback
    

👉 Beginners: keep **Auto-commit ON** until you learn transactions.

---

## 9. Import & Export Data

### Export table data

- Right-click table → **Export Data**
    
- Formats:
    
    - CSV
        
    - Excel
        
    - SQL INSERT
        
    - JSON
        

### Import data

- Right-click table → **Import Data**
    
- Map columns visually
    

Very useful for:

- Homework
    
- Experiments
    
- Data migration
    

---

## 10. Useful Beginner Features

### 10.1 Generate SQL automatically

Right-click table → **Generate SQL**

- SELECT
    
- INSERT
    
- UPDATE
    
- DELETE
    
- CREATE
    

Great for learning SQL syntax.

---

### 10.2 ER Diagram

- Select multiple tables
    
- Right-click → **ER Diagram**
    

Helps understand:

- Primary keys
    
- Foreign keys
    
- Relationships
    

---

### 10.3 Metadata View

- Table structure
    
- Column types
    
- Indexes
    
- Constraints
    

---

## 11. Common Beginner Mistakes

❌ Forgetting to commit  
❌ Editing production database accidentally  
❌ Running DELETE without WHERE  
❌ Mixing multiple databases in one SQL editor

✔ Tip: Always **check active connection** in SQL editor top bar.

---

## 12. Recommended Beginner Workflow

1. Connect database
    
2. Browse tables
    
3. View data
    
4. Generate SQL
    
5. Modify small data
    
6. Learn SELECT → UPDATE → DELETE
    
7. Export results
    

---

## 13. When Should You Use DBeaver?

Use DBeaver if you:

- Learn databases / SQL
    
- Work with multiple DB types
    
- Prefer GUI + SQL combined
    
- Want a free, professional tool
    

---

## 14. Next Steps (Advanced Topics)

Once comfortable, learn:

- Transaction isolation levels
    
- SQL execution plans
    
- SSH tunneling
    
- Database user management
    
- Version-controlled SQL scripts
    