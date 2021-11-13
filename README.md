## Overview 
The purpose of this project is to use a clustering algorithm to group cryptocurrency data to better understand the trends and what cryptocurrencies might be worth investing in. First, using Pandas, the data was preprocessed in order to perform PCA. 

### Preprocessing 
- All cryptocurrencies that are not being traded are removed
- The `IsTrading` column was dropped 
- All the rows that have at least one null value were removed
- All the rows that do not have coins being mined were removed
- The `CoinName` column is dropped

After preprocessing, the `get_dummies()` method is used to create variables for the text features, and the features from the X DataFrame were standardized using the StandardScaler `fit_transform()` function.

### Reducing Data Dimensions Using PCA
The PCA algorithm was used to reduce the dimensions of the X DataFrame to three principal components and these dimensions were placed in a new DataFrame, `pcs_df`.

### Clustering Cryptocurrencies Using K-means
Using the `pcs_df` DataFrame, an elbow curve using hvPlot was created to find the best value for K, which turned out to be 4. Then the `pcs_df` DataFrame was used to run the K-means algorithm to make predictions of the K clusters for the cryptocurrencies’ data.
