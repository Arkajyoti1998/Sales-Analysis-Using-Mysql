# Sales-Analysis-Using-Mysql<br>

# viewing the data<br>
select * from sales;<br>

# checking for the distinct values:-<br>
select distinct(STATUS)from sales;<br>
select distinct(YEAR_ID)from sales;<br>
select distinct(PRODUCTLINE)from sales;<br>
select distinct(COUNTRY)from sales;<br>
select distinct(PRODUCTCODE)from sales;<br>
select distinct(TERRITORY)from sales;<br>
select distinct(DEALSIZE)from sales;<br>
<br>
# ANALYSIS:-<br>
# Grouping sales by productline<br>
select PRODUCTLINE, sum(sales) Revenue<br>
from sales<br>
group by PRODUCTLINE<br>
order by Revenue desc;<br>
<br>
# Most ordered productline<br>
select PRODUCTLINE, count(ORDERNUMBER) as odercount<br>
from sales<br>
group by PRODUCTLINE<br>
order by odercount desc;<br>
<br>
# grouping sales by year<br>
select YEAR_ID, sum(sales) Revenue<br>
from sales<br>
group by YEAR_ID<br>
order by Revenue desc;<br>
<br>
# Checking why the sales is so low on year 2005<br>
select distinct(MONTH_ID)<br>
from sales<br>
where YEAR_ID=2005;           # They have made sales for 5 months only in 2005 <br>
<br>
# grouping sales by country<br>
select COUNTRY, sum(sales) Revenue<br>
from sales<br>
group by COUNTRY<br>
order by Revenue desc;<br>
<br>
# grouping sales by TERRITORY<br>
select TERRITORY, sum(SALES) Revenue<br>
from sales<br>
group by TERRITORY<br>
order by Revenue desc;<br>
<br>
# grouping sales by DEALSIZE<br>
select DEALSIZE, sum(SALES) Revenue<br>
from sales<br>
group by DEALSIZE<br>
order by Revenue desc;<br>

# the best month for sales in a specific year along with order count<br>
select  MONTH_ID, sum(sales) Revenue, count(ORDERNUMBER) Frequency<br>
from sales<br>
where YEAR_ID = 2004   #we can change according to our requirements<br>
group by  MONTH_ID<br>
order by Revenue desc;<br>
<br>
#As we found earlier november is the best month so lets check which what are the product that sare sold maximum in november<br>
select  MONTH_ID, PRODUCTLINE, sum(sales) Revenue, count(ORDERNUMBER)<br>
from sales<br>
where YEAR_ID = 2003 and MONTH_ID = 11    #we can change according to our requirements<br>
group by  MONTH_ID, PRODUCTLINE<br>
order by Revenue desc;<br>
<br>
# Finding the TotalSales, AvgSAles, OderCount, and the last order date for different customers<br>
select CUSTOMERNAME, <br>
sum(sales) TotalSales,<br>
avg(sales) AvgSales,<br>
count(ORDERNUMBER) OderCount,<br>
max(ORDERDATE) last_order_date<br>
from sales<br>
group by CUSTOMERNAME<br>
order by AvgSales desc;     #change this according to our requirement<br>
<br>
# City with the highest number of sales <br>
select city, sum(sales) Revenue<br>
from sales<br>
group by city<br>
order by Revenue desc;<br>
<br>
# City with the highest number of oder count<br>
select city, count(ORDERNUMBER) OderCount<br>
from sales<br>
group by city<br>
order by OderCount desc;<br>
<br>
# Country with the highest sales<br>
select country, sum(sales) Revenue<br>
from sales<br>
group by country<br>
order by Revenue desc;<br>
<br>
# Country with the highest number of oder count<br>
select country, count(ORDERNUMBER) OderCount<br>
from sales<br>
group by country<br>
order by OderCount desc;<br>
<br>
# best product in each country<br>
select country, YEAR_ID, PRODUCTLINE, sum(sales) Revenue<br>
from sales<br>
where country = 'USA'    #we change according to our requirement<br>
group by  country, YEAR_ID, PRODUCTLINE<br>
order by Revenue desc;<br>
<br>
# best product in each city<br>
select city, YEAR_ID, PRODUCTLINE, sum(sales) Revenue<br>
from sales<br>
where city = 'Madrid'    #we change according to our requirement<br>
group by  country, YEAR_ID, PRODUCTLINE<br>
order by Revenue desc;<br>
<br>
# sales in each quater<br>
select QTR_ID, sum(sales) as Revenue<br>
from sales<br>
group by QTR_ID<br>
order by Revenue;<br>
<br>
# oder count in each quater<br>
select QTR_ID, count(ORDERNUMBER) OderCount<br>
from sales<br>
group by QTR_ID<br>
order by OderCount;<br>


# DASHBOARD:- <br>
![Power BI Desktop 28-Jan-23 2_51_53 PM](https://user-images.githubusercontent.com/100423431/215258585-ab7661f5-3604-4df3-a974-e193b36734e3.png)
![Power BI Desktop 28-Jan-23 2_52_02 PM](https://user-images.githubusercontent.com/100423431/215258588-a0d091de-a0b4-4aa3-aeb0-01808d9b3ec7.png)
![Power BI Desktop 28-Jan-23 2_52_08 PM](https://user-images.githubusercontent.com/100423431/215258589-99d51a21-107d-4b14-a183-9e6e6abf0fae.png)
![Power BI Desktop 28-Jan-23 2_52_22 PM](https://user-images.githubusercontent.com/100423431/215258592-9c48ae9e-f828-4c62-9234-751bff3b987e.png)


