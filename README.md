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
    A[Raw Data] --> B[Data Cleaning]                 

    B --> C[Feature Engineering]
    C --> D[Random Forest Model]
    D --> E[Predictions]
 Data Modeling
Excess Readmission Rate = 
CALCULATE(
    AVERAGE('FY_2025_Hospital_Readmissions'[Excess Readmission Ratio]),
    'FY_2025_Hospital_Readmissions'[Excess Readmission Ratio] <> BLANK()
)

Readmission Count = 
CALCULATE(
    COUNTROWS('FY_2025_Hospital_Readmissions'),
    'FY_2025_Hospital_Readmissions'[Number of Readmissions] <> BLANK()
)

Discharge Count = 
CALCULATE(
    SUM('FY_2025_Hospital_Readmissions'[Number of Discharges]),
    'FY_2025_Hospital_Readmissions'[Number of Discharges] <> "N/A"
)

Here's a complete Python script using pandas, matplotlib, and seaborn:
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load the data
df = pd.read_csv('FY_2025_Hospital_Readmissions_Reduction_Program_Hospital.csv')

# Clean the data
# Convert 'Number of Discharges' to numeric, handling 'N/A' and 'Too Few to Report'
df['Number of Discharges'] = pd.to_numeric(df['Number of Discharges'], errors='coerce')

# Convert 'Number of Readmissions' to numeric
df['Number of Readmissions'] = pd.to_numeric(df['Number of Readmissions'], errors='coerce')

# Convert date columns to datetime
df['Start Date'] = pd.to_datetime(df['Start Date'])
df['End Date'] = pd.to_datetime(df['End Date'])

# Basic statistics
print("Basic Statistics:")
print(df.describe())

# Analysis by state
state_analysis = df.groupby('State').agg({
    'Excess Readmission Ratio': 'mean',
    'Number of Discharges': 'sum',
    'Number of Readmissions': 'sum'
}).sort_values('Excess Readmission Ratio', ascending=False)

print("\nState-wise Analysis:")
print(state_analysis)

# Analysis by measure
measure_analysis = df.groupby('Measure Name').agg({
    'Excess Readmission Ratio': 'mean',
    'Number of Discharges': 'sum',
    'Number of Readmissions': 'sum'
}).sort_values('Excess Readmission Ratio', ascending=False)

print("\nMeasure-wise Analysis:")
print(measure_analysis)

# Visualization 1: Excess Readmission Ratio by State
plt.figure(figsize=(12, 6))
sns.barplot(x=state_analysis.index, y=state_analysis['Excess Readmission Ratio'])
plt.title('Average Excess Readmission Ratio by State')
plt.xticks(rotation=45)
plt.ylabel('Excess Readmission Ratio')
plt.tight_layout()
plt.show()

# Visualization 2: Readmissions by Measure Type
plt.figure(figsize=(12, 6))
sns.barplot(x=measure_analysis.index, y=measure_analysis['Number of Readmissions'])
plt.title('Total Readmissions by Measure Type')
plt.xticks(rotation=45)
plt.ylabel('Number of Readmissions')
plt.tight_layout()
plt.show()

# Visualization 3: Scatter plot of Discharges vs Readmissions
plt.figure(figsize=(10, 6))
sns.scatterplot(data=df, x='Number of Discharges', y='Number of Readmissions', hue='State')
plt.title('Discharges vs Readmissions')
plt.tight_layout()
plt.show()

# Visualization 4: Boxplot of Excess Readmission Ratio by Measure
plt.figure(figsize=(12, 6))
sns.boxplot(data=df, x='Measure Name', y='Excess Readmission Ratio')
plt.title('Distribution of Excess Readmission Ratios by Measure')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

# Visualization 5: Top 10 Hospitals with highest readmission ratios
top_hospitals = df.groupby('Facility Name')['Excess Readmission Ratio'].mean().sort_values(ascending=False).head(10)
plt.figure(figsize=(12, 6))
sns.barplot(x=top_hospitals.values, y=top_hospitals.index)
plt.title('Top 10 Hospitals with Highest Average Excess Readmission Ratios')
plt.xlabel('Average Excess Readmission Ratio')
plt.tight_layout()
plt.show()

Additional Analysis Ideas:
# Correlation analysis
correlation = df[['Excess Readmission Ratio', 'Number of Discharges', 'Number of Readmissions']].corr()
print("\nCorrelation Matrix:")
print(correlation)

# Time series analysis (if you have multiple years of data)
# Trend analysis by measure type over time

# Facility-level benchmarking
# Compare specific hospitals to state/national averages

Conclusion

This analysis provides actionable insights for healthcare administrators to reduce preventable readmissions. By focusing on high-impact measures and learning from top performers, healthcare systems can improve patient outcomes while reducing costs associated with unnecessary readmissions.



