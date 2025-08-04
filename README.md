# Hospital Readmissions Reduction Program - Big Data Analytics Capstone Project  

**Author:** MUYOBOKE Emmanuel  
**ID:** 26227
**Faculty:** Information Technology  
**Date:** August 2025
email: muyobokeemmnauel04@gmail.com


![Healthcare Dashboard](https://via.placeholder.com/800x400?text=Hospital+Readmissions+Dashboard)  

## 📌 Project Overview  
This capstone project analyzes hospital readmissions data to identify patterns and provide actionable insights for healthcare improvement using big data analytics.

### 🎯 Key Objectives:
- Analyze **FY 2025 Hospital Readmissions Reduction Program** dataset (18,510 entries)
- Identify trends in readmission rates across conditions and regions
- Develop predictive model for Excess Readmission Ratio (ERR)
- Create interactive Power BI dashboard
- Propose targeted interventions using outlier detection

## 📂 Dataset
**Key Metrics:**
- `Excess Readmission Ratio (ERR)`
- `Predicted Readmission Rate`  
- `Number of Discharges`  
- `Medical Conditions`: AMI, HF, PN, COPD, CABG, Hip/Knee  

### 🧹 Data Cleaning Process:
```python
# Sample cleaning steps
df['Date'] = pd.to_datetime(df['Date'])
df.fillna(df.mean(), inplace=True)
df.drop(columns=['Footnote'], inplace=True)
🤖 Machine Learning Model
Model Architecture:
graph TD
    A[Raw Data] --> B[Data Cleaning]                 ![Uploading image.png…]()

    B --> C[Feature Engineering]
    C --> D[Random Forest Model]
    D --> E[Predictions]

