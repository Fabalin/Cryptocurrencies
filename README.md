# Cryptocurrencies
Unsupervised Machine Learning: Using PCA and K-means analysis to cluster Cryptocurrencies.

## Overview 
Cryptocurrency data from [Cryptocompare](https://min-api.cryptocompare.com/data/all/coinlist) API call has been analyzed using unspervised machine learning to cluster cryptocurrencies based on the features provided: Algorithm, Proof Type, Total Coin Supply, and Total Coins Mined. These data features were processed using PCA to reduce dimensions to 3 Principle Components, which were subsequently used to perform a K-means analysis with k=4 clusters, based on the eblow curve. 

The PCA cluster classifications have been saved as [cryptopcaclassification.csv](https://github.com/Fabalin/Cryptocurrencies/blob/main/cryptopcaclassification.csv) and visualized using 3D scatter cluster. An additional visualization was performed using the Total Coin Supply and Total Coins Mined features, along with the assigned classifications to determine the key features that contribute to clustering. *The analysis discounts cryptocurrencies that are currently not being traded.* 

## Software
- Python 3.7.13
- Jupyter Notebook v6.4.11
- ScreenToGif 2.37

### Dependencies 
- pandas 1.4.2
- numpy 1.21.5
- scipy 1.7.3
- plotply 5.8.2
- sklearn 1.0.2
- matplotlib 3.5.2

## Analysis and Results 
This analysis captures ***532 cryptocurrencies***. Since the data included categorical data in addition to multiple features, PCA was employed to consolidate and reduce the dimensions of features down to 3. These 3 principal components were used to construct the Elbow Curve to find the optimal amount of clusters. The ***k=4*** clusters were determined based on the change of slope that signals a dramatic shift in the amount of variation captured: 

![Elbow Curve](https://github.com/Fabalin/Cryptocurrencies/blob/main/Resources/cryptoElbow_curve.png)

The K-means algorithm was used to determine the classifications of each cryptocurrency, using the 3 principle components across 4 clusters. The result was visualzied using plotly's 3D scatter plot to reveal 4 groups: 

![3D Scatter](https://github.com/Fabalin/Cryptocurrencies/blob/main/Resources/3D_CryptoScattercluster.gif)

Classes 0 (purple circles) and 1 (pink diamonds) captured most of the cryptocurrencies and are localized along the cartesian plane of PC 1 and PC 2. 6 cryptocurrencies belong to Class 3 (yellow squares) and are mostly localized along the cartesian plane of PC 1 and PC 3. There is one Class 3 cryptocurrency (Vechain) that appears more to the middle of the 3D plane. Class 2 (Orange x) is a lone-wolf that exists also on the cartesian plane of PC 1 and PC 2 but opposite to the class 0 and 1 clusters across the PC 1 axis. Most of the variation of the cryptocurrencies is captured along the PC 2 axis with PC 3 being attributed to 6 currencies and PC 1 being attributed largely to BitTorrent. Inutition infers that two features appear to be large contributers to most of the viariation observed. *This is because most variations are captured across two planes: (PC 1 x PC 2) and (PC 2 x PC 3).* It is important to note that classes 0 and 1 have similar algorithms with class 1 displaying more variations. BitTorrent in Class 2 has its own unique Algorithm. Algorithms in class 3 appear to be distinct from all the other classes. This implies that although Algorithm similarity contribute to the variation observed, other features could have a greater impact that helps refine the classification.    

To investigate which of the two original features are responsible for most of the variation, an hv scatterplot was created using Total Coins Mined and Total Coin Supply. This was done since these two parameters include large numerical data points, which were then standardized between 0 and 1. 4 visible clusters can be seen in the graph produced: 

![hvPlot](https://github.com/Fabalin/Cryptocurrencies/blob/main/Resources/cryptohvplot.gif)

These 4 clusters do not adhere to the previous classifications assigned and visualized, using the k-means analysis in the 3D plot. This is true for classes 0, 1, and 3 with class 2 (BitTorrent) remaining as an outlier that is consistent with the 3D scatterplot. Class 1 had some coins, most noteably TurtleCoin, that exists as an distinguishable group from the rest. Since BitTorrent's classification is accurately captured but the rest of the clusters are indistinguishable, Total Coin Supply and Total Coins Mined features alone can categorize BitTorrent as separate but will fail to categorize the rest of the cryptocurrencies. 

## Summary 
The analysis produced 4 classifications from 532 currently trading cryptocurrencies. **Overall, the data displayed implies that Algorithm and Proof Types are key features that help differentiate and categorize cryptocurrencies.** Although the analysis of coin supply and coins mined is necessary, the magnitude of its contribution to the classifications is minimal. This conclusion could be different if currencies currently-not-being-traded are included in the analysis. Future analyses can focus on the features that contribute to the success or failure of the cryptocurrencies.  
