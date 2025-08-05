
# Online Course Sales Analysis Dashboard – Power BI



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
<img width="127" height="51" alt="image" src="https://github.com/user-attachments/assets/8832e84e-2c87-47b5-84dc-b0ad1ca26dfc" />
<img width="119" height="50" alt="image" src="https://github.com/user-attachments/assets/5cfc2799-60d7-42bb-9714-0eb8493d0adb" />
<img width="117" height="49" alt="image" src="https://github.com/user-attachments/assets/297b3668-b3ec-4559-a292-fcf9fc97f49c" />
<img width="116" height="50" alt="image" src="https://github.com/user-attachments/assets/b694a759-b308-4bdd-a224-298a076b9aca" />

###Report Snapshot (Power BI DESKTOP)

<img width="867" height="489" alt="image" src="https://github.com/user-attachments/assets/0d8954cc-6015-4207-bf99-0472077f96e6" />
<img width="870" height="498" alt="image" src="https://github.com/user-attachments/assets/d2dea50b-7484-4c53-8628-1be8fa3d4459" />



### Key Findings & Insights
Key Findings & Insights
🔹 Sales & Revenue Analysis
•    Monthly Revenue Trends:
o    Highest Sales occurred in March and April (16k each), indicating seasonal spikes — consider aligning course launches or promotions during these months.
o    May saw a revenue dip (7k) – explore potential marketing gaps or learner fatigue.
•    Discount Strategy Optimization:
o    Order volume increases from 192 to 217 for 0–20% discount range but declines sharply beyond that.
o    👉 Recommendation: Keep discounts within 10–20% to maximize orders and revenue without sacrificing price margins.
•    Top Revenue-Generating Courses:
o    Digital Marketing (10.9k), Python Basics (9.6k), JavaScript Essentials (9.2k)
o    These courses show high learner interest and can be prioritized for bundling or advanced versions.
🔹 Geographic Insights
•    Top Performing Countries by Revenue:
o    🇨🇦 Canada – 19k
o    🇺🇸 USA – 19k
o    🇮🇳 India – 18k
o    🇬🇧 UK – 16k
o    🇦🇺 Australia – 15k
•    👉 Suggestion: Target localized campaigns in these regions to further boost revenue.
🔹 Category & Customer Behavior
•    Popular Course Categories:
o    📊 Data – 304 orders
o    💼 Business – 291 orders
o    👨‍💻 Programming – 208 orders
o    🎨 Design – 197 orders
o    Indicates learner preference for data-driven and business-related skills.
•    Payment Preferences:
o    💳 Debit Card – 35.2%
o    💳 Credit Card – 33.3%
o    💲 PayPal – 31.5%
o    A balanced mix — ensure secure and flexible payment options are supported.
🔹 Course Completion & Engagement
•    Completion Rate Analysis:
o    Highest: ✅ Project Management Pro – 43%
o    Lowest: ❌ Machine Learning Intro – 25%
o    👉 Suggest reviewing course complexity, content length, or interactivity for low-performing courses.
•    Instructor Performance (Revenue / Rating):
o    ⭐ David Chen (SQL Beginners): 9.1k / 4.27
o    ⭐ Sandra White (Digital Marketing): 10k / 4.24
o    ⭐ Michael Lee (Data Science Bootcamp): 8.9k / 4.25
o    Shows positive correlation between instructor rating and revenue.
________________________________________
✅ Recommendations for Business Strategy
•    Launch seasonal promotions in high-performing months (Mar–Apr).
•    Maintain discounts in optimal 10–20% range for balancing profit and sales.
•    Focus on top-selling courses for further marketing, upselling, and course extension opportunities.
•    Improve course completion rates for lower-performing courses via better instructional design.
•    Expand in high-revenue countries (India, USA, Canada) with targeted marketing.
•    Monitor instructor effectiveness to identify training or content enhancement needs.

