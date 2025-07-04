# -Stored-Procedures-and-Functions
# SQL Procedures and Functions with Parameters and Conditional Logic

## 📘 Overview

This project demonstrates how to use SQL `CREATE PROCEDURE` and `CREATE FUNCTION` statements with parameters and conditional logic. These are essential tools in SQL for encapsulating complex logic, improving code reusability, and managing business rules directly in the database.

We use a simple example with a `Students` table to show how:
- A **stored procedure** can update student marks with conditional checks.
- A **user-defined function** can compute and return a student's grade based on their marks.

---

## 🧱 Table Structure

```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(50),
    Marks INT
);
```
1. CREATE PROCEDURE with Parameters and Conditional Logic
