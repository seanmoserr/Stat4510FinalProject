```
Sean Moser
```
```
Stat 4510
```
```
Applied Statistical Models 1
```
```
Final Project
```
# Introduction

This dataset originates from the University of California – Irvine’s Machine Learning
Repository. Thirteen different attributes compose this dataset of 178 instances. The dataset
consists of integer values produced through chemical analyses applied to each new instance of a
wine. Each wine has a classification of one, two, or three, with respect to the wine’s cultivar.
This type of classification problem can be especially relevant as we can use differing types of
analyses to determine origins of physical objects. These types of analyses could be especially
important for those in the sector who might be interested in determining a product’s origin,
validity, quality, etc. For the purposes of this project, we are answering the question: how can we
analyze the physiochemical properties of a random wine to predict the origin of a wine? The
dataset originated as a comma-separated value (.csv) file and needed minor reformatting in order
to properly prepare the data for analysis in R Studio. As the attribute associated with the wine’s
classification is a simple integer classification of one, two, or three, this attribute was changed to
a factor variable in R Studio.

# Methods

This dataset is best analyzed through several different classification methods, including
trees, linear discriminant analysis (LDA), support vector machines (SVM), random forests, and
K-nearest neighbor classification. We will examine each model’s misclassification rate and
explore what each specific model contributes to our overall understanding of our problem as well
as our dataset. The use of trees can help us specifically determine which characteristics are
important for determining if a wine originated from cultivator one, two, or three. Other models
will be helpful in determining the nature of the dataset and the differences that exist between the
different cultivator’s wines.

The data will be split using the `sample()` command in R and will reserve 80% of the
data for training models, with the remaining 20% reserved for testing models. We will also be
applying the Random Forest method to this dataset, to determine which of the twelve predictors
are especially useful in determining the classification of the wine.


# Results

The `pairs()` command was especially useful for orientating oneself to the problem and
demonstrating which factors seem highly correlated to a wine’s classification.

Using this command, we can see not only which variables are correlated with each other,
but how each variable affected each respective wine’s classification. We can see significant
nonflavonoid phenols as well as flavonoids are both correlated with each other and are useful in
predicting classification. We also can see hue is helpful in predicting classification.


# Results

Using a decision tree, we can successfully classify any given wine following the tree
down a terminal node. Below is the resultant tree produced.

After viewing the resultant tree, we see the important variables and their thresholds for
splitting to follow the tree down to a terminal node.


# Results

Above is the code for the linear discriminant analysis model, which tested to have the one
of the lowest misclassification rate for the models constructed, at 2.778% incorrect.


# Results

Another promising model was the support vector machines model. This model samples
using 10-fold cross validation and calculates the error for each specified cost. As shown below,
error was minimized at a cost of five at just 0.0277. This model works by constructing a
hyperplane that best separates the classes. The varying cost that is added when tuning the model
tells our machine how much significance, or penalty, should be applied when the model does
misclassify, which affects the bias-variance tradeoff.

Other models that were utilized, but performed more poorly include KNN models, which
tested at misclassification rates of ranging from 11-13%. Quadratic discriminant analysis
similarly tested poorly with a misclassification rate of 11%.


# Results

Finally, the use of a `RandomForest()` command will be beneficial in determining which
variables are important in correctly classifying a wine.

This model performs extremely well as the estimated error rate is calculated to be 2.11%.
The model struggles with classifying class two wines, yet makes no mistakes classifying class
one and three wines. A value of three for mtry was found to have the lowest OOB estimate of
error rate of the values tested.

A call to the `importance()` function displays which factors are significant for predicting
the outcome of the model. Variables with large “MeanDecreaseAccuracy” values are known to
be significant to the model in accurately predicting the classification. We find that malic acid
content, nonflavonoid phenols, and hue, are among some of the most significant factors in
predicting the classification accurately.

Random forests are especially beneficial when used accurately by solving the problem of
overfitting in a normal decision tree by comparing each decision trees amongst itself.


# Discussion

Our results show that given the analysis of a given wine’s physiochemical properties, we
can, with just under 98% accuracy, predict the origin of cultivation for the wine. As our linear
discriminant analysis model far outperformed our quadratic discriminant analysis model, we see
that this specific data benefits from a stricter, less-flexible model. This model benefits from
inflexible linear boundaries to designate classes, rather than the flexibility permitted in quadratic
discriminant analysis.

Not only do the models accurately predict the origin of a wine given these properties, we
now understand specifically which variables are important to classification. As shown above, we
were able to identify malic acid content, nonflavonoid phenols, and hue as three of the most
significant factors in accurate classification. Furthermore, we see wines with a lower
nonflavonoid phenol count are likely to be classified as class three wines. Wines with a higher
nonflavonoid phenol count but low malic acid count were classified as class two wines. Wines
with a higher nonflavonoid phenol count, a high phenolic presence were found to be classified as
class one wines. Using this dataset, the models had slight trouble correctly predicting class two
wines. As shown in the random forest method, all of the 2.11% error present was produced from
misclassifications regarding class two wines. The model correctly classified all class one and
class three wines. We gather class one wines are more acidic than class three wines.

This type of model is fundamental to our understanding of the world around us. Because
of the capabilities of our models and analyses, we are able to construct a deeper understanding of
whatever given subject we are working with. A physical object can be quantified and measured
through human processes, with a resulting correct classification from our processes. This is a
powerful ability that can be applied in many different sectors from business to engineering to
medicine. Not only is it powerful to be able to classify and predict, but these models equip us
with knowledge of specific factors and variables that contribute to a certain outcome. In our
example, we find class one wines to be exceptionally acidic. This could suggest information
about the cultivator’s land, crops, fermentation, etc. We also learn which variables are
unimportant in predicting a cultivator. This is beneficial when we may expect a relationship to
exist with a certain variable, but we may find no such relationship to exist. Data is an extremely
powerful tool; through these processes, we gain the ability to discern information, patterns, and
relationships simply beyond our scope of knowledge.


# Conclusion

How can we best analyze the physiochemical properties of wine to determine its origin of
cultivation? The best way found to analyze these physiochemical properties of wine for our
purposes of classification was to use a combination of methods to extrapolate the significant
variables in the model and build models that accurately predict a wine’s origin. In this specific
case, linear discriminant analysis and random forests were invaluable in determining the
underlying relationships between the variables and constructing a model with powerfully
accurate predictive power.

Future studies stemming from this project include the analysis of several physical objects
that can be measured and analyzed through different processes. This type of analysis
demonstrates our ability to measure and quantify real world objects and process them in order to
understand their underlying relationships on a deeper, complex level. As technology advances
and subsequently increases and complexity of our lives, models that can analyze and classify for
origin and quality can be useful to any number of sectors including food, media, medicine,
agriculture, transportation, etc. The possibilities with machine learning and statistical models in
this new age of data and technology are limitless.