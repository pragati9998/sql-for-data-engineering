# SQL Views – Interview Practice

This repository is a hands-on guide to SQL Views, designed specifically for technical interviews. It covers concepts, syntax, common pitfalls, and practical examples that are frequently asked in interviews.

---

## What You’ll Learn

* What SQL Views are and why they are used
* How to create, query, update, and drop views
* Updatable vs non-updatable views
* Views with JOIN, GROUP BY, and aggregate functions
* WITH CHECK OPTION and its role in data integrity
* Interview-ready explanations and examples

---

## Interview Definition

A SQL View is a virtual table created using a SELECT query. It does not store data physically but retrieves data dynamically from underlying base tables.

---

## Basic Syntax

```sql
CREATE VIEW view_name AS
SELECT column1, column2
FROM table_name
WHERE condition;
```

---

## Example Tables

### employees

| emp_id | emp_name | dept_id | salary |
| ------ | -------- | ------- | ------ |
| 1      | Tom      | 1       | 60000  |
| 2      | Anna     | 2       | 45000  |
| 3      | John     | 1       | 70000  |

### departments

| dept_id | dept_name |
| ------- | --------- |
| 1       | IT        |
| 2       | HR        |

---

## Simple View Example

```sql
CREATE VIEW it_employees AS
SELECT emp_id, emp_name, salary
FROM employees
WHERE dept_id = 1;
```

```sql
SELECT * FROM it_employees;
```

---

## View with JOIN (Interview Favorite)

```sql
CREATE VIEW employee_details AS
SELECT e.emp_id, e.emp_name, d.dept_name, e.salary
FROM employees e
JOIN departments d
ON e.dept_id = d.dept_id;
```

---

## View with Aggregation

```sql
CREATE VIEW avg_salary_per_dept AS
SELECT dept_id, AVG(salary) AS avg_salary
FROM employees
GROUP BY dept_id;
```

Note: Aggregated views are generally not updatable.

---

## Updatable View Example

```sql
CREATE VIEW high_salary_employees AS
SELECT emp_id, emp_name, salary
FROM employees
WHERE salary > 50000;
```

```sql
UPDATE high_salary_employees
SET salary = 75000
WHERE emp_id = 1;
```

---

## WITH CHECK OPTION

```sql
CREATE VIEW hr_employees AS
SELECT emp_id, emp_name, dept_id
FROM employees
WHERE dept_id = 2
WITH CHECK OPTION;
```

This prevents updates that violate the view condition.

---

## Dropping a View

```sql
DROP VIEW view_name;
```

---

## View vs Table (Interview Comparison)

| Feature          | View | Table |
| ---------------- | ---- | ----- |
| Stores data      | No   | Yes   |
| Physical storage | No   | Yes   |
| Supports joins   | Yes  | Yes   |
| Data security    | High | Low   |

---

## Common Interview Questions

* Do views store data? No
* Can we update data through views? Yes, if the view is updatable
* Can a view be created on another view? Yes
* Difference between View and Materialized View?

  * View: virtual and real-time
  * Materialized View: data is physically stored

---

## Practice Tasks

1. Create a view for employees earning above department average
2. Create a view using JOIN and WHERE
3. Test updating data through a view
4. Apply WITH CHECK OPTION and observe failures

---

## Who This Is For

* Students preparing for SQL interviews
* Freshers and interns (Data, Backend, DevOps roles)
* Anyone revising SQL concepts quickly

---

Good luck with your interview preparation.
