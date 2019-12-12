---
title: "Case Study 2"
author: "Jaclyn A Coate"
date: "2019-12-12"
output:
  revealjs::revealjs_presentation:
    transition: slide
    keep_md: true
    theme: serif
    highlight: pygments
    center: true
    css: styles.css
    includes:
      in_header: header.html
    self_contained: false
    reveal_plugins: ["chalkboard"]
    reveal_options:
      chalkboard:
        theme: whiteboard
        toggleNotesButton: false
---



# Introduction
## Contributors
### Jaclyn Coate





# Attrition

## Exploratory Data Analysis

- Correlation
- Trends
- Causation?



***
### Missing data evaluation

- No missing values 
- Continue w/ exploratory data analysis

![](J.Coate.Case.Study.2.Presentation_files/figure-revealjs/NA eval-1.png)

***
### Dropping all zero variance variables

- EmployeeCount
- Over18
- StandardHours



***
### Remove logically irrelevant variables

- EmployeeNumber
- ID
- PerformanceRating
  - Self given performance rating



***
### Storing all categorical variables as factors

- Attrition     | Business Travel | Over Time
- Departemtn    | Education Field | Over 18
- Gender        | Job Role        | Marital Status



***
### Storing all level variables as factors

- Job Involvement    | Environment Satis  | Education | 
- Relationship Satis | Stock Option Level | Over 18   | 
- Work Life Balance  | Relationship Satis | Job Level | Job Satisfaction



***
### Correlated Variables Review

- Highly correlated variables can weaken the model

***
### Correlated Variables Review

![](J.Coate.Case.Study.2.Presentation_files/figure-revealjs/attition: high correlation-1.png)


***
- Highly correlated relationships
  - Total Working Years v Monthly Income: .78
  - Years at Company v Years in Current Role: .78
  - Years at Company v Years with Current Manager: .77
  - Years at Company v Total Working Years: .64
  - Years at Company v Years Since Last Promotion: .64
  - Years with Current Manager v Years in Current Role: .71

***
### Correlated Variables Review

  - Drop: Monthly Income, Years In Current Role, Years Since Last Promotion, Years At Company, Total Working Years, Years With Current Manager
  - Keep: Years at Company
  


***
### Numeric v Categorical Review

- Comparison of Attrition (dependent variable of interest) to categorical variables
- Density plot
  - Colored by Attrition
  - If density plot shows peaks in separate areas then important variable
  - If density plot shows peaks in the same spot (clean overlay) then not an important variable

***
### Numeric v Categorical Review

![](J.Coate.Case.Study.2.Presentation_files/figure-revealjs/attrition: numeric v categorical graph grid-1.png)

***
### Numeric v Categorical Review

- Remove variables that have similar trends
- Keep variables that are showing opposite attrition Patterns
    - Monthly Income, Years In Current Role, Number Companies Worked, Age



***
### Categorical v Categorical Review

- Comparison of Attrition (dependent variable of interest) to numerical variables available
- Bar Chart
  - Colored by Attrition

***
### Categorical v Categorical Review

![](J.Coate.Case.Study.2.Presentation_files/figure-revealjs/attrition: categorical v categorical-1.png)

***
### Categorical v Categorical Review

- Remove variables that show a small | zero difference
- Keep variables that show a large difference



***
### K Nearest Neighbor Model Variables

- Response Variable: Attrition
- Explanatory Variables: Number of Companies Worked, Over Time, Stock Option Level



***
### K Nearest Neighbor Model Best K

![](J.Coate.Case.Study.2.Presentation_files/figure-revealjs/unnamed-chunk-1-1.png)

***
### Final KNN Model
#### Attrition = B_0 + Beta_1 * NumCompaniesWorked + B_2 * OverTime + B_3 * StockOptionLevel
  - Accuracy > 80%
  - Sensitivity > 80%
  - Specificity = 75%



***
## Attrition Recap

- Explanatory Variables
  - Number of Companies Worked, Overtime, & Stock Option Level
- Attrition = Beta<sub>0</sub> + Beta<sub>1</sub> * NumCompaniesWorked + Beta<sub>2</sub> * OverTime + Beta<sub>3</sub> * StockOptionLevel

# Salary

## Exploratory Data Analysis

- Correlation
- Trends
- Causation?

***
### Missing data evaluation

### Dropping all zero variance variables

### Removed logically irrelevant variables



***
### Correlated Variables Review

![](J.Coate.Case.Study.2.Presentation_files/figure-revealjs/salary: high correlation-1.png)

***
### Correlated Variables Review

- Monthly Income correlated variables
  - Monthly Income v Total Working Years: .78
  - Monthly Income v Age: .48
  - Monthly Income v Years in Current Role: .36
  - Monthly Income v Years At Company: .49
  - Monthly Income v Years With Current Manager: .33
  - Monthly Income v Years Since Last Promotion: .32

***
### Correlated Variables Review
- Correlated explanatory variables can weaken the model
- Keep: Total Working Years
- Drop: Age, Years In Current Role, Years At Company, Years With Current Manager, Years Since Last Promotion



***
### Numeric v Numeric Review

![](J.Coate.Case.Study.2.Presentation_files/figure-revealjs/salary: numeric v numeric graph grid-1.png)

***
### Numeric v Numeric Review

- Clear linear relationships are selected 
  - Keep: Monthly Income, Total Working Years
  - Drop: Percent Salary, Daily Rate, Distance from Home, Hourly Rate, Monthly Rate, Number of Companies Worked, Percent Salary Hike, Training Times Last Year
  


***
### Numeric v Categorical Review

- Comparison of Monthly Income (dependent variable of interest) to categorical variables left in model
- Boxplot
  - Variations of Monthly Income between boxplots

***
### Numeric v Categorical Review

![](J.Coate.Case.Study.2.Presentation_files/figure-revealjs/Asalar: numeric v categorical graph grid-1.png)

***
### Numeric v Categorical Review

- Categorical variables with Monthly Income distribution differences
  - Eduction, Job Level, Job Role
  


***
##### Monthly Income v Education

![](J.Coate.Case.Study.2.Presentation_files/figure-revealjs/Monthly Income v Education-1.png)

***
##### Monthly Income v Job Level

![](J.Coate.Case.Study.2.Presentation_files/figure-revealjs/Monthly Income v Job Level-1.png)

***
##### Monthly Income v Job Role

![](J.Coate.Case.Study.2.Presentation_files/figure-revealjs/Monthly Income v Job Role-1.png)

***
### Numeric v Categorical Review
- Upone closer reivew
  - Job Level, Job Role



***
### MSPE Model

- Response Variable: Monthly Income
- Explanatory Variables: Job Level, Job Role, Total Working Years

*** 
### MSPE Model

- MonthlyIncome = B<sub>0</sub> + B<sub>1</sub> * TotalWorkingYears + B<sub>2</sub> * JobRole + B<sub>3</sub> * JobLevel
- Root Mean Square Error < 931


```
## [1] 930.998
```

## Salary Recap

- Explanatory Variables
  - Job Level, Job Role, Total Working Years
- Best prediction model
  - MonthlyIncome = B<sub>0</sub> + B<sub>1</sub> * TotalWorkingYears + B<sub>2</sub> * JobRole + B<sub>3</sub> * JobLevel

# Job Role Trends

## Exploratory Data Analysis

- Trends
- Causation?





*** 
### Categorical v Categorical

![](J.Coate.Case.Study.2.Presentation_files/figure-revealjs/eda of job role v categorical var-1.png)

***
### Categorical v Categorical

- Insightful Job Role Trends
  - Attrition, OverTime, Job Satisfaction

***
#### Job Role v Attrition

- Sales Reps, Research Scientists, Labratory Technicians

![](J.Coate.Case.Study.2.Presentation_files/figure-revealjs/job role v attrition-1.png)

***
#### Job Role v Over Time

- Sales Executives, Research Scientists, Labratory Technicians

![](J.Coate.Case.Study.2.Presentation_files/figure-revealjs/job role v over time-1.png)

***
#### Job Role v Job Satisfaction

- Sales Executives, Research Scientists, Labratory Technicians

![](J.Coate.Case.Study.2.Presentation_files/figure-revealjs/job role v job satisfaction-1.png)

***
### Categorical v Numeric

- Trends among certain job roles
  - Keep: Age, Years Since Last Promotion, Years At Company

***
#### Job Role v Age

![](J.Coate.Case.Study.2.Presentation_files/figure-revealjs/Job Role v Age-1.png)

***
#### Job Role v Years Since Last Promotion

![](J.Coate.Case.Study.2.Presentation_files/figure-revealjs/Job Role v Years Since Last Promotion-1.png)

*** 
#### Job Role v Years At Company

![](J.Coate.Case.Study.2.Presentation_files/figure-revealjs/Job Role v Years At Company-1.png)

***
## Job Role Trends Recap

- Regularly reporting overtime, lack of worklife balance, and spikes in attrition
  - Sales Executives, Research Scientists, Labratory Technicians
- Trends along Managers
  - Older in age, longer time between promotions, longest time with company

# In Conclusion
***
### Recap
- Attrition can be predicted with over 80% accurancy, over 80% sensitivity, and 75% specificity
  - Number of Companies Worked, OverTime, Stock Option Level
- Salaries can be made competitive taking into account
  - Job Level, Job Role, Years at Company
- Showing patterns of overtime, low worklife balance, and attrition
  - Sales Executives, Research Scientists, Labratory Technicians

# Thank You
