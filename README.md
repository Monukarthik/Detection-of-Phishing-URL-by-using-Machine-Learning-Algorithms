# Detection-of-Phishing-URL-by-using-Machine-Learning-Algorithms
**Objective:**
The main objective of this project is to identify the Phishing URLs, based of various parameters like protocols, domains, sub-domains, extensions, and manny other parameters. A phishing Universsal Resource Locator(URL) is a URL, which mimics mimics trustful URLs, and try to steal your information. In this project, I trained a machine learning model on the dataset, collected from an open source Kaggle. I used the dataset on various machine learning algorithms, and chose XGBoost alogorithm, over other algorithms beacause of its high acuuracy prediction.

**Model Training:**
This data set comes under classification problem, as the input URL is classified as phishing (1) or legitimate (0). The algorithms used to train the model using the dataset are:
  Random Forest Classifier
  Support Vector Machine
  Decision Tree Classifier
  K-Nearest Neighbors
  Logistic Regression
  Multi-layer Perceptron
  Gradient Boosting Classifier
  XGBoost Classifier
  Naive Bayes Classifier
The model is trained on the dataset extracted from Kaggle. The evaluation is done with the sample if this dataset.

**Output:**
A pop-up window will open asking for you to enter the URL. After entering the URL, you click on the check button. This displays the probability of the URL, whether it is a phishing website or a legitimate website.
