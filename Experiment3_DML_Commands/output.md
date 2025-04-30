Question 1
---
Increase the reorder level by 30% for products from 'Food' category having quantity in stock less than 50% of existing reorder level in the products table

![image](https://github.com/user-attachments/assets/d6808661-aec8-4bea-9770-f735352c57a3)

```sql
UPDATE products
SET reorder_lvl=reorder_lvl*1.3
WHERE category='Food'
AND quantity<(reorder_lvl*0.5);
```
**Output:**

![image](https://github.com/user-attachments/assets/27042f9c-9b4d-48b4-9cb4-7895e2f7e7b0)

**Question 2**
---
Write a SQL query to reduce the reorder level by 30% where cost price is more than 50 and quantity in stock is less than 100 in the products table.

![image](https://github.com/user-attachments/assets/d5c32f3f-5fdd-4b48-8532-d341a7a0c922)

```sql
UPDATE products
SET reorder_lvl=reorder_lvl*0.7
WHERE cost_price>50
AND quantity<100;
```
**Output:**

![image](https://github.com/user-attachments/assets/eff30eb5-026c-4c1d-b4bf-7229274fb916)

**Question 3**
---
Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'

![image](https://github.com/user-attachments/assets/19a4f90b-02e8-424b-9f0e-4aea113b78b1)

```sql
UPDATE Employees
SET salary=salary*2
WHERE department_id = 20
AND job_id LIKE '%MAN%';
```
**Output:**

![image](https://github.com/user-attachments/assets/83db1717-75ad-4f6e-954a-c190e8bcd750)

**Question 4**
---
Write a SQL statement to Change the supplier name to 'A1 Suppliers' where the supplier ID is 8 in the suppliers table.
Table info
suppliers(supplier_id,supplier_name,contact_person,phone_number,email,address)

![image](https://github.com/user-attachments/assets/f73c3402-e38a-4006-b88d-374f62afbdf5)

```sql
UPDATE suppliers
SET supplier_name='A1 Suppliers'
WHERE supplier_id=8;
```
**Output:**

![image](https://github.com/user-attachments/assets/aef9d172-1c31-47be-a469-275ac14dd908)

**Question 5**
---
Decrease the reorder level by 30 percent where the product name contains 'cream' and quantity in stock is higher than reorder level in the products table.

![image](https://github.com/user-attachments/assets/87c5babd-df6a-4f9b-b62a-4cefa0eab06c)

```sql
UPDATE products
SET reorder_lvl=reorder_lvl*0.7
WHERE product_name LIKE '%cream%'
AND quantity> reorder_lvl;
```
**Output:**

![image](https://github.com/user-attachments/assets/d70e8337-58e5-4c1e-b169-24de74c6eb49)

**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is greater than or equal to 2.

![image](https://github.com/user-attachments/assets/8f6a6974-a537-403e-b5b0-e7aba36ac36e)

```sql
DELETE FROM Customer
WHERE GRADE>=2;
```
**Output:**

![image](https://github.com/user-attachments/assets/d573d023-dfed-429d-89ab-4cee6ca9fc0d)

**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' contains the substring 'Holmes'.

![image](https://github.com/user-attachments/assets/6b01804f-61cd-44ad-9fc8-3147e5356565)

```sql
DELETE FROM Customer
WHERE CUST_NAME LIKE '%Holmes%';
```
**Output:**

![image](https://github.com/user-attachments/assets/c107cc22-9bf2-4a1d-ab53-3bc9aacae66f)

**Question 8**
---
Write a SQL query to Delete customers from 'customer' table where 'OPENING_AMT' is between 4000 and 6000.

![image](https://github.com/user-attachments/assets/c1d8810e-1435-4f20-8457-9800ff5aae71)

```sql
DELETE FROM Customer
WHERE OPENING_AMT
BETWEEN 4000 AND 6000;
```
**Output:**

![image](https://github.com/user-attachments/assets/ae244e57-7af4-412b-a7c5-de69bbaaa648)

**Question 9**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is odd.

![image](https://github.com/user-attachments/assets/e95c188c-b75b-42a2-9085-c93ba14068db)

```sql
DELETE FROM Customer
WHERE GRADE%2 !=0;
```
**Output:**

![image](https://github.com/user-attachments/assets/e425d740-c01f-48ea-855a-9fc94693d4fb)

**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is exactly 2.

![image](https://github.com/user-attachments/assets/7078a74c-6db8-42bd-9d95-f5d30913575b)

```sql
DELETE FROM Customer
WHERE GRADE=2;
```
**Output:**

![image](https://github.com/user-attachments/assets/394b6599-2392-4e16-88df-6d6138c7e187)

## RESULT:
Thus, the SQL queries to implement different types of constraints and DML commands have been executed successfully.
