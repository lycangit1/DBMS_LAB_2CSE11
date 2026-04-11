# Exercise 1: Employee and Department Tables

## Objective
Create tables based on given constraints and perform basic SQL operations.

---

## Table Structure

### Employee Table

| Column Name | Data Type | Size | Constraints |
|-------------|----------|------|-------------|
| EMPNO       | NUMBER   | 4    | PRIMARY KEY |
| ENAME       | VARCHAR2 | 20   | NOT NULL    |
| JOB         | VARCHAR2 | 20   |             |
| MGR         | NUMBER   | 4    |             |
| HIREDATE    | DATE     |      |             |
| SAL         | NUMBER   | 10   |             |
| COMM        | NUMBER   | 7    |             |
| DEPTNO      | NUMBER   | 2    | FOREIGN KEY |

---

### Department Table

| Column Name | Data Type | Size | Constraints |
|-------------|----------|------|-------------|
| DEPTNO      | NUMBER   | 2    | PRIMARY KEY |
| DNAME       | VARCHAR2 | 15   | NOT NULL    |

---

## Sample Data

### Department Data

```sql
INSERT INTO DEPARTMENT VALUES (10, 'RESEARCH');
INSERT INTO DEPARTMENT VALUES (20, 'ACCOUNTING');
INSERT INTO DEPARTMENT VALUES (30, 'SALES');
INSERT INTO DEPARTMENT VALUES (40, 'OPERATIONS');
```

---

### Employee Data

```sql
INSERT INTO EMPLOYEE VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);
INSERT INTO EMPLOYEE VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);
INSERT INTO EMPLOYEE VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 300, 30);
INSERT INTO EMPLOYEE VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);
INSERT INTO EMPLOYEE VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);
INSERT INTO EMPLOYEE VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);
INSERT INTO EMPLOYEE VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 20);
INSERT INTO EMPLOYEE VALUES (7788, 'SCOTT', 'ANALYST', 7566, '09-DEC-82', 3000, NULL, 40);
INSERT INTO EMPLOYEE VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 20);
INSERT INTO EMPLOYEE VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);
INSERT INTO EMPLOYEE VALUES (7876, 'ADAMS', 'CLERK', 7788, '12-JAN-83', 1100, NULL, 20);
INSERT INTO EMPLOYEE VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);
INSERT INTO EMPLOYEE VALUES (7902, 'FORD', 'ANALYST', 7566, '03-DEC-81', 3000, NULL, 20);
INSERT INTO EMPLOYEE VALUES (7934, 'MILLER', 'CLERK', 7782, '23-JAN-82', 1300, NULL, 10);
```

---

## Queries

### 1. Create Employee Master Table

```sql
CREATE TABLE EMPLOYEE_MASTER AS
SELECT * FROM EMPLOYEE;
```

---

### 2. Delete Records Where Department Number is 10

```sql
DELETE FROM EMPLOYEE_MASTER
WHERE DEPTNO = 10;
```

---

### 3. Increase Salary by 10% for Department 20

```sql
UPDATE EMPLOYEE_MASTER
SET SAL = SAL * 1.10
WHERE DEPTNO = 20;
```

---

### 4. Modify Salary Column Size

```sql
ALTER TABLE EMPLOYEE_MASTER
MODIFY SAL NUMBER(10,2);
```

---

### 5. Drop Employee Master Table

```sql
DROP TABLE EMPLOYEE_MASTER;
```

---
