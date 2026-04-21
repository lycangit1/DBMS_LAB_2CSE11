# EXCERCISE:11

## Queries

### 1. Delete employees who joined before 31-Dec-82 and location is New York or Chicago
```sql
DELETE FROM EMPLOYEE
WHERE HIREDATE < '31-DEC-82'
AND DEPTNO IN (
    SELECT DEPTNO FROM DEPARTMENT
    WHERE LOCATION IN ('NEW YORK', 'CHICAGO')
);
```

### 2. Display employee name, job, deptname, location for managers
```sql
SELECT E.ENAME, E.JOB, D.DNAME, D.LOCATION
FROM EMPLOYEE E, DEPARTMENT D
WHERE E.DEPTNO = D.DEPTNO
AND E.JOB = 'MANAGER';
```

### 3. Display name and salary of FORD if salary = highest of his grade
```sql
SELECT E.ENAME, E.SAL
FROM EMPLOYEE E, SALGRADE S
WHERE E.ENAME = 'FORD'
AND E.SAL BETWEEN S.LOSAL AND S.HISAL
AND E.SAL = S.HISAL;
```

### 4. Top 5 earners of company (MariaDB version)
```sql
SELECT *
FROM EMPLOYEE
ORDER BY SAL DESC
LIMIT 5;
```

### 5. Employees getting highest salary
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE SAL = (SELECT MAX(SAL) FROM EMPLOYEE);
```

### 6. Employees whose salary = average of max and min
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE SAL = (
    (SELECT MAX(SAL) FROM EMPLOYEE) +
    (SELECT MIN(SAL) FROM EMPLOYEE)
)/2;
```

### 7. Display department names where at least 3 employees work
```sql
SELECT D.DNAME
FROM EMPLOYEE E, DEPARTMENT D
WHERE E.DEPTNO = D.DEPTNO
GROUP BY D.DNAME
HAVING COUNT(*) >= 3;
```

### 8. Managers whose salary > average salary of company
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE JOB = 'MANAGER'
AND SAL > (SELECT AVG(SAL) FROM EMPLOYEE);
```

### 9. Managers whose salary > average salary of their employees
```sql
SELECT M.ENAME
FROM EMPLOYEE M
WHERE M.EMPNO IN (SELECT DISTINCT MGR FROM EMPLOYEE WHERE MGR IS NOT NULL)
AND M.SAL > (
    SELECT AVG(E.SAL)
    FROM EMPLOYEE E
    WHERE E.MGR = M.EMPNO
);
```

### 10. Employees whose net pay ≥ any employee salary (MariaDB version)
```sql
SELECT ENAME, SAL, COMM,
(SAL + IFNULL(COMM,0)) AS NET_PAY
FROM EMPLOYEE
WHERE (SAL + IFNULL(COMM,0)) >= ANY (SELECT SAL FROM EMPLOYEE);
```
