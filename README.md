
# Online Course Sales Analysis Dashboard – Power BI



### Dashboard Link : https://app.powerbi.com/groups/me/reports/384d017e-e935-44dc-9e7d-1626c1a36de1/ReportSection

## Problem Statement

This Power BI project analyzes sales performance and learner engagement data from an online
course platform. The interactive dashboard provides insights into course-wise revenue, customer
behavior, payment methods, discount effectiveness, and course completion rates, helping
stakeholders make informed decisions to improve revenue, content quality, and user satisfaction.

The goal of this project is to:
- Understand sales trends and course performance.
- Analyze how discounts affect pricing and order volumes.
- Measure learner engagement through completion rates.
- Identify high-performing instructors and top-selling courses.
- Explore geographic and demographic patterns in sales.

### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : It was observed that in none of the columns errors & empty values were present.
- Step 4 : In the report view, under the view tab, theme was selected.
Step 5 : A column named "Discount Range" was created in which, discounts were grouped into various discount groups.
for creating new column following DAX expression was written;

Discount Range = 
SWITCH(TRUE(),
    'online_course_sales_dataset'[Discount Applied (%)] <= 10, "0-10%",
    'online_course_sales_dataset'[Discount Applied (%)] <= 20, "11-20%",
    'online_course_sales_dataset'[Discount Applied (%)] <= 30, "21-30%",
    'online_course_sales_dataset'[Discount Applied (%)] <= 40, "31-40%",
    'online_course_sales_dataset'[Discount Applied (%)] <= 50, "41-50%",
    "51%+"
)
Snap of new calculated column,

<img width="123" height="461" alt="Image" src="https://github.com/user-attachments/assets/02779182-da25-4648-b6e2-0ac7ff690d83" />






Step 6 : To analyze student engagement, a DAX measure was created to calculate the percentage of users who Completed their courses out of all those who enrolled.

Completion Rate (%) = 
DIVIDE(
    CALCULATE(COUNTROWS(online_course_sales_dataset), online_course_sales_dataset[Completion Status] = "Completed"),
    CALCULATE(COUNTROWS(online_course_sales_dataset), online_course_sales_dataset[Completion Status] IN {"Completed", "In Progress", "Not Started"})
) * 100
- Step 7 : Sales Analysis Visuals (Page 1)

 * Line Chart: Monthly Revenue Trends from November to May.
 * Stacked Bar Chart: Revenue by Course, highlighting top-performing courses like Digital Marketing and Python Basics.
 * Scatter Plot: Discount vs Final Price, showing a negative correlation.
 * Stacked Column Chart: Discount Range vs Total Revenue, clearly showing that as the discount range increases, total revenue decreases, indicating diminishing returns from higher discounts.
 * Country-wise Revenue Contribution using Decomposition Tree.
 * Line Chart: Discount vs Total Orders, it suggests that moderate discounts(up to 20%) encourage more purchases, while higher discounts may negatively impact perceived course value.

Course Performance Analysis (Page 2):

 * Stacked Column Chart: Number of Orders by Course Category (e.g., Data, Business, Programming).
 * Pie Chart: Payment Method Distribution – Credit Card, Debit Card, and PayPal.
 * Stacked Bar Chart: Completion Rate by Course, presenting how well each course retains learners based on their completion status.
 * Scatter Chart: Instructor Performance comparing revenue vs average course rating.
 * Stacked Column Chart: Number of orders by Country - top contributors: Canada, USA, India
 * Donut Chart: Course Completion Status - Shows distribution of Completed, In Progress, Not Starte.

- Step 8 : Visual filters (Slicers) were added for five fields named "Course Name", "Instructor", "Country", "Category" & "Payment Method".
- Step 9 : Four card visuals were added to the canvas, representing  total orders, total revenue, average selling price & average discount.           

- Step 14 : Calculated column was created in which, customers were grouped into various age groups.

for creating new column following DAX expression was written;
       
        Age Group = 
        
        if(airline_passenger_satisfaction[Age]<=25, "0-25 (25 included)",
        
        if(airline_passenger_satisfaction[Age]<=50, "25-50 (50 included)",
        
        if(airline_passenger_satisfaction[Age]<=75, "50-75 (75 included)",
        
        "75-100 (100 included)")))
        
Snap of new calculated column ,

![Snap_1](https://user-images.githubusercontent.com/102996550/174089602-ab834a6b-62ce-4b62-8922-a1d241ec240e.jpg)

        
- Step 15 : New measure was created to find total count of customers.

Following DAX expression was written for the same,
        
        Count of Customers = COUNT(airline_passenger_satisfaction[ID])
        
A card visual was used to represent count of customers.

![Snap_Count](https://user-images.githubusercontent.com/102996550/174090154-424dc1a4-3ff7-41f8-9617-17a2fb205825.jpg)

        
 - Step 16 : New measure was created to find  % of customers,
 
 Following DAX expression was written to find % of customers,
 
         % Customers = (DIVIDE(airline_passenger_satisfaction[Count of Customers], 129880)*100)
 
 A card visual was used to represent this perecntage.
 
 Snap of % of customers who preferred business class
 
 ![Snap_Percentage](https://user-images.githubusercontent.com/102996550/174090653-da02feb4-4775-4a95-affb-a211ca985d07.jpg)

 
 - Step 17 : New measure was created to calculate total distance travelled by flights & a card visual was used to represent total distance.
 
 Following DAX expression was written to find total distance,
 
         Total Distance Travelled = SUM(airline_passenger_satisfaction[Flight Distance])
    
 A card visual was used to represent this total distance.
 
 
 ![Snap_3](https://user-images.githubusercontent.com/102996550/174091618-bf770d6c-34c6-44d4-9f5e-49583a6d5f68.jpg)
 
 - Step 18 : The report was then published to Power BI Service.
 
 
![Publish_Message](https://user-images.githubusercontent.com/102996550/174094520-3a845196-97e6-4d44-8760-34a64abc3e77.jpg)

# Snapshot of Dashboard (Power BI Service)

![dashboard_snapo](https://user-images.githubusercontent.com/102996550/174096257-11f1aae5-203d-44fc-bfca-25d37faf3237.jpg)

 
 # Report Snapshot (Power BI DESKTOP)
 
 
