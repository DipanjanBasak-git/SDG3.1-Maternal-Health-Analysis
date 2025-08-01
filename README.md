# SDG3.1-Maternal-Health-Analysis

# Project Overview
This project presents a data-driven analysis of maternal health advancements, specifically focusing on the objectives of Sustainable Development Goal (SDG) 3.1. Utilizing an official government dataset, the analysis provides comprehensive insights into maternal mortality trends, regional disparities, and the discernible impact of healthcare expenditure. The entire project was executed within the IBM Cloud ecosystem, thereby demonstrating a robust and reproducible analytical pipeline.

# Key Features
Data Analysis & Preprocessing: Cleans and prepares data on maternal mortality and healthcare expenditure using Python's Pandas library.

Trend Visualization: Generates a line chart to visualize historical trends in Maternal Mortality Ratio (MMR) for a specific country.

Comparative Analysis: Creates a bar chart to compare MMR across different countries for a given year.

Correlation Analysis: Produces a heatmap to identify the statistical relationship between MMR and Healthcare Spending.

## Dataset
The primary dataset is SDG-3-1-DATA-GOV.csv, sourced from the official Data.gov.in AI Kosh platform.

Technologies & Tools
Platform: IBM Watsonx.ai Studio (Jupyter Notebook)

Data Storage: IBM Cloud Object Storage

Language: Python 3.11

Libraries:

pandas for data manipulation

matplotlib for plotting

seaborn for advanced statistical visualizations

Visualizations & Key Insights
The following visualizations were created as part of the project.

1. India's Maternal Health Trend
This line chart shows the consistent decline in India's Maternal Mortality Ratio over time, indicating positive progress toward the SDG 3.1 target.

Insight: National health policies are having a measurable, positive impact.

[Insert Image of India MMR Trend Line Chart Here]

2. Global Maternal Health Snapshot
This bar chart compares the Maternal Mortality Ratio across different countries for the latest year available in the dataset.

Insight: The chart highlights significant disparities in maternal health outcomes globally.

[Insert Image of Country-wise MMR Comparison Bar Chart Here]

3. MMR & Healthcare Spending Correlation
This heatmap visualizes the relationship between Maternal Mortality Ratio and a country's healthcare spending as a percentage of its GDP.

Insight: A strong negative correlation is observed, suggesting that higher healthcare spending is associated with lower maternal mortality.

[Insert Image of MMR vs. Healthcare Spending Heatmap Here]

Technical Deep Dive
Data Loading: Data was loaded directly from IBM Cloud Object Storage using a secure, generated code snippet that handles API keys and access tokens. This is the recommended method for cloud-native data projects.

Data Handling: Python's pandas library was used to filter and merge two distinct indicators from the large CSV file. Data types were explicitly cast to numeric formats to prevent errors during plotting.

Encoding Fix: A common UnicodeDecodeError was encountered during file reading. This was resolved by specifying encoding_errors='ignore' in the pd.read_csv function, ensuring that the file was read successfully despite containing non-standard characters.

How to Run the Project
Prerequisites: An active IBM Cloud account with access to Watsonx.ai Studio and Cloud Object Storage.

Upload Data: Upload the SDG-3-1-DATA-GOV.csv file to your IBM Cloud Object Storage.

Create Notebook: Create a new Jupyter Notebook in Watsonx.ai Studio and paste the provided code.

Execute: Run the code cells to perform the analysis and generate the visualizations.

Conclusion
This project demonstrates a practical and impactful application of data analysis to track a critical global health goal, providing clear and visual evidence that can inform policymakers and stakeholders.

About the Author
Name: [Your Full Name]

Institution: [Your College/University]
