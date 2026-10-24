# student_performance.sql-
-- Student Performance Analysis
-- Project: SQL practice

SELECT
    students.name,
    students.department,
    AVG(marks.score) AS average_score,
    MAX(marks.score) AS highest_score,
    CASE
        WHEN AVG(marks.score) >= 90 THEN 'Excellent'
        WHEN AVG(marks.score) >= 80 THEN 'Good'
        ELSE 'Needs Improvement'
    END AS performance
FROM students
INNER JOIN marks
    ON students.student_id = marks.student_id
GROUP BY
    students.student_id,
    students.name,
    students.department
ORDER BY average_score DESC;
