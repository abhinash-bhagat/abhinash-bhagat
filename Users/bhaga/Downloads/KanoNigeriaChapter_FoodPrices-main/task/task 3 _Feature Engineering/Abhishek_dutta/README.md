## The feature engineering data link is [here](https://drive.google.com/file/d/16iM85vxpGsQHrkLrq_ZVu9X5V5zu9Rao/view?usp=sharing)
## Feature engineering steps performed:

1. Dropping unnecessary columns:

- latitude and longitude - Information about location already captured in state column
- category - More focused on predicting commodity prices instead of the category of the commodity. Category is just a grouping of commodities
- pricetype & priceflag - Irrelevant for predicting food prices
- currency - We know the currency anyway (NGN)
- usdprice - Can simply multiple price in NGN with the USD conversion rate, so irrelevant

2. Drop 'Market_Name' column - We see that there is almost a 1 to 1 mapping between Local_Government and Market_Name. So, Market_Name can be dropped since it won't provide much value to the ML model. This will also help reduce dimensionality of our final dataset.

3. Analysing 'unit' column - My reasoning behind it is that unit serves as a sort of indicator and almost all commodities have a unique unit. We should use the unit later on after modelling which means that whenever a prediction occurs, it can be said that the prediction represents the corresponding unit of the commodity
- Oil (palm) - we will convert the L records into kg by using density of palm oil as 0.89 g/ml
- Yam & Yam (Abuja) - Can remove records which contain 100 Tubers

4. Account for inflation to create updated price column and then dropping inflation, price and year columns

5. Perform one-hot encoding on remaining categorical columns

