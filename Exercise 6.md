# EXCERCISE:6

## Queries

### 1. Display empno, ename, deptno with department name using DECODE
```sql
SELECT EMPNO, ENAME,
DECODE(DEPTNO,
10, 'RESEARCH',
20, 'ACCOUNTING',
30, 'SALES',
40, 'OPERATIONS') AS DEPARTMENT
FROM EMPLOYEE;
```

### 2. Display your age in days
```sql
SELECT SYSDATE - TO_DATE('01-JAN-2000','DD-MON-YYYY') AS AGE_IN_DAYS FROM DUAL;
```

### 3. Display your age in months
```sql
SELECT MONTHS_BETWEEN(SYSDATE, TO_DATE('01-JAN-2000','DD-MON-YYYY')) AS AGE_IN_MONTHS FROM DUAL;
```

### 4. Display current date in required format
```sql
SELECT TO_CHAR(SYSDATE, 'DDth Month Day YYYY') FROM DUAL;
```

### 5. Display formatted output for each employee
```sql
SELECT ENAME || ' has joined the company on ' ||
TO_CHAR(HIREDATE, 'Day DDth Month YYYY')
FROM EMPLOYEE;
```

### 6. Example formatted output for SCOTT
```sql
SELECT ENAME || ' has joined the company on ' ||
TO_CHAR(HIREDATE, 'Day DDth Month YYYY')
FROM EMPLOYEE
WHERE ENAME = 'SCOTT';
```

### 7. Find nearest Saturday after current date
```sql
SELECT NEXT_DAY(SYSDATE, 'SATURDAY') FROM DUAL;
```

### 8. Display current time
```sql
SELECT TO_CHAR(SYSDATE, 'HH:MI:SS AM') FROM DUAL;
```

### 9. Display date three months before current date
```sql
SELECT ADD_MONTHS(SYSDATE, -3) FROM DUAL;
```

### 10. Display employees who joined in December
```sql
SELECT * FROM EMPLOYEE
WHERE TO_CHAR(HIREDATE, 'MON') = 'DEC';
```

### 11. Display employees where first 2 chars of hiredate = last 2 chars of salary
```sql
SELECT * FROM EMPLOYEE
WHERE SUBSTR(TO_CHAR(HIREDATE,'DDMMYY'),1,2) =
SUBSTR(TO_CHAR(SAL), -2);
```

### 12. Display employees whose 10% salary equals year of joining
```sql
SELECT * FROM EMPLOYEE
WHERE SAL * 0.10 = TO_NUMBER(TO_CHAR(HIREDATE,'YYYY'));
```

### 13. Display employees who joined before 15th day of month
```sql
SELECT * FROM EMPLOYEE
WHERE TO_NUMBER(TO_CHAR(HIREDATE,'DD')) < 15;
```

### 14. Display employees who joined before 15th of month
```sql
SELECT * FROM EMPLOYEE
WHERE TO_CHAR(HIREDATE,'DD') < '15';
```

### 15. Display employees whose joining date matches deptno (logic-based)
```sql
SELECT * FROM EMPLOYEE
WHERE TO_CHAR(HIREDATE,'DD') = TO_CHAR(DEPTNO);
```
