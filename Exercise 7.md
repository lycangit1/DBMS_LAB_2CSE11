# EXCERCISE:7

## Queries

### 1. Compute the number of days remaining in this year
```sql
SELECT TO_DATE('31-DEC-' || TO_CHAR(SYSDATE,'YYYY'),'DD-MON-YYYY') - SYSDATE AS DAYS_LEFT
FROM DUAL;
```

### 2. Find the highest and lowest salaries and the difference between them
```sql
SELECT MAX(SAL) AS HIGHEST,
MIN(SAL) AS LOWEST,
(MAX(SAL) - MIN(SAL)) AS DIFFERENCE
FROM EMPLOYEE;
```

### 3. List employees whose commission is greater than 25% of their salaries
```sql
SELECT * FROM EMPLOYEE
WHERE COMM > 0.25 * SAL;
```

### 4. Display salary in dollar format
```sql
SELECT ENAME, TO_CHAR(SAL, '$9999') AS SALARY
FROM EMPLOYEE;
```

### 5. Matrix query to display job-wise salary based on department and total
```sql
SELECT JOB,
SUM(DECODE(DEPTNO,10,SAL)) AS DEPT10,
SUM(DECODE(DEPTNO,20,SAL)) AS DEPT20,
SUM(DECODE(DEPTNO,30,SAL)) AS DEPT30,
SUM(DECODE(DEPTNO,40,SAL)) AS DEPT40,
SUM(SAL) AS TOTAL
FROM EMPLOYEE
GROUP BY JOB;
```

### 6. Display total employees and count hired in specific years
```sql
SELECT COUNT(*) AS TOTAL,
SUM(DECODE(TO_CHAR(HIREDATE,'YYYY'),'1980',1,0)) AS "1980",
SUM(DECODE(TO_CHAR(HIREDATE,'YYYY'),'1981',1,0)) AS "1981",
SUM(DECODE(TO_CHAR(HIREDATE,'YYYY'),'1982',1,0)) AS "1982",
SUM(DECODE(TO_CHAR(HIREDATE,'YYYY'),'1983',1,0)) AS "1983"
FROM EMPLOYEE;
```

### 7. Get the last Sunday of any month
```sql
SELECT NEXT_DAY(LAST_DAY(SYSDATE)-7,'SUNDAY') FROM DUAL;
```

### 8. Display department numbers and total number of employees in each department
```sql
SELECT DEPTNO, COUNT(*) AS TOTAL_EMP
FROM EMPLOYEE
GROUP BY DEPTNO;
```

### 9. Display jobs and total number of employees in each job group
```sql
SELECT JOB, COUNT(*) AS TOTAL_EMP
FROM EMPLOYEE
GROUP BY JOB;
```

### 10. Display department numbers and total salary for each department
```sql
SELECT DEPTNO, SUM(SAL) AS TOTAL_SALARY
FROM EMPLOYEE
GROUP BY DEPTNO;
```
