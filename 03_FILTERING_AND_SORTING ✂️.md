# 03 - Filtering & Sorting ✂️

Raw query outputs can often contain duplicate entries or appear in an arbitrary order. SQL provides `DISTINCT`, `ORDER BY`, `LIMIT`, and `OFFSET` to clean, structure, and paginate your results.

> [!CONCEPT] 
> - `DISTINCT`: Eliminates duplicate rows from the query output. 
> - `ORDER BY`: Sorts returned rows in ascending (`ASC`) or descending (`DESC`) order. 
> - `LIMIT`: Restricts the maximum number of rows returned. 
> - `OFFSET`: Skips a specified number of rows before returning the remaining data (essential for pagination).

---
## 1. Syntax & Operators Breakdown

```SQL
SELECT DISTINCT column1, column2 FROM table_name 
WHERE condition ORDER BY column1 ASC|DESC 
LIMIT count OFFSET skip_count;
```

- **`DISTINCT`:** Removes duplicates across selected columns.
    
- **`ORDER BY`:** Defaults to `ASC` (A-Z, 0-9). Use `DESC` for reverse order (Z-A, 9-0).
    
- **`LIMIT` & `OFFSET`:** `LIMIT` defines how many rows to fetch; `OFFSET` defines how many rows to skip from the top.

## 2. Practical Examples 📝

### Target Database: `SciFi_Movies`

| **id** |  **title**   |   **director**    | **release_year** | **length_minutes** | **imdb_rating** |
| :----: | :----------: | :---------------: | :--------------: | :----------------: | :-------------: |
|   1    | Blade Runner |   Ridley Scott    |       1982       |        117         |       8.1       |
|   2    |  The Matrix  |    Wachowskis     |       1999       |        136         |       8.7       |
|   3    | Donnie Darko |   Richard Kelly   |       2001       |        113         |       8.0       |
|   4    | Interstellar | Christopher Nolan |       2014       |        169         |       8.7       |
|   5    |     Dune     | Denis Villeneuve  |       2021       |        155         |       8.0       |
|   6    |    Alien     |   Ridley Scott    |       1979       |        117         |       8.5       |
### Example A: Unique Directors (`DISTINCT`)

**Goal:** Retrieve a clean list of all directors without duplicates.

```SQL
SELECT DISTINCT director FROM SciFi_Movies;
```
#### Result Output

|     director      |
| :---------------: |
|   Ridley Scott    |
|    Wachowskis     |
|   Richard Kelly   |
| Christopher Nolan |
| Denis Villeneuve  |
### Example B: Pagination using `LIMIT` & `OFFSET`

**Goal (Page 1):** Retrieve the first 3 movies sorted alphabetically by title.

```SQL 
SELECT title, release_year FROM SciFi_Movies 
ORDER BY title ASC 
LIMIT 3;
```

#### Result Output (Page 1)

|    title     | release_year |
| :----------: | :----------: |
|    Alien     |     1979     |
| Blade Runner |     1982     |
| Donnie Darko |     2001     |
**Goal (Page 2):** Retrieve the _next_ 3 movies alphabetically, skipping the first 3.

```SQL
SELECT title, release_year FROM SciFi_Movies 
ORDER BY title ASC 
LIMIT 3 OFFSET 3;
```

#### Result Output (Page 2)

|    title     | release_year |
| :----------: | :----------: |
|     Dune     |     2021     |
| Interstellar |     2014     |
|  The Matrix  |     1999     |

---

## ⏭️ Next Step

> [!SUCCESS] Module 1 Complete! You have mastered the fundamentals of querying, filtering, pattern matching, sorting, and paginating single tables[cite: 14].
> 
> 🚀 **Coming Soon in Part 2:** Multi-table relational queries (`INNER JOIN`, `LEFT JOIN`) and data aggregations (`GROUP BY`, `HAVING`).