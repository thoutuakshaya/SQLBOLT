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
