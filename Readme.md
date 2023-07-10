# DataPrep using Python

Data Preprocessing involves transforming and manipulating raw data to improve its quality, consistency, and relevance for analysis. It encompasses several tasks, including handling missing values, standardizing variables, and removing outliers. By performing these preprocessing steps, data professionals ensure that subsequent analysis is based on reliable and accurate data, leading to better insights and predictions.

The pipeline consists of interconnected steps, each of which is responsible for a specific preprocessing task, such as:

1. Imputing missing values
2. Scaling numeric features
3. Finding and removing outliers
or encoding categorical variables

## Why should we normalize data in machine learning ?

The goal of normalization is to change the values of numeric columns in the dataset to use a common scale, without distorting differences in the ranges of values or losing information. Normalization is also required for some algorithms to model the data correctly.  However, using these techniques may enable the model to give better results, better accuracy and better predictions.

#### We can apply two kinds of scaling to numerical features 

* Normalizing — transforming numeric data to the same scale as other numeric data.
* Bucketing — transforming numeric (usually continuous) data to categorical data.

## Data Standardization

Standardizing a dataset involves rescaling the distribution of values so that the mean of observed values is 0 and the standard deviation is 1.

This can be thought of as subtracting the mean value or centering the data.

Like normalization, standardization can be useful, and even required in some machine learning algorithms when your data has input values with differing scales.

Standardization assumes that your observations fit a Gaussian distribution (bell curve) with a well-behaved mean and standard deviation. You can still standardize your data if this expectation is not met, but you may not get reliable results.

**Standardization requires that you know or are able to accurately estimate the mean and standard deviation of observable values. You may be able to estimate these values from your training data, not the entire dataset.**

Subtracting the mean from the data is called centering, whereas dividing by the standard deviation is called **scaling**. As such, the method is sometime called **“center scaling“**.

#### A value is standardized as follows:

* y = (x – mean) / standard_deviation

Where the mean is calculated as:

* mean = sum(x) / count(x)

And the standard_deviation is calculated as:

* standard_deviation = sqrt( sum( (x – mean)^2 ) / count(x))

We can guesstimate a mean of 10.0 and a standard deviation of about 5.0. Using these values, we can standardize the first value of 20.7 as follows:

y = (x – mean) / standard_deviation
y = (20.7 – 10) / 5
y = (10.7) / 5
y = 2.14
The mean and standard deviation estimates of a dataset can be more robust to new data than the minimum and maximum.

You can standardize your dataset using the scikit-learn object [StandardScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html).

[More..](https://machinelearningmastery.com/standardscaler-and-minmaxscaler-transforms-in-python/)

## This pipeline is designed to handle various preprocessing tasks on any given dataset.

1. The pipeline begins by identifying the numeric and categorical features in the dataset.

2. Next, the pipeline addresses any missing values present in the numeric features. It fills these missing values with the mean value of each respective numeric feature (you can modify this step according to your desired way of filling in missing values of a numerical feature). It ensures that missing data does not hinder subsequent analysis and computations.

3. The pipeline proceeds to handle missing values in the categorical features. It fills these missing values with the mode value, representing the most frequently occurring category.

4. The pipeline then identifies and handles outliers within the numeric features using the Interquartile Range (IQR) method. Calculating the quartiles and the IQR determines upper and lower boundaries for outliers. Any values outside these boundaries are replaced with the mean value of the respective numeric feature. This step helps prevent the influence of extreme values on subsequent analyses and model building.

5. After handling missing values and outliers, the pipeline normalizes the numeric features. This process ensures that all numeric features contribute equally to subsequent analysis, avoiding biases caused by varying magnitudes.