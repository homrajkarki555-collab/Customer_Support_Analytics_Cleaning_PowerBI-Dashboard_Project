# PROJECT-Customer_Support_Analytics_Cleaning/PowerBI_Dashboard
An end-to-end data analytics project using Python for cleaning and Power BI to build an interactive executive dashboard for call center performance tracking.

## Data Source- Organization OptiConnect Solutions

OptiConnect Solutions was a famous call center services provider company based out of technoville.It was a
renowned player in the customer service industry, providing topnotch support for a variety of products and
services.  Within the vast expanse of OptiConnect's customer service operations, the meticulous record-keeping
system captured crucial details through fields such as Call Id, Date, Agent name, Department, Answered (Y/N),
Resolved (Y/N), Speed of Answer, Average Talk Duration, and Satisfaction Rating.

The data spoke of a complex narrative, where agents strived to answer calls promptly, resolve issues efficiently,
and leave customers satisfied. The  organization found itself at the crossroads of optimizing its call center
performance to ensure unparalleled customer experiences.

# Data Preparation Report: Call Center Dataset

## Table of Content
#### 1. Objective 
- Key Questions
- Raw data- Call Centre Dataset
#### 2. Key Transformations & Steps
- Python codes
#### 3. Essential Python Functions Used
- Cleaned data- Call Center Dataset
#### 4. Power BI Interactive Visualization dashboard
- Power BI Performance Dashboard 
#### 5. Key Findings 


## 1. Objective
The goal is to transform a raw, messy dataset into a structured, clean, and "analysis-ready" format. This involved fixing structural issues, handling missing data logically, and ensuring data types were correct for Power BI visualization.
### Key Questions: 
- Were calls consistently answered in a timely manner? 
- Did the agents successfully resolve customer issues? 
- How did the speed of answer and average talk duration impact customer satisfaction? 
- Were there patterns or trends hidden within the data that could unlock the key to achieving optimal call center performance?
- <a href="https://github.com/homrajkarki555-collab/Customer_Support_Analytics_Cleaning_PowerBI-Dashboard_Project/blob/main/Call%20Centre%20Dataset%20-%20Sheet1.csv">Raw data- Call Centre Dataset </a>

## 2. Key Transformations & Steps
- Renamed columns to be more descriptive and "code-friendly" (removing spaces and fixing typos).Mapped: Unnamed: 0 to "Conversation_ID", Agent to "Agent_name", Speed of Answer to "Respond_time", and AvgTalkDuration to "Avg_handeling_time".
- Assigned Conversation_ID as the Primary Key (Index). This ensures every row is uniquely identifiable and prevents data duplication during joins.
- The original Date column was mixed. I split this into two distinct columns: Date (for daily trends) and Time (for hourly performance analysis).
- Converted Avg_handeling_time from a string format (MM:SS) into Total Seconds (Integer). Visualization tools cannot calculate averages on time strings, but they can on integers.
- Instead of just deleting rows with missing values, I used Grouped Imputation. Calculated the average performance for each specific agent and filled their specific missing values with their own average.
- Filled satisfaction rating nulls  with 0 to represent cases where no feedback was provided.
- Applied Rounding to all numerical values to ensure clean labels in charts and dashboards.
- <a href="https://github.com/homrajkarki555-collab/Customer_Support_Analytics_Cleaning_PowerBI-Dashboard_Project/blob/007d6417cae53ed13dcebdd88915f0c953404581/Call%20Center%20data%20Cleaning%20Python%20code.ipynb">Python codes </a>

## 3. Essential Python Functions Used
- I utilized the pandas library, which is the industry standard for data manipulation.
- .rename()	Changed column names for better readability.
- .set_index()	Established the Primary Key for the dataset.
- pd.to_datetime()	Converted text strings into actual Date/Time objects.
- .dt.date / .dt.time	Extracted specific components from the timestamp.
- .apply()	Used to run custom logic (like converting time to seconds).
- .groupby().transform()	Calculated averages for each agent to fill missing data.
- .fillna() / .replace()	Replaced Nulls and Zeros with calculated values.
- .round()	Cleaned up long decimal values for better presentation.
- The data is now 100% clean and stored in df_cleaned 
- <a href="https://github.com/homrajkarki555-collab/Customer_Support_Analytics_Cleaning_PowerBI-Dashboard_Project/blob/19391a8357ef60c889794942331d52546ffa73c0/Cleaned-%20Call%20Centre%20Dataset%20-%20Sheet1.csv">Cleaned data </a>

## 4. Power BI Interactive Visualization dashboard
- Implemented slicers for "Agent Name" and "Answered Status" (Y/N) to allow for granular, cross-filtered analysis of individual and team performance.
- Developed a custom DAX measure to accurately calculate the total volume of Missed Conversations, providing a clear metric for operational improvement {Missed Conversations = CALCULATE(DISTINCTCOUNT('df_cleaned'[Conversation_ID]), 'df_cleaned'[Answered (Y/N)] = "N")}
- Utilized high-visibility KPI Cards to display critical metrics, including Total Conversations, Missed Conversations, Average Handling Time (AHT), Average Response Time and Average Customer Satisfaction (CSAT).
- A Line Chart (Chat Flow) illustrates daily volume fluctuations, enabling the identification of peak traffic periods.
- A Bar Chart categorizes call volume by department to assess workload distribution across product lines.
- Integrated a Donut Chart to visualize the distribution of satisfaction ratings, allowing for a quick assessment of customer sentiment and service quality.
- <a href="https://github.com/homrajkarki555-collab/Customer_Support_Analytics_Cleaning_PowerBI-Dashboard_Project/blob/19391a8357ef60c889794942331d52546ffa73c0/Dashboard.png">Power BI Performance Dashboard </a>

## 5. Key Findings 
- 
