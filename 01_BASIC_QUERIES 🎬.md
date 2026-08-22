# 01 - Basic Tables & Queries 🎬
One of the most fundamental and frequent operations in SQL is selecting specific columns from a database table. This is accomplished using the **`SELECT`** statement.

> [!CONCEPT]
> The `SELECT` statement is the foundation of SQL. It allows you to query a database and retrieve specific data from one or more tables.

---

## 1.  Syntax Breakdown 
To retrieve specific columns from a table, use the following syntax:

```sql
SELECT column1, column2
FROM table_name;
```

- **Selecting Multiple Columns:** Separate each column name with a comma (`,`).
    
- **The `FROM` Clause:** Tells SQL exactly which table to retrieve the data from.

### Selecting All Columns

To retrieve **all columns** available in a table, use the asterisk (`*`) wildcard:

```sql
SELECT * FROM table_name;
```

>[!TIP] Best Practice
> While `SELECT *` is great for quick data exploration, explicitly naming your columns in production queries improves performance and maintainability.


---
##  2. Practical Example 📝

### Target Database: `Movies`

| **id** |  **title**   |   **director**    | **release_year** | **length_minutes** | **imdb_rating** |
| :----: | :----------: | :---------------: | :--------------: | :----------------: | :-------------: |
|   1    | Blade Runner |   Ridley Scott    |       1982       |        117         |       8.1       |
|   2    |  The Matrix  |    Wachowskis     |       1999       |        136         |       8.7       |
|   3    | Donnie Darko |   Richard Kelly   |       2001       |        113         |       8.0       |
|   4    | Interstellar | Christopher Nolan |       2014       |        169         |       8.7       |
|   5    |     Dune     | Denis Villeneuve  |       2021       |        155         |       8.0       |
|   6    |    Alien     |   Ridley Scott    |       1979       |        117         |       8.5       |

### Example A: Retrieving a Single Column

**Goal:** Retrieve only the movie titles.

```sql
SELECT title
FROM Movies;
```

### Result Output

|  **title**   |
| :----------: |
| Blade Runner |
|  The Matrix  |
| Donnie Darko |
| Interstellar |
|     Dune     |
|    Alien     |
### Example B: Retrieving Multiple Columns

**Goal:** Retrieve movie titles along with their duration in minutes.

```SQL
SELECT title, length_minutes 
FROM Movies;
```

#### Result Output

|  **title**   | **length_minutes** |
| :----------: | :----------------: |
| Blade Runner |        117         |
|  The Matrix  |        136         |
| Donnie Darko |        113         |
| Interstellar |        169         |
|     Dune     |        155         |
|    Alien     |        117         |

---

## Next Step ⏭️
[[02_QUERIES_WITH_CONSTRAINTS_PART_1 👮🏽]]
