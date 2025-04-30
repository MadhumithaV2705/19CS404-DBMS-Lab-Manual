**Question 1**
--
Write a SQL query to Add a new column mobilenumber as number in the Student_details table.
Sample table: Student_details

![image](https://github.com/user-attachments/assets/50b82986-2ad7-4c52-9270-69b0dfdab1d7)

### QUERY:
```sql
ALTER TABLE Student_details
ADD COLUMN mobilenumb number;

```
**Output:**

![image](https://github.com/user-attachments/assets/b7d633f4-11a1-4634-9810-ba9ca1545810)

**Question 2**
---
Write an SQL command can to add a column named email of type TEXT to the customers table

![image](https://github.com/user-attachments/assets/765b9980-e7aa-4b86-925f-5b8b1d5de207)

### QUERY:
```sql
ALTER TABLE Customers ADD COLUMN email
TEXT;
```
**Output:**

![image](https://github.com/user-attachments/assets/9d822908-7fe8-4571-8152-fcd79766221c)

**Question 3**
---
In the Books table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

![image](https://github.com/user-attachments/assets/26f29b71-4358-4d60-8283-dd55aaf19ab6)

### QUERY:
```sql
INSERT INTO Books (ISBN, Title, Author, Publisher, Year)
VALUES('978-1234567890', 'Introduction to AI', 'John Doe', NULL, NULL);
INSERT INTO Books (ISBN, Title, Author, Publisher, Year)
VALUES('978-9876543210', 'Deep Learning', 'Jane Doe', 'TechPress', '2022');
INSERT INTO Books (ISBN, Title, Author, Publisher, Year)
VALUES('978-1122334455', 'Cybersecurity Essentials', 'Alice Smith', NULL, 2021);
```

**Output:**

![image](https://github.com/user-attachments/assets/46a9de97-049b-475f-99f5-77ef4cf27250)

**Question 4**
---
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

![image](https://github.com/user-attachments/assets/79f19da6-5183-4315-974e-6188807f3acd)

### QUERY:
```sql
CREATE TABLE Orders(
OrderID integer primary key,
OrderDate date not null,
CustomerID integer,
foreign key (CustomerID) references Customers(CustomerID)
);
```
**Output:**

![image](https://github.com/user-attachments/assets/932d1b23-d8c0-47c4-8433-c6e30bd58655)

**Question 5**
---
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

![image](https://github.com/user-attachments/assets/cd4bd594-a57d-46c8-9ffe-a44db3f4a9c3)

### QUERY:
```sql
CREATE TABLE ProjectAssignments(
AssignmentID INTEGER PRIMARY KEY,
EmployeeID integer,
ProjectID integer,
AssignmentDate DATE NOT NULL,
FOREIGN KEY(EmployeeID) references Employees(EmployeeID),
FOREIGN KEY(ProjectID) references Projects(ProjectID)
);
```
**Output:**

![image](https://github.com/user-attachments/assets/8e5252ac-9406-437a-a010-6f569a45cb73)

**Question 6**
---
Create a table named Customers with the following columns:
CustomerID as INTEGER
Name as TEXT
Email as TEXT
JoinDate as DATETIME

![image](https://github.com/user-attachments/assets/8cc3b9a0-c44c-475a-bacb-d7ea36887df8)

### QUERY:
```sql
CREATE TABLE Customers(
CustomerID INTEGER,
Name TEXT,
Email TEXT,
JoinDate DATETIME
);
```
**Output:**

![image](https://github.com/user-attachments/assets/246efdb1-9d9b-4850-865a-5a1cdb28c8ad)

**Question 7**
---
create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

![image](https://github.com/user-attachments/assets/40556e99-9a5b-4edf-aa84-61f69b995bdb)

### QUERY:
```sql
CREATE TABLE jobs(
job_id integer primary key,
job_title text default '',
min_salary integer default 8000,
max_salary integer default null
);
```

**Output:**

![image](https://github.com/user-attachments/assets/3547b5dd-501f-4f67-942e-3104a4991858)

**Question 8**
---
Insert the below data into the Student_details table, allowing the Subject and MARKS columns to take their default values.

![image](https://github.com/user-attachments/assets/5ca1ff91-7c4e-4820-8934-75d699db2ea8)

### QUERY:
```sql
INSERT INTO Student_details (RollNo, Name, Gender)
VALUES (204, 'Samuel Black', 'M');
```
**Output:**

![image](https://github.com/user-attachments/assets/96a7acdb-8a85-4519-9c67-dacac216f656)

**Question 9**
---
Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

![image](https://github.com/user-attachments/assets/4bca0ac5-1898-4645-8aad-08e96dc088ce)

### QUERY:
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

![image](https://github.com/user-attachments/assets/8e09150c-4805-424f-a36e-8feb215ce707)

**Question 10**
---
Insert all books from Out_of_print_books into Books
Table attributes are ISBN, Title, Author, Publisher, YearPublished

![image](https://github.com/user-attachments/assets/96c1870f-477a-4131-a9ac-390264771d2f)

### QUERY:
```sql
INSERT INTO Books (ISBN, Title, Author, Publisher, YearPublished)
SELECT ISBN, Title, Author, Publisher, YearPublished FROM Out_of_print_books;
```
**Output:**

![image](https://github.com/user-attachments/assets/79de5057-4c64-41bf-bc74-6b45c33afad0)

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
