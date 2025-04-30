# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

#### ![image](https://github.com/user-attachments/assets/70d2e9d9-a23e-4b5e-8d82-37cc87087ad6)

### QUERY:
```sql
SELECT 
    s.name AS Salesman,
    c.cust_name,
    s.city
FROM 
    salesman s
JOIN 
    customer c ON s.city = c.city;
```
**Output:**

#### ![{7C8DEEAE-87BA-4127-A7AE-C6B6AD6F22BA}](https://github.com/user-attachments/assets/e5380387-067d-4d31-857c-12eefa54a608)

**Question 2**
---
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

#### ![{931A45E5-C732-49C6-927B-FB094B35A3E4}](https://github.com/user-attachments/assets/7b8accc7-ce3c-40ac-a95e-99fc187c361c)

### QUERY:
```sql
SELECT 
    o.ord_no, 
    o.purch_amt, 
    c.cust_name, 
    c.city
FROM 
    orders o
JOIN 
    customer c ON o.customer_id = c.customer_id
WHERE 
    o.purch_amt BETWEEN 500 AND 2000
ORDER BY 
    o.ord_no;
```
**Output:**
#### ![image](https://github.com/user-attachments/assets/1e0d9159-3286-4d45-80d9-3c3a02bd14b8)

**Question 3**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), with a left join on the "customer_id" column.

#### ![{8BD3A43B-938F-460E-B26B-93330C40634B}](https://github.com/user-attachments/assets/2a52616a-f59a-439c-93ad-2817981860a7)

### QUERY:
```sql
SELECT 
   cust_name
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id;
```
**Output:**

#### ![{FF9E3C19-D348-4621-8DF1-AE9AFF01F72F}](https://github.com/user-attachments/assets/7962ec0a-0198-4fe6-a8f1-6beb94778819)

**Question 4**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for test results with a test date between '2024-03-01' and '2024-03-31'.

#### ![image](https://github.com/user-attachments/assets/b9c7dec6-ac84-4592-a31a-6329ed809bf4)

### QUERY:
```sql
SELECT 
    p.*
FROM 
    patients p
INNER JOIN 
    test_results t ON p.patient_id = t.patient_id
WHERE 
    t.test_date BETWEEN '2024-03-01' AND '2024-03-31';
```
**Output:**

#### ![image](https://github.com/user-attachments/assets/9a167e7b-c150-4ba8-ae62-7c74c02da172)

**Question 5**
---
Write the SQL query that achieves the selection of the "cust_name" and "city" columns from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for customers in the city 'London'.

#### ![image](https://github.com/user-attachments/assets/ce0a7189-a3b1-4426-b961-5e7321a9d839)

### QUERY:
```sql
SELECT 
    c.cust_name, 
    c.city, 
    o.ord_no, 
    o.ord_date, 
    o.purch_amt
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
WHERE 
    c.city = 'London';
```
**Output:**

#### ![image](https://github.com/user-attachments/assets/cba5ae39-936c-42d8-8583-e673b9b77858)

**Question 6**
---
 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

#### ![{3770CC72-9E85-47F3-A703-B05CF32EEBE5}](https://github.com/user-attachments/assets/9886ae51-f6c3-498b-971d-ffd7e04a81c8)

### QUERY:
```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS "Salesman",
    s.commission
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id;
```
**Output:**

#### ![{3DAFA854-998B-4F80-9A5B-3DC9BEFA8639}](https://github.com/user-attachments/assets/895ef2e4-7db0-43e3-b359-30015c32b82d)

**Question 7**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column and a condition filtering for test results with the test name 'Blood Pressure'.

#### ![image](https://github.com/user-attachments/assets/c8bc312d-6c6d-414f-8f05-1fbff98bd9de)

### QUERY:
```sql
SELECT p.first_name AS patient_name, 
       t.*
FROM patients p
INNER JOIN test_results t ON p.patient_id = t.patient_id
WHERE p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

#### ![image](https://github.com/user-attachments/assets/4eef2b70-4271-4de4-8d1d-44420a3ccf0c)

**Question 8**
---
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  

#### ![image](https://github.com/user-attachments/assets/aca4ef83-d601-4454-8988-8b8bcdf4c83a)

### QUERY:
```sql
SELECT c.cust_name AS "Customer Name",
       c.city ,
       s.name AS "Salesman",
       s.city ,
       s.commission
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.city <> s.city
  AND s.commission > 0.12;
```
**Output:**

#### ![{AF2D39FB-016D-4DD8-B221-63F14C3FE7D4}](https://github.com/user-attachments/assets/e6fa4d65-7d4c-42a3-9be3-3324e3ef3687)

**Question 9**
---
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

#### ![image](https://github.com/user-attachments/assets/a9a2f917-d346-4192-8a00-49fd0d8a8edb)

### QUERY:
```sql
SELECT c.cust_name, c.city AS city, c.grade, s.name AS Salesman, s.city AS city
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.grade < 300
ORDER BY c.customer_id ASC;
```
**Output:**

#### ![{70D09A8D-CCC8-4773-8939-4BB874556E35}](https://github.com/user-attachments/assets/2beb1f48-5e8b-4902-a9f2-e96a432d14d9)

**Question 10**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the test name from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column.

#### ![image](https://github.com/user-attachments/assets/24901c71-fd33-49c4-b8f5-a47dae8804bf)

### QUERY:
```sql
SELECT 
    p.first_name AS patient_name, 
    t.test_name
FROM 
    patients p
INNER JOIN 
    test_results t ON p.patient_id = t.patient_id;
```
**Output:**

#### ![image](https://github.com/user-attachments/assets/bf372193-c5f8-441f-b04f-cce9e474112d)

## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
