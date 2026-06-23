# Student Management System

The Student Management System is a full-stack web application developed using PHP, Python Flask, MySQL, Docker, HTML, CSS, and AWS EC2 to simplify and automate student data management for educational institutions. The application provides separate portals for administrators and students, enabling secure access to academic information, attendance records, and student management operations.

The system is designed with a modular architecture that separates administrative functionalities from student functionalities, ensuring better maintainability, scalability, and security. The frontend is developed using HTML and CSS for a clean and responsive user interface, while PHP handles backend operations such as authentication, session management, database connectivity, and CRUD operations. A Python Flask service is integrated to support additional backend functionality and containerized deployment.

MySQL is used as the relational database for storing student records, login credentials, marks, and attendance details securely. Docker and Docker Compose are used to containerize the application, making deployment easy and consistent across environments. The project can also be deployed on AWS EC2 instances for cloud hosting and real-time accessibility.

## Admin Module

The Admin module provides complete control over the application. Administrators can securely log in and perform operations such as adding students, managing marks, maintaining attendance records, viewing all students, and updating or deleting student information. The admin dashboard acts as a centralized interface for monitoring and managing academic records efficiently.

## Student Module

The Student module allows students to register and securely access the system through their login credentials. Students can view their academic performance, attendance details, and personalized dashboard information. The module is designed to provide easy and secure access to student-related data.

## Features

### Admin Features

- Admin Login
- Add Students
- Manage Student Marks
- Manage Attendance
- View All Students
- Manage Student Records
- Dashboard Access
- Session Authentication

### Student Features

- Student Registration
- Student Login
- View Marks
- View Attendance
- Dashboard Access

## Technologies Used

- Frontend: CSS
- Backend: PHP
- Microservice/API: Python Flask
- Database: MySQL
- Containerization: Docker & Docker Compose
- Cloud Platform: AWS EC2

### Python Flask API

- Total Student Count API
- MySQL Database Integration
- Flask Backend Support

## Project Objectives

The main objective of this project is to automate and simplify the management of student records in educational institutions. The application reduces manual administrative work, improves data accessibility, provides secure role-based authentication, and supports scalable cloud deployment using Docker and AWS technologies.

## Deployment Support

The project is fully containerized using Docker, allowing seamless deployment in both local and cloud environments. AWS EC2 can be used to host the application for production-level deployment and remote accessibility.

## Project architecture
```text
student_management_system/
│
├── admin/
│   ├── admin_login.php
│   ├── admin_dashboard.php
│   ├── add_student.php
│   ├── manage_marks.php
│   ├── manage_attendance.php
│   └── logout.php
│
├── student/
│   ├── register.php
│   ├── student_login.php
│   ├── student_dashboard.php
│   ├── view_marks.php
│   ├── view_attendance.php
│   └── logout.php
│
├── assets/
│   ├── css/
│   │   └── style.css
│
├── config/
│   └── db.php
│
├── python/
│   ├── app.py
│   ├── requirements.txt
│   └── Dockerfile
│
├── sql/
│   └── database.sql
│
├── Dockerfile
│
├── docker-compose.yml
│
├── .gitignore
│
├── README.md
│
└── index.php
````

## **Architecture Overview**

```text
User Browser
     │
     ▼
AWS Security Group
     │
     ▼
Amazon EC2 Instance (Ubuntu)
     │
     ▼
Docker Engine
     │
     ├── PHP + Apache Container
     └── MySQL Container
```

# Execution Steps:

## Step-1: Launch EC2 Instance

Open AWS Console --> Navigate to EC2 Dashboard --> Click Launch Instance --> Instance Configuration --> Set Value for number of instances --> select AMI (Ubuntu Server 26.04) --> Instance Type	(t2.small/t3.small) --> Key Pair (Create/Select Existing) --> Security Group (Create/Select Existing)--> Storage Volume (20 GB) 

**student-sg**  make sure to allow these in the security group inbound rules

| Type       | Port |
| ---------- | ---- |
| SSH        | 22   |
| HTTP       | 80   |
| Custom TCP | 8080 |
| Custom TCP | 5000 |


## Step-2: Connect to EC2
```bash
ssh -i Donwloads/student-key.pem ubuntu@EC2-PUBLIC-IP
```

## Step-3: Update Ubuntu
```bash
sudo apt update
sudo apt upgrade -y
```
## Step-4: Install Git
```bash
sudo apt install git -y
```
## Step-5: Install Docker Engine
```bash
sudo apt install docker.io -y

Verify:

docker --version
```

## Step-6: Enable Docker
```bash
sudo systemctl enable docker
sudo systemctl start docker

Check status:

sudo systemctl status docker

Press:

q
```

## Correct way to install Docker Compose V2 on Ubuntu


### Step 1: Set up Docker’s official repository
```bash
sudo apt update
sudo apt install ca-certificates curl gnupg lsb-release -y

sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

```
### Step 2: Update package index
```bash
  sudo apt update
 ``` 
### Step 3: Install Docker Compose plugin
```bash
  sudo apt install docker-compose-plugin -y

  docker compose version

```
  **Add your user to the Docker group**

This allows you to run Docker commands without sudo:

# Create the docker group if it doesn't exist
```bash
sudo groupadd docker
```
# Add your user to the docker group
```bash
sudo usermod -aG docker $USER
```
# Apply the group change (you need to log out and back in, or run:)
```bash
newgrp docker
```
# Test
```bash
docker ps
git clone repo-url

docker compose up --build -d
````
## Access Application
### PHP Application
http://YOUR-EC2-IP:8080
### Flask API
http://YOUR-EC2-IP:5000
### Default Admin Login

| Username       | Password |
| ---------- | ---- |
| admin        | admin123   |


### Delete Containers:
```bash
docker compose down -v
``` 
