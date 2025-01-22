--- 
# Main-Flow-Task-2

Name: Sanskruti Thakur

Company: Main Flow Services And Technologies

Domain: SQL Developer

Duration: January 2025 to March 2025
---

# Overview of the Project

Project: Advanced Student Management System for SQL Developers  

This project focuses on the design and execution of an **Advanced Student Management System**, utilizing SQL. The primary objective is to manage student and course information efficiently while extracting meaningful insights through advanced SQL queries. The project involves creating relational tables, managing data with foreign keys, and performing complex joins and aggregations.
---

**Key Objectives**  

1. **Database Setup:**  
   - Extend the `StudentManagement` database.  
   - Create relational tables `Courses` and `Enrolments` with appropriate keys.  

2. **Data Insertion:**  
   - Populate `Courses` and `Enrolments` tables with realistic sample data.  

3. **Advanced Data Queries and Analysis:**  
   - List all students and the courses they are enrolled in.  
   - Compute the number of students enrolled in each course.  
   - Identify students enrolled in more than one course.  
   - Highlight courses with no enrollments.  
   - Determine the course with the highest enrollment.  
   - Find students not enrolled in any course.  

---

**Project Flow**

1. **Database and Table Extension:**  
   - Add relational tables to the existing `StudentManagement` database.  

2. **Data Population:**  
   - Populate `Courses` with course details and `Enrolments` with student-course associations.  

3. **Query Execution:**  
   - Perform advanced SQL queries involving joins, grouping, and aggregations.  

4. **Analysis and Insights:**  
   - Extract insights on student-course relationships and identify gaps in enrollments.  

---

**SQL Queries Used**

```sql
-- ## Creating and Populating Tables

-- Use the StudentManagement database
USE StudentManagement;

-- ### Creating the Courses Table
CREATE TABLE Courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(100) NOT NULL,
    course_description TEXT
);

-- ### Creating the Enrolments Table
CREATE TABLE Enrolments (
    enrolment_id INT PRIMARY KEY,
    student_id INT,
    course_id INT,
    enrolment_date DATE,
    FOREIGN KEY (student_id) REFERENCES Students(StudentID),
    FOREIGN KEY (course_id) REFERENCES Courses(course_id)
);

-- ### Inserting Data into Courses
INSERT INTO Courses (course_id, course_name, course_description)
VALUES
(1, 'Mathematics', 'A basic mathematics course'),
(2, 'Physics', 'An introductory course on physics'),
(3, 'Chemistry', 'Learn the basics of chemistry'),
(4, 'History', 'World history overview');

-- ### Inserting Data into Enrolments
INSERT INTO Enrolments (enrolment_id, student_id, course_id, enrolment_date)
VALUES
(1, 1, 1, '2025-01-01'),
(2, 1, 2, '2025-01-02'),
(3, 2, 3, '2025-01-03'),
(4, 3, 2, '2025-01-04');

-- ## Advanced Queries

-- ### 1. List All Students and Their Enrolled Courses
SELECT 
    s.Name AS student_name,
    c.course_name
FROM 
    Students s
INNER JOIN 
    Enrolments e ON s.StudentID = e.student_id
INNER JOIN 
    Courses c ON e.course_id = c.course_id;

-- ### 2. Find the Number of Students Enrolled in Each Course
SELECT 
    c.course_id,
    c.course_name,
    COUNT(e.student_id) AS enrolled_students
FROM 
    Courses c
LEFT JOIN 
    Enrolments e ON c.course_id = e.course_id
GROUP BY 
    c.course_id, c.course_name;

-- ### 3. List Students Enrolled in More Than One Course
SELECT 
    e.student_id,
    s.Name AS student_name,
    COUNT(e.course_id) AS courses_enrolled
FROM 
    Enrolments e
INNER JOIN 
    Students s ON e.student_id = s.StudentID
GROUP BY 
    e.student_id, s.Name
HAVING 
    COUNT(e.course_id) > 1;

-- ### 4. Find Courses with No Enrolled Students
SELECT 
    c.course_id,
    c.course_name
FROM 
    Courses c
LEFT JOIN 
    Enrolments e ON c.course_id = e.course_id
WHERE 
    e.enrolment_id IS NULL;

-- ### 5. List Courses with the Most Enrollments
SELECT 
    c.course_name, 
    COUNT(e.student_id) AS TotalEnrollments
FROM 
    Courses c
LEFT JOIN 
    Enrolments e ON c.course_id = e.course_id
GROUP BY 
    c.course_id, c.course_name
ORDER BY 
    TotalEnrollments DESC
LIMIT 1;

-- ### 6. Find Students Who Have Not Enrolled in Any Course
SELECT 
    s.StudentID, s.Name
FROM
    Students s
        LEFT JOIN
    Enrolments e ON s.StudentID = e.student_id
WHERE
    e.enrolment_id IS NULL;
```
---
![image](https://github.com/user-attachments/assets/c6597616-11d5-465a-8a29-6fd373e06e6a)
![image](https://github.com/user-attachments/assets/56d39650-1188-4e8c-ad0a-a18c691c3b20)
![image](https://github.com/user-attachments/assets/2242bc1d-8e1a-4d51-85b8-fa497be8a53d)
![image](https://github.com/user-attachments/assets/c98ddd78-4bd0-481a-989e-246145e451e3)
![image](https://github.com/user-attachments/assets/5e118ab1-4a22-4d95-8ffa-4d59cb9c55fd)
![image](https://github.com/user-attachments/assets/ddb56a76-3fc8-48a5-9ff7-f71445367047)
![image](https://github.com/user-attachments/assets/0e6f8064-b1a0-46bb-9c80-f238dbed8404)
![image](https://github.com/user-attachments/assets/cb4e0e19-f0b4-4616-bb40-62b7c428da87)
![image](https://github.com/user-attachments/assets/4889cdce-1a02-4b2c-b623-4a6bb83dd7c5)
![image](https://github.com/user-attachments/assets/e6b8f8f8-d9c6-4c06-82fd-4bac78f87878)


**Tools Used**  

1. **SQL Environment:** MySQL Workbench for query execution.  

---

**Insights and Findings**  

1. Students enrolled in multiple courses demonstrate significant academic interest.  
2. The course with the highest enrollment reflects student preferences or institutional emphasis.  
3. Identifying students without enrollments helps address inclusion gaps.  
4. Courses with zero enrollments might require review or promotional strategies.  

---

**Intended Use**  

1. Demonstrate SQL skills in relational database management and querying.  
2. Provide actionable insights for optimizing course offerings and student engagement.  
3. Serve as a reference for advanced database design and analysis practices.
