# Cryptocurrencies
## Overview

In this repository, an analysis was completed to identify what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for an investment bank to offer a new cryptocurrency investment portfolio. Using Jupyter Notebook, Python, and unsupervised learning with Principal component analysis (PCA), crypto_data.csv (https://min-api.cryptocompare.com/data/all/coinlist) was analyzed and a visualization was created to present before a board. 

## Results 

The first step involved was to preprocess the data. The data was cleaned by dropping null values and cryptocurrencies that were not currently be traded were removed from the dataset. Then, the data was standardized using the StandardScaler() method to ensure that the data was internally consistent. The data was reduced to 3 principal components and converted to a dataframe. An elbow curve was created to identify the best K-Means value for clustering:

`inertia = []
k = list(range(1,11))
for i in k:
    km = KMeans(n_clusters=i, random_state=0)
    km.fit(pcs_df)
    inertia.append(km.inertia_)
elbow_data = {"k": k, "inertia": inertia}
elbow_df = pd.DataFrame(elbow_data)
elbow_df.hvplot.line(x="k", y="inertia", title="Elbow Curve", xticks=k)`

Using a K-Means value of 4, the clustered dataframe was created. Finally, an hvplot.scatter plot was created with points that display the coin's name. 
![image](https://user-images.githubusercontent.com/95376544/165017629-9cafd109-5619-4449-aca7-82d3d14f5c9d.png)
