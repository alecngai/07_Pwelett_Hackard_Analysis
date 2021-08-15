# Pwelett Hackard Analysis by Alec Ngai

## Overview

We will complete two technical analysis using SQL and PGAdmin4, using the data proivded to us we will achieve two results:

1. The Number of Retiring Employees by Title
2. The Employees Eligible for the Mentorship Program

![ERD](https://github.com/alecngai/07_Pwelett_Hackard_Analysis/blob/main/Resources/ERD.png)

We are given the intial csv files, where we created an ERD to prepare us for this technical analysis. 

## Results: 
![sql1](https://github.com/alecngai/07_Pwelett_Hackard_Analysis/blob/main/Resources/retirement_titles_sql.png)

![rt](https://github.com/alecngai/07_Pwelett_Hackard_Analysis/blob/main/Resources/retirement_titles_df.png)

Here we ccan see we joined employees.csv and titles.csv to acquire a new table wwith the employee and their title, however this table introduces a new issue which is duplpicates employees with different titles. We then expore this table into retirement_titles.csv. This table consists of all the workforce including those who have retired and switched positions. 

![sql2](https://github.com/alecngai/07_Pwelett_Hackard_Analysis/blob/main/Resources/unique_titles_sql.png)

![ut](https://github.com/alecngai/07_Pwelett_Hackard_Analysis/blob/main/Resources/unique_titles_df.png)

To fix the duplicate issues, we use DISTINCT ON employee number, we take the most recent title by using Order by to_date DESC, this will fix our duplicate issue  and give us a more recent table which we export into unique_titles.csv.

![sql3](https://github.com/alecngai/07_Pwelett_Hackard_Analysis/blob/main/Resources/retiring_titles_sql.png)

![rt_2](https://github.com/alecngai/07_Pwelett_Hackard_Analysis/blob/main/Resources/retiring_titles.png)

With unique_titles.csv complete, we can now do analysis on it and count the titles, using the count function we order the data by the count which gives us this results, as we can see there are not many managers but alot of engineers. 

![sql4](https://github.com/alecngai/07_Pwelett_Hackard_Analysis/blob/main/Resources/mentorship_eligibilty_sql.png)

![me](https://github.com/alecngai/07_Pwelett_Hackard_Analysis/blob/main/Resources/mentorship_eligibilty.png)

Next we must find all emplolyees who have been here for more than 50 years and still currently employeed, this will allow us to find employees to be mentors for the future generation of employees. To achieve this we join three tables: employees, titles and dept_emp we then save and expore the result into mentorship_eligibility. 

## Summary: 
- How many roles will need to be filled as the "silver tsunami" begins to make an impact?

| title              | Count|
| ------------------ | -----|
|Assistant Engineer  |  78  |
|Engineer            |  501 | 
|Senior Engineer     |  169 | 
|Senior Staff        |  569 | 
|Staff               |  155 |
|Technique Leader    |   77 |

This table was created using groupby and count on the membership_eligibility.csv, we can see the amount of roles that need to be filled soon as all these employees are close to their retirement age. 

- Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?