# Nhlakanipho-s-Portfolio
# Sales Data Analysis for a Motor Company 
# This document shows the sales data analysis I conducted using Sequel Query Language (SQL)
# The code below highlights the different queries I conducted in order to answer the questioons related to the business task. 

--CHECKING DATA FOR UNIQUE VALUES
SELECT DISTINCT status,
FROM `skilful-nexus-407309.google_captstone_project.salesdata`

SELECT DISTINCT YEAR_ID,
FROM `skilful-nexus-407309.google_captstone_project.salesdata`

SELECT DISTINCT PRODUCTLINE,
FROM `skilful-nexus-407309.google_captstone_project.salesdata`

SELECT DISTINCT TERRITORY,
FROM `skilful-nexus-407309.google_captstone_project.salesdata`

SELECT DISTINCT COUNTRY,
FROM `skilful-nexus-407309.google_captstone_project.salesdata`

SELECT DISTINCT DEALSIZE,
FROM `skilful-nexus-407309.google_captstone_project.salesdata`

--ANALYSIS BY AGGREGATE FUNCTIONS

SELECT PRODUCTLINE, SUM(SALES) AS REVENUE
FROM `skilful-nexus-407309.google_captstone_project.salesdata`
GROUP BY PRODUCTLINE
ORDER BY 2 desc

SELECT YEAR_ID, SUM(SALES) AS REVENUE
FROM `skilful-nexus-407309.google_captstone_project.salesdata`
GROUP BY YEAR_ID
ORDER BY 2 desc

SELECT DEALSIZE, SUM(SALES) AS REVENUE
FROM `skilful-nexus-407309.google_captstone_project.salesdata`
GROUP BY DEALSIZE
ORDER BY 2 desc

SELECT MONTH_ID, SUM(SALES) AS REVENUE
FROM `skilful-nexus-407309.google_captstone_project.salesdata`
GROUP BY MONTH_ID
ORDER BY 2 desc

SELECT MONTH_ID, PRODUCTLINE, SUM(SALES) AS Revenue,COUNT(ORDERNUMBER) AS FREQUENCY
FROM `skilful-nexus-407309.google_captstone_project.salesdata`
WHERE YEAR_ID = 2004 and MONTH_ID = 11 
GROUP BY MONTH_ID, PRODUCTLINE
ORDER BY 3 DESC

--RFM Analysis. AN ANALYSIS ON WHO IS OUR BEST CUSTOMER. 
--RFM (Recency,Frequency and Monetary Value) is a measure of the indexing value that uses past purchasing behaviour to segment customers. 

SELECT CUSTOMERNAME,
SUM(SALES) AS MonetaryValue,
AVG(SALES) AS AvgMonetaryValue,
COUNT(ORDERNUMBER) AS Frequency,
MAX(ORDERDATE) AS LastOrderDate,
FROM `skilful-nexus-407309.google_captstone_project.salesdata`
GROUP BY CUSTOMERNAME
