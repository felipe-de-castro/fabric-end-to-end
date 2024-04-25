# Microsoft Fabric-end-to-end

This is a basic end-to-end project using Microsoft Fabric Lakehouse building a medallion architecture. <br>
I do not own the whole project ideia, i just followed with almost all steps and incremented with new ideas that made sense.
Throughout this project, the bulb emoji ( :bulb: ) is my idea.

## Creating Workspace and Lakehouse
In Fabric using the Data Engineering component, got to "WorkSpaces" > "New Workspace" > Setup with a name of your choice.<br>
As soon as the workspace loads, you will be able to create the 'Lakehouse' itens clicking on the "+ New " button.

## Ecommerce Dataset Overview
For the dataset, we have two excels workbooks with sales information and return information. <br>
In the sales worksheet, includes order ID, order date, shipping date, aging, shipping mode, and product details. <br> 
Additionally, we track profit, discount, shipping costs, and order priority, whether it's medium or high. <br> 
In the 'return' sheet, we list all products returned by customers.

## Lakehouse - Upload Files from Local System using Python
In the Lakehouse create 2 folders, 'Current' and 'Archives'. :file_folder:	<br>

💡*In the original project the files were uploaded manually* , so I choose to upload them by code (python) and using github api looking for any files in 'files' folder.
 Can check it out in the notebook [Notebook ingest_data](notebooks/ingest_data.ipynb)

## Loading Bronze Table - Bronze Sales
Utilizing notebook in pyspark was done the ingestion from the .xlsx files in 'files' folder throught github api link.

  [Notebook ingest_data](notebooks/ingest_data.ipynb)

## Dimensional Model Overview

1. Loading Order Return Dimension - Gold Layer [notebook link](notebooks/gold-order_returns.ipynb)
2. Loading Customer Dimension - Gold Layer [notebook link](notebooks/gold_customer.ipynb)
3. Loading Date Dimension - Gold Layer [notebook link](notebooks/gold_date.ipynb)
4. Loading Fact Sale Fact Table - Gold Layer [notebook link](notebooks/gold_fact_sale.ipynb)
5. Loading Order Priority Dimension - Gold Layer [notebook link](notebooks/gold_order_priority.ipynb)
6. Loading Product Dimension - Gold Layer [notebook link](notebooks/gold_product.ipynb)
7. Loading Ship Mode Dimension - Gold Layer [notebook link](notebooks/gold_shipmode.ipynb)

##  Mounting to Lakehouse and Archiving Files
In this part, using [mssparkutils](https://learn.microsoft.com/en-us/azure/synapse-analytics/spark/microsoft-spark-utilities?pivots=programming-language-python) you will be able to work with file systems, such as copie files, move them, list a directory etc. <br>
After the files been updated and the data used to bulding the models, we will mount the enviroment file system so the files can be moved to a 'Archives' folder (created earlier).

[Notebook to mount and Archive files](notebooks/Archives.ipynb)

##  Running all notebook in Data Factory.
## Creating Data Pipeline to run Final Notebook
## Creating Semantic Model and Creating Auto Generated Report
## Creating Auto Generated Report from Semantic Model
## Connecting to Semantic Model Using Power BI Desktop in Direct Lake and Direct Query Mode
