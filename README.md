# Hotel-analytics
Power BI dashboard for analyzing hotel performance across cities and platforms.  A data-driven Power BI report for hotel revenue, occupancy, and ADR metrics.  Interactive hotel analytics dashboard using Power BI and DAX.  Visualizing key hotel KPIs including revenue, RevPAR, occupancy, and realization.
# Dashboard Overview
![image](https://github.com/user-attachments/assets/2d681a6f-4b37-4815-b627-f0fd079c9dc1)
# Dax Queries  
Average Daily Rate = DIVIDE([Revenue],[Total Bookings],0)  
Revpar(revenue per room) = DIVIDE([Revenue],[Total capacity])   
DURN = DIVIDE([total_checkout],[No of days])  
DBRN = DIVIDE([total Bookings],[No of days])  
DSRN = DIVIDE([Total capacity],[No of days])  
No shows % = DIVIDE([total no shows],[Total Bookings])  
occupancy% = DIVIDE([Total successful Bookings],[Total capacity],0)  
Realisation% = 1-([Cancellation%]+[No shows %])  
Average ratings = AVERAGE(fact_bookings[ratings_given])  
Booking % = DIVIDE([Total Bookings],[Total capacity])  
Cancellation% = DIVIDE([total cancellation],[Total Bookings])  
No of days = DATEDIFF(MIN(dim_date[date]),MAX(dim_date[date]),DAY)+1  
Revenue = SUM(fact_bookings[revenue_realized])  
Total Bookings = COUNT(fact_bookings[booking_id])  
total_checkout = CALCULATE(COUNTROWS(fact_bookings),fact_bookings[booking_status]="checked out")  
total no shows = CALCULATE(COUNTROWS(fact_bookings),fact_bookings[booking_status]="No show")  
total cancellation = CALCULATE(COUNTROWS(fact_bookings),fact_bookings[booking_status]="Cancelled") 

ADR wow change% =   
var selv = IF(HASONEFILTER(dim_date[Wn]),SELECTEDVALUE(dim_date[Wn]),MAX(dim_date[Wn]))  
var revcw = CALCULATE([ADR],dim_date[Wn]=selv-1)  
var revpw = CALCULATE([ADR],FILTER(ALL(dim_date),dim_date[Wn]=selv-1))  
RETURN  
DIVIDE(revcw,revpw,0)-1  

Total successful Bookings = SUM(fact_aggregated_bookings[successful_bookings])

# ---------------------Insights and trends----------------------------
![image](https://github.com/user-attachments/assets/edd3390f-1881-4111-8fae-ccbab880d56d)  

![image](https://github.com/user-attachments/assets/8062a076-0cfd-4e30-af5d-1050c75aa50d)




 
