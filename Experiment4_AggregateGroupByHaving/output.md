**Question 1**
--
How many medical records does each doctor have?

![image](https://github.com/user-attachments/assets/dd908901-7e06-4a9c-baef-6c4598706dea)

```sql
SELECT
DoctorID,
COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY DoctorID;
```
**Output:**

![image](https://github.com/user-attachments/assets/e4a58d71-417d-4be9-b5d1-e782e8c91afa)

**Question 2**
---
What is the total number of appointments scheduled for each day?
Table: Appointments
name                 type
-------------------  ----------
AppointmentID        INTEGER
PatientID            INTEGER
DoctorID             INTEGER
AppointmentDateTime  DATETIME
Purpose              TEXT
Status               TEXT

![image](https://github.com/user-attachments/assets/f77047ea-d15d-4488-89e9-ced5511419af)

```sql
SELECT
DATE(AppointmentDateTime) AS
AppointmentDate,
COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DATE(AppointmentDateTime);
```
**Output:**

![{DA566AA8-4334-490C-ADB8-65C100C1FB8C}](https://github.com/user-attachments/assets/f1ca1b81-3307-4fd5-b9b0-3605c83f7199)

**Question 3**
---
Write a SQL query that counts the number of unique salespeople. Return number of salespeople.
Sample table: orders
ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001

```sql
SELECT
COUNT(DISTINCT salesman_id) AS COUNT
FROM orders;
```
**Output:**

![image](https://github.com/user-attachments/assets/e5ffdfd5-b70d-44b3-865a-ea09436739c6)

**Question 4**
---
Write a SQL query to find the difference between the maximum and minimum price of fruits?

![image](https://github.com/user-attachments/assets/5bb0007a-8a9c-4b1b-90a3-2edbc37022af)

```sql
SELECT
MAX(price) - MIN(price)
AS price_diff
FROM fruits;
```
**Output:**

![image](https://github.com/user-attachments/assets/093d45d9-176e-4442-be51-8ef5cd649bcc)

**Question 5**
---
Write a SQL query to find how many employees have an income greater than 50K?

![image](https://github.com/user-attachments/assets/adc07e67-4b6e-470f-88c7-c2611d7a3976)

```sql
SELECT
COUNT(*) AS 'employees_count'
FROM employee
WHERE income > 50000;
```
**Output:**

![image](https://github.com/user-attachments/assets/d51bcce5-a70e-4589-af44-1bebfe49b84b)

**Question 6**
---
Write a SQL query to  find the average salary of all employees?

![image](https://github.com/user-attachments/assets/2a43e9b9-00ba-42c5-93f5-d7aacdb7f52d)

```sql
SELECT
AVG(income) AS 'Average_Salary'
FROM employee;
```
**Output:**

![image](https://github.com/user-attachments/assets/198fc1c5-e5c0-4cb6-a48a-0bc60c2e1116)

**Question 7**
---
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.

![image](https://github.com/user-attachments/assets/d0c05c1e-90aa-47ef-917b-72c4de41b935)

```sql
SELECT
age,
MIN(income) AS 'Income'
FROM employee
GROUP BY age
HAVING MIN(income) <1000000;
```
**Output:**

![{B21F4764-C98D-4AEA-997A-35461D5E388E}](https://github.com/user-attachments/assets/8a7f7bfd-0794-40b1-a5ba-94807e1bee85)

**Question 8**
---
Write the SQL query that achieves the grouping of data by city, calculates the average income for each city, and includes only those cities where the average income is greater than 500,000.

![image](https://github.com/user-attachments/assets/b6c5109e-5fb3-4b28-8943-6cd8f5c222e2)

```sql
SELECT
city,
AVG(income) AS 'AVG(income)'
FROM employee
GROUP BY city
HAVING AVG(income) > 500000;
```
**Output:**

![image](https://github.com/user-attachments/assets/8612f6d4-e106-4928-b57b-02b69cdb3360)

**Question 9**
---
Write the SQL query that accomplishes the selection of product which has lowest price in each category from the "products" table and includes only those products where the minimum price is less than 10.

![image](https://github.com/user-attachments/assets/c3519640-69cc-4821-b750-1e86053c81ef)

```sql
SELECT
category_id,
MIN(price) AS 'Price'
FROM products
GROUP BY category_id
HAVING MIN(price)<10;
```
**Output:**

![{2A8A4E00-81F6-4C92-BBEA-BD0646F2EA71}](https://github.com/user-attachments/assets/e4c3855c-2ecd-4a0c-b41d-c4ae29203054)

**Question 10**
---
Write a SQL query to find  how many employees work in California?

![image](https://github.com/user-attachments/assets/bed2a74e-6b63-424a-a310-c202d9509f90)

```sql
SELECT
COUNT(*) AS 'employees_in_california'
FROM employee
WHERE city='California';
```
**Output:**

![{B5B6B0A0-FF4F-4C5F-93CC-6C174E5F06B4}](https://github.com/user-attachments/assets/c18129fb-279d-4c33-8738-9ec9bc4fdba1)

## RESULT:
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
