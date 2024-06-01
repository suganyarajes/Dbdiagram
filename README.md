#Guvi Zen Class Database Model
This repository contains the database model for the Guvi Zen class, designed using DBML (Database Markup Language). The schema includes tables for students, class sessions, and tasks, with defined relationships and constraints to ensure data integrity and efficient management.

#Project Overview
The Guvi Zen Class database is structured to manage information related to students, their classes, and the tasks they complete. The database is designed to be used with PostgreSQL.

#Database Schema
#Students Table
This table stores information about students enrolled in the Guvi Zen class.

id: Unique identifier for each student (Primary Key, Auto Increment).
name: Name of the student (Not Null).
course: Course the student is enrolled in (Not Null).
email: Email address of the student (Unique).
created_at: Timestamp of when the student record was created.
updated_at: Timestamp of the last update to the student record.
Zen_Class Table
This table stores information about each class session in the Guvi Zen class.

day: Day number of the class (Primary Key).
topic: Topic covered in the class (Not Null).
task: Task assigned during the class (Not Null).
recorded_link: Link to the recorded class session (Not Null).
mentor: Name of the mentor for the session (Default: 'vishnu').
Tasks Table
This table stores information about the tasks completed by students.

student_id: Reference to the student's ID (Foreign Key to students.id).
day: Reference to the day of the class (Foreign Key to zen_class.day).
task_completion: Status of task completion (Not Null).
DBML Representation
The schema is defined using DBML for readability and ease of use.

#dbml
Copy code
Project GuviZenClass {
    database_type: 'PostgreSQL'
    Note: 'DB model for Guvi Zen class'
}

Table students {
    id integer [primary key, increment]
    name varchar(255) [not null]
    course varchar(20) [not null]
    email varchar(100) [unique]
    created_at datetime
    updated_at datetime
}

Table zen_class {
    day integer [primary key]
    topic varchar(255) [not null]
    task varchar(255) [not null]
    recorded_link varchar(255) [not null]
    mentor varchar(255) [default: 'vishnu']
}

Table tasks {
    student_id integer [ref: > students.id]
    day integer [ref: > zen_class.day]
    task_completion varchar(255) [not null]
}
Getting Started
To set up the database:

Ensure you have PostgreSQL installed.
Use a DBML tool to convert the DBML schema to SQL.
Execute the generated SQL scripts to create the tables in your PostgreSQL database.
Contributing
Contributions are welcome! Please fork the repository and submit pull requests for any improvements or bug fixes.

#License
This project is licensed under the MIT License.
