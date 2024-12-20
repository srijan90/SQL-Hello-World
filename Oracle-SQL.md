# Course Introduction
So happy to see you here! Welcome to the New World of SQL, the only language to speak with relational data. Before we start any of the practices or courses, you should have your prerequisites ready. Here are the prerequisites:

- **One Computer:** Ensure you have a computer available.
- **Oracle Database:** Either a local database or a cloud database.
- **SQL Developer:** Make sure SQL Developer is installed on your machine.
- **Database Connection:** Connect SQL Developer to the database before you start.<BR>
<BR>Note: I need everyone utilizing this particular file or course to please collaborate and raise your pull requests to complete the above activities. Once you are ready, we can start with the course content below.

## Lets Begin..!<BR> ##
**Fetch all Data:**
```sql
SELECT * FROM departments
```

**Fetch data from specific columns:**
```sql
SELECT department_id, location_id FROM departments
```

**Using Arithmetic Operators:**
```sql
SELECT last_name, salary, salary + 300 FROM employees
```

**Operator Precedence:**
```sql
SELECT last_name, salary, 12*salary+100 FROM employees
```
```sql
SELECT last_name, salary, 12*(salary+100) FROM employees
```

**Null Value:**
```sql
SELECT last_name, job_id, salary, commission_pct FROM employees
```

**Null Values in Arithmetic Expressions:**
```sql
SELECT last_name, 12*salary*commission_pct FROM employees
```

**Using Column Aliases:**
```sql
SELECT last_name AS name, commission_pct comm FROM employees
```
```sql
SELECT last_name "Name" , salary*12 "Annual Salary" FROM employees
```

**Concatenation Operator:**
```sql
SELECT last_name||job_id AS "Employees" FROM employees
```

**Using Literal Character Strings:**
```sql
SELECT last_name ||' is a '||job_id AS "Employee Details" FROM employees
```

**Duplicate Rows:**
```sql
SELECT department_id FROM employees
```
```sql
SELECT DISTINCT department_id FROM employees
```

**Displaying Table Structure (Example):**
```sql
DESCRIBE employees
```

**Limiting the Rows That Are Selected:**

**Using the WHERE Clause:**
```sql
SELECT employee_id, last_name, job_id, department_id FROM employees WHERE department_id = 90
```

**Character Strings and Dates:**
```sql
SELECT last_name, job_id, department_id FROM employees WHERE last_name = 'Whalen'
```


**Using Comparison Conditions:**
```sql
SELECT last_name, salary FROM employees WHERE salary <= 3000
```

**Using the BETWEEN Condition:**
```sql
SELECT last_name, salary FROM employees WHERE salary BETWEEN 2500 AND 3500
```

**Using the IN Condition:**
```sql
SELECT employee_id, last_name, salary, manager_id FROM employees WHERE manager_id IN (100, 101, 201)
```

**Using the LIKE Condition:**
```sql
SELECT first_name FROM employees WHERE first_name LIKE 'S%'
```
```sql
SELECT last_name FROM employees WHERE last_name LIKE '_o%'
```

**Using the NULL Conditions:**
```sql
SELECT last_name, manager_id FROM employees WHERE manager_id IS NULL
```

**Using the AND Operator:**
```sql
SELECT employee_id, last_name, job_id, salary FROM employees WHERE salary >= 10000 AND job_id LIKE '%MAN%'
```

**Using the OR Operator:**
```sql
SELECT employee_id, last_name, job_id, salary FROM employees WHERE salary >= 10000 OR job_id LIKE '%MAN%'
```

**Using the NOT Operator:**
```sql
SELECT last_name, job_id FROM employees WHERE job_id NOT IN ('IT_PROG', 'ST_CLERK', 'SA_REP')
```

**Using the ORDER BY Clause:**
```sql
SELECT last_name, job_id, department_id, hire_date FROM employees ORDER BY hire_date
```

**Sorting:**
- Sorting in descending order:
```sql
SELECT last_name, job_id, department_id, hire_date FROM employees ORDER BY hire_date DESC
```
- Sorting by column alias:
```sql
SELECT employee_id, last_name, salary*12 annsal FROM employees ORDER BY annsal
```
- Sorting by multiple columns:
```sql
SELECT last_name, department_id, salary FROM employees ORDER BY department_id, salary DESC
```

**Using the & Substitution Variable:**
```sql
SELECT employee_id, last_name, salary, department_id FROM employees WHERE employee_id = &employee_num
```

**Character and Date Values with Substitution Variable:**
```sql
SELECT last_name, department_id, salary*12 FROM employees WHERE job_id = '&job_title'
```

**Specifying Column Names, Expressions, and Text:**
```sql
SELECT employee_id, last_name, job_id, &column_name FROM employees WHERE &condition ORDER BY &order_column
```

**Using the && Substitution Variable:**
```sql
SELECT employee_id, last_name, job_id, &&column_name FROM employees ORDER BY &column_name
```

**Using the VERIFY Command:**
```sql
SET VERIFY ON
SELECT employee_id, last_name, salary, department_id FROM employees WHERE employee_id = &employee_num
```

**Using Case-Manipulation Functions:**
```sql
SELECT employee_id, last_name, department_id FROM employees WHERE last_name = 'higgins'
```

**Using the Character-Manipulation Functions:**
```sql
SELECT employee_id, CONCAT(first_name, last_name) NAME, job_id, LENGTH(last_name), INSTR(last_name, 'a') "Contains 'a'?" FROM employees WHERE SUBSTR(job_id, 4) = 'REP'
```

**Using the ROUND Function:**
```sql
SELECT ROUND(45.923, 2), ROUND(45.923, 0), ROUND(45.923, -1) FROM DUAL
```

**Using the TRUNC Function:**
```sql
SELECT ROUND(45.923, 2), ROUND(45.923), ROUND(45.923, -1) FROM DUAL
```

**Using the MOD Function:**
```sql
SELECT last_name, salary, MOD(salary, 5000) FROM employees WHERE job_id = 'SA_REP'
```


**Working with Dates:**
```sql
SELECT last_name, hire_date FROM employees WHERE hire_date < '01-FEB-88'
```

**Using Arithmetic Operators with Dates:**
```sql
SELECT last_name, (SYSDATE - hire_date) / 7 AS WEEKS FROM employees WHERE department_id = 90
```

**Using the TO_CHAR Function with Dates:**
```sql
SELECT last_name, TO_CHAR(hire_date, 'fmDDMonth YYYY') AS HIREDATE FROM employees
```

**Using the TO_CHAR Function with Numbers:**
```sql
SELECT TO_CHAR(salary, '$99,999.00') SALARY FROM employees WHERE last_name = 'Ernst'
```

**Example of RR Date Format:**
```sql
SELECT last_name, TO_CHAR(hire_date, 'DD-Mon-YYYY') FROM employees WHERE hire_date < TO_DATE('01-Jan-90', 'DD-Mon-RR')
```

**Nesting Functions:**
```sql
SELECT last_name, UPPER(CONCAT(SUBSTR(LAST_NAME, 1, 8), '_US')) FROM employees WHERE department_id = 60
```

**Using the NVL Function:**
```sql
SELECT last_name, salary, NVL(commission_pct, 0), (salary*12) + (salary*12*NVL(commission_pct, 0)) AN_SAL FROM employees
```

**Using the NVL2 Function:**
```sql
SELECT last_name, salary, commission_pct, NVL2(commission_pct, 'SAL+COMM', 'SAL') income FROM employees WHERE department_id IN (50, 80)
```

**Using the NULLIF Function:**
```sql
SELECT first_name, LENGTH(first_name) "expr1", last_name, LENGTH(last_name) "expr2", NULLIF(LENGTH(first_name), LENGTH(last_name)) result FROM employees
```

**Using the COALESCE Function:**
```sql
SELECT last_name, COALESCE(manager_id, commission_pct, -1) comm FROM employees ORDER BY commission_pct
```

**CASE Expression:**
```sql
CASE expr WHEN comparison_expr1 THEN return_expr1 [WHEN comparison_expr2 THEN return_expr2 WHEN comparison_exprn THEN return_exprn ELSE else_expr] END
```

**Using the CASE Expression:**
```sql
SELECT last_name, job_id, salary, CASE job_id WHEN 'IT_PROG' THEN 1.10 * salary WHEN 'ST_CLERK' THEN 1.15 * salary WHEN 'SA_REP' THEN 1.20 * salary ELSE salary END "REVISED_SALARY" FROM employees
```

**DECODE Function:**
```sql
SELECT last_name, job_id, salary, DECODE(job_id, 'IT_PROG', 1.10*salary, 'ST_CLERK', 1.15*salary, 'SA_REP', 1.20*salary, salary) REVISED_SALARY FROM employees
```
```sql
SELECT last_name, salary, DECODE(TRUNC(salary / 2000, 0), 0, 0.00, 1, 0.09, 2, 0.20, 3, 0.30, 4, 0.40, 5, 0.42, 6, 0.44, 0.45) TAX_RATE FROM employees WHERE department_id = 80
```

**Using the AVG and SUM Functions:**
```sql
SELECT AVG(salary), MAX(salary), MIN(salary), SUM(salary) FROM employees WHERE job_id LIKE '%REP%'
```

**Using the MIN and MAX Functions:**
```sql
SELECT MIN(hire_date), MAX(hire_date) FROM employees
```

**Using the COUNT Function:**

- COUNT(*) returns the number of rows in a table:
```sql
SELECT COUNT(*) FROM employees WHERE department_id = 50
```
- COUNT(expr) returns the number of rows with non-null values for the expr:
```sql
SELECT COUNT(commission_pct) FROM employees WHERE department_id = 80
```
**Using the DISTINCT Keyword:**
```sql
SELECT COUNT(DISTINCT department_id) FROM employees
```

**Group Functions and Null Values:**
- Group functions ignore null values in the column:
```sql
SELECT AVG(commission_pct) FROM employees
```
- The NVL function forces group functions to include null values:
```sql
SELECT AVG(NVL(commission_pct, 0)) FROM employees
```

**Using the GROUP BY Clause:**
```sql
SELECT department_id, AVG(salary) FROM employees GROUP BY department_id
```

**Using the GROUP BY Clause:**
```sql
SELECT AVG(salary) FROM employees GROUP BY department_id
```

**Using the GROUP BY Clause on Multiple Columns:**
```sql
SELECT department_id dept_id, job_id, SUM(salary) FROM employees GROUP BY department_id, job_id
```

**Using the HAVING Clause:**
```sql
SELECT department_id, MAX(salary) FROM employees GROUP BY department_id HAVING MAX(salary) > 10000
```
```sql
SELECT job_id, SUM(salary) PAYROLL FROM employees WHERE job_id NOT LIKE '%REP%' GROUP BY job_id HAVING SUM(salary) > 13000 ORDER BY SUM(salary)
```

**Nesting Group Functions:**
```sql
SELECT MAX(AVG(salary)) FROM employees GROUP BY department_id
```

**Retrieving Records with Natural Joins:**
```sql
SELECT department_id, department_name, location_id, city FROM departments NATURAL JOIN locations
```

**Retrieving Records with the USING Clause:**
```sql
SELECT employees.employee_id, employees.last_name, departments.location_id, department_id FROM employees JOIN departments USING (department_id)
```

**Using Table Aliases:**
```sql
SELECT e.employee_id, e.last_name, d.location_id, department_id FROM employees e JOIN departments d USING (department_id)
```

**Retrieving Records with the ON Clause:**
```sql
SELECT e.employee_id, e.last_name, e.department_id, d.department_id, d.location_id FROM employees e JOIN departments d ON (e.department_id = d.department_id)
```

**Self-Joins Using the ON Clause:**
```sql
SELECT e.last_name emp, m.last_name mgr FROM employees e JOIN employees m ON (e.manager_id = m.employee_id)
```

**Applying Additional Conditions to a Join:**
```sql
SELECT e.employee_id, e.last_name, e.department_id, d.department_id, d.location_id FROM employees e JOIN departments d ON (e.department_id = d.department_id) AND e.manager_id = 149
```

**Creating Three-Way Joins with the ON Clause:**
```sql
SELECT employee_id, city, department_name FROM employees e JOIN departments d ON d.department_id = e.department_id JOIN locations l ON d.location_id = l.location_id
```

**Retrieving Records with Non-Equijoins:**
```sql
SELECT e.last_name, e.salary, j.grade_level FROM employees e JOIN job_grades j ON e.salary BETWEEN j.lowest_sal AND j.highest_sal
```

**LEFT OUTER JOIN:**
```sql
SELECT e.last_name, e.department_id, d.department_name FROM employees e LEFT OUTER JOIN departments d ON (e.department_id = d.department_id)
```

**RIGHT OUTER JOIN:**
```sql
SELECT e.last_name, e.department_id, d.department_name FROM employees e RIGHT OUTER JOIN departments d ON (e.department_id = d.department_id)
```

**FULL OUTER JOIN:**
```sql
SELECT e.last_name, d.department_id, d.department_name FROM employees e FULL OUTER JOIN departments d ON (e.department_id = d.department_id)
```

**Creating Cross Joins:**
```sql
SELECT last_name, department_name FROM employees CROSS JOIN departments
```

**Using a Subquery:**
```sql
SELECT last_name FROM employees WHERE salary > (SELECT salary FROM employees WHERE last_name = 'Abel')
```

**Executing Single-Row Subqueries:**
```sql
SELECT last_name, job_id, salary FROM employees WHERE job_id = (SELECT job_id FROM employees WHERE employee_id = 141) AND salary > (SELECT salary FROM employees WHERE employee_id = 143)
```

**Using Group Functions in a Subquery:**
```sql
SELECT last_name, job_id, salary FROM employees WHERE salary = (SELECT MIN(salary) FROM employees)
```

**The HAVING Clause with Subqueries:**
```sql
SELECT department_id, MIN(salary) FROM employees GROUP BY department_id HAVING MIN(salary) > (SELECT MIN(salary) FROM employees WHERE department_id = 50)
```

**Using the ANY Operator in Multiple-Row Subqueries:**
```sql
SELECT employee_id, last_name, job_id, salary FROM employees WHERE salary < ANY (SELECT salary FROM employees WHERE job_id = 'IT_PROG') AND job_id <> 'IT_PROG'
```

**Using the ALL Operator in Multiple-Row Subqueries:**
```sql
SELECT employee_id, last_name, job_id, salary FROM employees WHERE salary < ALL (SELECT salary FROM employees WHERE job_id = 'IT_PROG') AND job_id <> 'IT_PROG'
```

**Using the UNION Operator:**
```sql
SELECT employee_id, job_id FROM employees UNION SELECT employee_id, job_id FROM job_history
```

**Using the UNION ALL Operator:**
```sql
SELECT employee_id, job_id, department_id FROM employees UNION ALL SELECT employee_id, job_id, department_id FROM job_history ORDER BY employee_id
```

**Using the INTERSECT Operator:**
```sql
SELECT employee_id, job_id FROM employees INTERSECT SELECT employee_id, job_id FROM job_history
```

**MINUS Operator:**
```sql
SELECT employee_id, job_id FROM employees MINUS SELECT employee_id, job_id FROM job_history
```

**Controlling the Order of Row:**
Produce an English sentence using two UNION operators.
```sql
COLUMN a_dummy NOPRINT

SELECT 'sing' AS "My dream", 3 a_dummy FROM dual
UNION
SELECT 'I''d like to teach', 1 a_dummy FROM dual
UNION
SELECT 'the world to', 2 a_dummy FROM dual
ORDER BY a_dummy
```

**Inserting New Rows:**
```sql
INSERT INTO departments(department_id, department_name, manager_id, location_id) VALUES (70, 'Public Relations', 100, 1700)
```

**Inserting Rows with Null Values:**
```sql
INSERT INTO departments VALUES (100, 'Finance', NULL, NULL)
```

**Inserting Special Values:**
```sql
INSERT INTO employees (employee_id, first_name, last_name, email, phone_number, hire_date, job_id, salary, commission_pct, manager_id, department_id) VALUES (113, 'Louis', 'Popp', 'LPOPP', '515.124.4567', SYSDATE, 'AC_ACCOUNT', 6900, NULL, 205, 100)
```

**Inserting Specific Date Values:**
```sql
INSERT INTO employees VALUES (114, 'Den', 'Raphealy', 'DRAPHEAL', '515.127.4561', TO_DATE('FEB 3, 1999', 'MON DD, YYYY'), 'AC_ACCOUNT', 11000, NULL, 100, 30)
```

**Creating a Script:**
```sql
INSERT INTO departments (department_id, department_name, location_id) VALUES (&department_id, '&department_name', &department_location)
```

**Write your INSERT statement with a subquery:**
```sql
INSERT INTO sales_reps(id, name, salary, commission_pct) SELECT employee_id, last_name, salary, commission_pct FROM employees WHERE job_id LIKE '%REP%'
```

**Updating Rows in a Table:**
```sql
UPDATE employees SET department_id = 70 WHERE employee_id = 113
```

**Updating Two Columns with a Subquery:**
```sql
UPDATE employees SET job_id = (SELECT job_id FROM employees WHERE employee_id = 205), salary = (SELECT salary FROM employees WHERE employee_id = 205) WHERE employee_id = 114
```

**Updating Rows Based on Another Table:**
```sql
UPDATE copy_emp SET department_id = (SELECT department_id FROM employees WHERE employee_id = 100) WHERE job_id = (SELECT job_id FROM employees WHERE employee_id = 200)
```

**Deleting Rows from a Table:**
```sql
DELETE FROM departments WHERE department_name = 'Finance'
```

**Deleting Rows Based on Another Table:**
```sql
DELETE FROM employees WHERE department_id = (SELECT department_id FROM departments WHERE department_name LIKE '%Public%')
```

**TRUNCATE Statement:**
```sql
TRUNCATE TABLE table_name
```

**Using a Subquery in an INSERT Statement:**
```sql
INSERT INTO (SELECT employee_id, last_name, email, hire_date, job_id, salary, department_id FROM employees WHERE department_id = 50) VALUES (99999, 'Taylor', 'DTAYLOR', TO_DATE('07-JUN-99', 'DD-MON-RR'), 'ST_CLERK', 5000, 50)
```

**Using a Subquery in an INSERT Statement:**
```sql
SELECT employee_id, last_name, email, hire_date, job_id, salary, department_id FROM employees WHERE department_id = 50
```

**Committing Data:**
```sql
DELETE FROM employees WHERE employee_id = 99999; 1 row deleted.
INSERT INTO departments VALUES (290, 'Corporate Tax', NULL, 1700); 1 row created.
COMMIT;
```
**State of the Data After ROLLBACK:**
```sql
DELETE FROM copy_emp; 22 rows deleted.
ROLLBACK; Rollback complete.
```
