# SQL Student Performance Analysis

This project demonstrates the use of SQL to manage and analyze student academic data, including marks and attendance, using four tables: Students, Subjects, Scores, and Attendance.

## Project Objective
The main goal of this project is to:
- Create relational tables for students, subjects, scores, and attendance.
- Perform SQL joins to extract meaningful insights.
- Calculate subject-wise averages and student-wise performance metrics.

## Database Tables
1. **Students** – Stores student details.
2. **Subjects** – Contains subject information.
3. **Scores** – Holds marks for each student per subject.
4. **Attendance** – Tracks attendance status for each student in each subject.

## Key SQL Queries
- **Join Multiple Tables:** Combined data from all four tables to view each student's marks and attendance.
- **Average Marks by Subject:**
  ```sql
  SELECT sub.SubjectName, AVG(sc.Marks) AS AvgMarks
  FROM Scores sc
  JOIN Subjects sub ON sc.SubjectID = sub.SubjectID
  GROUP BY sub.SubjectName;

High Performance Students (with attendance filter):

SELECT s.Name, AVG(sc.Marks) AS AvgMarks,
       SUM(CASE WHEN a.Status='Present' THEN 1 ELSE 0 END)/COUNT(a.AttendanceID) AS AttendanceRatio
FROM Scores sc
JOIN Students s ON sc.StudentID = s.StudentID
LEFT JOIN Attendance a ON sc.StudentID = a.StudentID AND sc.SubjectID = a.SubjectID
GROUP BY s.Name
HAVING AVG(sc.Marks) > 70 AND 
       SUM(CASE WHEN a.Status='Present' THEN 1 ELSE 0 END)/COUNT(a.AttendanceID) > 0.5;

Project Steps

Created the database and all four tables using SQL CREATE TABLE statements.
Inserted sample data for students, subjects, scores, and attendance.
Wrote SQL queries to analyze the data.
Took screenshots of queries and their outputs.

Output Example

Subject-wise average marks displayed for each subject.
High-performance students filtered by marks and attendance criteria.
Skills Used
SQL Joins (INNER JOIN, LEFT JOIN)
GROUP BY and HAVING

Aggregate functions (AVG, SUM, COUNT)

CASE statements
How to Use This Project
Clone this repository or download the files.
Import the SQL scripts into your preferred database (MySQL, PostgreSQL, etc.).
Run the queries to reproduce the results.

Author

Harsha Sree – Beginner in SQL and Power BI, aspiring Business Analyst.

