# Credit Risk & Credit Score Analysis | **Exploratory Data Analysis (EDA)**
#### **Tools: Python, Pandas, NumPy, Matplotlib, Seaborn**

--- 

## Project Overview

In today's financial landscape, accurate credit score assessment is vital for both financial institutions and customers. Paisabazaar, a leading financial services company, helps individuals find and apply for banking and credit products.

This project performs an **Exploratory Data Analysis (EDA)** on customer financial and behavioral data to understand patterns, detect anomalies, and extract data-driven insights to support credit risk assessment, reduce potential loan defaults, and improve decision-making efficiency.

---

## Problem Statement

Paisabazaar relies on accurate assessment of customer creditworthiness to support loan approvals and mitigate financial risk. Existing credit evaluation approaches can be further strengthened by leveraging exploratory data analysis to understand how income, debt, credit utilization, and payment behavior collectively influence customer credit scores.

**Goal:**  
To perform Exploratory Data Analysis (EDA) on customer financial and behavioral data in order to identify key patterns, risk indicators, and relationships that influence credit score categories, enabling Paisabazaar to:

- Improve credit risk assessment and early risk identification  
- Support data-driven credit policy decisions  
- Enable targeted financial product strategies based on customer profiles  
- Lay a strong analytical foundation for future predictive modeling


---


## Business Objectives

1. **Strengthen Credit Risk Understanding:**  
   Identify financial and behavioral factors that differentiate Good, Standard, and Poor credit score segments.

2. **Support Risk-Aware Decision Making:**  
   Highlight early risk indicators such as high credit utilization, delayed payments, and frequent credit inquiries.

3. **Enable Customer Segmentation:**  
   Assist in grouping customers based on income, credit behavior, and financial stability.

4. **Foundation for Future Modeling:**  
   Provide clean, validated insights that can be leveraged for building predictive credit scoring models in future phases.

---

## Dataset Description

* **Size:** 100,000 records, 28 columns
* **Features include:**

  * **Demographic:** Age, Occupation, Name, SSN
  * **Financial:** Annual Income, Monthly In-hand Salary, Number of Bank Accounts, Credit Cards, Loans, Interest Rate
  * **Credit Information:** Credit Utilization Ratio, Outstanding Debt, Credit History Age, Credit Mix
  * **Behavioral Metrics:** Payment Behavior, Delayed Payments, Credit Inquiries, Payment of Minimum Amount
  * **Target Variable:** Credit Score (Good, Standard, Poor)

**Source:** Dataset provided as `dataset.csv`

---

## Methodology

###  Data Cleaning & Preparation

* Removed irrelevant columns (Customer_ID, Name, SSN, etc.)
* Handled missing values (imputed `Annual_Income` with mean)
* Converted data types for analysis (`Monthly_Balance` to numeric)
* Removed outliers in `Annual_Income` using IQR
* Created new features:

  * `Debt_to_Income_Ratio = Outstanding_Debt / Annual_Income`
  * `Income_Bracket` categorized into Low, Medium, High

### Exploratory Data Analysis (EDA)

#### **Univariate Analysis**

* Age distribution histogram → identify dominant demographics
* Income and Monthly Salary histograms → understand financial spread
* Credit Score bar plot → check class distribution (Good, Standard, Poor)
* Credit Utilization box plot → detect over-leveraged customers
* Interest Rate histogram → analyze borrowing costs

#### **Bivariate Analysis**

* Credit Score vs Age (box plot) → correlation with financial stability
* Credit Score vs Income (violin plot) → income disparity across credit scores
* Number of Loans vs Credit Score (stacked bar) → effect of multiple loans
* Delay from Due Date vs Credit Score → payment punctuality correlation
* Occupation vs Credit Score (bar plot) → occupational influence on credit

#### **Multivariate Analysis**

* Pair plots for Annual_Income, Outstanding_Debt, Credit_Utilization_Ratio, Credit_History_Age vs Credit Score
* Correlation heatmap → identify relationships among financial attributes
* Credit Score distribution across top 10 Loan Types (heatmap)

---

## Key Insights

* **Demographics:** Majority of customers aged 30-40, working population drives financial engagement
* **Income Distribution:** Skewed toward middle-income, enabling targeted loan and credit products
* **Credit Scores:** Standard category dominates, Good and Poor categories require attention for targeted interventions
* **Behavioral Trends:** Timely payments correlate with better credit scores; delayed payments are a key risk factor
* **Occupational Insights:** Healthcare and technical roles dominate Good and Standard credit scores

---

## Project Structure

```
Paisabazaar-Credit-EDA/
│
├── dataset.csv                 # Raw dataset
├── EDA_Notebook.ipynb          # Jupyter notebook with full analysis
├── images/                     # Folder containing all plots
├── README.md                   # Project overview and summary
├── requirements.txt            # Python libraries required
```

---

## Imported Libraries


### This project uses the following Python libraries for data manipulation, visualization, and analysis:

```python


# Data manipulation and numerical analysis
import pandas as pd
import numpy as np

# Data visualization
import matplotlib.pyplot as plt
import seaborn as sns

# Image and plot styling utilities
import matplotlib.image as mpimg
import matplotlib.lines as lines
import matplotlib.patches as patches

# Warnings handling
import warnings
warnings.filterwarnings('ignore')
```

## **Credit Score Distribution**
### Chart - 1 visualization code
```python
fig,ax = plt.subplots(1,1,figsize = (18,10))

palette = ['#0066ff', '#000000', '#FFFFFF'] 
sns.countplot(x = 'Credit_Score', data = bank_df , palette = palette , ax = ax)

apply_chart_styling(ax = ax,fig = fig,title = 'Credit Score Distribution' , subtitle = 'Analyzing Credit Score Count',insight_text = '''

The Credit Score Distribution chart reveals that 
the Standard credit score category has the highest count, 
indicating that most individuals fall within this middle range. 
In contrast, the Good credit score 
category shows a lower count, 
while the Poor category has the fewest individuals. 
This distribution suggests opportunities for Paisabazaar 
to provide targeted 
financial education and products 
aimed at improving credit ratings, 
particularly for those in the Standard category. 
Additionally, 
developing tailored services, such as credit-building 
loans and educational resources, 
could help customers transition to a Good credit score. 
Overall, analyzing this distribution allows for better 
customer segmentation and 
more personalized marketing strategies, 
ultimately guiding strategic decisions 
related to product development and customer engagement.''')

plt.tight_layout()
plt.show()
```
---
![image alt](https://github.com/SatyaGanesh07/Credit-Score-Prediction-Analysis/blob/d961ba28cc4129d430ca4bfd2e945cd7e6c9d72a/Visuals/visual%201.png)
---
--- 

## Age Demographics
### Chart - 2 visualization code
```python
fig,ax = plt.subplots(1,1,figsize = (18,10))

sns.histplot(x = 'Age' , data = bank_df , ax = ax ,kde = True, bins = 30, color = '#0066FF')
apply_chart_styling(ax = ax,fig = fig,title = 'Age Distribution' , subtitle = 'Analyzing Age Distribution',insight_text = '''
The Age Distribution chart provides insights into 
the demographic makeup of the customer base. 
It shows that the age group between 30 and 40 years has the highest count of customers, 
indicating that this demographic is most actively engaged with the services offered. 
The count gradually decreases for ages below 30 and above 40, suggesting a decline in 
participation among younger and older age groups. 

The overlayed trend line illustrates a 
generally declining pattern as age increases, 
with a slight uptick in the 50s, indicating a 
potential interest in financial products among older customers. 
This information can help Paisabazaar tailor their marketing strategies 
and product offerings to cater specifically to the age group with the 
highest engagement, while also exploring ways to attract younger customers and 
retain older clients. ''')
plt.tight_layout()
plt.show()
```
![image alt](https://github.com/SatyaGanesh07/Credit-Score-Prediction-Analysis/blob/d961ba28cc4129d430ca4bfd2e945cd7e6c9d72a/Visuals/visual%202.png)

--- 

## Income Distrubution

### Chart - 3 visualization code
```python
fig, ax = plt.subplots(1, 2, figsize=(18, 10))

# Flatten the axes array for easier iteration
axes = ax.flatten()

variables = ['Annual_Income', 'Monthly_Inhand_Salary']

for i, var in enumerate(variables):
    sns.histplot(bank_df[var], bins=30, kde=True, ax=axes[i], color='#0066ff')
    
    apply_chart_styling(
        ax=axes[i], 
        fig=fig, 
        title=f'Distribution of Annual Income and Monthly in hand Salary ', 
        subtitle=f'Analyzing income to capture variations across individuals.', 
        insight_text='''The Distribution of Annual Income and Monthly 
In-Hand Salary** chart provides insights 
into the financial status of individuals within the dataset.
The left side of the chart shows the distribution of **Annual Income**, 
with a prominent peak around the 20,000 to 40,000 range, 
indicating that a significant number of individuals earn within this bracket. 
There’s a gradual decline in frequency as income increases, 
suggesting a right-skewed distribution.
        
On the right side, the **Monthly In-Hand Salary** distribution mirrors 
the annual income distribution but reveals a more pronounced peak between 2,000 to 4,000. 
This indicates that most individuals have a monthly salary that correlates with their annual income, 
further emphasizing the skewness towards lower incomes.
        
The analysis suggests that a large segment of the population earns modest incomes, 
and there may be potential opportunities for financial products aimed at individuals within this 
income range, particularly focusing on budgeting and savings. Additionally, the consistent patterns 
between annual income and monthly salary imply stability in financial planning among the demographic. '''
)

# Hide unused subplots if any
for j in range(len(variables), len(axes)):
    axes[j].axis('off')

plt.tight_layout()
plt.show()
```
![image alt](https://github.com/SatyaGanesh07/Credit-Score-Prediction-Analysis/blob/d961ba28cc4129d430ca4bfd2e945cd7e6c9d72a/Visuals/visual%203.png)

--- 

## Credit Utilization 
### Chart - 4 visualization code
```python
fig,ax = plt.subplots(1,1,figsize = (18,10))
palette = ['#0066ff', '#000000', '#FFFFFF']
sns.boxplot(x ='Credit_Utilization_Ratio', data = bank_df , palette = palette , ax = ax)

for line in ax.artists:
    if line.get_label() == 'median':
        line.set_color('red')  

apply_chart_styling(fig = fig, ax = ax ,title = 'Credit Utilization', subtitle = 'Analyzing Credit Utilization', insight_text = ''' The provided visualization displays credit utilization distribution. 
The chart seems to analyze the ratio, with values concentrated 
between approximately 28% to 35%. 
There is a moderate range of variation in credit utilization. 
This analysis might indicate that users in 
the sample have credit usage within this range, 
and deviations outside of it are minimal.''')
plt.tight_layout()
plt.show()
```
![image alt](https://github.com/SatyaGanesh07/Credit-Score-Prediction-Analysis/blob/d961ba28cc4129d430ca4bfd2e945cd7e6c9d72a/Visuals/visual%204%20.png)

--- 
## Distribution Of Interest Rate

### Chart - 5 visualization code
```python
fig,ax = plt.subplots(1,1,figsize = (18,10))
palette = ['#0066ff', '#000000', '#FFFFFF']
sns.histplot(x ='Interest_Rate', data = bank_df , color = '#0066FF' , ax = ax,bins = 30 ,kde =True)

apply_chart_styling(fig = fig, ax = ax ,title = 'Distribution Of Interest Rate', subtitle = 'Analyzing Interest Rate', insight_text = '''The chart depicts the distribution of interest rates. It shows variability across a broad range, 
with a few notable peaks. 
The most significant spikes occur around the 5% and 20% interest rates. 
These peaks suggest that a large portion of the data points 
cluster at these rates. Additionally, the density curve overlaid highlights fluctuations, 
with rates predominantly falling between 0% and 35%. 
This suggests a diverse spread of interest rates with concentrations at specific points.''')
plt.tight_layout()
plt.show()
```
![image alt](https://github.com/SatyaGanesh07/Credit-Score-Prediction-Analysis/blob/d961ba28cc4129d430ca4bfd2e945cd7e6c9d72a/Visuals/visual%205%20.png)

--- 
# **Bivariate Analysis**
## Age and impact on it's Credit Score
### Chart - 6 visualization 
```python
fig,ax = plt.subplots(1,1,figsize = (18,10))

sns.boxplot(x = 'Credit_Score' , y = 'Age' , data = bank_df , ax = ax, palette = palette)

for line in ax.artists:
    if line.get_label() == 'median':
        line.set_color('red')  
        
apply_chart_styling(fig = fig , ax = ax , title = 'Age and Its Impact on Credit Score', subtitle = 'Analyzing the Correlation Between Age Groups and Creditworthiness', insight_text = '''The chart shows a comparison 
between age groups and credit scores. 
The age distribution for good, standard, and poor credit scores spans 
a similar range, 
generally between 30 to 50 years. 
The median age for individuals with good and poor credit is around 40, 
while for those with standard credit, the median is closer to 35. 
This indicates that age does not strongly influence credit score differences in this dataset. ''')
plt.tight_layout()
plt.show()
```
![image alt](https://github.com/SatyaGanesh07/Credit-Score-Prediction-Analysis/blob/d961ba28cc4129d430ca4bfd2e945cd7e6c9d72a/Visuals/visual%206.png)

--- 
### Chart - 7 visualization code
```python
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(18,10))


sns.violinplot(x='Credit_Score', y='Annual_Income', data=bank_df, ax=ax1, palette=palette)
ax1.set_title('Annual Income and Credit Score')
ax1.set_ylabel('Annual Income')


sns.violinplot(x='Credit_Score', y='Monthly_Inhand_Salary', data=bank_df, ax=ax2, palette=palette)
ax2.set_title('Monthly Inhand Salary and Credit Score')
ax2.set_ylabel('Monthly Inhand Salary')

apply_chart_styling(fig=fig, ax=ax1, title='Income and Its Impact on Credit Score', subtitle='Analyzing the Correlation Between Income and Creditworthiness', insight_text=''' ''')
apply_chart_styling(fig=fig, ax=ax2, title='', subtitle='', insight_text='''The chart shows the correlation between income and credit scores using violin plots. 
The left plot compares annual income with credit scores, showing that individuals with higher 
credit scores tend to have higher annual incomes. The distribution narrows for those with standard and poor credit scores, 
indicating lower annual incomes in those groups.
The right plot focuses on monthly in-hand salary, reinforcing a similar trend. 
Those with good credit scores have higher monthly salaries, 
while the distribution for individuals with standard and poor credit scores shifts 
towards lower monthly incomes. The overall insight is that higher incomes are associated 
with better credit scores. ''')
plt.tight_layout()
plt.show()
```
![image alt](https://github.com/SatyaGanesh07/Credit-Score-Prediction-Analysis/blob/d961ba28cc4129d430ca4bfd2e945cd7e6c9d72a/Visuals/visual%207-.png)

---
### The Relationship Between Credit Inquiries and Credit Score

```python
fig, ax = plt.subplots(1, 1, figsize=(18, 10))


sns.countplot(data=bank_df, x='Num_Credit_Inquiries', hue='Credit_Score', ax=ax, palette= palette)

# Apply chart styling
apply_chart_styling(
    fig=fig,
    ax=ax,
    title='The Relationship Between Credit Inquiries and Credit Score',
    subtitle='Exploring How Credit Inquiries Impact Creditworthiness',
    insight_text='''
    The provided chart explores the relationship between credit inquiries and creditworthiness. 
    It reveals that while a 
    higher number of inquiries can generally lead to a lower credit score, 
    there are exceptions. 
    Individuals with credit scores between 700 and 800, 
    considered good to excellent, can have a higher number of inquiries without significantly 
    impacting their score. 
    However, for those with lower credit scores, 
    even a moderate number of inquiries can negatively 
    affect their creditworthiness'''
)

plt.tight_layout()
plt.show()
```
![image alt](https://github.com/SatyaGanesh07/Credit-Score-Prediction-Analysis/blob/d961ba28cc4129d430ca4bfd2e945cd7e6c9d72a/Visuals/visual%207.png)

---
## Solution to Business Objective
I suggest the client implement a predictive credit scoring model. This model can accurately predict individual credit scores based on customer data, enabling Paisabazaar to achieve its business objectives of:

Enhancing Credit Risk Management: By accurately assessing creditworthiness, the model can help minimize the risk of loan defaults and bad debt.

Personalizing Financial Product Recommendations: Tailored financial product offerings based on predicted credit scores can improve customer satisfaction and engagement.

Optimizing Loan Approval Processes: Automated credit score predictions can streamline the loan approval process, leading to faster and more efficient decisions.

Increasing Customer Satisfaction: Providing personalized financial advice and product recommendations can enhance customer trust and loyalty.
The model can be built using machine learning techniques, leveraging features such as income, credit card usage, loan history, and payment behavior to predict credit scores with high accuracy.

--- 

## Conclusion

This exploratory analysis highlights key financial and behavioral factors influencing credit score categories, including income levels, credit utilization, payment behavior, and credit inquiries. The findings emphasize the dominance of mid-risk customers and the importance of timely payments in maintaining credit health. These insights can support improved credit risk assessment and provide a strong analytical foundation for future predictive modeling initiatives.

---
# Tools & Technologies

* **Python**
* **Pandas, NumPy**
* **Matplotlib, Seaborn**

--- 
## Project Scope

This project focuses on **Exploratory Data Analysis (EDA)** to understand the key factors influencing credit scores.  
While no machine learning model is built in this phase, the insights derived from EDA are intended to support future development of predictive credit scoring models.
3. Open `EDA_Notebook.ipynb` and run all cells to reproduce the analysis.

---
## Contact

For any questions or suggestions, please open an issue or contact me via LinkedIn:  
[Satya Ganesh LinkedIn](https://www.linkedin.com/in/satya-ganesh-5a89b2283/)

