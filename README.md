## refer : https://sqlbolt.com/lesson/select_queries_introduction




# Database Normalization

## What is Database Normalization?
- Organizes data into multiple related tables.
- Reduces duplicate (redundant) data.
- Improves data consistency and integrity.
- Allows each type of data to grow independently.
  - Example: Engine types can be stored separately from car models.

## Advantages
- Minimizes data duplication.
- Prevents update, insert, and delete anomalies.
- Saves storage space.
- Makes database maintenance easier.
- Improves data integrity.

## Disadvantages
- Queries become more complex.
- Multiple tables need to be joined.
- Too many joins may reduce query performance on large databases.

---

# Multi-Table Queries

## Why JOIN is Needed
- In a normalized database, related information is stored in different tables.
- To retrieve complete information, we combine tables using JOIN.

Example:
- `Students` table → Student details.
- `Courses` table → Course details.
- `Enrollments` table → Links students and courses.

---

# Primary Key

- A column that uniquely identifies each row.
- Must contain unique values.
- Cannot contain NULL values.
- Commonly an auto-increment integer.
- Can also be a UUID or unique string.

Example:
```sql
StudentID
---------
1
2
3
```

---

# INNER JOIN

## Definition
- Combines rows from two tables only when the matching values exist in both tables.

## Syntax

```sql
SELECT column1, column2
FROM table1
INNER JOIN table2
ON table1.id = table2.id;
```

## How it Works
1. Takes the first table.
2. Takes the second table.
3. Compares the columns specified in the `ON` condition.
4. Returns only matching rows.
5. Ignores non-matching rows.

---

# Query Execution Order

```sql
SELECT ...
FROM table1
INNER JOIN table2
ON table1.id = table2.id
WHERE condition
ORDER BY column
LIMIT number OFFSET number;
```

Execution order:
1. FROM
2. INNER JOIN
3. ON
4. WHERE
5. SELECT
6. ORDER BY
7. LIMIT
8. OFFSET

---

# Important Note

✅ `INNER JOIN` and `JOIN` are exactly the same.

These two queries are identical:

```sql
SELECT *
FROM Students
JOIN Marks
ON Students.id = Marks.id;
```

```sql
SELECT *
FROM Students
INNER JOIN Marks
ON Students.id = Marks.id;
```

Both return **only the matching rows**.

---

# Quick Revision

- Normalization → Reduce redundancy.
- Data stored in multiple related tables.
- Primary Key → Uniquely identifies a row.
- JOIN → Combines tables.
- INNER JOIN = JOIN.
- Returns only matching rows.
- `ON` specifies the matching condition.

- LEFT JOIN keeps all rows from the primary left table.Missing matches from the right table become NULL.WHERE right_table.column IS NULL filters out everything except unmatched data.
- join structure
# LEFT JOIN table name ON table1.name=table.name 
In addition to querying and referencing raw column data with SQL, you can also use expressions to write more complex logic on column values in a query= ( / % *)
count ,sum ,avg,max,min

<img width="430" height="200" alt="image" src="https://github.com/user-attachments/assets/7d97cd8a-65d1-4e0d-98fd-fa84fa1efc9a" />

SELECT group_by_column, AGG_FUNC(column_expression) AS aggregate_result_alias, …
FROM mytable
WHERE condition
GROUP BY column
HAVING group_condition;


# SCHEMA
For example, in our Movies table, the values in the Year column must be an Integer, and the values in the Title column must be a String.
## Inserting new data
When inserting data into a database, we need to use an INSERT statement, which declares which table to write into, the columns of data that we are filling, and one or more rows of data to insert. In general, each row of data you insert should contain values for every corresponding column in the table. You can insert multiple rows at a time by just listing them sequentially.

Insert statement with values for all columns
INSERT INTO mytable
VALUES (value_or_expr, another_value_or_expr, …),
       (value_or_expr_2, another_value_or_expr_2, …),
       …;

