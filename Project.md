# Project Source Code
## Written in the R language, converted to markdown

```
##PROJECT
library(readr)
wine.data <- read_csv("~/Documents/Stat 4510/Project/wine.data.csv")
View(wine.data)
wine.data$Alcohol <- as.factor(wine.data$Alcohol)
str(wine.data)
```
```
##Basic knn classification
set.seed(444)
library(class)
train <- sample(1:nrow(wine.data), 0.8*nrow(wine.data), replace=F)
wine.train <- wine.data[train, ]
wine.test <- wine.data[-train, ]

wine.knn2 <- knn(train = wine.train[, -1, drop = FALSE],
                test = wine.test[, -1, drop = FALSE],
                cl = wine.train$Alcohol,
                k=2)
wine.knn3 <- knn(train = wine.train[, -1, drop = FALSE],
                test = wine.test[, -1, drop = FALSE],
                cl = wine.train$Alcohol,
                k=3)
wine.knn4 <- knn(train = wine.train[, -1, drop = FALSE],
                test = wine.test[, -1, drop = FALSE],
                cl = wine.train$Alcohol,
                k=4)

table(wine.test$Alcohol == wine.knn2)
table(wine.test$Alcohol == wine.knn3)
table(wine.test$Alcohol == wine.knn4)

mean(wine.test$Alcohol != wine.knn2)
mean(wine.test$Alcohol != wine.knn3)
mean(wine.test$Alcohol != wine.knn4)
```



```
##Tree method
library(tree)
wine.tree = tree(wine.train$Alcohol ~ wine.train$`Malic acid` + wine.train$Ash + wine.train$`Alcalinity of ash`
                + wine.train$Magnesium + wine.train$`Total phenols` + wine.train$Flavanoids + wine.train$`Nonflavanoid phenols`
                + wine.train$Proanthocyanins + wine.train$`Color intensity` + wine.train$Hue + wine.train$`OD280/OD315 of diluted wines`
                + wine.train$Proline)
summary(wine.tree)
plot(wine.tree)
text(wine.tree, pretty=0)

##SVM
pairs(wine.data, col=wine.data$Alcohol)
library(e1071)
svm.model <- svm(Alcohol ~., data=wine.test,
                 kernel="linear", cost=1, scale=T)
svm.pred <- predict(svm.model, data=wine.test)
table(svm.pred, wine.test$Alcohol)


tuned.svm = tune("svm", Alcohol~., data=wine.train,
                 kernel="linear", ranges=list(cost=c(0.01, 0.5, 1, 5, 10)))
summary(tuned.svm)
```
```
##LDA
library(MASS)
lda.fit <- lda(Alcohol ~ ., data = wine.train)
lda.pred <- predict(lda.fit, wine.test)
mean(wine.test$Alcohol != lda.pred$class)
```
```
##QDA
qda.fit <- qda(Alcohol ~ ., data = wine.train)
qda.pred <- predict(qda.fit, wine.test)
mean(wine.test$Alcohol != qda.pred$class)
```
```
##RandomForest
library(randomForest)
wine.rf3 = randomForest(wine.train$Alcohol ~ wine.train$`Malic acid` + wine.train$Ash + wine.train$`Alcalinity of ash`
                         + wine.train$Magnesium + wine.train$`Total phenols` + wine.train$Flavanoids + wine.train$`Nonflavanoid phenols`
                         + wine.train$Proanthocyanins + wine.train$`Color intensity` + wine.train$Hue + wine.train$`OD280/OD315 of diluted wines`
                         + wine.train$Proline, mtry=3, importance = TRUE)
wine.rf3

importance(wine.rf3)
```

### Back to home
* [Home](/README.md)

