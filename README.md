CREATE DATABASE IF NOT EXISTS manoj_db;
USE manoj_db;
CREATE TABLE Students (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    age INT,
    email VARCHAR(100)
);
INSERT INTO Students (name, age, email) VALUES
('Manoj Kumar', 22, 'manoj@example.com'),
('Aarav Singh', 20, 'aarav.singh@example.com'),
('Priya Sharma', 21, 'priya.sharma@example.com'),
('Rahul Verma', 23, 'rahul.verma@example.com'),
('Neha Patel', 22, 'neha.patel@example.com'),
('Vikram Das', 24, 'vikram.das@example.com');
CREATE TABLE Courses (
    course_id INT PRIMARY KEY AUTO_INCREMENT,
    course_name VARCHAR(100) NOT NULL,
    instructor VARCHAR(100),
    duration_weeks INT,
    start_date DATE
);
INSERT INTO Courses (course_name, instructor, duration_weeks, start_date) VALUES
('Java Programming', 'Anita Desai', 8, '2025-06-01'),
('Web Development', 'Ravi Kumar', 10, '2025-06-10'),
('Database Systems', 'Meera Iyer', 6, '2025-06-05'),
('Cloud Computing', 'Arjun Singh', 12, '2025-06-15'),
('Python for Data Science', 'Sunita Rao', 9, '2025-06-20');
CREATE TABLE Enrollments (
    enrollment_id INT PRIMARY KEY AUTO_INCREMENT,
    student_id INT,
    course_id INT,
    enrollment_date DATE DEFAULT CURRENT_DATE,
    FOREIGN KEY (student_id) REFERENCES Students(id),
    FOREIGN KEY (course_id) REFERENCES Courses(course_id)
);
INSERT INTO Enrollments (student_id, course_id) VALUES
(1, 1),  -- Manoj Kumar → Java Programming
(2, 2),  -- Midhun→ Web Development
(3, 1),  -- Pranay → Java Programming
(4, 3),  -- Rahul  → Database Systems
(5, 4),  -- Naman→ Cloud Computing
(1, 5);  -- Manoj Reddy→ Python for Data Science
SELECT 
    s.name AS student_name,
    c.course_name,
    c.instructor,
    e.enrollment_date
FROM Enrollments e
JOIN Students s ON e.student_id = s.id
JOIN Courses c ON e.course_id = c.course_id;
