# HR-Analytics
https://github.com/user-attachments/assets/f1247121-bfa4-4f75-a628-e082bbafcddc

# Project Overview
This project presents a Power BI solution developed to transform raw HR data from AtLabs into actionable insights. Recognizing the critical role of human capital in a software company's success, this project provides a dynamic and interactive dashboard that answers key questions related to the workforce.

Through intuitive visualizations, stakeholders can gain a clear understanding of:
* **Where are our retention challenges most significant?**
* **Are there any demographic groups experiencing higher turnover?**
* **How does compensation vary across different regions and employee segments?**
* **What are the trends in employee performance and satisfaction?**

# Data Description

This project utilizes an HR dataset comprising several tables designed to provide a comprehensive view of employee information, performance, and satisfaction. Below is the metadata for each table:

### 1. Performance

This table contains data related to employee performance reviews.

| Column Name                     | Description                                                                                                | Data Type |
| :------------------------------ | :--------------------------------------------------------------------------------------------------------- | :-------- |
| `PerformanceID`                 | A unique ID that identifies an individual performance review.                                               | `text`    |
| `EmployeeID`                    | A unique ID that identifies an employee. Connects to DimEmployee.                                            | `text`    |
| `ReviewDate`                    | Date an employee's review took place.                                                                        | `date`    |
| `EnvironmentSatisfaction`         | Rating for employees' satisfaction with their environment. Connects to DimSatisfiedLevel.                     | `number`  |
| `JobSatisfaction`               | Rating for employees' satisfaction with their job role. Connects to DimSatisfiedLevel.                         | `number`  |
| `RelationshipSatisfaction`      | Rating for employees' satisfaction with their relationships at work. Connects to DimSatisfiedLevel.             | `number`  |
| `WorkLifeBalance`               | Rating for employees satisfaction with their work-life balance. Connects to DimSatisfiedLevel.                 | `number`  |
| `SelfRating`                      | Rating for employees performance based on their own view. Connects to DimRatingLevel.                         | `number`  |
| `ManagerRating`                   | Rating for employees performance based on their manager's view. Connects to DimRatingLevel.                     | `number`  |
| `TrainingOpportunitiesWithinYear` | Number of training opportunities offered in the last 12 months.                                             | `number`  |
| `TrainingOpportunitiesTaken`      | Number of training opportunities taken.                                                                    | `number`  |

### 2. Employee

This table contains core employee information.

| Column Name             | Description                                                                                                | Data Type   |
| :---------------------- | :--------------------------------------------------------------------------------------------------------- | :-------- |
| `EmployeeID`            | A unique ID that identifies an employee.                                                                    | `text`    |
| `FirstName`             | First name of an employee.                                                                                 | `text`    |
| `LastName`              | Last name of an employee.                                                                                  | `text`    |
| `Gender`                | Self-defined employee gender identity.                                                                       | `text`    |
| `Age`                   | Current age of an employee.                                                                                | `number`  |
| `BusinessTravel`        | Frequency of business travel (Frequent Traveller, Some Travel, No Travel).                                    | `text`    |
| `Department`            | Department an employee works in (Technology, HR, Sales).                                                    | `text`    |
| `DistanceFromHome`      | Kilometer distance between an employee's home and their office.                                             | `number`  |
| `State`                 | State where the employee lives.                                                                              | `text`    |
| `Ethnicity`             | Self-defined employee ethnicity.                                                                           | `text`    |
| `Education`             | Education level for employees. Connects to DimEducationLevel.                                                | `number`  |
| `EducationField`        | Employee field of study.                                                                                   | `text`    |
| `JobRole`               | Current/latest employee job role.                                                                            | `text`    |
| `MaritalStatus`         | Current/latest employee marital status.                                                                      | `text`    |
| `Salary`                | Current/latest employee salary.                                                                            | `number`  |
| `StockOptionLevel`      | The banding level for stock options that the employee has.                                                    | `number`  |
| `Overtime`              | Indicates whether an employee is expected to work overtime in their role ("Yes" or "No").                     | `text`    |
| `HireDate`              | Date the employee joined the company.                                                                        | `date`    |
| `Attrition`             | Indicates whether an employee has left the organization ("Yes" or "No").                                     | `text`    |
| `YearsAtCompany`        | Number of years since the employee joined the organization.                                                  | `number`  |
| `YearsInMostRecentRole`  | Number of years the employee has been in their most recent role.                                            | `number`  |
| `YearsSinceLastPromotion` | Number of years since the employee last got promoted.                                                        | `number`  |
| `YearsWithCurrManager`  | Number of years the employee has been with their current manager.                                            | `number`  |

### 3. Satisfied Level

This table provides the descriptive labels for satisfaction ratings.

| Column Name       | Description                                                                                               | Data Type |
| :---------------- | :-------------------------------------------------------------------------------------------------------- | :-------- |
| `SatisfactionID`  | A unique ID that connects to EnvironmentSatisfaction, JobSatisfaction, RelationshipSatisfaction, and Work-Life Balance in FactPerformance Rating. | `number`  |
| `SatisfactionLevel` | Provides meaning to the satisfaction level (e.g., Very Satisfied, Satisfied, Neutral).                       | `text`    |

### 4. Rating Level

This table provides the descriptive labels for performance ratings.

| Column Name   | Description                                                                          | Data Type    |
| :------------ | :----------------------------------------------------------------------------------- | :-------- |
| `RatingID`    | A unique ID that connects to SelfRating and ManagerRating in FactPerformanceRating. | `number`  |
| `RatingLevel` | Provides meaning to the rating level (e.g., Above and Beyond, Exceeds Expectation).   | `text`    |

### 5. Education Level

This table provides the descriptive labels for education levels.

| Column Name       | Description                                                        | Data Type      |
| :---------------- | :----------------------------------------------------------------- | :-------- |
| `EducationLevelID` | A unique ID that connects to Education in DimEmployee.             | `number`  |
| `EducationLevel`  | Provides meaning to the education level (e.g., Doctorate, Masters). | `text`    |

**Note:** "Dim" and "Fact" prefixes in the original metadata refer to dimensional modeling concepts, which are relevant to how the data might be structured for analysis (e.g., dimensions for descriptive attributes, facts for measurable events).

![Data Model](HR-Analytics/Images/data_model.jpg)

# Data Exploration and Analysis
This project involved a thorough exploration of AtLabs' HR data to understand key workforce dynamics and inform strategic decision-making. The analysis covered several key areas:

**1. Employee Demographics:**

* Analysis of employee distribution by age, gender, ethnicity, and state to understand the composition of the workforce.
* Examination of education levels and fields of study to identify the skills and qualifications present within the company.
* Investigation of marital status and its potential correlation with other factors like job role or attrition.

**2. Attrition Analysis:**

* Calculation and visualization of overall attrition rates to identify the extent of employee turnover.
* Detailed analysis of attrition rates by state, department, job role, and demographic groups to pinpoint areas with higher turnover.
* Exploration of factors potentially influencing attrition, such as salary, tenure, years in role, and stock options.

**3. Compensation Analysis:**

* Examination of salary distributions across the company to understand pay ranges and identify potential outliers.
* Comparison of average salaries by department, job role, education level, and demographic groups to detect any pay disparities.
* Analysis of the relationship between salary and factors like years of experience, performance ratings, and promotion history.

**4. Performance and Satisfaction:**

* Analysis of employee satisfaction levels across different dimensions (environment, job, relationships, work-life balance).
* Comparison of self-ratings and manager ratings to identify potential discrepancies in performance perception.
* Exploration of the impact of training opportunities on employee performance and satisfaction.

**5. Tenure and Engagement:**

* Analysis of employee tenure to understand the length of time employees stay with the company.
* Investigation of the relationship between tenure and factors like job role, department, and manager relationships.
* Exploration of employee engagement through metrics like overtime work and business travel frequency.

**Some of the DAX measures used are mentioned below:**

| Measure Name               | Description                                                                                             | Formula                                                                                                                               |
| :------------------------- | :------------------------------------------------------------------------------------------------------ | :-------------------------------------------------------------------------------------------------------------------------------------- |
| `Active Employees`         | Calculates the total number of employees who have not left the organization.                           | `CALCULATE([Total Employees], FILTER(Employee, Employee[Attrition] = "No"))`                                                            |
| `HeadCount YOY Growth`     | Determines the percentage change in the total number of employees compared to the previous year.        | `VAR LastYear = CALCULATE([Total Employees], DATEADD('Calendar'[Date], -1, YEAR)) RETURN DIVIDE([Total Employees] - LastYear, LastYear, 0)` |
| `EnvSat tooltip`           | Retrieves the text description of the environment satisfaction rating based on the numerical value.      | `VAR RatingID = CALCULATE(MAX(PerformanceRating[EnvironmentSatisfaction]), USERELATIONSHIP('Calendar'[Date], PerformanceRating[ReviewDate])) RETURN LOOKUPVALUE(SatisfiedLevel[SatisfactionLevel], SatisfiedLevel[SatisfactionID], RatingID)` |
| `Attrition Change Label`   | Creates a visual label (arrow and percentage) indicating the change in attrition rate year-over-year. | `VAR curr = [Attrition Rate CY] VAR prev = [Attrition Rate PY] VAR pct = DIVIDE(curr - prev, prev, 0) VAR arrow = IF(pct>0, UNICHAR(8593), UNICHAR(8595)) RETURN arrow&" "&FORMAT(pct, "0.00%")` |
| `Recently Promoted CY`     | Counts the number of active employees promoted within the current fiscal year.                        | `CALCULATE(DISTINCTCOUNT(Employee[EmployeeID]), Employee[Attrition] = "No", Employee[YearsSinceLastPromotion] = 0, 'Calendar'[FiscalYearNum] = MAX('Calendar'[FiscalYearNum]))` |

Check out the transformed Data: 


