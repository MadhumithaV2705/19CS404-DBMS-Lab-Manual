# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```
**Question 1**
--
-- Insert the below data into the Student_details table, allowing the Subject and MARKS columns to take their default values.
Table Attributes are RollNo, Name, Gender

```sql
INSERT INTO Student_details (RollNo, Name, Gender)
VALUES (204, 'Samuel Black', 'M');
```
**Output:**

![{D9783C4A-030D-4671-A62A-C4E6D929FD78}](https://github.com/user-attachments/assets/b8e87c04-b91d-4d52-8213-d56c9f71995b)

**Question 2**
---
-- Write a SQL query to Add a new column mobilenumber as number in the Student_details table.

```sql
ALTER TABLE Student_details
ADD COLUMN mobilenumb number;
```
**Output:**
![{A945739D-AE5B-47F9-AED5-1FB77C1A507F}](https://github.com/user-attachments/assets/44965939-baff-4d3c-a802-2e1088a09af8)

**Question 3**
---
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql
CREATE TABLE Orders(
OrderID integer primary key,
OrderDate date not null,
CustomerID integer,
foreign key (CustomerID) references Customers(CustomerID)
);
```

**Output:**

![{306234BC-8A06-4D4D-BB4A-8EB46D0BCE76}](https://github.com/user-attachments/assets/7e55316f-9992-4c5f-9afb-13b94d030ee1)

**Question 4**
---
Insert all books from Out_of_print_books into Books
Table attributes are ISBN, Title, Author, Publisher, YearPublished

```sql
INSERT INTO Books (ISBN, Title, Author, Publisher, YearPublished)
SELECT ISBN, Title, Author, Publisher, YearPublished FROM Out_of_print_books;
```
**Output:**

![{E69ED4A2-7DA2-46D8-B85B-37B7F551BBB4}](https://github.com/user-attachments/assets/e99580fd-f9c2-4c0c-b7da-4b56e540c572)

**Question 5**
---
Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

```sql
CREATE TABLE contacts(
contact_id integer primary key,
first_name text not null,
last_name test not_null,
email text,
phone text not null CHECK(LENGTH(phone)>=10)
);
```
**Output:**
![{FAFBD9A5-BD7D-4B7C-9C07-2082CC654DA2}](https://github.com/user-attachments/assets/cee6c7d3-f84a-46ec-920a-6810cd970d31)

**Question 6**
---
create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

```sql
CREATE TABLE jobs(
job_id integer primary key,
job_title text default '',
min_salary integer default 8000,
max_salary integer default null
);
```
**Output:**
![image](https://github.com/user-attachments/assets/917efc0d-49a8-4f80-8d59-be7a62fa0301)

**Question 7**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should set NULL on updates and deletes.
item_desc and rate should not accept NULL.

```sql
CREATE TABLE item(
item_id text primary key,
item_desc text not null,
rate integer not null,
icom_id text(4),
foreign key (icom_id) references company(com_id)
ON UPDATE SET NULL
ON DELETE SET NULL
);
```

**Output:**
![image](https://github.com/user-attachments/assets/aa3b00f7-91c4-4186-ad7f-e4da99650674)

**Question 8**
---
Write a SQL query to Add a new column Mobilenumber as number in the Student_details table.
![image](https://github.com/user-attachments/assets/abf2dca0-e11b-4982-93f9-19a0c39cc1c7)

```sql
ALTER TABLE Student_details
add column Mobilenumber number;
```
**Output:**
![image](https://github.com/user-attachments/assets/302a74cf-2114-4ecf-a3ce-328ba6269710)

**Question 9**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.

```sql
CREATE TABLE item(
item_id text primary key,
item_desc text not null,
rate integer not null,
icom_id text(4),
foreign key (icom_id) references company(com_id)
ON UPDATE CASCADE
ON DELETE CASCADE
);
```
**Output:**

![image](https://github.com/user-attachments/assets/a3441f90-96e5-44ba-a8ac-c62828d44ff4)

**Question 10**
---
Insert a customer with CustomerID 301, Name Michael Jordan, Address 123 Maple St, City Chicago, and ZipCode 60616 into the Customers table.

```sql
INSERT INTO Customers(CustomerID,Name, Address, City, ZipCode)
VALUES ('301', 'Michael Jordan', '123 Maple St', 'Chicago', '60616');
```
**Output:**

![image](https://github.com/user-attachments/assets/7b91ff37-c514-42bf-a2b6-fe10e0a9c5ce)

 ## RESULT:
 Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
