SELECT AVG(grade) AS average_grade
FROM Enrollments;

SELECT Students.name, Courses.course_name
FROM Enrollments
JOIN Students ON Enrollments.student_id = Students.student_id
JOIN Courses ON Enrollments.course_id = Courses.course_id;

SELECT grade_level, COUNT(*) AS student_count
FROM Students
GROUP BY grade_level;

SELECT course_id, MAX(grade) AS max_grade
FROM Enrollments
GROUP BY course_id;

SELECT AVG(grade) AS average_grade
FROM Enrollments
JOIN Students ON Enrollments.student_id = Students.student_id
WHERE Students.grade_level = 3;

SELECT Students.name, Courses.course_name, Courses.credits
FROM Enrollments
JOIN Students ON Enrollments.student_id = Students.student_id
JOIN Courses ON Enrollments.course_id = Courses.course_id;

SELECT course_id, AVG(grade) AS average_grade
FROM Enrollments
GROUP BY course_id
HAVING AVG(grade) > 3.0;

SELECT DISTINCT Students.name
FROM Students
WHERE Students.student_id NOT IN (
    SELECT student_id
    FROM Enrollments
    WHERE grade = 4.0
);

SELECT Students.name
FROM Enrollments
JOIN Students ON Enrollments.student_id = Students.student_id
GROUP BY Students.name
HAVING AVG(grade) > (SELECT AVG(grade) FROM Enrollments);

SELECT Students.name, COUNT(Enrollments.course_id) AS course_count, AVG(Enrollments.grade) AS average_grade
FROM Enrollments
JOIN Students ON Enrollments.student_id = Students.student_id
GROUP BY Students.name;
