# EXCERCISE:10

## Queries

### 1. Employees from dept 10 with salary greater than ANY employee in other departments
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE DEPTNO = 10
AND SAL > ANY (SELECT SAL FROM EMPLOYEE WHERE DEPTNO <> 10);
```

### 2. Employees from dept 10 with salary greater than ALL employees in other departments
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE DEPTNO = 10
AND SAL > ALL (SELECT SAL FROM EMPLOYEE WHERE DEPTNO <> 10);
```

### 3. Employees in SALES department with grade C
```sql
SELECT E.*
FROM EMPLOYEE E, DEPARTMENT D, SALGRADE S
WHERE E.DEPTNO = D.DEPTNO
AND D.DNAME = 'SALES'
AND E.SAL BETWEEN S.LOSAL AND S.HISAL
AND S.GRADE = 'C';
```

### 4. Employees who are not managers and who manage someone
```sql
SELECT ENAME, JOB
FROM EMPLOYEE
WHERE JOB <> 'MANAGER'
AND EMPNO IN (
    SELECT DISTINCT MGR 
    FROM EMPLOYEE 
    WHERE MGR IS NOT NULL
);
```

### 5. Employees whose manager name is JONES
```sql
SELECT E.ENAME
FROM EMPLOYEE E, EMPLOYEE M
WHERE E.MGR = M.EMPNO
AND M.ENAME = 'JONES';
```

### 6. Employees working in SALES department
```sql
SELECT E.ENAME
FROM EMPLOYEE E, DEPARTMENT D
WHERE E.DEPTNO = D.DEPTNO
AND D.DNAME = 'SALES';
```

### 7. Employee name, deptname, salary and comm (2000–5000) where location is CHENNAI
```sql
SELECT E.ENAME, D.DNAME, E.SAL, E.COMM
FROM EMPLOYEE E, DEPARTMENT D
WHERE E.DEPTNO = D.DEPTNO
AND E.SAL BETWEEN 2000 AND 5000
AND D.LOCATION = 'CHENNAI';
```

### 8. Employees whose salary is greater than their manager
```sql
SELECT E.ENAME
FROM EMPLOYEE E, EMPLOYEE M
WHERE E.MGR = M.EMPNO
AND E.SAL > M.SAL;
```

### 9. Employees working in same department as their manager
```sql
SELECT E.ENAME
FROM EMPLOYEE E, EMPLOYEE M
WHERE E.MGR = M.EMPNO
AND E.DEPTNO = M.DEPTNO;
```

### 10. Employee name and grade (dept 10 or 30, grade not 4, joined before 31-Dec-82)
```sql
SELECT E.ENAME, S.GRADE
FROM EMPLOYEE E, SALGRADE S
WHERE E.SAL BETWEEN S.LOSAL AND S.HISAL
AND E.DEPTNO IN (10, 30)
AND S.GRADE <> 'D'
AND E.HIREDATE < '31-DEC-82';
```
