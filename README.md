# WIP
# Combining SQL and Tableau exercise
## Problem 1: Create a visualization that provides a breakdown between the male and female employees working in the company each year, starting from 1990. 

```SQL
SELECT
    YEAR(de.from_date) AS Calendar_year,
    e.gender,
    COUNT(e.emp_no) AS num_of_employees
FROM
    t_employees e
        JOIN
    t_dept_emp de ON de.emp_no = e.emp_no
GROUP BY calendar_year , e.gender
HAVING calendar_year >= 1990;
```

**Things to remember**
1. Start by listing out the columns that you want
2. Which tables do I need? Get the aliases --> adjust the select statement
3. Remember to use *HAVING* because *COUNT* is used and is an aggregate function

### Problem 1 Visualisation
![Picture1](https://user-images.githubusercontent.com/90490472/180726559-b9b30781-f2da-4798-937b-3dc65f556a82.png)

## Problem 2: Compare the number of male managers to the number of female managers from different departments for each year, starting from 1990

```SQL
SELECT
    d.dept_no, 
    ee.gender, 
    dm.emp_no, 
    dm.from_date, 
    dm.to_date, 
    e.calendar_year, 
    CASE
        WHEN
            YEAR(dm.to_date) >= e.calendar_year 
                AND YEAR(dm.from_date) <= e.calendar_year 
        THEN 
            1 
        ELSE 0 
    END AS active 
FROM 
    (SELECT 
        YEAR(hire_date) AS calendar_year <
    FROM 
        t_employees 
	GROUP BY calendar_year) e 
        CROSS JOIN 
    t_dept_manager dm 
        JOIN 
    t_departments d ON dm.dept_no = d.dept_no 
        JOIN 
    t_employees ee ON dm.emp_no = ee.emp_no 
ORDER BY ee.emp_no AND e.calendar_year; 
```

### Problem 2 Visualisation
![Picture1](https://user-images.githubusercontent.com/90490472/180970655-bb8f966e-30e2-4d83-96fa-8e656b17d5f4.png)

## Problem 3: Compare the average salary of female versus male employees in the entire company until year 2002, and add a filter allowing you to see that per each department.
