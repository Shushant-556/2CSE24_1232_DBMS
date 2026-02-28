<center><h2>Experiment 6</h2></center>

<h4>Queries:</h4>

-- 1. Display empno, ename, deptno from employee table. Instead of displaying department numbers, display the related department name.
SELECT EMPNO, ENAME,
CASE DEPTNO
    WHEN 10 THEN 'RESEARCH'
    WHEN 20 THEN 'ACCOUNTING'
    WHEN 30 THEN 'SALES'
    WHEN 40 THEN 'OPERATIONS'
    ELSE 'UNKNOWN'
END AS DEPARTMENT_NAME
FROM EMPLOYEE;

-- 2. Display your age in days.
SELECT DATEDIFF(CURDATE(), '2004-12-19') AS AGE_IN_DAYS;

-- 3. Display your age in months.
SELECT TIMESTAMPDIFF(MONTH, '2004-12-19', CURDATE()) AS AGE_IN_MONTHS;

-- 4. Display the current date as 15th August Friday Nineteen Ninety-Seven.
SELECT DATE_FORMAT(CURDATE(), '%D %M %W %Y') AS FORMATTED_DATE;

-- 5. Display the following output for each row from employee table.
SELECT CONCAT(ENAME, ' has joined the company on ',
DATE_FORMAT(HIREDATE, '%W %D %M %Y')) AS EMPLOYEE_DETAILS
FROM EMPLOYEE;

-- 6. Scott has joined the company on Wednesday 13th August Nineteen Ninety.
SELECT CONCAT(ENAME, ' has joined the company on ',
DATE_FORMAT(HIREDATE, '%W %D %M %Y')) AS JOINING_INFO
FROM EMPLOYEE
WHERE ENAME = 'SCOTT';

-- 7. Find the date for nearest Saturday after current date.
SELECT DATE_ADD(CURDATE(),
INTERVAL (5 - WEEKDAY(CURDATE()) + 7) % 7 DAY) AS NEAREST_SATURDAY;

-- 8. Display current time.
SELECT CURTIME() AS CURRENT_TIME;

-- 9. Display the date three months before the current date.
SELECT DATE_SUB(CURDATE(), INTERVAL 3 MONTH) AS DATE_BEFORE_3_MONTHS;

-- 10. Display those employees who joined the company in the month of December.
SELECT * FROM EMPLOYEE
WHERE MONTH(HIREDATE) = 12;

-- 11. Display those employees whose first 2 characters of hiredate equal last 2 characters of salary.
SELECT * FROM EMPLOYEE
WHERE LEFT(HIREDATE,2) = RIGHT(SAL,2);

-- 12. Display those employees whose 10% of salary is equal to the year of joining.
SELECT * FROM EMPLOYEE
WHERE (SAL * 0.10) = YEAR(HIREDATE);

-- 13. Display those employees who joined the company before 15th of the month.
SELECT * FROM EMPLOYEE
WHERE DAY(HIREDATE) < 15;

-- 14. Display those employees who have joined before 15th of the month.
SELECT * FROM EMPLOYEE
WHERE DAY(HIREDATE) < 15;

-- 15. Display those employees whose joining date is available in deptno.
SELECT * FROM EMPLOYEE
WHERE DAY(HIREDATE) = DEPTNO;