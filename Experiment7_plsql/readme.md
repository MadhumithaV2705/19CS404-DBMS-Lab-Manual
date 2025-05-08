# Experiment 6: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

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

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### PROGRAM:

```
DECLARE
   num1 NUMBER := 45;
   num2 NUMBER := 80;
BEGIN
   IF num1 > num2 THEN
      DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num1);
   ELSE
      DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num2);
   END IF;
EXCEPTION
   WHEN OTHERS THEN
      DBMS_OUTPUT.PUT_LINE('An error occurred: ' || SQLERRM);
END;
```

### OUTPUT:
![image](https://github.com/user-attachments/assets/7e07de12-dc5e-4649-9c27-3f109530b0f6)

---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### PROGRAM:
```
DECLARE
   n NUMBER := 10;
   sum NUMBER := 0;
   i NUMBER := 1;
BEGIN
   WHILE i <= n LOOP
      sum := sum + i;
      i := i + 1;
   END LOOP;
   DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
EXCEPTION
   WHEN OTHERS THEN
      DBMS_OUTPUT.PUT_LINE('An error occurred: ' || SQLERRM);
END;
```

### OUTPUT:
![image](https://github.com/user-attachments/assets/becfa364-73a1-4236-b38e-611eadcf9850)

---

## 3. Write a PL/SQL program to generate Fibonacci series

### PROGRAM:
```
DECLARE
   n NUMBER := 7;
   a NUMBER := 0;
   b NUMBER := 1;
   c NUMBER;
   i NUMBER := 3;  -- Start from 3 because first two terms are already defined
BEGIN
   DBMS_OUTPUT.PUT_LINE('Fibonacci sequence:');
   DBMS_OUTPUT.PUT_LINE(a);
   DBMS_OUTPUT.PUT_LINE(b);

   WHILE i <= n LOOP
      c := a + b;
      DBMS_OUTPUT.PUT_LINE(c);
      a := b;
      b := c;
      i := i + 1;
   END LOOP;
EXCEPTION
   WHEN OTHERS THEN
      DBMS_OUTPUT.PUT_LINE('An error occurred: ' || SQLERRM);
END;
```

### OUTPUT:
![image](https://github.com/user-attachments/assets/59ac90d5-238b-493e-8c67-6e03fc552aaf)

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### PROGRAM:
```
DECLARE
   n NUMBER := 1535;
   rev NUMBER := 0;
   rem NUMBER;
   original NUMBER := 1535;  -- store original for display
BEGIN
   WHILE n > 0 LOOP
      rem := MOD(n, 10);
      rev := (rev * 10) + rem;
      n := TRUNC(n / 10);
   END LOOP;

   DBMS_OUTPUT.PUT_LINE('n = ' || original);
   DBMS_OUTPUT.PUT_LINE('Reversed number is ' || rev);
EXCEPTION
   WHEN OTHERS THEN
      DBMS_OUTPUT.PUT_LINE('An error occurred: ' || SQLERRM);
END;
```

### OUTPUT:
![image](https://github.com/user-attachments/assets/e689b2ae-dba3-4819-956b-084db04f9525)


## 5. Write a PL/SQL program to find the largest of three numbers

### PROGRAM:
```
DECLARE
   a NUMBER := 10;
   b NUMBER := 9;
   c NUMBER := 15;
   largest NUMBER;
BEGIN
   IF a >= b AND a >= c THEN
      largest := a;
   ELSIF b >= a AND b >= c THEN
      largest := b;
   ELSE
      largest := c;
   END IF;

   DBMS_OUTPUT.PUT_LINE('a = ' || a || ', b = ' || b || ', c = ' || c);
   DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || largest);
EXCEPTION
   WHEN OTHERS THEN
      DBMS_OUTPUT.PUT_LINE('An error occurred: ' || SQLERRM);
END;
```

### OUTPUT:
![image](https://github.com/user-attachments/assets/2c249a89-8cec-457e-b012-ece612ab7717)

## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
