# HR Transformations

1. **(a)** Create a new table for your analysis called `employee_sales`
  **(b)** Load the table `employee` into `employee_sales`. 

  > The `employee` table should have been populated with data from the csv. 

  **(c)** Select these columns: `Attrition`, `Department`, `JobSatisfaction` & `MonthlyIncome`

  ```sql
  CREATE TABLE employee_sales
  (
    Attrition string,
    Department string,
    JobSatisfaction int,
  MonthlyIncome int
  );
  ```

  ```sql
  INSERT OVERWRITE TABLE employee_sales
  SELECT Attrition, Department, JobSatisfaction, MonthlyIncome FROM employee;
  ```

 2. Round the data found in the `MonthlyIncome` to the nearest $1000.

    ```sql
    INSERT OVERWRITE TABLE employee_sales
    SELECT Attrition, Department, JobSatisfaction, ROUND(MonthlyIncome,-3) AS MonthlyIncome
    FROM employee_sales;
    ```

3. Filter the data to only look at those items in the `Sales` Department.

   ```sql
   INSERT OVERWRITE TABLE employee_sales
   SELECT *
   FROM employee_sales
   WHERE Department LIKE "%Sales%";
   ```

4. Order the data by `JobSatisfaction` from highest to lowest.
  ```sql
  INSERT OVERWRITE TABLE employee_sales
  SELECT *
  FROM employee_sales
  ORDER BY JobSatisfaction DESC;
  ```

  

