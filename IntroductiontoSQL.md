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
