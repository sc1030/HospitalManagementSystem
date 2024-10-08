# Hospital Management System

## Overview

The **Hospital Management System** is a Java-based application that interacts with a MySQL database to manage patient and doctor information. It provides functionalities to add patients, view patient and doctor information, and book appointments. This system makes use of JDBC (Java Database Connectivity) to perform database operations.

## Features

- Add new patients to the database.
- View existing patients.
- View doctors' information.
- Book an appointment between a patient and a doctor.

## Prerequisites

Before you begin, ensure you have the following installed on your system:

1. [Java JDK 8 or higher](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html)
2. [MySQL Server](https://dev.mysql.com/downloads/installer/)
3. MySQL JDBC Driver (included in most modern Java IDEs, or can be downloaded from [here](https://dev.mysql.com/downloads/connector/j/))

## Setup Instructions

### Step 1: Clone the Repository
Clone this repository to your local machine:
```bash
git clone https://github.com/yourusername/HospitalManagementSystem.git
Step 2: Database Setup
Log into your MySQL server:

bash
Copy code
mysql -u root -p
Create the database:

sql
Copy code
CREATE DATABASE hospital;
USE hospital;
Create the necessary tables:

sql
Copy code
CREATE TABLE patients (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    age INT,
    gender VARCHAR(10),
    address VARCHAR(255)
);

CREATE TABLE doctors (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    specialization VARCHAR(100)
);

CREATE TABLE appointment (
    id INT AUTO_INCREMENT PRIMARY KEY,
    patient_id INT,
    doctor_id INT,
    appointment_date DATE,
    FOREIGN KEY (patient_id) REFERENCES patients(id),
    FOREIGN KEY (doctor_id) REFERENCES doctors(id)
);
Step 3: Update Database Configuration
In the HospitalManagementSystem.java file, update the database credentials with your MySQL server information:

java
Copy code
private static final String url = "jdbc:mysql://localhost:3306/hospital";
private static final String username = "root";
private static final String password = "YourPasswordHere";
