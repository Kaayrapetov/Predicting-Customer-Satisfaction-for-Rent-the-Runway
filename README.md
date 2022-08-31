# Predicting Customer Satisfaction for Rent the Runway
## Katrin Ayrapetov


## Table of Contents
<br> &emsp;&emsp;1.BACKGROUND AND PROBLEM STATEMENT
<br> &emsp;&emsp;2. DATA COLLECTION AND CLEANING
<br> &emsp;&emsp;3. EXPLORATORY DATA ANALYSIS
<br> &emsp;&emsp;4. FEATURE SELECTION
<br> &emsp;&emsp;5. MODELS
<br> &emsp;&emsp;6. CONCLUSIONS

### 1.BACKGROUND AND PROBLEM STATEMENT
<br> &emsp;&emsp;Rent the Runway is an e-commerce platform that allows users to rent, subscribe, or buy designer apparel and accessories. It was founded by Jennifer Hyman and Jennifer Fleiss, who launched the company in November 2009.
<br> &emsp;&emsp;The customer success department at Rent the Runway would like to use existing feedback, together with customer data, to predict which customers have a higher chance of not being satisfied with their rentals, even if they do not leave a negative review. 
<br> &emsp;&emsp;Those customers then can be reached directly with “Win Back” promotions to ensure repeat service and a chance for a positive rental experience to take place in the future. 

### 2.DATA COLLECTION AND CLEANING

The website offers 7,980 different dresses. All the data for the dresses was scraped.  All the current  208,747 dress reviews were scraped from the website. 

Overview of Data Cleaning: 
* All the entries that were in the wrong column were re-entered in the correct column. Regex was used a lot for this purpose. 
* Height was converted from feet and inches to just inches. 
* A new feature "BMI" was created out of the weight and height features. 
* The date that the garment was rented was replaced with the season that the garment was rented. 
* Rows where all of the customer measurements (Weight, Age, Height, Body Type) were missing were deleted. 
* After the cleaning of the customer data, 161,418 observations remain. 

* The Retail price of the dress, the Rent price of dress, the number of reviews left for the dress will be stripped off extra symbols and just turned into an integer. 
* The product description will be broken up into three additional features: Sleeves, Neckline and Dress Style. 
* For example:
<br> &emsp;&emsp; **Product Detail:** 'Blue printed cotton (69% Cotton, 27% Nylon, 4% Spandex). Hourglass. Sleeveless. Square neckline. 45" from shoulder to hemline.' <br>
becomes 
<br> &emsp;&emsp; **New Features:** 
<br> &emsp;&emsp; **Sleeves:** Sleeveless, 
<br>&emsp;&emsp; **Neckline:** Square Neckline, 
<br>&emsp;&emsp; **Dress_Style:** Hourglass 


The cleaned data set has about 156,433 observations. 

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


### 4.FEATURE SELECTION
Using a Chi Squared test , we selected features that exhibit the most dependence with Customer Satisfaction. 


### 5.MODELS

**Target Variable:**
1: Not Satisfied with Rental (Satisfaction Rating of 1,2,3 stars) 
0: Satisfied with Rental (Satisfaction Rating 4,5 stars)

#### Logistic Regression 
<br>&emsp;&emsp;**Accuracy** - 0.836 
<br>&emsp;&emsp;**ROC AUC** - 0.535

#### Naive Bayes Classifier 
<br>&emsp;&emsp;**Accuracy** - 0.803
<br>&emsp;&emsp;**ROC AUC** - 0.629

#### Knn Classifier 
<br>&emsp;&emsp;**Accuracy** - 0.834
<br>&emsp;&emsp;**ROC AUC** - 0.5320

#### Random Classifier 
<br>&emsp;&emsp;**Accuracy** - 0.8695
<br>&emsp;&emsp;**ROC AUC** - 0.6642

#### XGBoost  
<br>&emsp;&emsp;**Accuracy** - 0.8698
<br>&emsp;&emsp;**ROC AUC** - 0.6638



<br> **For the Neural Network**
<br>&emsp;&emsp;The numerical data was turned into categorical by binning along the 10 percentiles.  
<br>&emsp;&emsp;Entity embedding was used on all the features. 
<br>&emsp;&emsp;An Additional Batch Normalization Layer was added. 


<br> **Metrics for the Neural Network**
<br>&emsp;&emsp; Accuracy:  0.8479
<br>&emsp;&emsp; ROC AUC: 0.81281

### 6.CONCLUSIONS
<br>&emsp;&emsp;We built a model that classifies whether a customer will be happy with their dress with 87% accuracy and is able to find 76% of customers who are not satisfied with the purchase. 
<br>&emsp;&emsp;It is recommended that those customers should be reached out to with a “Win Back” promotion even if they do not leave a negative review. 

##### Table 1. Data Dictionary

Variable | Description | Values|
---------|-------------|-------|
Size   | The size of the dress rented.|Sizes 0 to 24
Overall_fit  | The overall fit of the garment as judged by customer. |True to Size, Large, Small, Unknown
Rented_for |   the type of event for which the garment was rented. |Vacation, Wedding, Everyday, unknown, Party, Date, Work, Formal Affair 
Size_usually_worn  | the size usually worn by the customer. | various sizes
Height |  the reported height of the customer in inches. | various heights
Age  |the reported age of the customer in years. |various ages
Bust_size  | the reported bust size of  the customer.|various bustsizes
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
Rating | the number of stars out of five stars that the customer left rated the garment with.| out of five stars



