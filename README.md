## *Performing a Conditional Search*
### **Overview**

This hands-on AWS lab demonstrates how to use conditional search queries in SQL to filter and analyze data.
You’ll connect to a MySQL database (world) hosted on Amazon RDS, using an EC2 Command Host via AWS Systems Manager (Session Manager).
The lab focuses on applying SQL operators and functions to refine query results.

---

### **Objectives & Learning Outcomes**

After completing this lab, I was able to:

Use the SELECT statement with a WHERE clause to filter records

Apply the BETWEEN operator for range-based conditions

Use the LIKE operator with wildcard (%) characters for pattern searches

Assign column aliases using the AS keyword

Use functions like SUM() and LOWER() in both SELECT and WHERE clauses


### **Architecture**
<p align="center"> <img src="architecture/database-lab-architecture.png" alt="Database Architecture" width="650"/> </p>

Architecture Summary:

User (Lab Student) connects via AWS Management Console

Amazon EC2 Command Host runs the MySQL client

Amazon RDS MySQL hosts the world database

SQL queries use conditional operators and functions to search and aggregate data

### **Commands and Steps** 
```
bash
# Step 1: Connect to the MySQL database
sudo su
cd /home/ec2-user/
mysql -u root --password='re:St@rt!9'

# Step 2: View databases and confirm 'world' exists
SHOW DATABASES;

# Step 3: Review the table data and structure
SELECT * FROM world.country;

# Step 4: Use WHERE and AND operators for conditional search
SELECT Name, Capital, Region, SurfaceArea, Population 
FROM world.country 
WHERE Population >= 50000000 AND Population <= 100000000;

# Step 5: Use BETWEEN operator for range-based search
SELECT Name, Capital, Region, SurfaceArea, Population 
FROM world.country 
WHERE Population BETWEEN 50000000 AND 100000000;

# Step 6: Use LIKE operator with wildcard to find Europe regions
SELECT SUM(Population) 
FROM world.country 
WHERE Region LIKE "%Europe%";

# Step 7: Use AS operator for column alias
SELECT SUM(Population) AS "Europe Population Total" 
FROM world.country 
WHERE Region LIKE "%Europe%";

# Step 8: Perform case-sensitive search using LOWER() function
SELECT Name, Capital, Region, SurfaceArea, Population 
FROM world.country 
WHERE LOWER(Region) LIKE "%central%";

# Step 9: Challenge - Calculate total surface area and population for North America
SELECT SUM(SurfaceArea) AS "Total Surface Area", 
       SUM(Population) AS "Total Population" 
FROM world.country 
WHERE Region LIKE "%North America%";
```

## **Screenshots**

1️⃣ 01_show_databases.png


2️⃣ 02_between_operator.png


3️⃣ 03_like_operator.png


4️⃣ 04_sum_function_alias.png


5️⃣ 05_lower_function_challenge.png


### **Tools Used**

Amazon EC2 (Command Host) – to execute SQL queries

Amazon RDS (MySQL) – hosts the world database

AWS Systems Manager (Session Manager) – for secure, browser-based shell access

MySQL Command Line Interface – for database operations

### **Key Takeaways**

Learned how to perform conditional searches with SQL operators (WHERE, AND, BETWEEN, LIKE).

Practiced using functions like SUM() and LOWER() for aggregation and case-sensitive filtering.

Understood how column aliases (AS) make results easier to read.

Strengthened understanding of query optimization and readability in cloud-based MySQL environments.

### **Author**

Amarachi Emeziem
Cloud Security & IT Support Specialist | AWS & Azure Certified

LinkedIn
 
