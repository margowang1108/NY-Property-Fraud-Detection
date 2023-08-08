# NY_property-Fraud-Detection

## Unsupervised anomaly detection (fraud) algorithm

This notebook has good example algorithms to do a forensic-type analysis, looking for anomalies in a dataset. I first do some data cleaning (exclusions, imputation), then build variables that are designed to look for the kinds of anomalies I am interested in, in this case, unusual property valuations.

After I build the variables I know I have lots of correlations and too high dimensionality so I need to remove correlations and reduce dimensionality. Since I don't have a dependent variable the easiest useful thing to do is PCA. I z scale, do PCA, keep the top PCs, then z scale again in order to make each retained PC equally important (optional step).

I use two different anomaly detection (fraud) algorithms. The first just looks for outliers in the final scaled PC space using a Minkowski distance from the origin. The second method makes a simple autoencoder and the fraud score is then the reproduction error. It's important to note that each/either of these two methods would be a fine fraud score by itself.

Since I have two scores and I don't really know which one is better I just average the two scores. To do this I replace the score with its rank order and then average the rank-ordered scores for our final score.

Finally, I sort all the records by this final score and explore the top n records. To help the investigation I show which of the variables are driving these top-scoring records with a heat map of the variable scores, which can point the investigators to what's making the high score for these top-scoring records.

This problem is an invented problem to demonstrate the process of building unsupervised fraud models. The data set is real and the invented problem is realistic. What's lacking the most is the ability to interact with domain experts in order to do proper exclusions and design good/appropriate variables.

The data can be found here: https://data.cityofnewyork.us/Housing-Development/Property-Valuation-and-Assessment-Data/rgy2-tti8
