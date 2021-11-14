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
Using the `pcs_df` DataFrame, an elbow curve using hvPlot was created to find the best value for K, which turned out to be 4 as seen in the following plot.

<img width="716" alt="Screen Shot 2021-11-13 at 6 03 03 PM" src="https://user-images.githubusercontent.com/85901073/141661520-dc433419-db6c-42fa-b564-9669307a9593.png">

Then the `pcs_df` DataFrame was used to run the K-means algorithm to make predictions of the K clusters for the cryptocurrencies’ data, producing the following dataframe `clustered_df`: 

<img width="777" alt="Screen Shot 2021-11-13 at 7 03 51 PM" src="https://user-images.githubusercontent.com/85901073/141662563-9dc2847d-53b3-48f0-b007-b3aa994e5930.png">

### Visualizing Cryptocurrencies Results
Using Plotly Express and `hvplot`, the distinct groups that correspond to the three principal components in `pcs_df` were visualized, then a table with all the currently tradable cryptocurrencies was created using the `hvplot.table()` function. Below is the 3D scatter of the PCA data and the clusters:

<img width="719" alt="Screen Shot 2021-11-13 at 7 09 08 PM" src="https://user-images.githubusercontent.com/85901073/141662643-51a8e2e8-80e2-4140-8968-6edaf3e0219a.png">


