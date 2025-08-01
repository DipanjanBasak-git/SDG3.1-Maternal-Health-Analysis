# SDG3.1-Maternal-Health-Analysis

## Project Overview
This project presents a data-driven analysis of maternal health advancements, specifically focusing on the objectives of Sustainable Development Goal (SDG) 3.1. Utilizing an official government dataset, the analysis provides comprehensive insights into maternal mortality trends, regional disparities, and the discernible impact of healthcare expenditure. The entire project was executed within the IBM Cloud ecosystem, thereby demonstrating a robust and reproducible analytical pipeline.

## Key Features
Data Analysis & Preprocessing: Cleans and prepares data on maternal mortality and healthcare expenditure using Python's Pandas library.

Trend Visualization: Generates a line chart to visualize historical trends in Maternal Mortality Ratio (MMR) for a specific country.

Comparative Analysis: Creates a bar chart to compare MMR across different countries for a given year.

Correlation Analysis: Produces a heatmap to identify the statistical relationship between MMR and Healthcare Spending.

## Dataset
The primary dataset is SDG-3-1-DATA-GOV.csv, sourced from the official Data.gov.in AI Kosh platform.

## Technologies & Tools
Platform: IBM Watsonx.ai Studio (Jupyter Notebook)

Data Storage: IBM Cloud Object Storage

Language: Python 3.11

Libraries:

pandas for data manipulation

matplotlib for plotting

seaborn for advanced statistical visualizations

## Visualizations & Key Insights
The following visualizations were created as part of the project.

## 1.Data Preprocessing
Data Loading: The SDG-3-1-DATA-GOV.csv file was loaded from IBM Cloud Object Storage. An encoding error was resolved by specifying encoding_errors='ignore' in the pd.read_csv function to ensure successful file ingestion.

Data Handling: Python's pandas library was used to filter and merge two distinct indicators (Maternal Mortality Ratio and Healthcare Spending) from the large CSV file. Data types were explicitly cast to numeric formats to prevent errors during plotting.
<img width="1919" height="866" alt="Screenshot 2025-07-27 171656" src="https://github.com/user-attachments/assets/f67824a6-7657-43ef-9189-5a8a0441d2a5" />


## 2. India's Maternal Health Trend
This line chart shows the consistent decline in India's Maternal Mortality Ratio over time, indicating positive progress toward the SDG 3.1 target.

Insight: National health policies are having a measurable, positive impact.

<img width="1887" height="700" alt="Screenshot 2025-07-27 171514" src="https://github.com/user-attachments/assets/43e5b87a-d89c-4706-8e3e-590d69f863be" />


## 3. Global Maternal Health Snapshot
This bar chart compares the Maternal Mortality Ratio across different countries for the latest year available in the dataset.

Insight: The chart highlights significant disparities in maternal health outcomes globally.

<img width="1885" height="734" alt="Screenshot 2025-07-27 171534" src="https://github.com/user-attachments/assets/6a032073-a592-410b-b8e3-19b3f510d5bd" />


## 4. MMR & Healthcare Spending Correlation
This heatmap visualizes the relationship between Maternal Mortality Ratio and a country's healthcare spending as a percentage of its GDP.

Insight: A strong negative correlation is observed, suggesting that higher healthcare spending is associated with lower maternal mortality.

<img width="1868" height="686" alt="Screenshot 2025-07-27 171544" src="https://github.com/user-attachments/assets/519f1493-24b7-4772-9055-182992735162" />"

## Technical Deep Dive
Data Loading: Data was loaded directly from IBM Cloud Object Storage using a secure, generated code snippet that handles API keys and access tokens. This is the recommended method for cloud-native data projects.

Data Handling: Python's pandas library was used to filter and merge two distinct indicators from the large CSV file. Data types were explicitly cast to numeric formats to prevent errors during plotting.

Encoding Fix: A common UnicodeDecodeError was encountered during file reading. This was resolved by specifying encoding_errors='ignore' in the pd.read_csv function, ensuring that the file was read successfully despite containing non-standard characters.

## How to Run the Project
Prerequisites: An active IBM Cloud account with access to Watsonx.ai Studio and Cloud Object Storage.

Upload Data: Upload the SDG-3-1-DATA-GOV.csv file to your IBM Cloud Object Storage.

Create Notebook: Create a new Jupyter Notebook in Watsonx.ai Studio and paste the provided code.

Execute: Run the code cells to perform the analysis and generate the visualizations.

Conclusion
This project demonstrates a practical and impactful application of data analysis to track a critical global health goal, providing clear and visual evidence that can inform policymakers and stakeholders.

## About the Author
Name: Dipanjan Basak
Institution: Institute of Engineering and Management (IEM)
