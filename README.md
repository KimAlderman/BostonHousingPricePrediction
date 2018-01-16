# BostonHousingPricePrediction

Udacity Machine Learning Nanodegree project: predicting Boston housing prices

This was my second project in my Machine Learning Nanodegree at Udacity. Tools and techniques used in this project include:

* data exploration through summary statistics and data visualization
* defining a performance metric (coefficient of determination for this project)
* splitting data into train & test sets, shuffling, and cross-validation
* sklearn and matplotlib libraries for Python
* learning curves & complexity curves to analyze model performance
* bias/variance tradeoff 
* sklearn implementation of a decision-tree model
* use of gridsearch for hyperparameter tuning and optimization
* sensitivity analysis
* real-life applicability

Two changes I would make now that I have more experience with machine learning algorithms:

1. I would use randomizedsearch instead of gridsearch for hyperparameter tuning. It has proven more robust at finding optimal values and is usually faster on very large data sets.
2. In evaluating the reasonableness of predictions for the three properties, in addition to using statistics (mean, median, standard deviations), I would utilized sklearns nearest neighbor function. Example code:

```python
from sklearn.neighbors import NearestNeighbors
num_neighbors=5
def nearest_neighbor_price(x):
    def find_nearest_neighbor_indexes(x, X):  # x is your vector and X is the data set.
        neigh = NearestNeighbors( num_neighbors )
        neigh.fit(X)
        distance, indexes = neigh.kneighbors( x )
        return indexes
    indexes = find_nearest_neighbor_indexes(x, features)
    sum_prices = []
    for i in indexes:
        sum_prices.append(prices[i])
    neighbor_avg = np.mean(sum_prices)
    return neighbor_avg
print nearest_neighbor_price( [4, 55, 22])
index = 0  
for i in client_data:
    val=nearest_neighbor_price(i)
    index += 1
    print "The predicted {} nearest neighbors price for home {} is: ${:,.2f}".format(num_neighbors,index, val)
```
