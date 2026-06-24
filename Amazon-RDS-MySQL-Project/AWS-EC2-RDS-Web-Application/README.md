### AWS RDS with EC2 Integration

## Project Overview:-
This project demonstrates the deployment of a PHP application on an Amazon EC2 instance that connects securely to an Amazon RDS MySQL database.
The application retrieves data stored in RDS and displays it through a web interface hosted on EC2.

## Services Used
Amazon EC2
Amazon RDS MySQL
Amazon VPC
Security Groups
Apache HTTP Server
PHP
MySQL

## Architecture
```text
+----------------+
| User Browser   |
+----------------+
        |
        ▼
+----------------+
| EC2 Instance   |
| Apache + PHP   |
+----------------+
        |
        ▼
+----------------+
| RDS MySQL      |
| Private Access |
+----------------+
```

## Steps Performed
1. EC2 Setup
* Launched Amazon Linux EC2 instance
* Installed Apache Web Server
* Installed PHP and MySQL client packages
* Configured HTTP access

2. RDS Setup
* Created MySQL RDS instance
* Disabled Public Access
* Configured database credentials

3. Security Group Configuration
* Allowed HTTP traffic to EC2
* Allowed MySQL port 3306 from EC2 Security Group to RDS

4. Database Configuration
**Created Database**
```sql
CREATE DATABASE studentdb;
```
**Created Table**
```sql
CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50),
    course VARCHAR(50)
);
```
**Inserted Sample Data**
```sql
INSERT INTO students(name, course)
VALUES
('Vedant', 'DevOps'),
('Rahul', 'AWS'),
('Amit', 'Linux');
```

5. Application Deployment
Developed a PHP script that:
* Connects to Amazon RDS
* Retrieves records from MySQL database
* Displays data in a table format

## PHP Connection Script
```php
<?php

// Database Configuration
$servername = "rds-endpoint";
$username   = "username";
$password   = "password";
$dbname     = "studentdb";

// Create Connection
$conn = new mysqli(
    $servername,
    $username,
    $password,
    $dbname
);

// Check Connection
if ($conn->connect_error) {
    die("Connection Failed: " . $conn->connect_error);
}

// Query Data
$sql = "SELECT * FROM students";
$result = $conn->query($sql);

// Display Data
echo "<h2>Student Records</h2>";

if ($result && $result->num_rows > 0) {

    echo "<table border='1' cellpadding='10' cellspacing='0'>";
    echo "<tr>";
    echo "<th>ID</th>";
    echo "<th>Name</th>";
    echo "<th>Course</th>";
    echo "</tr>";

    while ($row = $result->fetch_assoc()) {

        echo "<tr>";
        echo "<td>" . $row["id"] . "</td>";
        echo "<td>" . $row["name"] . "</td>";
        echo "<td>" . $row["course"] . "</td>";
        echo "</tr>";
    }

    echo "</table>";

} else {

    echo "No records found.";
}

// Close Connection
$conn->close();

?>
```

## Screenshots
