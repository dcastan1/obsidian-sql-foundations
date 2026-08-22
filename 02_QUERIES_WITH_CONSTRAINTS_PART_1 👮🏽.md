# 02 - Queries with Constraints (Part 1) 👮🏽

In real-world applications, queries rarely retrieve every single row from a database. To filter data and extract only the relevant records, SQL relies on conditional filtering using the **`WHERE`** clause.


>[!CONCEPT] 
>The `WHERE` clause allows you to filter query results by specifying exact conditions. Only rows that satisfy all criteria are returned.

---
## 1. Syntax & Operators Breakdown

To filter data, append the `WHERE` clause after `FROM`:

```sql
SELECT column1, column2 
FROM table_name 
WHERE condition;
```

### Combining Conditions

You can apply multiple constraints by linking them with logical operators:

- **`AND`**: Returns rows where **all** conditions are true.
    
- **`OR`**: Returns rows where **at least one** condition is true.

### Common Numerical & Range Operators

|          **Operator**           |               **Condition**                |           **Example**            |
| :-----------------------------: | :----------------------------------------: | :------------------------------: |
| `=`, `!=`, `<`, `<=`, `>`, `>=` |  Standard numerical comparison operators   |          `year >= 2000`          |
|      `BETWEEN ... AND ...`      |    Value falls within range (inclusive)    |   `year BETWEEN 2000 AND 2010`   |
|    `NOT BETWEEN ... AND ...`    |   Value falls outside range (inclusive)    | `year NOT BETWEEN 2000 AND 2010` |
|           `IN (...)`            |     Value exists within a defined list     |        `id IN (1, 3, 5)`         |
|         `NOT IN (...)`          | Value does not exist within a defined list |      `id NOT IN (2, 4, 6)`       |

---

## 2. Practical Examples 📝

### Target Database: `SciFi_Movies` 

| **id** |  **title**   |   **director**    | **release_year** | **length_minutes** |
| :----: | :----------: | :---------------: | :--------------: | :----------------: |
|   1    | Blade Runner |   Ridley Scott    |       1982       |        117         |
|   2    |  The Matrix  |    Wachowskis     |       1999       |        136         |
|   3    | Donnie Darko |   Richard Kelly   |       2001       |        113         |
|   4    | Interstellar | Christopher Nolan |       2014       |        169         |
|   5    |     Dune     | Denis Villeneuve  |       2021       |        155         |
|   6    |    Alien     |   Ridley Scott    |       1979       |        117         |
### Example A: Filtering by Range (`BETWEEN`)

**Goal:** Find all movies released between the years 2000 and 2015.

```sql
SELECT title, director, release_year FROM SciFi_Movies 
WHERE release_year BETWEEN 2000 AND 2015;
```

#### Result Output

|  **title**   |   **director**    | **release_year** |
| :----------: | :---------------: | :--------------: |
| Donnie Darko |   Richard Kelly   |       2001       |
| Interstellar | Christopher Nolan |       2014       |
### Example B: Combining Multiple Conditions (`AND`)

**Goal:** Find movies released after the year 2000 that are longer than 120 minutes.

```sql
SELECT title, release_year, length_minutes FROM SciFi_Movies 
WHERE release_year > 2000 AND length_minutes > 120;
```

#### Result Output

|  **title**   | **release_year** | **length_minutes** |
| :----------: | :--------------: | :----------------: |
| Interstellar |       2014       |        169         |
|     Dune     |       2021       |        155         |

---
## Next Step ⏭️

[[02_QUERIES_WITH_CONSTRAINTS_PART_2 👮🏻‍♂️]]
