# companydb-sql-using-Sub-querying-database

A subquery is a query nested inside another SQL statement (SELECT, INSERT, UPDATE, DELETE). It returns a value or set of values used by the outer query to filter, compare, or compute results.

Types of subqueries with Company_DB examples

Single row subquery- It return one scalar value used for comparison.
Example: employees earning more than the overall average salary.

SELECT EmpName, Salary
FROM Employees
WHERE Salary > (SELECT AVG(Salary) FROM Employees);

Multi row subquery-return multiple values used with IN, ANY, or ALL.

Example: employees who work in departments located in Chennai or Bangalore.

SELECT EmpName
FROM Employees
WHERE DeptID IN (
  SELECT DeptID FROM Departments WHERE Location IN ('Chennai','Bangalore')
);

Correlated subquery
Intent: the inner query references columns from the outer query; evaluated per outer row.
Example: employees whose salary is greater than the average salary of their own department.
SELECT e1.EmpName, e1.Salary
FROM Employees AS e1
WHERE e1.Salary > (
  SELECT AVG(e2.Salary) FROM Employees AS e2 WHERE e2.DeptID = e1.DeptID
);



