# Digital-Music-Store
# Digital Music Store - Data Analysis 🎵📊  

A data analysis project to help **Chinook Digital Music Store** optimize business opportunities and answer key business-related questions.  

## 📌 Project Overview  
This project analyzes **revenue trends, top-performing artists, and regional sales** using SQL and PostgreSQL.  
Interactive dashboards are created using **Tableau** to visualize insights for better decision-making.  

## 🛠️ Technologies Used  
- **SQL** (PostgreSQL)  
- **pgAdmin4** (Database Management)  
- **Tableau** (Data Visualization)  

## 📂 Database Schema  
The analysis is based on the **Chinook Database**, which includes tables like **Albums, Artists, Customers, Employees, Invoices, and Tracks**.  

[schema credit](https://github.com/lerocha/chinook-database/wiki/Chinook-Schema)  

![Chinook Database Schema](https://raw.githubusercontent.com/ptyadana/data-analysis-digital-music-store/master/ChinookSchema.png)  

## 📊 Key Analysis & Insights  
✅ **Top Artists & Albums:** Identified best-selling artists and albums.  
✅ **Revenue Trends:** Analyzed sales by region and genre to optimize marketing strategies.  
✅ **Customer Analysis:** Determined high-value customers based on purchase behavior.  
✅ **Performance Metrics:** Used SQL queries and Tableau dashboards for real-time data insights.  

## 📌 SQL Queries Used  
Here are some key queries used in the analysis:  

### 🎼 Top 5 Best-Selling Artists  
```sql
SELECT ar.Name AS Artist, SUM(il.UnitPrice * il.Quantity) AS TotalRevenue
FROM InvoiceLine il
JOIN Track t ON il.TrackId = t.TrackId
JOIN Album al ON t.AlbumId = al.AlbumId
JOIN Artist ar ON al.ArtistId = ar.ArtistId
GROUP BY ar.Name
ORDER BY TotalRevenue DESC
LIMIT 5;
