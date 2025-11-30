# HR ANALYTICS: EMPLOYEE ATTRITION DRIVERS
Power BI dashboard built from IBM HR Analytics Employee Attrition &amp; Performance dataset. Provides insights on attrition, demographics, job satisfaction, and performance trends to support data-driven HR decisions.

## I. EXECUTIVE SUMMARY & BUSINESS INSIGHTS
This diagnostic project analyzed the root causes of employee turnover (attrition rate of 16%) using the IBM HR Analytics dataset.

### KEY ANALYTICAL FINDINGS

1.  **Overall Status:** The total number of employees is 1,000, with 237 leaving, resulting in an attrition rate of 16% (0.16), which is significant.
2.  **Departmental Concentration:** The **Sales** department had the highest attrition rate, followed by Human Resources and Research & Development. This suggests that the turnover problem is department-specific, not company-wide.
3.  **Tenure Risk:** Employees in the **"Early Career (0-2 Years)"** group were most susceptible to attrition, indicating underlying issues with onboarding or role adjustment.
4.  **Primary Driver (Non-Monetary):** Employees with the **lowest levels of job satisfaction (ratings 1 and 2)** contributed the highest number of attrition events. This finding is the primary proxy for non-monetary reasons for leaving.
5.  **Age Demographics:** The **25-34 age group** accounted for the largest share of attrition (47.26% of total attrition), followed by the 35-44 age group (21.52%).
6.  **Senior Attrition:** Employees with **Research Director and Manager** positions who left (Leavers) had the highest average salaries. This indicates that the turnover problem also affects senior/high-paid employees, suggesting issues beyond mere compensation.

### ACTIONABLE RECOMMENDATIONS

1.  Focus retention resources on the **Early Career cohort (0-2 Years)**. Develop a structured mentorship program and conduct a role evaluation at six months to prevent rapid turnover.
2.  Conduct an in-depth audit to understand the drivers of turnover in the **Sales** and **Human Resources** departments (e.g., workload, leadership, or target pressure).
3.  Since Job Satisfaction ratings 1 and 2 are the primary drivers, implement targeted engagement surveys to identify and address issues with work culture, work-life balance, and managerial support, particularly in the 25-34 age group.
4.  Investigate income comparisons in Research Director and Manager positions. High attrition in the high-paying segment indicates a lack of **growth opportunities** or **recognition** commensurate with the market.
5.  Use this data to create targeted quarterly reports to key department managers, urging them to take corrective action and strengthen internal communications.

## II. KEY VISUAL PROOF
IBM HR Analytics Employee Attrition & Performance_001.jpg
https://github.com/divabintang/HR_Analytics_PowerBI_Project1/blob/7e8f8a84864a1b5d5a146442fb0e0005fb964274/IBM%20HR%20Analytics%20Employee%20Attrition%20%26%20Performance_001.jpg

## III. TECHNICAL HIGHLIGHTS & DAX MODELING
* **Tools Used:** Power BI Desktop (DAX, Power Query) for Data Modeling and Diagnostic Analysis.
* **Source File:** The full Power BI source file (.pbix) is included in this repository.

### DAX Modeling Proof
```dax
-- Employee Attrition & Performance Measures

AttritionRate =
    DIVIDE([TotalAttrition], [TotalEmployees])

AverageEmployeeTenure =
    AVERAGE('WA_Fn-UseC_-HR-Employee-Attrition'[YearsAtCompany])

AvgIncomeLeavers =
    CALCULATE(
        AVERAGE('WA_Fn-UseC_-HR-Employee-Attrition'[MonthlyIncome]),
        'WA_Fn-UseC_-HR-Employee-Attrition'[Attrition] = "Yes"
    )

AvgIncomeStayers =
    CALCULATE(
        AVERAGE('WA_Fn-UseC_-HR-Employee-Attrition'[MonthlyIncome]),
        'WA_Fn-UseC_-HR-Employee-Attrition'[Attrition] = "No"
    )

TotalAttrition =
    SUM('WA_Fn-UseC_-HR-Employee-Attrition'[AttritionNumerical])

TotalEmployees =
    COUNTROWS('WA_Fn-UseC_-HR-Employee-Attrition')
```

## IV. DATASET METADATA
The analysis utilizes the **IBM HR Analytics Employee Attrition & Performance Dataset** (https://github.com/divabintang/HR_Analytics_PowerBI_Project1/blob/main/WA_Fn-UseC_-HR-Employee-Attrition.csv)

| Field Name | Data Type | Purpose in Analysis |
| :--- | :--- | :--- |
| **Attrition** | Text | Dependent Variable (Yes/No) |
| **MonthlyIncome** | Numerical | Used for Compensation Gap Analysis |
| **YearsAtCompany** | Numerical | Used to create the **Tenure Group** |
| **JobSatisfaction** | Numerical | Key driver for non-monetary attrition |
| **Department** | Text | Used for Attrition Rate by Segment |
| **JobRole** | Text | Used for Attrition Rate by Segment |
| **Age** | Numerical | Used to create the **Age Group** |
| **Gender** | Text | Used for Demographic segmentation |
