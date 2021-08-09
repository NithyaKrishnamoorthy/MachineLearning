##Introduction

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


