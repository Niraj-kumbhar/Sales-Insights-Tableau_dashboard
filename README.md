# Sales-Insights-Tableau Dashboard

> this project is for my study purpose. ref: [CodeBasics-Tableau Project](https://www.youtube.com/watch?v=CCNd2fUfFkk&list=PLeo1K3hjS3usDI9XeUgjNZs6VnE0meBrL)

## Screenshot:
![Dashboard_Screenshot](https://user-images.githubusercontent.com/89059809/181613201-8d03a955-2c7c-4b16-a15a-9ec06661bcd3.png)

## Analysis
Data is present in MySQL database. [Database File](https://github.com/Niraj-kumbhar/Sales-Insights-Tableau_dashboard/blob/main/db_dump.sql)
<br>
* **Transaction table**
  * Observed negative and zero values in 'Sales_amount' column.<br>
 ```SELECT  * FROM sales.transactions t ORDER BY t.sales_amount ASC ;```<br><br>
  <img src="https://user-images.githubusercontent.com/89059809/181693376-4e2f087b-be50-46cb-b742-cd1a2d827116.png" height=400 width=600>
  
  * Observed some values in 'USD'<br>
  ```SELECT DISTINCT t.currency from sales.transactions t ;```<br><br>
  <img src="https://user-images.githubusercontent.com/89059809/181696363-3ba21d07-7682-4b2f-9d10-99f607723816.png">
* **Market table**
  * Observed 2 rows with null in zone column<br>
  ```SELECT  * FROM  sales.markets m ;```<br><br>
  <img src="https://user-images.githubusercontent.com/89059809/181697082-ae340a29-4b58-4a5b-ae2d-1c6438e1cb2b.png">

## Preprocessing
We haven't change any thing in database side. 
* I used Tableau's data filters to exclude negative or zero sales values. (sales_amount>1)
* Used data filters exclude both Market code with NULL values.
* Created Calculated field to convert 'USD' to 'INR'. <br>
  Logic: ```IF [currency]=="USD" THEN [sales_amount]*79.66 ELSE [sales_amount] END```
  here I have hard coded dollar covertion but we can use other techniques.
  
#### link to dashboard:
[Tableau_public](https://prod-apsoutheast-a.online.tableau.com/t/nirajkumbhar/views/Book1/SalesInsightsDashboard?:showAppBanner=false&:display_count=n&:showVizHome=n&:origin=viz_share_link)
