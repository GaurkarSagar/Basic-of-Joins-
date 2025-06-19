CREATE DATABASE HARRY;
USE HARRY;

CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Age INT,
    Gender VARCHAR(10),
    City VARCHAR(50)
);

INSERT INTO Students VALUES
(1, 'Sagar', 'Gaurkar', 23, 'Male', 'Nagpur'),
(2, 'Priya', 'Sharma', 22, 'Female', 'Pune'),
(3, 'Rohan', 'Patil', 24, 'Male', 'Mumbai'),
(4, 'Neha', 'Singh', 21, 'Female', 'Nagpur'),
(5, 'Amit', 'Joshi', 25, 'Male', 'Delhi');

SELECT * FROM Students;

CREATE TABLE Courses (
    CourseID INT PRIMARY KEY,
    CourseName VARCHAR(100),
    Instructor VARCHAR(50)
);

INSERT INTO Courses VALUES
(101, 'SQL Basics', 'Mr. Verma'),
(102, 'Python Programming', 'Ms. Joshi'),
(103, 'Data Analysis', 'Dr. Khan'),
(104, 'Web Development', 'Mr. Rao');

SELECT * FROM Courses;

CREATE TABLE Enrollments (
    EnrollmentID INT PRIMARY KEY,
    StudentID INT,
    CourseID INT,
    Marks INT,
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
    FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);

INSERT INTO Enrollments VALUES
(1, 1, 101, 85),
(2, 1, 102, 78),
(3, 2, 101, 90),
(4, 3, 103, 88),
(5, 4, 102, 95),
(6, 5, 104, 80),
(7, 2, 104, 70),
(8, 3, 101, 60),
(9, 5, 103, 72),
(10, 4, 101, 91);

SELECT * FROM Enrollments;

-- List students with their courses and marks:
SELECT s.FirstName, s.LastName, c.CourseName, e.Marks 
FROM Students s
JOIN Enrollments e On s.StudentID = e.StudentID
JOIN Courses C On e.CourseID = c.CourseID;

-- Students who scored above 80:
SELECT s.FirstName, s.LastName, e.Marks
FROM Students s
Join Enrollments e On s.StudentID = e.StudentID
Where Marks > 80;# Basic-of-Joins-
