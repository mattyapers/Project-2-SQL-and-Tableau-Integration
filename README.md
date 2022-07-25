# The-Business-Intelligence-Analyst-Course-2022
Udemy's The Business Intelligence Analyst Course 2022

# Combining SQL and Tableau exercise
## Problem 1: Create a visualization that provides a breakdown between the male and female employees working in the company each year, starting from 1990. 

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

**Things to remember**
1. Start by listing out the columns that you want
2. Which tables do I need? Get the aliases --> adjust the select statement
3. Remember to use *HAVING* because *COUNT* is used and is an aggregate function
