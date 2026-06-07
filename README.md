# companydb-sql-using-Sub-querying-database

A subquery is a query nested inside another SQL statement (SELECT, INSERT, UPDATE, DELETE). It returns a value or set of values used by the outer query to filter, compare, or compute results.

Types of subqueries with Company_DB examples

Single row subquery- It return one scalar value used for comparison.
Example: employees earning more than the overall average salary.

SELECT EmpName, Salary
FROM Employees
WHERE Salary > (SELECT AVG(Salary) FROM Employees);
OUTPUT
<img width="1600" height="711" alt="image" src="https://github.com/user-attachments/assets/c19471a5-1e44-4223-abc1-21d935366432" />

Multi row subquery-return multiple values used with IN, ANY, or ALL.

Example: employees who work in departments located in Chennai or Bangalore.

SELECT EmpName
FROM Employees
WHERE DeptID IN (
  SELECT DeptID FROM Departments WHERE Location IN ('Chennai','Bangalore')
);
OUTPUT
<img width="1595" height="732" alt="image" src="https://github.com/user-attachments/assets/fd00a168-f9c7-41c3-93b6-f6f0dd47ee52" />

Correlated subquery
Intent: the inner query references columns from the outer query; evaluated per outer row.
Example: employees whose salary is greater than the average salary of their own department.
SELECT e1.EmpName, e1.Salary
FROM Employees AS e1
WHERE e1.Salary > (
  SELECT AVG(e2.Salary) FROM Employees AS e2 WHERE e2.DeptID = e1.DeptID
);
OUTPUT
<img width="1600" height="799" alt="image" src="https://github.com/user-attachments/assets/75317d9d-8f4c-4231-a187-2dc80983e4bd" />
-- FIND EMPLOYEE WHOSE JOINED AFTER THE AVG JOIN DATE OF THEIR DEPT
Select
EmpName,
JoinDate
from employees as e1
where JoinDate>
(Select avg(JoinDate)
from employees as e2
where e2.DeptID=e1.DeptID);

OUTPUT
<img width="1596" height="759" alt="image" src="https://github.com/user-attachments/assets/babfb384-deca-49c9-ab07-846243d51a46" />



