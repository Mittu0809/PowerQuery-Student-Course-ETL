# PowerQuery-Student-Course-ETL
This project employs Power Query to clean and analyze student course registration data from Excel. It streamlines data processing by removing duplicates, handling missing values, and creating fields like Student ID and Fee Status. The outcome is a clean dataset and a pivot table for efficient analysis of course registrations and fees.


Student Course Data Transformation using Power Query
This project demonstrates how to clean, transform, and analyze a dataset of student course registrations using Power Query in Excel. The project includes data loading, cleaning steps, transformation tasks, and creating a pivot table for further insights.

Project Overview : 

The raw dataset is in Excel format with the following columns:

Name
Email
Course
Registration Date
Fee Paid 


Through this project, we connect to the raw Excel file, clean and transform the data in Power Query, and load the final dataset back into Excel to create a pivot table for course-wise fee and student count analysis.

Steps : 
1. Connect to the Data
Source File: Load the raw Excel file and open it in Power Query Editor.

2. Data Cleaning Steps
After examining the data, we perform the following cleaning tasks:

Step 2.1: Remove Unnecessary Columns 

Extra columns with null values are removed. Select these columns and delete them, keeping only the required columns: Name, Email, Course, Registration Date, and Fee Paid. 

Step 2.2: Remove Unnecessary Rows 

Remove the first three rows that contain null or irrelevant data, ensuring that the actual data starts from row 4. 

Step 2.3: Promote Headers 

Set the first row as headers for all columns. 

Step 2.4: Change Data Types 

Assign suitable data types: 

Name: Text
Email: Text
Course: Text
Registration Date: Date
Fee Paid: Whole Number 

Step 2.5: Filter Blanks 

Registration Date: Filter out null values, as records without registration dates are invalid.
Course: Filter out blank entries. 

Step 2.6: Remove Duplicates 

Identify and remove duplicate records based on the Email column to ensure each student is only listed once. 

3. Data Transformation Steps
   
Next, we create new columns for additional analysis:

Step 3.1: Generate Student ID 

Student ID: Combine the first name with the first letter of the last name from the Name column. (e.g., "Hailey Antcliff" becomes "HaileyA").
Use Add Column > Column from Examples to auto-generate this pattern.
Rename the generated column to "Student ID". 

Step 3.2: Determine Term Start Date 

Term Start Date: Based on Registration Date, create a conditional column with two date options:
If Registration Date is before December 15, 2022, set Term Start Date to February 1, 2023.
Otherwise, set Term Start Date to April 1, 2023.
Use Add Column > Conditional Column to define this logic and generate the column. 

Step 3.3: Calculate Fee Status 

Fee Status: Create a new column with three categories based on Fee Paid:
Not Paid if Fee Paid is null.
Fully Paid if Fee Paid is 500.
Partly Paid if Fee Paid is less than 500.
Use Add Column > Conditional Column to define these conditions and rename the resulting column as "Fee Status". 

4. Load Data into Excel
   
Query Name: Rename the query as "Students Courses" for clarity.
Load: Close the Power Query Editor and load the cleaned and transformed data back into Excel. 

5. Post-Load Adjustments
Change the Term Start Date column format from General to Date in Excel for consistency.

6. Create Pivot Table for Analysis
Insert a pivot table in a new worksheet with the following layout:
Rows: Course
Values:
Fee Paid to calculate total fees by course.
Email (count) to determine the number of students per course.

Results and Analysis : 

The pivot table provides a summary of the data, showing:

Total fees paid per course.
The number of students registered for each course.
