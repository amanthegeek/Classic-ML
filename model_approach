# ml_phishing_classification
## Following steps were followed for the analysis:
1 - Loading the basic libraries (numpy, pandas, matplotlib, seaborn)
2 - Loading the Dataset
3 - Exploratory Data Analysis
  - Checking the head of the dataset:
    (On a first glance, the DataSet appeard to be very clean, organized and     pre-processed with feature engineering techniques, in order to obtain       categorical atteributes)
  - Overview of the Dataset using .info():
    (All the attributes, including the output variable were of integer        DataType. So, DataType conversions were not needed)
  - Checking for Null values:
    (No Null values were present. So, imputations were not required)
  - Visualizing the correlation-coefficient among all the attributes:
    ( Attributes like Prefix_Suffix, Domain_registeration_length,     URL_of_Anchor, age_of_domain, DNSRecord, web_traffic and Google_Index showed  high levels of positive / negative correlation with the output variables)
  - Visualizing the output variable, Result:
     Here, we could see that the samples of both the classes are present in     similar proportion. So, we did not require to use any of the      oversampling techniques.
  There were a total of 2456 samples.
  1362 were non-phishing and 1094 were phishing websites.
## - Statistical Significance Analysis:
  (Here, we try to test the significance of each of the input variables with  respect to the output variable using statsmodel Logit proportion testing techniques with a  level of significance 0.05.
  Here, the null hypothesis is:
  𝐻0:𝛽𝑖=0 i,e., Comparision are Not statistically significant.
  𝐻𝐴:𝛽𝑖!=0 i,e., Comparision are statistically significant.
  The following attributes were found to be significant:
  Prefix_Suffix
    having_Sub_Domain
    SSLfinal_State
    port
    Request_URL
    URL_of_Anchor
    Links_in_tags
    Submitting_to_email
    popUpWidnow
    age_of_domain
    DNSRecord
    web_traffic
    Page_Rank
    Google_Index
    Links_pointing_to_page
  
  4 - Performing a 70:30 Train-Test Split for validating the model on unseen data.
  5 - Fitting a base Logistic Regression model to the training data without any specified parameters.
    - The accuracy on the training data was  95.2298 %
    - The accuracy on the test data is  93.4871 %
      (Here, the training accuracy was slightly higher than the test accuracy, which suggested a slight overfitting of the model to the training samples. Though, both the accuracies are high, which suggests a good fit.The overfitting can be fixed using Ridge(L2 norm).)
  6 - Regularizing the Logistic Regression model using Ridge:
    (Initially we fit the data the data to the Ridge classifier with random parameters, then we try to find the best value for the parameter followed by changing the original ridge model parameter)
  7 - Comparing the bias and varience of base Logistic regression and tuned Ridge classifier to find optimum fit obtaining the scores:
    Accuracy score: 0.940 (+/- 0.01194) [Logit]
    Accuracy score: 0.940 (+/- 0.00767) [Ridge]
  8 - Using GridSearchCV to tune Ridge model:
    Best parameter for Ridge classifier:  Alpha = 0.5550000000000004
  9 - Checking train and test accuracy on the Ridge classifier:
    The accuracy on the training data is  94.3511 %
    The accuracy on the test data is  93.279 %
    (Although the overfitting had reduced, the recall was still on the higher side)
  10 - Confusion metrix analysis:
    Here, the four values obtained for the metrix are:

    True Positives: Phishing websites classified as Phishing websites

    False Positives: Non-Phishing websites classified as Phishing websites

    True Negatives: Non-Phishing websites classified as Non-Phishing websites

    False Negatives: Phishing websites classified as Non-Phishing websites
    
   ( To build a model that solves this particular business problem, our primary goal must be to reduce the number of False Negatives (Type 2 error) and then try to reduce False Positives (Type 1 error) if the former is achieved as if a small fraction genuine websites are classified as phishing websites, the damage done is less compared to classing Phishing websides as genuine websites)
   11 - Calculating the Sensitivity of the Ridge model (proportion of total positives identified correctly)
    The Sensitivity / Recall / TPR of the model is  89.2377 %
    The Specificity of the model is  96.6418 %
    The f1-score of the model is  0.9234
    (One key point to note is that since Ridge Regression has low Recall, we might try to fix this using a different threshold using Logistic Regression)
   12 - Tuning the threshold in order to increase the recall (which is out prime objective):
   (Here we try to find an optimum value of the threshold such that the Recall is maximized without sacrificing much on the accuracy or F1-score)
    On plotting the Accuracy and Recal vs the threshold, 0.35 was founf to be an optimum value.Fior threshold = 0.35
    Accuracy:  93.0754 %
    Recall:  95.5157 %
    Precision:  89.8734 %
    F1-score:  92.6087 %
    So we can conclude that, for threshold = 0.35, the recall is optimally    high as well as the Accuracy and the F1-score is retained as well
    13 - Fitting base advanced models (DT, NB, KNN, SVM)
      Logit: 0.987600 (0.000009)
      Decisiion Tree: 0.973327 (0.000128)
      Naive Bayes: 0.979830 (0.000026)
      KNN: 0.989014 (0.000038)
      SVM: 0.990546 (0.000018)
    14 - Fitting tuned DT and KNN models for better performance using GridSearchCV with 'Recall' as the scoring criteria:
      Logit: 0.941352 (0.000276)
      Ridge: 0.940959 (0.000229)
      Decisiion Tree: 0.964170 (0.000165)
      Naive Bayes: 0.923858 (0.000096)
      KNN: 0.945445 (0.000353)
      SVM: 0.958065 (0.000239)
      Tuned Decision Tree: 0.959280 (0.000181)
      Tuned KNN: 0.968651 (0.000191)
      (Here, we find the tuned KNN and the base SVM to be the top two best   models in terms of accuracy and consistency)
      For trained KNN:
        The accuracy on the training data is  98.8804 %
        The accuracy on the test data is  95.5193 %
        (Here both train and test accuracy are very close and high at the same time but overfitting is clearly apearent)
       For base SVM:
       The accuracy on the training data is  96.6921 %
       The accuracy on the test data is  95.112 %
       (Here both train and test accuracy are very close and high at the same time but no major overfitting is apearent. We shall consider the best model so far)
    15 - Fitting tuned ensemble models for enhanced prediction. 
      Logit: 0.941352 (0.000276)
      Ridge: 0.940959 (0.000229)
      Decisiion Tree: 0.962945 (0.000171)
      Naive Bayes: 0.923858 (0.000096)
      KNN: 0.945445 (0.000353)
      SVM: 0.958065 (0.000239)
      Tuned Decision Tree: 0.958465 (0.000191)
      Tuned KNN: 0.968651 (0.000191)
      Tuned RF: 0.964176 (0.000234)
      Tuned AB: 0.944621 (0.000237)
 15 - Checking performance of the tuned RF model:
    The accuracy on the training data is  98.9822 %
    The accuracy on the test data is  96.334 %
    The Sensitivity / Recall / TPR of the model is  95.5157 %
    The Specificity of the model is  97.0149 %
    The f1-score of the model is  0.9595
 ## So, a tuned RF with the parameters {'criterion': 'entropy', 'max_features': 'sqrt'} remains to be our final model returning a 10-fold cross-validation accuracy of about 96.67 % on the train set. Also, the recall of the model is about 96 % while the sensitivity is about 97 %.
