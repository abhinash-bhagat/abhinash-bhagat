# Data Gathering and Preprocessing

This repository contains datasets and the jupyter notebook used for our task. The task involves merging two primary datasets: **food price data and inflation data**. These datasets were collected, cleaned, and merged to support our research. The data preprocessing steps are described below.

## Food Price Data

### Data Source
The food price data was sourced from the [Humanitarian Data Exchange (HDX)](https://data.humdata.org/dataset/wfp-food-prices-for-nigeria?). You can access the original dataset [here](https://data.humdata.org/dataset/42db041f-7aaf-4ab4-961f-2a12096861e7/resource/12b51155-0cd3-4806-9924-61ede4077591/download/wfp_food_prices_nga.csv).

### Data Preprocessing Steps
1. Renaming Columns: Columns were renamed to provide clearer labels.
2. Removing First Row: The first row, which often contains metadata, was removed.
3. Date Conversion: The 'Date' column was converted to a datetime data type.
4. Extracting Year and Month: New columns for 'year' and 'month' were created based on the 'date' column.
5. Filtering Data: Rows with a 'priceflag' of 'forecast' were removed.
6. Unit Conversion: The 'price' column was standardized to represent prices per 1 KG where applicable.
7. Season Mapping: A new 'season' column was created based on the 'month' column.
8. Data Types: Data types were adjusted for numeric columns (latitude, longitude, price, usdprice, Inflation).

## Inflation Data

### Data Source
The inflation data was sourced from [macrotrends](https://www.macrotrends.net/countries/NGA/nigeria/inflation-rate-cpi). You can access the original dataset [here](https://dagshub.com/Omdena/KanoNigeriaChapter_FoodPrices/raw/278dd0522a02d7e1407777bb82a1f796b399b3ed/task%20%20/task%201_%20data%20collection%20%20and%20preprocessing%20/inflation_data.csv).

### Data Preprocessing Steps
1. Date Conversion: The 'DATE' column was converted to a datetime data type.
2. Year Filtering: Data was filtered to include only years from 2002 onwards.
3. Column Removal: The 'DATE' column was dropped from the dataset.

## Merging Datasets

The two datasets were merged on the 'year' column using a left join to create a consolidated dataset that includes both food price and inflation data.

## Correlation Analysis

A correlation analysis was performed on the merged dataset to understand the relationships between different variables.

## Save Preprocessed Data

The final preprocessed dataset, which is too large to be uploaded directly to this repository, is available for download at the following link:

- [Preprocessed Data (CSV)](https://github.com/armaf002/Food-price/raw/main/preprocessed_data%20(1).csv)


**This preprocessed data is available for further work in various tasks ahead.**






# Task1 Active Collaborators
1. **Raj Kumar (Team Lead)**
2. Ridwan Abdurahman
3. Utkarsh Bhalwankar
4. Anupama Mathpal
5. Abhishek Dutta
6. Prashant Singh
7. Milan Waghmare
8. Mvpandiyan M
9. Manasvi Agarwal
