**Question 1**
--
Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.
Employees table
---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```sql
UPDATE employees
SET email = 'Unavailable';
```
**Output:**
![{3369C292-94C6-4E7E-8F92-76F8A3A48817}](https://github.com/user-attachments/assets/d8e7f1c2-177b-4505-b9b2-94882a503ee3)

**Question 2**
Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.
Employees table
---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```sql
UPDATE EMPLOYEES
SET email = 'not available',
    commission_pct=0.55
WHERE department_id = 110;
```
**Output:**
![{6FB23C0C-0258-41A8-A4CB-7137FB3A79AE}](https://github.com/user-attachments/assets/2541ba62-6db2-4fb4-b484-4538d7b8eecc)

**Question 3**
---
Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.
PRODUCTS TABLE
name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
UPDATE products
SET reorder_lvl=40
WHERE category='Grocery';
```
**Output:**
![{7ADF4769-DC7A-4648-A53F-0A986151DC5E}](https://github.com/user-attachments/assets/a6475b9a-36cc-4135-a08c-0f2d148ffa5f)

**Question 4**
---
Write a SQL query to Delete customers with 'CUST_COUNTRY' 'UK' and 'WORKING_AREA' 'London' whose 'GRADE' is less than 3
![image](https://github.com/user-attachments/assets/ce2f8a14-a5d2-430f-8b18-ab4e5c235e8f)
```sql
DELETE FROM Customer
WHERE CUST_COUNTRY LIKE '%UK%' AND WORKING_AREA LIKE '%LONDON' AND GRADE < 3;
```
**Output:**
![image](https://github.com/user-attachments/assets/ca87b0a6-5997-46bb-8f39-d83003f2c4b6)

**Question 5**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3
![image](https://github.com/user-attachments/assets/d7a11f2f-3924-4990-b829-a511489a5cc2)

```sql
DELETE FROM Surgeries
WHERE surgeon_id = 3 OR surgeon_id=4;
```
**Output:**
![{823B246B-A386-4DBF-A913-F96FA9DF4574}](https://github.com/user-attachments/assets/dd4874fd-43e8-4232-9b51-18909965f00d)

**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_COUNTRY' is neither 'India' nor 'USA'.
![image](https://github.com/user-attachments/assets/dc03d99c-c094-44ce-a861-d08dacfcf197)

```sql
DELETE FROM Customer
WHERE CUST_COUNTRY NOT IN  ('India', 'USA'); 
```
**Output:**
![image](https://github.com/user-attachments/assets/ca0f244a-43f4-4dca-a3a7-e37b4c138db0)

**Question 7**
---
Write a SQL query to Delete All Doctors with a NULL Specialization

```sql
DELETE FROM Doctors
WHERE specialization IS NULL;
```
**Output:**
![{1BFBC803-5A31-42D6-903B-04C4F7548961}](https://github.com/user-attachments/assets/ca69037d-ad15-4665-a7f4-1d4535d220cd)

**Question 8**
---
Write a query to fetch details of employees with the address as “DELHI(DEL)” from EmployeeInfo table.
![image](https://github.com/user-attachments/assets/d19cb403-91ed-44c0-b162-c20e0b3c385e)

```sql
SELECT * FROM EmployeeInfo
WHERE Address LIKE '%DELHI(DEL)%';
```
**Output:**
![image](https://github.com/user-attachments/assets/0b02bd82-cebd-4e87-9fef-de619378dcf5)

**Question 9**
---
Write a query to fetch last 5 rows in EmployeeInfo table.
![image](https://github.com/user-attachments/assets/2dc65dfc-bf60-4ea9-8c3d-1dd7e7a8e095)

```sql
SELECT *
FROM EmployeeInfo
ORDER BY EmpID DESC
LIMIT 5;
```
**Output:**
![{31F96618-03FC-40EB-8D7F-6638EFFAF50B}](https://github.com/user-attachments/assets/d42ecb1d-52c3-401a-a7db-ab9df8dde820)

**Question 10**
---
Write a SQL query to find the details of those salespeople who live in cities other than Paris and Rome. Return salesman_id, name, city, commission.
![image](https://github.com/user-attachments/assets/7bd274da-0134-4ae2-9aa1-fb9f122afa62)

```sql
SELECT salesman_id, name, city, commission
FROM salesman
WHERE city NOT IN ('Paris', 'Rome');
```
**Output:**
![image](https://github.com/user-attachments/assets/70e6747c-7dc2-4a98-b8ed-6fd3a1a8f17b)

## RESULT:
Thus, the SQL queries to implement different types of constraints and DML commands have been executed successfully

![Output10](output.png)
