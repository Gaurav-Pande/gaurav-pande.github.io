---
layout: page
title:  "Gender Classifier"
date:   2016-01-01 08:43:59
permalink: /classifier/
categories: limbo
desc: "spark based ml application for gender classifier"
---

**Technologies**: Python,Openshift,MachineLearning

**Repo Link**: [link](https://github.com/Gaurav-Pande/openshift-python.git)

---


This project aims to learn the machine learning  basics and also use redhat opendhift to deploy the same application. 
The code uses the scikit-learn machine learning library to train a decision tree on a small dataset of body human names with (height, width, and shoe size) labeled male or female. Then we can predict the gender of someone given a name, and it will showcase a random picture of based on the name you type. I build this code on the top of the flask web based application, where one can simply type the name and click submit button.

We Calculated the performance matrix using LinearDiscriminantAnalysis, KNeighborsClassifier, DecisionTreeClassifier, and GaussianNB 

Insatallation steps are written in the [README](https://github.com/Gaurav-Pande/openshift-python/blob/master/README.md) file in the repo.

The code implementation for the gender classifier is as:

```

  # Gaurav pande
  # A classifier that predicts whether a name is male or female
  # Uses a DecisionTree Classifier
  # Data from a list of 258000 names, 50/50 ratio between male and female
  # Features are the digits that correspond with the letters in the name
  # Labels are the gender
  import csv
  from sklearn import tree
  from sklearn.model_selection import train_test_split
  from sklearn.metrics import accuracy_score
  from sklearn import model_selection
  from sklearn.metrics import classification_report
  from sklearn.metrics import confusion_matrix
  from sklearn.metrics import accuracy_score
  from sklearn.linear_model import LogisticRegression
  from sklearn.tree import DecisionTreeClassifier
  from sklearn.neighbors import KNeighborsClassifier
  from sklearn.discriminant_analysis import LinearDiscriminantAnalysis
  from sklearn.naive_bayes import GaussianNB
  from sklearn.svm import SVC
  source = 'names.csv'
  flag = 0

  class GenderClassifier:

      # turns a word into a list of digits
      @classmethod
      def wordToDigits(self,word):
              wordD = [-1]*10 # give default values to the digits
              for i in range(min(len(list(word)),10)): # cut off the word if it's more than 10 characters
                  char = list(word)[i]
                  number = ord(char.lower()) - 97
                  wordD[i] = (number)
              return(wordD)

      @classmethod
      def performanceMatrix(self,X_train,Y_train):
              models = []
              #models.append(('LR', LogisticRegression()))
              models.append(('LDA', LinearDiscriminantAnalysis()))
              models.append(('KNN', KNeighborsClassifier()))
              models.append(('CART', DecisionTreeClassifier()))
              models.append(('NB', GaussianNB()))
              seed = 2
              scoring = 'accuracy'
              results = []
              names = []
              for name, model in models:
                  kfold = model_selection.KFold(n_splits=2, random_state=seed)
                  cv_results = model_selection.cross_val_score(model,X_train,Y_train , cv=kfold, scoring=scoring)
                  results.append(cv_results)
                  names.append(name)
                  msg = "%s: %f (%f)" % (name, cv_results.mean(), cv_results.std())
                  print(msg)

      @classmethod
      def accuracy(self,clf,X_test,Y_test):
              predictions = clf.predict(X_test)
              print("Accuracy: %.2f" % accuracy_score(Y_test, predictions))

      @classmethod
      def predict(self,name):
              namesToTest = name.split()
              # import training data
              with open(source) as csvfile:
                  readCSV = csv.reader(csvfile, delimiter=',')
                  names = []
                  sexes = []
                  for row in readCSV:
                      name = row[1]
                      sex = int(row[3] == 'boy')  # 0 girl, 1 images
                      names.append(name)
                      sexes.append(sex)
              # gather and format features and labels
              X = []
              for name in names:
                  # turn names into digits
                  nameD = GenderClassifier.wordToDigits(name)
                  X.append(nameD)
                  Y = sexes
              print("training data set")    # split training / testing data
              X_train, X_test, Y_train, Y_test = train_test_split(X, Y, test_size=.0002)
              # classifier
              #print(X_train)
              clf = tree.DecisionTreeClassifier()  # decide classifier

              # from sklearn.neighbors import KNeighborsClassifier
              # clf = KNeighborsClassifier()

              # fit to classifier
              clf = clf.fit(X_train, Y_train)  # find patterns in data
              print(sum(abs(clf.predict(X_test) - Y_test)))

              GenderClassifier.accuracy(clf, X_test, Y_test)
              #global flag
              #if flag==0:
              #    GenderClassifier.performanceMatrix(X_train, Y_train)
              #    flag=1
              # Spot Chec k Algorithms
              print("predict value")

              genderName = {0: "Girl", 1: "Boy"}
              for nameToTest in namesToTest:
                  predictedGender = genderName[int(clf.predict([GenderClassifier.wordToDigits(nameToTest)]))]
                  print("Predicted Gender of %s: %s" % (nameToTest.title(),predictedGender))
                  return (nameToTest.title(),predictedGender)

```


---
