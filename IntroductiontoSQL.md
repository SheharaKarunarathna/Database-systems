# Introduction to SQL

## DDL and DML
### Data defining language - DDL
The SQL DDL provides commands for defining relation schemas,deleting relations and modifiying relation schemas
```
DDL changes the structure
```
### Data manipulating language - DML
Commands that insert, modify, delete, or read data inside database objects.
```
DML changes the data inside the structure
```
## SQL Integrity

**Integrity** in databases means ensuring data is **accurate, consistent, and reliable** throughout its lifecycle.

---
## SQL Data Types

SQL data types define the kind of values a column can store.

---

### 1. **String Data Types**
| Data Type          | Description | Example |
|--------------------|-------------|---------|
| `CHAR(n)`          | Fixed-length string (n chars) | `CHAR(5)` → `'ABC  '` |
| `VARCHAR(n)`       | Variable-length string (up to n chars) | `VARCHAR(20)` → `'Hello'` |
| `TEXT`             | Large variable-length text | `'This is a long paragraph...'` |

---

### 2. **Numeric Data Types**
| Data Type     | Description | Example |
|---------------|-------------|---------|
| `INT` / `INTEGER` | Whole numbers (4 bytes) | `123` |
| `SMALLINT`    | Smaller range integers (2 bytes) | `120` |
| `BIGINT`      | Large integers (8 bytes) | `9000000000` |
| `DECIMAL(p,s)` / `NUMERIC(p,s)` | Fixed-point numbers (p = total digits, s = digits after decimal) | `DECIMAL(5,2)` → `123.45` |
| `FLOAT`       | Approximate floating-point number | `123.456` |
| `REAL` / `DOUBLE` | Higher precision floating-point numbers | `3.1415926535` |

---

### 3. **Date & Time Data Types**
| Data Type     | Description | Example |
|---------------|-------------|---------|
| `DATE`        | Stores date (YYYY-MM-DD) | `2025-08-11` |
| `TIME`        | Stores time (HH:MM:SS) | `14:35:50` |
| `DATETIME`    | Stores date & time | `2025-08-11 14:35:50` |
| `TIMESTAMP`   | Stores date & time (auto updates on change) | `2025-08-11 14:35:50` |
| `YEAR`        | Stores year (2 or 4 digits) | `2025` |

---

### 4. **Boolean Data Type**
| Data Type | Description | Example |
|-----------|-------------|---------|
| `BOOLEAN` | Stores TRUE or FALSE values | `TRUE` |

---

### 5. **Binary Data Types**
| Data Type    | Description | Example |
|--------------|-------------|---------|
| `BINARY(n)`  | Fixed-length binary data | `10101010` |
| `VARBINARY(n)` | Variable-length binary data | `10101010 11110000` |
| `BLOB`       | Large binary objects (e.g., images, files) | *(binary content)* |

---

**Note:**  
- Available data types can vary slightly depending on the SQL database (MySQL, PostgreSQL, SQL Server, Oracle).
- Always choose the smallest data type that can hold your data efficiently.

varchar(10) "AVI" may or may not be equal to char(10) "AVI" so storing words in varchar mode is recommended. 
## Primary Key & Foreign Key in SQL

---

### 1. **Primary Key**
- A column (or set of columns) that **uniquely identifies** each row in a table.
- Rules:
  - Must contain **unique** values.
  - Cannot contain `NULL` values.
  - Only **one primary key** per table (but it can have multiple columns – composite key).
- Example:
  ```sql
  CREATE TABLE Students (
      StudentID INT PRIMARY KEY,
      Name VARCHAR(50),
      Age INT
  );
  
### 2. **Foreign Key**
- A column in one table that refers to the primary key in another table.
- Used to maintain referential integrity between tables.
- Can have NULL values (unless specified otherwise).

Example:
```sql
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    StudentID INT,
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID) // Here this means the foreign key StudentID should be the primary key of the Students
);
```
### Composite Keys
You can also have multiple attributes (columns) together as Primary Key or Foreign Key (composite keys).
Example:
```sql
CREATE TABLE StudentCourses (
    StudentID INT,
    CourseID INT,
    PRIMARY KEY (StudentID, CourseID),
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
    FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);
```
## Understanding Primary Key in SQL

---

### 1. **Definition**
A **Primary Key** is a column (or set of columns) in a table that **uniquely identifies** each row in that table.

Think of it like a **National ID number**:
- Every person has a unique ID.
- No two people share the same ID.
- An ID must always exist (cannot be empty).

---

### 2. **Rules of Primary Key**
- **Uniqueness:** No two rows can have the same primary key value.
- **No NULLs:** Every row must have a value for the primary key.
- **One per table:** A table can have only one primary key (but it can contain multiple columns – composite key).

---

### 3. **Example**
```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(50),
    Age INT
);
```
Here:
StudentID is Primary Key.
It makes sure no two students have the same ID.
You cannot insert a student without an ID or with an already-used ID.

4. Composite Primary Key
Sometimes a unique row is identified by more than one column combined.

```sql
CREATE TABLE Enrollments (
    StudentID INT,
    CourseID INT,
    PRIMARY KEY (StudentID, CourseID)
);
```
Here:
The combination of (StudentID, CourseID) is unique.
A student can enroll in multiple courses, but not the same course twice.
## DROP, DELETE, and ALTER TABLE in SQL

---

### 1. **DROP**
- Completely **removes a table** (structure + all data).
- Once dropped, the table is gone and cannot be recovered (unless backed up).
- Syntax:
```sql
DROP TABLE table_name;
```
### 2. **DELETE**
Removes data from a table but keeps the table structure.
Can delete specific rows using WHERE or all rows if WHERE is omitted.

Syntax:
```sql
DELETE FROM table_name WHERE condition;
Example:
```
```sql
DELETE FROM Students WHERE Age < 18;  -- Deletes only students younger than 18
DELETE FROM Students;                 -- Deletes all rows, table remains
```
### 3. ALTER TABLE
Changes the structure of an existing table.
Common uses:

Add a column:
```sql
ALTER TABLE Students ADD Email VARCHAR(100);
```
Modify a column:
```sql
ALTER TABLE Students MODIFY Name VARCHAR(100);
Rename a column (MySQL example):
```
```sql
ALTER TABLE Students RENAME COLUMN Name TO FullName;
```
Drop a column:
```sql
ALTER TABLE Students DROP COLUMN Email;
```
## SELECT, SELECT *, and SELECT DISTINCT in SQL

---

### 1. SELECT
- Retrieves **specific columns** from a table.
- Use when you want to fetch only certain fields.
- Syntax:
```sql
  SELECT column1, column2 FROM table_name;
```
### 2. SELECT * (Select All)
Retrieves all columns from a table.
Use when you want every column without listing them individually.
Syntax:

```sql
SELECT * FROM table_name;
```
Example:
```sql
SELECT * FROM Students;
```
Result: Returns all columns (StudentID, Name, Age, etc.) for all rows.
### 3. SELECT DISTINCT
Retrieves unique rows based on the specified columns.
Removes duplicate entries in the result.
Syntax:

```sql
SELECT DISTINCT column1, column2 FROM table_name;
```
Example:

```sql
SELECT DISTINCT Age FROM Students;
```
Result: Returns each distinct age only once, even if multiple students share the same age.
