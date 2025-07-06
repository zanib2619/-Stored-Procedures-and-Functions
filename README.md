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
INSERT INTO Students (StudentID, Name, Marks) VALUES (1, 'Zanib', 50);
INSERT INTO Students (StudentID, Name, Marks) VALUES (2, 'Fiza', 60);
```
1. CREATE PROCEDURE with Parameters and Conditional Logic

```


GO   

CREATE PROCEDURE AddMarks
    @stu_id INT,
    @marks_to_add INT
AS
BEGIN
    SET NOCOUNT ON;

    DECLARE @currentMarks INT;

    
    SELECT @currentMarks = Marks
    FROM Students
    WHERE StudentID = @stu_id;

    IF @currentMarks IS NULL
    BEGIN
        SELECT 'Student not found' AS Message;
    END
    ELSE
    BEGIN
        UPDATE Students
        SET Marks = Marks + @marks_to_add
        WHERE StudentID = @stu_id;
    END
END;


EXEC AddMarks @stu_id = 1, @marks_to_add = 10;
EXEC AddMarks @stu_id = 999, @marks_to_add = 10;
```
# CREATE FUNCTION with Parameters and Conditional Logic

```
CREATE FUNCTION dbo.GetStudentMarksOrMessage
(
    @stu_id INT
)
RETURNS VARCHAR(50)
AS
BEGIN
    DECLARE @result VARCHAR(50);
    DECLARE @marks INT;

    SELECT @marks = Marks
    FROM Students
    WHERE StudentID = @stu_id;

    IF @marks IS NULL
        SET @result = 'Student Not Found';
    ELSE
        SET @result = CAST(@marks AS VARCHAR(50));

    RETURN @result;
END;
SELECT dbo.GetStudentMarksOrMessage(1) AS Result;
SELECT dbo.GetStudentMarksOrMessage(999) AS Result;
```




   
