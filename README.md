# Wine-Quality-Prediction---Kaggle-challenge

In this work we analyse two datasets on wine quality available from the UCI machine learning repository (http://archive.ics.uci.edu/ml/datasets/Wine+Quality).


### Dependencies
The code is in python. Other than this, please install the following libraries using pip.
* Pandas: pip install pandas
* matplotlib: pip install matplotlib
* numpy: pip install numpy
* scikit-learn: pip install scikit-learn



![correlation matrix](index.png)




Assumption
We will be assuming that wines having value higher than 6 will be considered good and other wines are not good.

![Count of Quality Parameter](count.png)

### Preprocessing Data for performing Machine learning algorithms

```python
#1 - Bad
#2 - Average
#3 - Excellent
#This will be split in the following way. 
#1,2,3 --> Bad
#4,5,6,7 --> Average
#8,9,10 --> Excellent
#Create an empty list called Reviews
reviews = []
for i in wine['quality']:
    if i >= 1 and i <= 3:
        reviews.append('1')
    elif i >= 4 and i <= 7:
        reviews.append('2')
    elif i >= 8 and i <= 10:
        reviews.append('3')
wine['Reviews'] = reviews

wine['Reviews'].value_counts()
```
    2    4698
    3     180
    1      20
    Name: Reviews, dtype: int64
    
    
**1. Logistic Regression**

```python
#converting the numpy array to list
x=np.array(y_pred).tolist()

#printing first 5 predictions
print("\nThe prediction:")
for i in range(0,5):
    print(x[i])
    
#printing first five expectations
print("\nThe expectation:")
print (y_test.head())
```    
    The prediction:
    
    6
    6
    5
    6
    6
    
    The expectation:
    
    3782    2
    2359    2
    1976    2
    3099    2
    4428    2
    Name: Reviews, dtype: object

The following features can be excluded as they have small correlation with wine type:
- citric acid
- pH



** *
## Conclusion

Afer the all steps performing on our problem statement, we conclude that
* **Type** of wine is not important to predict target.
* **All the feature** vectors of dataset important to predict quality of data.
* Alcohal, fixed acidity, sulfur dioxide, density are major predictors as observed during data analysis.
* For Red-wine, **Desicion Tree** technique gives 61% accuracy .
* For White-wine, **Desion Tree** technique gives 62% accuracy . 
** ** 
* To get more accurate model performed binning of target variable as 
    * 1,2,3 --> Bad 
    * 4,5,6,7 --> Average 
    * 8,9,10 --> Excellent
* After above preprocessing step,
    * Logistic Regression --> Accuracy: 96.46
    * Decision Tree --> Accuracy: 94.14
    * Random Forest --> 97
    * SVM --> 95.85
    
* **Random Forest** Algorithm give best case accuracy.

** *   
