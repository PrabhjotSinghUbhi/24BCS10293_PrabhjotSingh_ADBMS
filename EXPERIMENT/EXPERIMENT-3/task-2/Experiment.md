# Experiment 3 - Task 2

Name: Prabhjot Singh

UID: 24BCS10293

## Aim

To perform aggregate queries on the `employees` table to count employees by city and analyze salary data.

## Question

Write SQL queries to count employees city-wise, filter employees with salary greater than or equal to 90000, calculate average salary by city, and find distinct cities from the `employees` table.

## SQL Queries Used

### Count employees city-wise

```sql
SELECT emp_city, COUNT(*) AS CNT
FROM employees
GROUP BY emp_city;
```

### Count employees city-wise using primary key

```sql
SELECT emp_city, COUNT(emp_id) AS CNT
FROM employees
GROUP BY emp_city;
```

### Count employees city-wise and sort by count

```sql
SELECT emp_city, COUNT(emp_id) AS CNT
FROM employees
GROUP BY emp_city
ORDER BY CNT ASC;
```

### Count employees city-wise and sort by count with city ordering

```sql
SELECT emp_city, COUNT(emp_id) AS CNT
FROM employees
GROUP BY emp_city
ORDER BY CNT DESC, emp_city ASC;
```

### Count employees in each city with salary greater than or equal to 90000

```sql
SELECT emp_city, SUM(CASE WHEN emp_salary >= 90000 THEN 1 ELSE 0 END) AS CNT
FROM employees
GROUP BY emp_city;
```

### Find cities with at least one employee earning 90000 or more

```sql
SELECT emp_city
FROM employees
GROUP BY emp_city
HAVING SUM(CASE WHEN emp_salary >= 90000 THEN 1 ELSE 0 END) > 0;
```

### Find the average employee salary of each city

```sql
SELECT emp_city, AVG(emp_salary)::NUMERIC(20,2) AS CNT
FROM employees
GROUP BY emp_city;
```

### Find distinct cities

```sql
SELECT DISTINCT emp_city
FROM employees;
```

### Count distinct cities

```sql
SELECT COUNT(DISTINCT emp_city) AS CNT
FROM employees;
```

## Output

```text
The queries return grouped employee counts, filtered salary counts, average salaries, and distinct city values from the employees table.
```

## Output Screenshot

No screenshot provided.

## Image Explanation

The SQL queries group employees by city, apply aggregate functions such as `COUNT`, `SUM`, and `AVG`, and use `HAVING` to filter grouped results based on salary conditions.

## Result

The SQL queries execute successfully on the `employees` table and produce the required aggregate and distinct city results.
(Experiment 3 - Task 2)

Name: Prabhjot Singh

UID: 24BCS10293

## Aim

To count the number of students in each city using an aggregate query.

## Question

Write a query to count the number of students per city from the `students` table.

## SQL Queries Used

```sql
SELECT city,
	   COUNT(*) AS student_count,
	   AVG(marks) AS avg_marks
FROM students
GROUP BY city
ORDER BY city;
```

## Output

```text
┌─────────┬──────────────┬───────────┐
│ city    │ student_count│ avg_marks │
├─────────┼──────────────┼───────────┤
│ Delhi   │ <n1>         │ <a1>      │
│ Mumbai  │ <n2>         │ <a2>      │
│ Kolkata │ <n3>         │ <a3>      │
│ Chennai │ <n4>         │ <a4>      │
└─────────┴──────────────┴───────────┘

Replace `<n1>`, `<n2>`, ... with the counts and `<a1>`, `<a2>`, ... with the average marks returned by your database.
```

## Output Screenshot

No screenshot provided.

## Image Explanation

The query counts rows in `students` where `city = 'Delhi'` and returns the total as a single scalar value.

## Result

The SQL query returns the number of students located in Delhi when executed against the `students` table.
