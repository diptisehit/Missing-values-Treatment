**For coding see the Missing_values&encoding.ipynb file**

# What is a Missing Value?
Missing values are data points that are absent for a specific variable in a dataset. They can be represented in various ways, such as blank cells, null values, or special symbols like “NA” or “unknown.” These missing data points pose a significant challenge in data analysis and can lead to inaccurate or biased results.

# Types of Missing Values :

There are three main types of missing values:

1. Missing Completely at Random (MCAR): MCAR is a specific type of missing data in which the probability of a data point being missing is entirely random and independent of any other variable in the dataset. In simpler terms, whether a value is missing or not has nothing to do with the values of other variables or the characteristics of the data point itself. 
2. Missing at Random (MAR): MAR is a type of missing data where the probability of a data point missing depends on the values of other variables in the dataset, but not on the missing variable itself. This means that the missingness mechanism is not entirely random, but it can be predicted based on the available information. We can use bivariate imputations for this
3. Missing Not at Random (MNAR): MNAR is the most challenging type of missing data to deal with. It occurs when the probability of a data point being missing is related to the missing value itself. This means that the reason for the missing data is informative and directly associated with the variable that is missing. We can use univariate imputations for this.

# Methods for Identifying Missing Data :

1. .isnull()
2. .info()
3. .isna()

# Ways to solve the missing value problem :

1. Remove the samples or variable which are containing missing values(if the missing data is => 25% generally or as per shareholders' instructions). In Machine Learning, Complete Case Analysis (CCA) is a technique in which all the samples containing missing values are dropped or removed from the dataset.
2. Impute the missing values with any strategy(if the missing data is < 25%).

# Types of Imputation of the missing data :

1.  Univariate imputations: Here, the missing values are imputed using only the particular column of the respective missing values.For Example, if there is a missing value present in the Age column, then the missing value will only be imputed using the values of the Age column, Any of the other columns of the dataset will not be used for the imputation. Mean, median, and Most_Frequent are examples of univariate missing data imputation.
2.  Bivariate imputations : In this, the missing value is imputed using the values of the multiple columns in the dataset. For Example, if a missing value is present in the Age column, then this missing value will be imputed using the Age column and some other columns of the dataset. KNN Imputer and Iterative Imputer are examples of multivariate imputation.

# Univariate imputations: 

In this case first check the variable type. In case of -
1. Numerical variable :
   
    a) variable having outliers : Use median to impute the missing values.
   
    b) variable having no outliers : Use mean to impute the missing values.
   
3. Categorical variable: Use mode (most frequent) to fill the missing values.

# Bivariate imputations :

1. KNN Imputer: Here the euclidian distance between the data points is calculated and depending upon the euclidian distance between points, the neighbors are considered for imputing the missing data. Once we have the neighbors of the missing data based on the euclidian distance, then we calculate the mean of the neighbor’s datapoint values and impute the missing value by the mean. This technique involves the calculation of the euclidian distance in it. So it requires a higher amount of computation power as compared to the normal univariate imputation.
2. Iterative Imputer : Here in the first step all the missing data are imputed by the mean of the respective columns, and then by moving left to the right, only one sample imputed with mean is again considered as missing values and a part from the dataset is considered as training, and testing set with dependent and independent features. In the last step, a machine learning algorithm is used to train on the dummy dataset, and the missing value is imputed by the algorithm’s results. It involves the machine learning algorithm calculation in it. So Iterative Imputer is the imputation technique that requires the most time and computation power compared to the other imputation techniques. Also, it is slow but gives accurate results. One assumption for Iterative Imputer is that this technique is best suitable for the data missing at random.
