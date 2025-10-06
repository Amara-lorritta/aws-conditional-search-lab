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

---

### **Architecture**
<img width="1536" height="1024" alt="ed5c1026-12b8-4aa9-b71f-6a10db0ebb83" src="https://github.com/user-attachments/assets/d598006e-47ef-4802-b4ef-722809045c91" />

Architecture Summary:

User (Lab Student) connects via AWS Management Console

Amazon EC2 Command Host runs the MySQL client

Amazon RDS MySQL hosts the world database

SQL queries use conditional operators and functions to search and aggregate data

---

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

---

## **Screenshots**

01_show_databases.png
<img width="1100" height="501" alt="Screenshot 2025-10-06 054122" src="https://github.com/user-attachments/assets/3aaf294b-b7fe-4be6-a0de-3ecff949fcbd" />

2️⃣ 02_between_operator.png
<img width="1347" height="424" alt="Screenshot 2025-10-06 055754" src="https://github.com/user-attachments/assets/b3e16e49-6ce9-4099-9c6c-c7ccd75be485" />

3️⃣ 03_like_operator.png
<img width="1096" height="382" alt="Screenshot 2025-10-06 060255" src="https://github.com/user-attachments/assets/643262fe-2edd-4836-942d-93208ac495ef" />

4️⃣ 04_sum_function_alias.png
<img width="1546" height="216" alt="Screenshot 2025-10-06 060744" src="https://github.com/user-attachments/assets/3d3c536e-d5c4-4bc1-b8f5-13816f30f058" />

---

### **Tools Used**

Amazon EC2 (Command Host) – to execute SQL queries

Amazon RDS (MySQL) – hosts the world database

AWS Systems Manager (Session Manager) – for secure, browser-based shell access

MySQL Command Line Interface – for database operations

---

### **Key Takeaways**

Learned how to perform conditional searches with SQL operators (WHERE, AND, BETWEEN, LIKE).

Practiced using functions like SUM() and LOWER() for aggregation and case-sensitive filtering.

Understood how column aliases (AS) make results easier to read.

Strengthened understanding of query optimization and readability in cloud-based MySQL environments.

---

### **Author**

Amarachi Emeziem
Cloud Security & IT Support Specialist | AWS & Azure Certified

LinkedIn: https://www.linkedin.com/in/amarachilemeziem/
 
