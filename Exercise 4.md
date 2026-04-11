# EXCERCISE:4

## Queries

### 1. Display the list of employees who have joined the company before 30th June 80 or after 31st Dec 81
```sql
SELECT * FROM EMPLOYEE
WHERE HIREDATE < '30-JUN-80' OR HIREDATE > '31-DEC-81';
```

### 2. Display the names of employees whose names have second alphabet A in their names
```sql
SELECT ENAME FROM EMPLOYEE
WHERE ENAME LIKE '_A%';
```

### 3. Display the names of employees whose name is exactly five characters in length
```sql
SELECT ENAME FROM EMPLOYEE
WHERE LENGTH(ENAME) = 5;
```

### 4. Display the names of employees whose names have second alphabet A in their names
```sql
SELECT ENAME FROM EMPLOYEE
WHERE ENAME LIKE '_A%';
```

### 5. Display the names of employees who are not working as salesman or clerk or analyst
```sql
SELECT ENAME FROM EMPLOYEE
WHERE JOB NOT IN ('SALESMAN', 'CLERK', 'ANALYST');
```

### 6. Display the name of the employee along with their annual salary. The name of the employee earning highest salary should appear first
```sql
SELECT ENAME, SAL*12 AS ANNUAL_SALARY
FROM EMPLOYEE
ORDER BY ANNUAL_SALARY DESC;
```

### 7. Display name, sal, hra, pf, da, totalsal for each employee
```sql
SELECT ENAME, SAL,
SAL*0.15 AS HRA,
SAL*0.10 AS DA,
SAL*0.05 AS PF,
(SAL + SAL*0.15 + SAL*0.10 - SAL*0.05) AS TOTALSAL
FROM EMPLOYEE;
```

### 8. Update the salary of each employee by 10% increment who are not eligible for commission
```sql
UPDATE EMPLOYEE
SET SAL = SAL * 1.10
WHERE COMM IS NULL;
```

### 9. Display those employees whose salary is more than 3000 after giving 20% increment
```sql
SELECT ENAME FROM EMPLOYEE
WHERE SAL * 1.20 > 3000;
```

### 10. Display those employees whose salary contains at least 3 digits
```sql
SELECT ENAME FROM EMPLOYEE
WHERE LENGTH(SAL) >= 3;
```
