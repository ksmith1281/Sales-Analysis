# Sales Analysis
The documents in this repository showcase some examples on how I clean up a give csv file to perform data analysis. It is written in a Jupyter Notebook for easy readability. Here is an outline of the process and some of the questions that I have answered.

# Setup
Before I import the CSV file, I need to import the necessary Libraries such as pandas. Once this is complete, I make any adjustments to the final settings for better viewing and usability. 

# CSV Import and Info on Data
We are working with a csv file called 'orders_complete'. This file contains a concatenation of each order by items sold. As a result, this imported dataframe will have many null values as not each row represents a unique order but a specific item from a unique. Furthermore, only some customer and location information is provided, often when the orders were done online.

# Data Clean Up
Before we do any calculation or analysis, we much first clean our data. We will use the original dataframe initially as our location for all changes. Once we have enough to work with, we will select particular columns from this dataframe and call it our working dataframe: df_core. This method is useful as a project continue, you can simply revisit the cleaning portion of the code to adjust whatever is needed, and just add this to the working dataframe.

## 1. ID Name for Orders
This data can be thought of as a concatenation of every order's line items. For example, if customer 1 orders a shirt and a CD, while customer 2 orders a shirt, then we will see 3 rows: Each row corresponding to each line item. Each order has a unique Order ID, initially in column called 'Name', and has the format '#1234'. Let's change the name of the column and remove the '#' from all the values:

## 2. Filling NaN's for Matching OrderIDs
For each case where multiple items are part of an order (that is associated with a match OrderID), fields such as 'Billing Name' and 'Billing Street' are only filled in for the first item. This section works to fill null values present with the proper matching details. Additionally, we reorder the columns.
## 3. Number of Items Per Order
It is often useful to know the total number of items per order as this can indicate a specific type of value per customer, as well as a saturation of a given customer.
## 4. Create a Year and Month Column
Although a datetime column is sufficient for most date calculations, it is often convenient to quickly look at a month or year using these columns.
## 5. Adding Item Identifiers
Often analysis is based upon if an item is of a certain type. This could be simply a shirt versus a CD, or perhaps part of a unit sale or event. When the item has a condition that can be searched, we can do this here and add a column indicating as such.
### Example: Online Orders & Pledge Campaign
We can consider identifiers specific to the order as well as the item, in some cases these are interchangable. For example, all items that are part of an online orders will be given a Boolean value 'True'. If our point of sale has a non-NaN. For Pledge items, a new column can be made when the string 'Pledge' is found in the lineitem.

# Defining our Working Dataframe
Up to this point, we will have what I called df_raw as our dataframe, but it is filled with many columns. Depending on the analysis, it is recommended that we define a new dataframe that fits the needs of the current analysis, as the project grows, multiple dataframes can be defined and analysis. Some of which can be exported and used in other Data Analysis clients such as SQL. In this code, we will define the df_core and take opportunity to rename any columns and move their position that works with our needs.

# Testing
Next is simply the analysis, perhaps this is simply inquires of questions or building out plots. But to ensure that everything is working as expected, I add a testing section. This may appear in multiple locations as testing may be needed in multiple parts of the process.

# Insights
Here are some of the questions asked in this:
1. How many people took part in the Free Shipping and Handling Offer?
2. How many bought free Cd and the upsell offer?
3. What City/state do our customers reside in?
4. Cities/states with largest amount purchased? This is obviously Texas, but what are the top 5 or 10 other states/markets?
5. How many people bought free CD and came back for another purchase at a later date?
