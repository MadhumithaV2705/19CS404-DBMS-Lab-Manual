# Experiment 8: PL/SQL Cursor Programs

## AIM
To write and execute PL/SQL programs using cursors and exception handling to manage runtime errors effectively and display appropriate messages.

## THEORY

In PL/SQL, cursors are used to handle query result sets row-by-row. 

There are two types of cursors:

- Implicit Cursors: Automatically created by PL/SQL for single-row queries.
- Explicit Cursors: Declared and controlled by the programmer for multi-row queries.

Types of Explicit Cursors:

1. Simple Cursor: Basic cursor to iterate over multiple rows.

2. Parameterized Cursor: Accepts parameters to filter the result dynamically.

3. Cursor FOR Loop: Simplifies cursor operations (open, fetch, close).

4. %ROWTYPE Cursor: Fetches entire row into a record using %ROWTYPE.

5. Cursor with FOR UPDATE: Used for row-level locking and updating the rows while looping.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:

- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

**Exception Handling**

PL/SQL provides a robust mechanism to handle runtime errors using exception handling blocks. When an error occurs during execution, control is passed to the EXCEPTION section, where specific or general errors can be handled gracefully.

### Components of Exception Handling:
- Predefined Exceptions: Automatically raised by PL/SQL for common errors (e.g., NO_DATA_FOUND, TOO_MANY_ROWS, ZERO_DIVIDE).
- User-defined Exceptions: Declared explicitly in the declaration section using the EXCEPTION keyword.
- WHEN OTHERS: A generic handler for all exceptions not handled explicitly.

```sql
BEGIN
   -- Statements
EXCEPTION
   WHEN exception_name THEN
      -- Handling code
   WHEN OTHERS THEN
      -- Handling for unknown errors
END;
```

### **Question 1: Simple Cursor with Exception Handling**

**Write a PL/SQL program using a simple cursor to fetch employee names and designations from the `employees` table. Implement exception handling for the following cases:**

## PL/SQL QUERY:
```
-- Step 1: Drop the table if it exists (for cleaning up) and create the employees table
BEGIN
    EXECUTE IMMEDIATE 'DROP TABLE employees';
EXCEPTION
    WHEN OTHERS THEN
        NULL; -- Ignore the error if the table does not exist
END;
/

-- Create the employees table
CREATE TABLE employees (
    emp_id      NUMBER PRIMARY KEY,
    emp_name    VARCHAR2(100),
    designation VARCHAR2(100)
);

-- Step 2: Insert sample data into the employees table
INSERT INTO employees (emp_id, emp_name, designation) VALUES (1, 'Alice Johnson', 'Manager');
INSERT INTO employees (emp_id, emp_name, designation) VALUES (2, 'Bob Smith', 'Developer');
INSERT INTO employees (emp_id, emp_name, designation) VALUES (3, 'Charlie Brown', 'Analyst');
COMMIT;

-- Step 3: PL/SQL block with cursor and exception handling
DECLARE
    CURSOR emp_cursor IS
        SELECT emp_name, designation FROM employees;
    
    v_emp_name employees.emp_name%TYPE;
    v_designation employees.designation%TYPE;
BEGIN
    -- Open the cursor to fetch the employee data
    OPEN emp_cursor;

    -- Fetch and process data from the cursor
    LOOP
        FETCH emp_cursor INTO v_emp_name, v_designation;
        EXIT WHEN emp_cursor%NOTFOUND;  -- Exit the loop when no more data is found

        -- Display the employee name and designation
        DBMS_OUTPUT.PUT_LINE('Employee Name: ' || v_emp_name || ', Designation: ' || v_designation);
    END LOOP;

    -- Close the cursor after use
    CLOSE emp_cursor;

EXCEPTION
    -- Handle the case when no rows are fetched
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employee records found.');

    -- Handle any other unexpected errors
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An error occurred: ' || SQLERRM);
END;
/
```

**OUTPUT:**  
![image](https://github.com/user-attachments/assets/88c97e8f-50ef-49a8-96a1-33a15a165660)

---

### **Question 2: Parameterized Cursor with Exception Handling**

**Write a PL/SQL program using a parameterized cursor to retrieve and display employees with a salary in a given range. Implement exception handling for the following errors:**

### PL/SQL QUERY:

```
DECLARE
    -- Input salary range
    v_min_salary NUMBER := 4000;  -- Set to a value that has employee matches
    v_max_salary NUMBER := 8000;

    -- Parameterized cursor to fetch employees in the range
    CURSOR emp_cursor(p_min NUMBER, p_max NUMBER) IS
        SELECT emp_id, emp_name, designation, salary
        FROM employees
        WHERE salary BETWEEN p_min AND p_max;

    v_found BOOLEAN := FALSE;

BEGIN
    -- Cursor FOR loop to fetch and display employee details
    FOR emp_rec IN emp_cursor(v_min_salary, v_max_salary) LOOP
        v_found := TRUE;
        DBMS_OUTPUT.PUT_LINE(
            'ID: ' || emp_rec.emp_id ||
            ', Name: ' || emp_rec.emp_name ||
            ', Designation: ' || emp_rec.designation ||
            ', Salary: ' || emp_rec.salary
        );
    END LOOP;

    -- If no data found, display a custom message for employees in the range
    IF NOT v_found THEN
        DBMS_OUTPUT.PUT_LINE('No employees found in the specified salary range.');
    END IF;

EXCEPTION
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
/
```
**OUTPUT:**  
![image](https://github.com/user-attachments/assets/e5be826e-ea53-4c83-a506-4867be326535)

---

### **Question 3: Cursor FOR Loop with Exception Handling**

**Write a PL/SQL program using a cursor FOR loop to retrieve and display all employee names and their department numbers from the `employees` table. Implement exception handling for the following cases:**

### PL/SQL QUERY:
```
-- Enable DBMS output
SET SERVEROUTPUT ON;
/

-- Step 1: Drop and create the employees table with dept_no
BEGIN
    EXECUTE IMMEDIATE 'DROP TABLE employees';
EXCEPTION
    WHEN OTHERS THEN
        NULL; -- Ignore if table doesn't exist
END;
/

CREATE TABLE employees (
    emp_id      NUMBER PRIMARY KEY,
    emp_name    VARCHAR2(100),
    designation VARCHAR2(100),
    salary      NUMBER,
    dept_no     NUMBER
);
/

-- Step 2: No INSERT statements – table remains empty

-- Step 3: PL/SQL block using Cursor FOR loop and exception handling

DECLARE
    v_found BOOLEAN := FALSE;
BEGIN
    -- Cursor FOR loop to fetch employee names and dept numbers
    FOR emp_rec IN (
        SELECT emp_name, dept_no FROM employees
    ) LOOP
        v_found := TRUE;
        DBMS_OUTPUT.PUT_LINE('Name: ' || emp_rec.emp_name || 
                             ', Department No: ' || emp_rec.dept_no);
    END LOOP;

    -- Check if no data was found
    IF NOT v_found THEN
        RAISE NO_DATA_FOUND;
    END IF;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employee records found.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
/
```

**Output:**  

![image](https://github.com/user-attachments/assets/2ef9bbde-f637-4bf1-a284-4b6bb4f4e75b)

---

### **Question 4: Cursor with `%ROWTYPE` and Exception Handling**

**Write a PL/SQL program that uses a cursor with `%ROWTYPE` to fetch and display complete employee records (emp_id, emp_name, designation, salary). Implement exception handling for the following errors:**

### PL/SQL QUERY:
```
-- Enable DBMS output
SET SERVEROUTPUT ON;

-- 1) Drop & recreate the employees table
BEGIN
  EXECUTE IMMEDIATE 'DROP TABLE employees';
EXCEPTION
  WHEN OTHERS THEN
    NULL;  -- ignore if it doesn't exist
END;


CREATE TABLE employees (
  emp_id      NUMBER PRIMARY KEY,
  emp_name    VARCHAR2(100),
  designation VARCHAR2(100),
  salary      NUMBER
);

-- 2) Insert a single row (so cursor can open)
BEGIN
  INSERT INTO employees VALUES (1, 'Alice', 'Manager', 6000);
  COMMIT;
END;
/

-- 3) PL/SQL block with %ROWTYPE cursor and a forced divide-by-zero
DECLARE
  CURSOR c_emp IS
    SELECT * FROM employees;
  v_emp   c_emp%ROWTYPE;
  v_dummy NUMBER;
BEGIN
  OPEN c_emp;
    FETCH c_emp INTO v_emp;
  CLOSE c_emp;

  -- FORCE an unexpected error (division by zero)
  v_dummy := v_emp.salary / 0;

  -- (any normal display logic here would never be reached)
EXCEPTION
  WHEN NO_DATA_FOUND THEN
    DBMS_OUTPUT.PUT_LINE('No employee records found.');
  WHEN OTHERS THEN
    DBMS_OUTPUT.PUT_LINE('An unexpected error occurred.');
END;
/
```
**OUTPUT:**  
![image](https://github.com/user-attachments/assets/20bcd2b2-7b7d-43d6-8ee5-e27706841d25)

---

### **Question 5: Cursor with FOR UPDATE Clause and Exception Handling**

**Write a PL/SQL program using a cursor with the `FOR UPDATE` clause to update the salary of employees in a specific department. Implement exception handling for the following cases:**

### PL/SQL QUERY:
```
DECLARE
    -- Declare the cursor for department 5 employees
    CURSOR emp_cursor IS
        SELECT emp_id, salary
        FROM employees
        WHERE dept_no = 5
        FOR UPDATE; -- Lock the rows for updating

    -- Declare variables to store fetched data from the cursor
    v_emp_id   employees.emp_id%TYPE;
    v_salary   employees.salary%TYPE;

    -- Variable to check if employees were found
    v_found    BOOLEAN := FALSE;

BEGIN
    -- Open the cursor to fetch employees in department 5
    OPEN emp_cursor;

    -- Loop through each employee in department 5
    LOOP
        FETCH emp_cursor INTO v_emp_id, v_salary;
        EXIT WHEN emp_cursor%NOTFOUND;  -- Exit loop when no more employees are found

        -- Update the salary by 10%
        v_salary := v_salary * 1.10;

        -- Update the employee's salary in the table
        UPDATE employees
        SET salary = v_salary
        WHERE emp_id = v_emp_id;

        v_found := TRUE; -- Mark that employees were found and updated
    END LOOP;

    -- Close the cursor after processing all employees
    CLOSE emp_cursor;

    -- Display the result
    IF v_found THEN
        DBMS_OUTPUT.PUT_LINE('Salaries updated for department 5.');
    ELSE
        RAISE NO_DATA_FOUND;  -- Raise an exception if no employees were found in dept 5
    END IF;

EXCEPTION
    -- Handle case where no employees are found in department 5
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employees found in department 5.');

    -- Handle any other unexpected errors
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
```

**OUTPUT:**  
![image](https://github.com/user-attachments/assets/66757ac1-7a96-4b1d-9121-3d73900b66e6)

---

## RESULT:
Thus, the program successfully executed and displayed employee details using a cursor. 

