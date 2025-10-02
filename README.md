# 🎓 SQL Practice Project_Basic — University Database

A complete **SQL practice project** designed for mastering **Primary Keys**, **Foreign Keys**, and different types of **JOINs** (`INNER`, `LEFT`, `RIGHT`) and Group by, order by clauses.  
This project is built around a **University Management System** and is perfect for beginners and intermediate learners who want hands-on SQL experience.

---

## 🧩 Database Overview

This database simulates a small **University** with three main entities:

| Table | Description |
|--------|-------------|
| **Faculty** | Stores information about faculty members (teachers). |
| **Course** | Stores all courses taught by faculty. |
| **Enrollment** | Stores student enrollments, linking courses and faculty. |

---

## 🏗️ Database Schema

### 1️⃣ Faculty Table
```sql
CREATE TABLE Faculty (
  faculty_id INT PRIMARY KEY,
  faculty_name VARCHAR(100) NOT NULL,
  designation VARCHAR(50),
  experience INT
);

INSERT INTO Faculty (faculty_id, faculty_name, designation, experience) VALUES
(101, 'Dr. Alice Martin', 'Professor', 15),
(102, 'Dr. Brian Clark', 'Associate Professor', 10),
(103, 'Dr. Clara Johnson', 'Assistant Professor', 5),
(104, 'Dr. David Lee', 'Professor', 20),
(105, 'Dr. Emma Green', 'Lecturer', 3);
------------------------------------------

CREATE TABLE Course (
  course_id INT PRIMARY KEY,
  course_name VARCHAR(100) NOT NULL,
  credits INT,
  faculty_ref INT,
  FOREIGN KEY (faculty_ref) REFERENCES Faculty(faculty_id)
);
INSERT INTO Course (course_id, course_name, credits, faculty_ref) VALUES
(201, 'Database Systems', 4, 101),
(202, 'Operating Systems', 3, 102),
(203, 'Data Structures', 4, 103),
(204, 'Artificial Intelligence', 3, 104),
(205, 'Computer Networks', 4, 105);
-------------------------------------------
CREATE TABLE Enrollment (
  enrollment_id INT PRIMARY KEY,
  student_name VARCHAR(100) NOT NULL,
  course_ref INT,
  faculty_ref INT,
  grade VARCHAR(2),
  FOREIGN KEY (course_ref) REFERENCES Course(course_id),
  FOREIGN KEY (faculty_ref) REFERENCES Faculty(faculty_id)
);
INSERT INTO Enrollment (enrollment_id, student_name, course_ref, faculty_ref, grade) VALUES
(301, 'John Doe', 201, 101, 'A'),
(302, 'Sara White', 201, 101, 'B'),
(303, 'Michael Brown', 202, 102, 'A'),
(304, 'Nina Patel', 203, 103, 'A'),
(305, 'Ryan Smith', 204, 104, 'B'),
(306, 'Lily Johnson', 205, 105, 'A');
------------------------------------------
