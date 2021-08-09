### Introduction

Machine learning can enhance the prediction of outcomes through techniques that classify the data into predetermined categories. This project proposes a machine learning approach to predict the success of telemarketing calls for selling bank long-term deposits, by predicting which category of customers are more likely to accept such offer. The aim of this study is to present an evaluation and comparison of how different selected machine learning techniques can be applied on customer records of a bank and how these various techniques differ in terms of capabilities of predicting offer acceptance outcomes. The purpose is to uncover how machine learning could support customers’ value creation, by providing better-targeted clusters of customers for promotion campaigns. 

### Data:

The project is based on a series of data points related to about 48,000 bank customers. The data source comes specifically from a tele-marketing campaign outcome of a Portuguese retail bank on term deposit product, with data collected from 2008 to 2013 (Moro et al., 2011 and 2014), available on UCI Machine Learning Depository. There are a set of 20 features related to client information, contact modes and social-economic attributes. These are - 
<ol>
	<li>client data attributes (age, job, marital status, education, has credit card default, has housing loan, has personal loan)</li> 
	<li>contact attributes (contact mode, month, day of the week, duration of the call, contacted by how many promotion campaign, how many days have passed since the last contact, outcome of previous campaign and how many times the client has been contacted for campaign purpose)</li> 
	<li>social and economic data attributes (employment variation rate, consumer price index, consumer confidence index, Euribor3month lending rate and number of employers in the bank)</li> 
</ol>


### Methodology:

Data Preprocessing:

An initial high-level inspection of the dataset allowed to make three observations before proceeding to the data preprocessing process. 

1) The first observation was to exclude the attribute “call duration”, based on the rational that the duration of the call would have a strong correlation to the call outcome: a short call has high probability to reflect a failure and a longer call a success. 
2) The second observation was that this dataset has a very imbalanced class distribution, where only 11% of the bank clients yield successful outcome whereas the remaining 89% of the bank clients declined the offer.
3) The third observation was regarding any unknown values, with a significant spike in proportion representing 20% of the data for the feature “Default”, referring to whether a client has a credit card default - as illustrated in the below Figure 1.

![image](https://user-images.githubusercontent.com/25719700/128672488-3deb67a0-110e-40dd-90c3-11d54314f060.png)

The data pre-processing process was then established in three steps.
Step 1: The attribute “call duration” was dropped. 
Step 2: Data resampling based on a down-sampling of the major class distribution (nonexistent past contact outcome) down to 25% of its original size (from 36,548 clients representing 89% of the sample population to now 64%). This resampling represents a trade-off between class balancing and loss of information. 
Step 3: Handling unknown values. Any unknown values from their respective columns were removed, in order to obtain a sub-set of data with complete information. There is also a trade-off risk in terms of losing part of the information distribution. 

Feature Selection:

First, categorical values (such as marital status) were converted into encoded numerical values (single = 0, married = 1, divorced = 2). Then, “GridSearchCV” was applied to fine-tune hyperparameters for Random Forest Classifier. Finally, the Random Forest Classifier was fed with the best parameters obtained from previous steps. The decrease in impurity is illustrated in the below figure. It is noticeable that the columns with unknown values are not the top-raking attributes. Further to that, for feature ‘default” (i.e. has a credit card default before), 97% of the observations has a value “No”, which indicates that this column does not provide useful information to the classifier since the vast majority of the observations are sharing the same value. Hence it is concluded that removing the unknown values from all feature variables would be appropriate for this study. 

![image](https://user-images.githubusercontent.com/25719700/128672735-7e2c07c5-4ae0-4412-a593-785974e557aa.png)

Model building:

The classification techniques selected for this study were based on the comparison of the following machine learning techniques: 
- Logistic Regression (LR)
- Gaussian Naive Bayes (GNB)
- Support Vector Machine (SVM)
- XGBoost
- Random Forest

Evaluation:

The models were evaluated based on recall and F1-Score. In this case, the outcome is to predict whether the client will subscribe to term deposits or not. So a high recall is preferred where the models predit the most number of positive results.

![image](https://user-images.githubusercontent.com/25719700/128673275-a8351187-4d05-4d57-8f7d-f79626bbaffc.png)

### Conclusion
Observations<br>
Data quality was the main issue in this case study. There were both a significant imbalanced class distribution and a non-negligible amount of unknown values. Some data had to be excluded during the data pre-processing. The dominant features selected from the feature ranking process were “static” for most of them across all observations, which provide only very limited information to the training model, with little room for improvement. Another dataset limitation was the customer profile, where only 3% of observations had a past contact outcome. This is a critical limitation for the prediction of campaign success rate.     

Learning<br>
The main take away from the case study results is that data pre-processing was critical. The results raise the question of using a combined classifier instead, since a single classifier may not be working well for all classes. Regarding the top features that have been identified, some of them will not be very useful for the bank to take an action on. Indeed, social and economic data are cyclical, tend to be static, and are out of control for the bank. 

Recommendations<br>
The first recommendation is about the data collection process. In order to improve the quality and relevance of the data,it is suggested to the bank to collect data with more granularity in terms of data attributes (such as income, type of financial products already held by the customer, etc.). It is also crucial to improve the data granularity in terms of distribution (there is currently a significant imbalanced between existing and new customers, as well as customer who have already accepted an offer versus those who have not). 
The second recommendation is linked to the campaign strategy. The case study results have highlighted the dominant effect coming from social and economic aspects. The bank can prioritize resources to contact customers during favorable economic cycle. For new customer, retirees and students (age feature) as well as people holding university degree (education feature) tend to respond better to the offer. At that point, it is unclear if the unified machine learning model was not satisfactory due to data quality issue or features specificities. As the bank broaden their customer and accumulate more contact data, we might be able to use a unified model to train and achieve better accuracy as more data become more available

For further research
Based on the results, the recommendation is to explore the possibility to use a 2-classifier model, based on customer’s relationship with the bank – as illustrated by the following figure. The rationale is that one-size-fit-all solution is not the most optimal approach. Exploring a 2-classifier model approach may provide better prediction results.
 
2-Classifier model proposal based on customer’s relationship with the bank

![image](https://user-images.githubusercontent.com/25719700/128673615-60995fc1-efa6-4097-9176-3e74233ef50d.png)

### Case study conclusion
The solution is an attempt to use machine-learning methods in order to predict the success of telemarketing calls for selling bank long-term deposits, by predicting which category of customers are more likely to accept such offer. The model elegance and innovativeness of the case study was to start with a real case dataset, including various types of data quality issues and to explore various ways of managing these qualitative deficiencies. The case study was also able to reveal problem, apply several machine-learning methods (Logistic Regression, Gaussian Naive Bayes, Support Vector Machine, Random Forest and XGBoost) and proposed a series of improvements (including using Random Forest). Despite facing some results limited by data quality issues, the case study paid attention to results completeness by providing an extensive series of results for each machine learning methods, including a focus on accuracy. To finish, the case study results are opening some proposal for further research and methodology innovation, as its results raise the question of using a combined classifier instead, since a single classifier may not be working well for all classes.

