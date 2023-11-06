# Feature engineering steps taken

## Step 1: Drop irrelevant columns

'latitude','longitude','State','Local_Government' 

Market_Name has been chosen over these columns as there is a stronger negative correlation between Market_Name and price than the others:

| Metric           | Pearson Correlation | Spearman Correlation |
|------------------|---------------------|----------------------|
| latitude         | -0.025368           | -0.153525            |
| longitude        | -0.004234           | -0.167992            |
| State            | 0.000567            | -0.044269            |
| Market_Name      | -0.033355           | -0.264915            |
| Local_Government | -0.013005           | -0.149497            |
| price            | 1.000000            | 1.000000             |

'usdprice' : dropped because price is converted to 'NGN'
'currency' : There is only one currency in the dataset, so this column is not relevant
'priceflag' : irrelevant

## Step 2: Check for inconsistant values

There are no values below or equal to zero

## Step 3: Seasonality

The creation of sine and cosine wavelets here is likely aimed at capturing the cyclical nature of seasonal effects on the dataset. Seasonality often impacts pricing, availability, and demand for certain commodities. By transforming the date information into a cyclical continuous feature through sine and cosine wavelets, your model can better understand the recurring nature of seasons. This is an elegant way to encode cyclical data, allowing the model to recognize, for instance, that December comes after November and before January, year after year.

new columns = ['sin_date','cos_date']

## step 4: Group commodities 

Grouping commodities that have similar distributions can help in reducing the dimensionality of the data, making the model simpler and potentially reducing overfitting. It also helps in making the model more generalizable, as it can learn patterns across a group of similar commodities instead of learning patterns for each commodity independently.

| Commodity           | Group            |
|---------------------|------------------|
| Beans (red)         | Beans (grouped)  |
| Beans (white)       | Beans (grouped)  |
| Cowpeas (brown)     | Cowpeas (grouped)|
| Cowpeas (white)     | Cowpeas (grouped)|
| Maize (white)       | Maize (grouped)  |
| Maize (yellow)      | Maize (grouped)  |
| Meat (beef)         | Meat (grouped)   |
| Meat (goat)         | Meat (grouped)   |
| Rice (imported)     | Rice (grouped)   |
| Rice (local)        | Rice (grouped)   |
| Rice (milled, local)| Rice (grouped)   |
| Sorghum (brown)     | Sorghum (grouped)|
| Sorghum (white)     | Sorghum (grouped)|


## Step 5: Convert Units

Standardizing units across the dataset ensures consistency and makes comparisons meaningful. If different rows have prices per kilogram, per tuber, per liter, etc., it would be hard to compare them or use them in a single model. By converting everything to a common unit, you ensure that a price in one row represents the same quantity of commodity as a price in another row. This consistency is crucial for accurate analysis and modeling.

Yams: Assume an average weight of 1.5 kg per tuber.
Potatoes: Assume an average weight of 0.2 kg per tuber.
Cassava: Assume an average weight of 1 kg per tuber.
Palm Oil: Assume an average weight of 1.123 kg per litre.
    
Source: "LOCAL WEIGHTS AND MEASURES IN NIGERIA"

100 Tubers converted to kg
Palm oil standardised to Litre not KG

units remaining: ['1KG' 'Unit' 'L' '30 pcs']

## Step 6: Checked for outliers

Sliced out each commodity per year and checked for outliers using the Interquartile Range (IQR) method. This was done because data is not stationary and the distribution changes over time. An IQR of 2 was used to determine outliers for price 1.5 was used for inflation. Total outliers removed where 2562 (3.99%)


## Step 7: Duplicated rows

Calculate the mean price of rows that are duplicated based on all features remaining except price. Dataset reduced by 17.46% (10764 rows)

## Step 8: Encoding

Ordinal encoding categorical variables by ranking commodities, categories, and market names by price, provides ordinal information that could be meaningful for the model. This ordinal encoding can capture useful information about the relationships between categories. The ranking provides a way to keep some order information which could be beneficial for certain algorithms. Moreover, this method of encoding can also help in reducing the feature space, making the model simpler and potentially more interpretable, while also being more robust to the introduction of new categories in the future.

This method was applied to the following columns:
['Commodity','Market_Name','category']

## Step 9: Season Encoding

| Season            | Encoding |
|-------------------|----------|
| Dry Season        | 2        |
| Early Rainy Season| 3        |
| Peak Rainy Season | 1        |
| Late Rainy Season | 0        |

This correlated with the pricings of the commodity so a similar approach was taken as in step 8. Assuming that local farming is at it's peak during the rainy season, the prices of commodities should be lower. This was not the case for all commodities, but the majority of them.
