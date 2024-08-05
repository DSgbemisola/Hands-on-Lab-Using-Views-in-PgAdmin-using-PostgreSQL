# Hands-on Lab: Using Views in PostgreSQL using PgAdmin

This is a hands-on project on creating views tables in the PostgreSQL database service using views in PgAdmin.

# Software Used in this Lab

PgAdmin 4 (PostgreSQL 15)

# Database Used in this Lab

The database used in this lab is an internal database belonging to IBM; a sample HR database. This is an HR database schema that consists of 5 tables called EMPLOYEES, JOB_HISTORY, JOBS, DEPARTMENTS and LOCATIONS. Each table has a few rows of sample data. The following diagram shows the tables for the HR database:

![image](https://github.com/user-attachments/assets/067a7925-0c1d-4a68-a62f-6f9879919301)

# Objectives

The objectives of this project were to:

After completing this lab, you will be able to:

1. Create a View and show a selection of data for a given table
2. Update a View to combine two or more tables in meaningful ways
3. Drop a created View

# Highlights

In SQL, a view is an alternative way of representing data that exists in one or more tables. Just like a real table, it contains rows and columns. The fields in a view are fields from one or more real tables in the database. Though views can be queried like a table, views are dynamic; only the definition of the view is stored, not the data.
The SELECT statement that you use to create the view can name other views and tables, and it can use the WHERE, GROUP BY, and HAVING clauses. It cannot use the ORDER BY clause or name a host variable. 

- How does the syntax of a CREATE VIEW statement look?

      CREATE VIEW view_name AS
      SELECT column1, column2, ...
      FROM table_name
      WHERE condition;
  
- How does the syntax of a REPLACE VIEW statement look?

      CREATE OR REPLACE VIEW view_name AS
      SELECT column1, column2, ...
      FROM table_name
      WHERE condition;

- How does the syntax of a DROP VIEW statement look?

      DROP VIEW view_name;
  

# Task A: Create a view called EMPSALARY to display salary along with some basic sensitive data of employees from the HR database. 

- To create the EMPSALARY view from the EMPLOYEES table, I issued the following query:

      CREATE VIEW Empsalary AS
      SELECT emp_id, f_name, l_name, b_date, sex, salary
      FROM employees;

  ![image](https://github.com/user-attachments/assets/9c70ea28-c8d4-4653-9761-26b4ed27f227)

- To retrieve all the records, I issued the following query:

      SELECT * FROM EMPSALARY;

  ![image](https://github.com/user-attachments/assets/4552cdd0-3fd4-4741-897e-2bd6051a0747)

# Task B: It now seems that the EMPSALARY view we created in task A doesn’t contain enough salary information, such as max/min salary and the job title of the employees, update the EMPSALARY view.

- To create an updated EMPSALARY VIEW, I issued the following query:

      CREATE OR REPLACE VIEW empsalary AS
      SELECT emp_id, f_name, l_name, b_date, sex, salary, job_title, min_salary, max_salary
      FROM employees, jobs
      WHERE employees.job_id = jobs.job_ident
  
![image](https://github.com/user-attachments/assets/a405afc9-af47-445f-ae60-fce4348cda2e)

- To retrieve the updated records of EMPSALARY, I isssued the following query:

      SELECT * FROM empsalary

  ![image](https://github.com/user-attachments/assets/90b877f6-697a-4c60-986e-7b286e52277d)

  # Task C: Delete the created EMPSALARY view

- To delete the created EMPSALARY view, I isssued the following query:

      DROP VIEW empsalary

![image](https://github.com/user-attachments/assets/669be424-1051-4891-8f8e-d3af8337e53a)

- To verify whether the EMPSALARY view has been deleted or not, I used the following query:

      SELECT * FROM empsalary

  ![image](https://github.com/user-attachments/assets/b08751b6-b6fb-4f52-ac6e-4dfdecfc749b)



