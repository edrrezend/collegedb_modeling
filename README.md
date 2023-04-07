# Relational database for college management

## Enviroment:
Microsoft SQL Server + BrModelo

### Objective:
To perform centralized control of students, teachers, courses, disciplines, academic history, and classes.

### Project phases:

•	Requirements gathering

•	Entity and relationship identification

•	E-R model

•	E-R diagram

•	Normalization

•	Implementation

•	Basic tests

### Business Rules:

•	A student can only be enrolled in one course at a time

•	Students have a unique identification code (RA)

•	Courses are composed of disciplines

•	Disciplines can be mandatory or elective, depending on the course

•	Disciplines belong to specific departments

•	Each discipline has a unique identification code

•	Students can freeze their enrollment, not being enrolled in any discipline for the semester

•	In each semester, each student can enroll in a maximum of 9 disciplines

•	A student can fail a maximum of 3 times in the same discipline.

•	The college will have a maximum of 3000 students enrolled simultaneously, in 10 different courses

•	300 new students enter each year

•	There are 90 total available disciplines

•	An academic history shows all the disciplines taken by a student, including final grades, attendance, and the period when the course was taken

•	Teachers can be registered even if they are not teaching disciplines

•	There are 40 teachers working in the school

•	Each teacher will teach a maximum of 4 different disciplines

•	Each teacher is linked to a department

•	Teachers are identified by a teacher code

### Identifying entities:

•	Students

•	Teachers

•	Disciplines

•	Departments

•	Courses

•	Academic history

•	Depends (self-relationship of Disciplines)

### Identifying associative entities:

•	teacher_discipline

•	course_discipline

•	discipline_history

### Creating conceptual, logical, and physical models:

•	Entities

•	Relationships

•	Cardinalities

•	Associative Entities

•	Attributes

•	Constraints

•	Primary and foreign keys

## Conceptual Model:

![collegeDB_concept](https://user-images.githubusercontent.com/124625776/230535395-e6ceea16-95e9-4de6-af6c-a991ebf535ed.png)

## Logical Model:

![collegeDB_logic](https://user-images.githubusercontent.com/124625776/230535193-4aff41d2-6b3f-4d9a-9c3c-754fee8c0904.png)

## Physical Model:

[collegedb_tables.txt](https://github.com/edrrezend/collegedb_modeling/files/11175909/collegedb_tables.txt)

