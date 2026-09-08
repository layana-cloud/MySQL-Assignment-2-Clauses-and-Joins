# MySQL-Assignment-2-Clauses-and-Joins
https://drive.google.com/drive/folders/18yTRylyM6FVu45j5DJWkv94nW7Xy2AhV?usp=sharing
1.	Distinct Values: 
	a query to retrieve distinct salaries from the Employees table.
### DISTINCT Salary Values

The following query retrieves all unique salary values from the `employees` table:

```sql
SELECT DISTINCT salary
FROM employees;
2.	Alias (AS): 
	Provide aliases for the "age" and "salary" columns as "Employee_Age" and "Employee_Salary", respectively.
### Employee Age and Salary

The following query displays employee age and salary using column aliases:

```sql
SELECT age AS Employee_Age,
       salary AS Employee_Salary
FROM employees;
3.	Where Clause & Operators: 
	Retrieve employees with a salary greater than ₹50000 and hired before 2016-01-01.
### Query: salary > 50000 and hire_date < '2016-01-01'
```sql
select * from employees
where salary > 50000 and hire_date < '2016-01-01';
	Find the employee whose designation is missing and fill it with "Data Scientist".
update employees
SET designation = 'Data Scientist'
where designation is NULL AND employee_id=5004;
Sorting and Grouping Data:
1.	ORDER BY:

	Find employees sorted by department ID in ascending order and salary in descending order.
select * from employees
order by department_id asc, salary desc;
2.	LIMIT:

	Display the first 5 employees hired in the year 2018.
select * from employees
where year(hire_date)=2018
order by hire_date asc
limit 5;
3.	Aggregate Functions:

	Calculate the sum of all salaries in the Finance department.
SELECT SUM(salary) AS Total_Fianace_Salary FROM employees
WHERE designation = 'Finance';
	Find the minimum age among all employees.
SELECT MIN(age) AS minimum_age FROM employees;
4.	GROUP BY:

	List the maximum salary for each location.
### 7. Max Salary by Location
```sql
SELECT location, MAX(salary) AS max_salary
FROM employees
GROUP BY location;
	Calculate the average salary for each designation containing the word 'Analyst'.
### 8. Average Salary by Designation
```sql
SELECT designation, AVG(salary) AS avg_salary
FROM employees
GROUP BY designation;
5.	HAVING:

	Find departments with less than 3 employees
SELECT department_name, COUNT(*) AS employee_count FROM employees GROUP BY department_name;
	Find locations with female employees whose average age is below 30.
### 10. Average Age by Location
```sql
SELECT location, AVG(age) AS avg_age
FROM employees
GROUP BY location;
Joins:
1.	Inner Join: 

	List employee names, their designations, and department names where employees are assigned to a department.
### 11. Employee Name, Designation and Department
```sql
SELECT e.employee_name, e.designation, d.department_name
FROM employees e
JOIN departments d ON e.department_id = d.department_id;
2.	Left Join:

	List all departments along with the total number of employees in each department, including departments with no employees.
### 12. Total Employees by Department
```sql
SELECT d.department_name, COUNT(e.employee_id) AS Total_employees
FROM employees e
JOIN departments d ON e.department_id = d.department_id
GROUP BY d.department_name;
3.	Right Join:

	Display all locations along with the names of employees assigned to each location. If no employees are assigned to a location, display NULL for employee name.
### 13. Employees Grouped by Location
```sql
SELECT location, employee_name
FROM employees
ORDER BY location;

