# Predicting Customer Satisfaction for Rent the Runway
## Katrin Ayrapetov


## Table of Contents
<br> &emsp;&emsp;1.BACKGROUND AND PROBLEM STATEMENT
<br> &emsp;&emsp;2. DATA COLLECTION AND CLEANING
<br> &emsp;&emsp;3. EXPLORATORY DATA ANALYSIS
<br> &emsp;&emsp;4. MODEL
<br> &emsp;&emsp;5. CONCLUSIONS

### 1.BACKGROUND AND PROBLEM STATEMENT
<br> &emsp;&emsp;Rent the Runway is an e-commerce platform that allows users to rent, subscribe, or buy designer apparel and accessories. It was founded by Jennifer Hyman and Jennifer Fleiss, who launched the company in November 2009.
<br> &emsp;&emsp; The customer success department at Rent the Runway would like to be able to predict which customers are more likely to not be satisfied with their rental. Those customers then can be reached directly with proactive “Win Back” promotions to ensure repeat service and a chance for a positive rental experience to take place in the future.   
<br> &emsp;&emsp;Using historic data for 160,000 dress rentals, a classification model was built to determine whether a customer will be satisfied with the rental with 93% accuracy. 


### 2.DATA COLLECTION AND CLEANING

The website offers 7,980 different dresses. All the data for the dresses was scraped.  All the current  208,747 dress reviews were scraped from the website. 

Overview of Data Cleaning: 
* All the entries that were in the wrong column were re-entered in the correct column. 
* A new feature "BMI" was created out of the weight and height features. 
* Rows where all of the customer measurements (Weight, Age, Height, Body Type) were missing were deleted. 
* The block of text describing the dress was used to create three new features: Sleeves, Neckline, Dress Style.
<br> &emsp;&emsp; **Product Detail:** 'Blue printed cotton (69% Cotton, 27% Nylon, 4% Spandex). Hourglass. Sleeveless. Square neckline. 45" from shoulder to hemline.' <br>
becomes 
<br> &emsp;&emsp; **New Features:** 
<br> &emsp;&emsp; **Sleeves:** Sleeveless, 
<br>&emsp;&emsp; **Neckline:** Square Neckline, 
<br>&emsp;&emsp; **Dress_Style:** Hourglass 


The cleaned data set has 156,433 observations. 

**Features describing the customer:**  Type_of_customer, Size of the garment customer rented, Size the customer usually wears, Height, Age, Bust Size, Body Type, Weight, Season the garment was rented, Reason the garment was rented, Overall fit of the garment  

**Features describing the dress:** Retail Price of the garment, Rent price of the garment,  Number of Reviews left for that Garment, Dress Style, Sleeves and Neckline

### 3.EXPLORATORY DATA ANALYSIS
Our representative customer is: 
<br> &emsp;&emsp;36 years old
<br> &emsp;&emsp;5’4’’ and 140 pounds 
<br> &emsp;&emsp;Size 10 
<br> &emsp;&emsp;Renting mostly for special occasions like dates, vacations and weddings. 


Our representative garment is: 
<br> &emsp;&emsp;Sleeveless
<br> &emsp;&emsp;Has a v-neckline
<br> &emsp;&emsp;Has an hourglass shape 

### 5.MODELS

**Target Variable:**
1: Not Satisfied with Rental (Satisfaction Rating of 1,2,3 stars) 
0: Satisfied with Rental (Satisfaction Rating 4,5 stars)



The model I used in this study is **Catboost Classification**.  **CatBoost** is an open source algorithm based on gradient boosted decision trees. It supports numerical, categorical and text features.


#### Classification Metrics
<br>&emsp;&emsp;**Accuracy** - 0.93
<br>&emsp;&emsp;**ROC AUC** - 0.81


### 6.CONCLUSIONS
<br>&emsp;&emsp;We built a model that classifies whether a customer will be happy with their dress with 87% accuracy and is able to find 76% of customers who are not satisfied with the purchase. 
<br>&emsp;&emsp;It is recommended that those customers should be reached out to with a “Win Back” promotion even if they do not leave a negative review. 

##### Table 1. Data Dictionary

Variable | Description | Values|
---------|-------------|-------|
Type of Customer   | The customer is desginated as "Top Contributor" if they review items often|Top Contributor, unknown
Size   | The size of the dress rented.|Sizes 0 to 24
Rented_for |   the type of event for which the garment was rented. |Vacation, Wedding, Everyday, unknown, Party, Date, Work, Formal Affair 
Size_usually_worn  | the size usually worn by the customer. | various sizes
Height |  the reported height of the customer in inches. | various heights in inches
Age  |the reported age of the customer in years. |various ages in years
Band_Size  | The band size of the customer's Bust Size |Integer values betwen 28 and 48. 
Cup_Size  | The cup size of the customer's Bust Size |capital letter for Bust Size
Body_type | what body type the customer thinks they have |athletic, hourglass, pear, straightnarrow, petite, unknown, fullbust, apple 
Weight | the reported weight of the customer in pounds. |various weights
Brand  |the brand of the dress|various brands
Dress_Description | the specific garment name |various dress descriptions 
Retail_price  |the retail price of the dress|dollar amount
Rent_price | the rent price of the dress|dollar amount
Number_of_reviews | the number of reviews left for the particular dress|integer value
Sleeves | the type of sleeves on the garment has |sleeveless , long_sleeves, short_sleeves, three_quarter_sleeves, cap_sleeves, flutter_sleeves strapless, other 
Neckline|the type of neckline on the garment |v_neckline, crew_neckline, high_neckline, square_neckline, off_shoulder, shirt_collar_neckline, boat_neckline, scoop_neckline, sweetheart, halter, straight_neckline, mock_neckline, cowl_neckline, turtleneck, other                     
Dress_style| the cut of the bodice of the dress|hourglass,sheath, shift, gown,sleeveless, maxi,wrap, blouson, full skirt, short sleeves, a-line, long sleeves,empire_waist, cap sleeves, strapless, shirtdress, other 
Fabric | A column was created for each of 13 most commonly occuring fabrics | A number between 0 and 100 designating the amount of given fabric in blend
Rating | the number of stars out of five stars that the customer left rated the garment with.| out of five stars



