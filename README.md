# The-Business-Intelligence-Analyst-Course-2022
Udemy's The Business Intelligence Analyst Course 2022

# Combining SQL and Tableau exercise
## Problem 1: Create a visualization that provides a breakdown between the male and female employees working in the company each year, starting from 1990. 

SELECT<br/>
    YEAR(de.from_date) AS Calendar_year,<br/>
    e.gender,<br/>
    COUNT(e.emp_no) AS num_of_employees<br/>
FROM<br/>
    t_employees e<br/>
        JOIN<br/>
    t_dept_emp de ON de.emp_no = e.emp_no<br/>
GROUP BY calendar_year , e.gender<br/>
HAVING calendar_year >= 1990;

**Things to remember**
1. Start by listing out the columns that you want
2. Which tables do I need? Get the aliases --> adjust the select statement
3. Remember to use *HAVING* because *COUNT* is used and is an aggregate function

### Problem 1 Visualisation
![Picture1](https://user-images.githubusercontent.com/90490472/180726559-b9b30781-f2da-4798-937b-3dc65f556a82.png)
