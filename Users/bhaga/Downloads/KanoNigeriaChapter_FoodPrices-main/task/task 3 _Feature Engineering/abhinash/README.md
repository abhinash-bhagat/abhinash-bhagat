## The link to download the feature engineering dataset is [here](https://drive.google.com/file/d/133VI2Pp-R0LY1tKvUMn34M8YJdLLyVZN/view?usp=sharing)

Certainly, here's the feature engineering report without any additional content:

## Feature Engineering Report

### Author: Abhinash Bhagat

#### Summary:

In the process of feature engineering, several steps were undertaken to transform the raw dataset into a format suitable for machine learning models. The approach involved dropping unnecessary columns, converting categorical data into numerical features, and leveraging cyclic encoding for date-related features.

#### Steps Taken:

1. **Dropping Columns:**
   - **Geographical Columns:** Removed columns related to geography to focus on non-location-specific patterns.
     - State
     - Market Name
     - Local Government
   - **Unitary Columns:** Eliminated columns related to pricing units due to the varied nature of data.
     - USD Price
     - Currency
     - Priceflag
     - Unit (data represented different physical quantities)

2. **Conversion of Categorical Data:**
   - **Mapping Technique:** Converted categorical data into numerical features using a mapping approach instead of traditional encoding techniques. This ensured that the categorical data was represented in a numeric format suitable for machine learning algorithms.
     - Season
     - Commodity
     - Category
     - Month
     - Price Type

3. **Cyclic Encoding for Date Column:**
   - Utilized cyclic encoding to incorporate the date column as a feature, capturing potential seasonality in the dataset.
   - Implemented a general formula leveraging the month to represent its cyclical nature, aiding in capturing patterns related to specific months or seasons in the data.

