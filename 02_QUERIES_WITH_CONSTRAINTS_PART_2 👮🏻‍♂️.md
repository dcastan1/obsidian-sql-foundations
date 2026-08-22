# 02 - Queries with Constraints (Part 2) 👮🏻‍♂️

Filtering string and text data often requires pattern matching rather than exact value comparisons. SQL provides string comparison operators, the `LIKE` clause, and wildcards (`%`, `_`) to search for flexible text patterns. 

> [!CONCEPT] > Text constraint filtering allows you to find exact strings, match case-insensitive patterns using wildcards, or check if a string exists within a defined list.
> 

---
## 1. Syntax & Operators Breakdown

To filter string data, use the `WHERE` clause followed by string operators:

```SQL
SELECT column1, column2 
FROM table_name 
WHERE text_column LIKE 'pattern';
```

### String Comparison Operators

|  **Operator**  |                       **Condition**                       |                     **Example**                     |
| :------------: | :-------------------------------------------------------: | :-------------------------------------------------: |
|      `=`       |                    Exact string match                     |             `director = 'Ridley Scott'`             |
|  `!=` or `<>`  |               Exact string inequality match               |             `director != 'Wachowskis'`              |
|     `LIKE`     |     Pattern match (case-insensitive in most dialects)     |               `title LIKE '%Matrix%'`               |
|   `NOT LIKE`   |                   Inverse pattern match                   |               `title NOT LIKE 'The%'`               |
|      `%`       | Wildcard: Matches **zero or more** characters[cite: 7, 8] |                 `title LIKE 'The%'`                 |
|      `_`       |  Wildcard: Matches **exactly one** character[cite: 7, 8]  |                 `title LIKE 'D_ne'`                 |
|   `IN (...)`   |   Matches any string value listed in a set[cite: 7, 8]    | `director IN ('Ridley Scott', 'Christopher Nolan')` |
| `NOT IN (...)` |    Excludes string values listed in a set[cite: 7, 8]     |          `director NOT IN ('Wachowskis')`           |
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
### Example A: Wildcard Search (`LIKE %`)

**Goal:** Find all movies that contain the word "Runner" anywhere in the title.

```SQL
SELECT title, director, release_year FROM SciFi_Movies 
WHERE title LIKE '%Runner%';
```
#### Result Output

|  **title**   | **director** | **release_year** |
| :----------: | :----------: | :--------------: |
| Blade Runner | Ridley Scott |       1982       |
### Example B: Matching a List of Strings (`IN`)

**Goal:** Retrieve all movies directed by either Ridley Scott or Christopher Nolan.

```SQL 
SELECT title, director, release_year FROM SciFi_Movies 
WHERE director IN ('Ridley Scott', 'Christopher Nolan');
```

#### Result Output

|  **title**   |   **director**    | **release_year** |
| :----------: | :---------------: | :--------------: |
| Blade Runner |   Ridley Scott    |       1982       |
| Interstellar | Christopher Nolan |       2014       |
|    Alien     |   Ridley Scott    |       1979       |

---
## Next Step ⏭️
[[Filtering and Sorting 📉]]
