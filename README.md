# Data Analyses project with Python and SQL
## Product Sales Report for company **Pens and Printers**

### Contents:
1. [Project Code (Jupyter Notebook)](https://github.com/Overmarss/Product-Sales-Report/blob/main/product_sales.ipynb)
2. [Presentation Slides](https://github.com/Overmarss/Product-Sales-Report/blob/main/Report.pdf)
3. [Data Source](https://github.com/Overmarss/Product-Sales-Report/blob/main/product_sales.csv)
4. [Dataset befor data cleaning and validation - initial dataset](https://github.com/Overmarss/Product-Sales-Report/blob/main/product_sales_old.csv)

### Concept
The idea of the project is to find business insights from *report* of the Sale Team and provide recommendations for the business.

### Business problems
Business focus has been on selling products to enable our customers to be more creative, focused on tools for brainstorming. We have tested three different sales strategies for this, targeted email and phone calls, as well as combining the two.
#### Sales strategies:
- **Email**: Customers in this group received an email when the product line was launched, and a further email three weeks later. This required very little work for the team.
- **Call**: Customers in this group were called by a member of the sales team. On average members of the team were on the phone for around thirty minutes per customer. 
- **Email and call**: Customers in this group were first sent the product information email, then called a week later by the sales team to talk about their needs and how this new product may support their work. The email required little work from the team, the call was around ten minutes per customer.
### Business questions:
+ *How many customers were there for each approach?*
+ *What does the spread of the revenue look like overall? And for each method?*
+ *Was there any difference in revenue over time for each of the methods?*
+ *Which method would you recommend we continue to use?*
### Data structure
Data information table:
| **Column Name**  | **Details** |
| ------------- | ------------- |
| **week**  | Week sale was made, counted as weeks since product launch  |
| **sales_method**  | Character, which of the three sales methods were used for that customer  |
| **customer_id**  | Character, unique identifier for the customer  |
| **nb_sold** | Numeric, number of new products sold  |
| **revenue** | Numeric, revenue from the sales, rounded to 2 decimal places. |
| **years_as_customer** | Numeric, number of years customer has been buying from us (company founded in 1984) |
| **nb_site_visits**  | Numeric, number of times the customer has visited our website in the last 6 months  |
| **state** | Character, location of the customer i.e. where orders are shipped |
### Data validation
Using SQL database [PostgreSQL](https://www.postgresql.org/) I cleaned and validated [initial dataset](https://github.com/Overmarss/Product-Sales-Report/blob/main/product_sales_old.csv).

**Data Validation steps:**
- *sales_method*: initial dataset had 5 categories with some naming errors. Category 'email' was renamed into 'Email', and category 'em + call' was renamed to 'Email + Call'. This transformation changed the names of categories sales_method into 3 unique values.
- *revenue*: numeric values had missing values ('NA'). The maximum value is '238.32', the minimum is '32.54', without extreme points. Missing values were replaced with mean value '93.93'.
- *years_as_customer*: 42 unique values without missing values, from 0 to 63, as the company was founded in 1984, years as a customer must have values from 0 to 38. Rows with values more than 38 years were replaced with value 38. Rows values changed for 5 rows.
