# Module17
**Required Assignment 17.1: Comparing Classifiers**

https://github.com/maniliy07/Module17/blob/main/prompt_III.ipynb

Our dataset comes from the UCI Machine Learning repository [link](https://archive.ics.uci.edu/ml/datasets/bank+marketing).  The data is from a Portugese banking institution and is a collection of the results of multiple marketing campaigns.  We will make use of the article accompanying the dataset [here](CRISP-DM-BANK.pdf) for more information on the data and features.

The business objective of this task is to optimize the effectiveness of a Portuguese banking institution's direct marketing campaigns. Specifically, the goal is to:

Predict Customer Subscription: Build a predictive model to determine whether a client will subscribe to a term deposit (indicated by the target variable $y$).

Optimize Marketing Resources: By identifying clients with a high probability of subscribing, the bank can focus its resources (time, staffing, and marketing budget) on the most promising leads, thereby reducing the number of unnecessary or unproductive contacts.

Identify Key Success Factors: Analyze client demographics (age, job, education), past campaign outcomes, and socio-economic indicators (employment variation rate, consumer price index) to understand which factors most significantly influence a client's decision to subscribe.

Ultimately, this allows the bank to increase its conversion rate for term deposits while maintaining cost-efficient marketing operations.

### Problem 3: Understanding the Features

Examine the data description below, and determine if any of the features are missing values or need to be coerced to a different data type.

```
Input variables:
# bank client data:
1 - age (numeric)
2 - job : type of job (categorical: 'admin.','blue-collar','entrepreneur','housemaid','management','retired','self-employed','services','student','technician','unemployed','unknown')
3 - marital : marital status (categorical: 'divorced','married','single','unknown'; note: 'divorced' means divorced or widowed)
4 - education (categorical: 'basic.4y','basic.6y','basic.9y','high.school','illiterate','professional.course','university.degree','unknown')
5 - default: has credit in default? (categorical: 'no','yes','unknown')
6 - housing: has housing loan? (categorical: 'no','yes','unknown')
7 - loan: has personal loan? (categorical: 'no','yes','unknown')
# related with the last contact of the current campaign:
8 - contact: contact communication type (categorical: 'cellular','telephone')
9 - month: last contact month of year (categorical: 'jan', 'feb', 'mar', ..., 'nov', 'dec')
10 - day_of_week: last contact day of the week (categorical: 'mon','tue','wed','thu','fri')
11 - duration: last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.
# other attributes:
12 - campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)
13 - pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted)
14 - previous: number of contacts performed before this campaign and for this client (numeric)
15 - poutcome: outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success')
# social and economic context attributes
16 - emp.var.rate: employment variation rate - quarterly indicator (numeric)
17 - cons.price.idx: consumer price index - monthly indicator (numeric)
18 - cons.conf.idx: consumer confidence index - monthly indicator (numeric)
19 - euribor3m: euribor 3 month rate - daily indicator (numeric)
20 - nr.employed: number of employees - quarterly indicator (numeric)

Output variable (desired target):
21 - y - has the client subscribed a term deposit? (binary: 'yes','no')
```


**The Business Objective of this task is to develop a predictive model that identifies the likelihood of a client subscribing to a term deposit following a direct marketing (telemarketing) campaign.**

By accurately predicting the outcome ($y$), the bank can achieve the following goals

:Increase Campaign Efficiency: Focus marketing efforts and resources on clients with the highest probability of conversion, rather than contacting the entire database.

Reduce Operational Costs: Minimize the time and labor costs spent on "unsuccessful" calls.

Enhance Customer Experience: Reduce "marketing fatigue" by avoiding unnecessary contact with customers who have a low propensity to subscribe.

Identify Key Drivers: Determine which factors (e.g., economic indicators like the euribor3m rate, or customer demographics like job and education) are the strongest predictors of a successful subscription to inform future product offerings and strategy.


To establish a baseline for your classifier, we look at the performance of a Majority Class Classifier (also known as a "Zero Rule" model). This model always predicts the most frequent outcome regardless of the input data.


***Based on the distribution of your training data:***

**"No" (Did not subscribe): ~88.73%**

**"Yes" (Subscribed): ~11.27%**

**Baseline Accuracy: 88.73%**

If your model simply predicts "no" for every single client, it will be correct approximately 88.73% of the time. This is the score to beat.

Why this matters:
The Accuracy Trap: Any model that achieves an accuracy lower than or equal to 88.73% is effectively performing no better (or worse) than a model that does not learn anything from the features.

Beyond Accuracy: Because the dataset is imbalanced (only ~11% subscribed), accuracy alone is not a sufficient metric. While the baseline accuracy is high, the baseline Recall for the "yes" class is 0%. A useful business model must aim to beat the 88.7% accuracy while specifically maximizing the identification of the "yes" subscribers through metrics like F1-Score, Precision, and Recall.


                    
