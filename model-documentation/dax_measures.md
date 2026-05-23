The following DAX code on the-is page are the ones that were used in this project to calculate the following:

1. Total Headcount
This counts every employee record in your dataset.

Total Employees = COUNT(HR_Data[EmployeeNumber])


2. Exited Employees
This counts how many people left the company by filtering where the Attrition text equals "Yes".

Exited Employees = CALCULATE([Total Employees], HR_Data[Attrition] = "Yes")


3. Active Employees
This tracks your current workforce baseline by filtering where Attrition equals "No".

Active Employees = CALCULATE([Total Employees], HR_Data[Attrition] = "No")


4. Attrition RateThis calculates the percentage of the workforce that has left. We use the DIVIDE function instead of the forward slash ($/$) operator because it automatically handles mathematical edge cases (like preventing "Divide by Zero" errors if a filtered segment has zero employees).

Attrition Rate = DIVIDE([Exited Employees], [Total Employees], 0)


5. Average Monthly Salary
Helps identify if lower pay scales correlate with higher employee departures.

Average Monthly Income = AVERAGE(HR_Data[MonthlyIncome])


6. Burnout Attrition Rate
This measures the attrition rate specifically for employees who are logged as working overtime. This isolates a clear business problem.

Burnout Attrition Rate = CALCULATE([Attrition Rate], HR_Data[OverTime] = "Yes")


7. Average Years of Service (Tenure)
Tracks organizational experience levels.

Average Tenure = AVERAGE(HR_Data[YearsAtCompany])


