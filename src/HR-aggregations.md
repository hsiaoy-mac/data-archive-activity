# HR Aggregations

1) **(a)** Create two tables, one showing the number of salespeople with attrition and the other showing the number of salespeople with non-attrition.

   ```sql
   SELECT COUNT(Attrition) AS attrition
   FROM employee
   WHERE Department LIKE "%Sales%" AND Attrition LIKE "%Yes%";
   ```

   ```sql
   SELECT COUNT(Attrition) AS non_attrition
   FROM employee
   WHERE Department LIKE "%Sales%" AND Attrition LIKE "%No%";
   ```

2) Create three statistics tables, showing the monthly income for all salespeople, those with attrition, and those without attrition.

   ```sql
   SELECT AVG(MonthlyIncome) AS average_monthly_income, MIN(MonthlyIncome) AS min_monthly_income, MAX(MonthlyIncome) AS max_monthly_income
   FROM employee
   WHERE Department LIKE "%Sales%";
   ```

   ```sql
   SELECT AVG(MonthlyIncome) AS average_monthly_income, MIN(MonthlyIncome) AS min_monthly_income, MAX(MonthlyIncome) AS max_monthly_income
   FROM employee
   WHERE Department LIKE "%Sales%" AND Attrition LIKE "%Yes%";
   ```

   ```sql
   SELECT AVG(MonthlyIncome) AS average_monthly_income, MIN(MonthlyIncome) AS min_monthly_income, MAX(MonthlyIncome) AS max_monthly_income
   FROM employee
   WHERE Department LIKE "%Sales%" AND Attrition LIKE "%No%";
   ```

3) Create two tables (one for salespeople with attrition and one for salespeople without attrition) showing the monthly income and the count of salespeople making that amount.

   ```sql
   SELECT MonthlyIncome, COUNT(MonthlyIncome) AS count FROM employee_sales
   WHERE Attrition LIKE "%Yes%"
   GROUP BY MonthlyIncome;
   ```

   ```sql
   SELECT MonthlyIncome, COUNT(MonthlyIncome) AS count FROM employee_sales
   WHERE Attrition LIKE "%No%"
   GROUP BY MonthlyIncome;
   ```

   