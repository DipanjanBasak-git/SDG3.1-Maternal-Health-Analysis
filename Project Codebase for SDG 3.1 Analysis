```python
# filename: SDG3.1_Maternal_Health_Analysis.ipynb

# This is a Jupyter Notebook file that contains all the code for the project.
# It performs data loading, preprocessing, and visualization for the SDG 3.1 analysis.

# --- Step 1: Data Loading ---
# This code block is for loading the data from IBM Cloud Object Storage.
# You will get this snippet from your IBM Watsonx.ai Notebook.
# It is unique to your project. Replace the placeholders with your actual values.
import os, types
import pandas as pd
from botocore.client import Config
import ibm_boto3

def __iter__(self): return 0

# The following code accesses a file in your IBM Cloud Object Storage.
# The credentials are included here, but should be handled securely in a real-world application.
cos_client = ibm_boto3.client(service_name='s3',
    ibm_api_key_id='II6VJp-2VTOPzaLtpb_t0KBfTF96XP9HzSR62tRY9gUI',
    ibm_auth_endpoint="[https://iam.cloud.ibm.com/identity/token](https://iam.cloud.ibm.com/identity/token)",
    config=Config(signature_version='oauth'),
    endpoint_url='[https://s3.direct.us-south.cloud-object-storage.appdomain.cloud](https://s3.direct.us-south.cloud-object-storage.appdomain.cloud)')

bucket = 'datadrivenanalysisofmaternalhealt-donotdelete-pr-4sbgnmcwzt9lt0'
object_key = 'SDG-3-1-DATA-GOV.csv'

body = cos_client.get_object(Bucket=bucket,Key=object_key)['Body']
# This line adds a missing method to the file-like object so pandas can read it.
if not hasattr(body, "__iter__"): body.__iter__ = types.MethodType( __iter__, body )

# Read the CSV file. The 'encoding_errors' parameter is used to handle
# non-standard characters in the file, preventing a crash.
df_0 = pd.read_csv(body, encoding_errors='ignore')
print("Data Loading Successful. First 5 rows:")
print(df_0.head())

# --- Step 2: Data Preprocessing and Cleaning ---
# This code prepares the data for visualization by filtering, merging, and cleaning.
# We will create a new DataFrame 'merged_df' containing only the relevant data.

import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np

# Use the loaded DataFrame df_0
df = df_0.copy()

# Filter for Maternal Mortality Ratio (MMR) data using its unique indicator ID.
mmr_indicator = '3.1.1: Maternal Mortality Ratio (MMR), (per 1,00,000 live births)'
mmr_data = df[df['Indicator'] == mmr_indicator].copy()
# Rename columns for clarity and extract the start year from the 'TimePeriod' string.
mmr_data = mmr_data[['AreaName', 'TimePeriod', 'DataValue']].rename(columns={'DataValue': 'Maternal Mortality Ratio'})
mmr_data['StartYear'] = mmr_data['TimePeriod'].apply(lambda x: int(x.split('-')[0]) if '-' in x else int(x))

# Filter for Healthcare Spending data using its unique indicator ID.
hc_spending_indicator = '3.c.2: Percentage of government spending (including current and capital expenditure) in health sector to GDP'
hc_spending_data = df[df['Indicator'] == hc_spending_indicator].copy()
# Rename columns for clarity and extract the start year from the 'TimePeriod' string.
hc_spending_data = hc_spending_data[['AreaName', 'TimePeriod', 'DataValue']].rename(columns={'DataValue': 'Healthcare Spending (% of GDP)'})
hc_spending_data['StartYear'] = hc_spending_data['TimePeriod'].apply(lambda x: int(x.split('-')[0]) if '-' in x else int(x))

# Merge the two dataframes on 'AreaName' and 'StartYear' to align the data.
# This is crucial for comparing MMR and Healthcare Spending for the same country and year.
merged_df = pd.merge(mmr_data, hc_spending_data, on=['AreaName', 'StartYear'], how='inner', suffixes=('_mmr', '_hc'))

# Clean and convert data types to ensure they are numerical for plotting.
merged_df['Year'] = merged_df['StartYear']
merged_df['Maternal Mortality Ratio'] = pd.to_numeric(merged_df['Maternal Mortality Ratio'], errors='coerce')
merged_df['Healthcare Spending (% of GDP)'] = pd.to_numeric(merged_df['Healthcare Spending (% of GDP)'], errors='coerce')

# Drop any rows with missing values (NaN) that resulted from the conversion.
merged_df.dropna(inplace=True)

print("\nFinal Merged Data for Visualizations:")
print(merged_df.head())


# --- Step 3: Visualization 1 - India MMR Trend Line ---
# This visualizes the trend of MMR in India over the years.

plt.figure(figsize=(10, 6))
# Filter the merged data specifically for India.
india_data = merged_df[merged_df['AreaName'] == 'India']
# Plot the trend line.
plt.plot(india_data['Year'], india_data['Maternal Mortality Ratio'], marker='o', color='green')
plt.title('India Maternal Mortality Ratio (MMR) Trend', fontsize=16)
plt.xlabel('Year', fontsize=12)
plt.ylabel('MMR per 100,000 live births', fontsize=12)
plt.grid(True)
plt.tight_layout()
plt.show()


# --- Step 4: Visualization 2 - Country-wise MMR Comparison ---
# This compares MMR across all countries for the latest available year.

# Filter for Maternal Mortality Ratio (MMR) data for all countries from the original DataFrame.
mmr_indicator = '3.1.1: Maternal Mortality Ratio (MMR), (per 1,00,000 live births)'
mmr_data = df_0[df_0['Indicator'] == mmr_indicator].copy()

# Clean 'TimePeriod' to get a single year and convert DataValue to a numeric type.
mmr_data['Year'] = mmr_data['TimePeriod'].apply(lambda x: int(x.split('-')[0]))
mmr_data['DataValue'] = pd.to_numeric(mmr_data['DataValue'], errors='coerce')

# Find the latest year with data.
latest_year = mmr_data['Year'].max()

# Filter for data from the latest year.
latest_year_data = mmr_data[mmr_data['Year'] == latest_year]

# Create a bar chart for country comparison.
plt.figure(figsize=(12, 7))
sns.barplot(data=latest_year_data, x='AreaName', y='DataValue', palette='viridis')
plt.title(f'Maternal Mortality Ratio by Country ({latest_year})', fontsize=16)
plt.ylabel('MMR per 100,000 live births', fontsize=12)
plt.xlabel('Country', fontsize=12)
plt.tight_layout()
plt.show()


# --- Step 5: Visualization 3 - Correlation Heatmap ---
# This visualizes the correlation between MMR and Healthcare Spending based on the merged data.

# Calculate the correlation matrix for the two key indicators.
corr_df = merged_df[['Maternal Mortality Ratio', 'Healthcare Spending (% of GDP)']].corr()
plt.figure(figsize=(8, 6))
# Create the heatmap.
sns.heatmap(corr_df, annot=True, cmap='coolwarm', fmt=".2f", linewidths=.5)
plt.title('Correlation between MMR and Healthcare Spending', fontsize=14)
plt.tight_layout()
plt.show()
