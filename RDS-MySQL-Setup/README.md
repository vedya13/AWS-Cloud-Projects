# AWS RDS MySQL Setup

## Project Overview

This project demonstrates the deployment and configuration of an Amazon RDS MySQL database instance on AWS. The objective was to create a development database environment, configure connectivity, and prepare the database for application use.

---

## Scenario

A startup wants to migrate its local MySQL database to AWS. As a cloud engineer, the task was to create an Amazon RDS MySQL instance, configure networking and security settings, and establish database connectivity.

---

## Services Used

- Amazon RDS
- MySQL Community Edition
- Amazon VPC
- Security Groups
- Amazon EC2 (for database connectivity testing)

---

## Configuration Details

| Parameter | Value |
|------------|--------|
| Database Engine | MySQL Community |
| DB Instance Class | db.t3.micro |
| Storage Type | General Purpose SSD (gp3) |
| Allocated Storage | 20 GB |
| Availability | Single DB Instance |
| Public Access | Enabled |
| Database Port | 3306 |

---

## Step 1: RDS Instance Configuration

Configured the RDS MySQL instance using Full Configuration mode. Selected the Free Tier template, configured credentials, selected the db.t3.micro instance type, allocated 20 GB SSD storage, and enabled public access.

![RDS Setup Configuration]

---

## Project Status

- [x] RDS Instance Configuration Completed
- [ ] Database Available Verification
- [ ] Security Group Configuration
- [ ] Endpoint Retrieval
- [ ] EC2 Connectivity Testing
- [ ] Database Creation (dev_db)
- [ ] Database Verification

---

## Outcome

Successfully configured an Amazon RDS MySQL instance for development purposes. Additional steps include connectivity verification, database creation, and testing.
