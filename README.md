# Credit-Card-Financial-Dashboard.

Agenda:
"Develop a data-driven dashboard to optimize credit card operations by providing data visualizations of key performance indicators. Which will empower stakeholders with actionable insights to drive business growth and enhance customer satisfaction."



Steps perform:
1.  Import Data from SQL database.
a.	Importing CSV File from SQL database to power Bi. 
The Above mention steps are being done within my Postgre SQL Database.



Dax Quries :

 
1. Created a column name (Customer Age Group)
Custme Age Group = SWITCH(
        TRUE(),
         customer[Customer_Age]<30,"20-30",
            customer[Customer_Age]>= 30 && customer[Customer_Age]<40, "30-40",
     customer[Customer_Age]>= 40 && customer[Customer_Age]<50, "40-50",
            customer[Customer_Age]>= 50 && customer[Customer_Age]<60, "50-60",
            customer[Customer_Age]>= 6,"60+",
            “Unknown”
             )

2. Created a column name (Customer Income Group)
Customer Income Group = SWITCH(
        TRUE(),
        customer[Income]<35000,"Low",
        customer[Income]>=35000 && customer[Income] < 70000,"Medium",
        customer[Income]>=70000,"High",
        "Unknow"
)

 3. Created another column name (Revenue Generated)
Revenue Generated = credit_card[Annual_Fees]+ credit_card[Total_Trans_Amt] +credit_card[Interest_Earned]

4 Created another column name (Week Number)
Week_Number = WEEKNUM(credit_card[Week_Start_Date])

5  Created a measure name (current week revenue )
Current_Week_Revenue = CALCULATE(
    SUM(credit_card[Revenue Generated]),
    FILTER(
        ALL(credit_card),
        credit_card[Week_Number]=MAX(credit_card[Week_Number])))

6 Created a measure name (Previous Week Revenue)
Current_Week_Revenue = CALCULATE(
    SUM(credit_card[Revenue Generated]),
    FILTER(
        ALL(credit_card),
        credit_card[Week_Number]=MAX(credit_card[Week_Number])-1))

7 Created a new measure name (Week Over Week Revenue )
Week_Over_Week_Revenue = DIVIDE((credit_card[Current_Week_Revenue]-credit_card[Previous_Week_Revenue]),credit_card[Previous_Week_Revenue])



Project Insights:

1.	A 12.8% decrease in revenue has been observed.
2.	Total Transaction amount count is getting decrease by 1384 as compared with previous week (51).
3.	Females are significantly more likely to be delinquent (57.98%) compared to males (42.02%).
4.	Activation rate of credit card with in 1 month for female (59.8%) is more as compare to male.
5.	Use of card for Swipe is more while doing expenses by customer then another method. 
6.	Self-employed Customer having more Delinquent percentage then other group. 
7.	Credit card limit by Bule card (76.91 %) is more as compare to other.
8.	Credit card limit is more for female (59.75 %) as compare to male. 
9.	Credit card limit is (25.10 %) more for Self-employed as compare to other job Category. 

