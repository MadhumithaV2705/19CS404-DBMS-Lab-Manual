# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
How many patients have insurance coverage valid in each year?

![image](https://github.com/user-attachments/assets/2ff3e60c-7a4a-441a-b61a-38125ba7318b)

### QUERY:
```sql
SELECT
SUBSTR(ValidityPeriod, 1, 4) AS
ValidityYear,
COUNT(DISTINCT PatientID) AS TotalPatients
FROM Insurance
GROUP BY SUBSTR(ValidityPeriod, 1, 4);

```
**Output:**

![image](https://github.com/user-attachments/assets/0d3dd0e5-985d-4866-85fd-03e6dcbc40b2)

**Question 2**
---
How many medical records does each doctor have?

![image](https://github.com/user-attachments/assets/be2ea7d8-353a-4876-b079-458016f1e517)

### QUERY:
```sql
SELECT
DoctorID,
COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY DoctorID;
```
**Output:**

![image](https://github.com/user-attachments/assets/26663ae8-361f-41bc-bd43-9ba33ebe4e3d)

**Question 3**
---
What is the total number of appointments scheduled for each day?

![image](https://github.com/user-attachments/assets/5a80932a-94dd-4009-b41d-1538e06beadc)

### QUERY:
```sql
SELECT
DATE(AppointmentDateTime) AS
AppointmentDate,
COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DATE(AppointmentDateTime);
```
**Output:**

![image](https://github.com/user-attachments/assets/84b2d94b-8429-4e2a-b458-734dbbc9684e)

**Question 4**
---
Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

![image](https://github.com/user-attachments/assets/3f21ae05-bd9d-4f40-aa78-2ad40b85a736)

### QUERY:
```sql
SELECT
COUNT(DISTINCT salesman_id) AS COUNT
FROM orders;
```
**Output:**

![image](https://github.com/user-attachments/assets/81a12684-c572-4849-95ce-1968a93d0e4e)

**Question 5**
---
Write a SQL query to find the difference between the maximum and minimum price of fruits?

![image](https://github.com/user-attachments/assets/0a874768-ae8f-41e4-80a1-45896f3af54f)

### QUERY:
```sql
SELECT
MAX(price) - MIN(price)
AS price_diff
FROM fruits;
```
**Output:**

![image](https://github.com/user-attachments/assets/1a836c7f-02b4-4f1a-a827-e3d83680c17e)

**Question 6**
---
Write a SQL query to find how many employees have an income greater than 50K?

![image](https://github.com/user-attachments/assets/9d310184-ad8b-49b0-9341-83e6a3bcf487)

### QUERY:
```sql
SELECT
COUNT(*) AS 'employees_count'
FROM employee
WHERE income > 50000;
```
**Output:**

![image](https://github.com/user-attachments/assets/d461eef2-125b-4f24-8db5-7f79f8cecd6e)

**Question 7**
---
Write a SQL query to  find the average salary of all employees?

![image](https://github.com/user-attachments/assets/2ef11b69-062a-4c97-8b5a-5b812798cc44)

### QUERY:
```sql
SELECT
AVG(income) AS 'Average_Salary'
FROM employee;
```
**Output:**

![image](https://github.com/user-attachments/assets/326455d9-a2cf-4332-8fa9-41b9c4d5d63b)

**Question 8**
---
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.

![image](https://github.com/user-attachments/assets/3e4454bf-8dd8-4ab0-8e37-0b4f5aa41ba0)

### QUERY:
```sql
SELECT
age,
MIN(income) AS 'Income'
FROM employee
GROUP BY age
HAVING MIN(income) <1000000;
```
**Output:**

![image](https://github.com/user-attachments/assets/60fba5ed-7b20-4713-81c8-be7188e898a2)

**Question 9**
---
Write the SQL query that achieves the grouping of data by city, calculates the average income for each city, and includes only those cities where the average income is greater than 500,000.

![image](https://github.com/user-attachments/assets/51fd31dd-4a3c-414a-999f-a3e1142b9a50)

### QUERY:
```sql
SELECT
city,
AVG(income) AS 'AVG(income)'
FROM employee
GROUP BY city
HAVING AVG(income) > 500000;
```
**Output:**

![image](https://github.com/user-attachments/assets/42fd89a2-3a78-447e-9a07-b0863098ee77)

**Question 10**
---
Write the SQL query that accomplishes the selection of product which has lowest price in each category from the "products" table and includes only those products where the minimum price is less than 10.

![image](https://github.com/user-attachments/assets/30418c80-dcfd-453c-9e86-63d92fa21b8b)

### QUERY:
```sql
SELECT
category_id,
MIN(price) AS 'Price'
FROM products
GROUP BY category_id
HAVING MIN(price)<10;
```
**Output:**

![image](https://github.com/user-attachments/assets/0ce20627-2424-4d1b-be9b-99634fb1e509)

### Screenshot of Module 3 SEB Completion Grade:
![image](https://github.com/user-attachments/assets/5b693285-6261-4351-8039-f8b32bab81c8)

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
