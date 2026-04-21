# EXCERCISE:9

## Queries

### 1. Display employee name who earns highest salary
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE SAL = (SELECT MAX(SAL) FROM EMPLOYEE);
```

### 2. Employee number and name of clerk earning highest salary among clerks
```sql
SELECT EMPNO, ENAME
FROM EMPLOYEE
WHERE JOB = 'CLERK'
AND SAL = (SELECT MAX(SAL) FROM EMPLOYEE WHERE JOB = 'CLERK');
```

### 3. Salesman earning more than highest salary of any clerk
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE JOB = 'SALESMAN'
AND SAL > (SELECT MAX(SAL) FROM EMPLOYEE WHERE JOB = 'CLERK');
```

### 4. Clerks earning more than JAMES but less than SCOTT
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE JOB = 'CLERK'
AND SAL > (SELECT SAL FROM EMPLOYEE WHERE ENAME = 'JAMES')
AND SAL < (SELECT SAL FROM EMPLOYEE WHERE ENAME = 'SCOTT');
```

### 5. Employees earning more than JAMES or more than SCOTT
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE SAL > (SELECT SAL FROM EMPLOYEE WHERE ENAME = 'JAMES')
OR SAL > (SELECT SAL FROM EMPLOYEE WHERE ENAME = 'SCOTT');
```

### 6. Employees earning highest salary in their respective departments
```sql
SELECT E.ENAME
FROM EMPLOYEE E
WHERE E.SAL = (
    SELECT MAX(SAL)
    FROM EMPLOYEE
    WHERE DEPTNO = E.DEPTNO
);
```

### 7. Employees earning highest salary in their respective job groups
```sql
SELECT E.ENAME
FROM EMPLOYEE E
WHERE E.SAL = (
    SELECT MAX(SAL)
    FROM EMPLOYEE
    WHERE JOB = E.JOB
);
```

### 8. Employees working in ACCOUNTING department
```sql
SELECT E.ENAME
FROM EMPLOYEE E, DEPARTMENT D
WHERE E.DEPTNO = D.DEPTNO
AND D.DNAME = 'ACCOUNTING';
```

### 9. Employees working in MUMBAI
```sql
SELECT E.ENAME
FROM EMPLOYEE E, DEPARTMENT D
WHERE E.DEPTNO = D.DEPTNO
AND D.LOCATION = 'MUMBAI';
```

### 10. Job groups having total salary greater than max salary of managers
```sql
SELECT JOB
FROM EMPLOYEE
GROUP BY JOB
HAVING SUM(SAL) > (
    SELECT MAX(SAL)
    FROM EMPLOYEE
    WHERE JOB = 'MANAGER'
);
```
