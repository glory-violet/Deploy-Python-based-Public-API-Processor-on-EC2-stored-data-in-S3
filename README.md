# Deploy-Python-based-Public-API-Processor-on-EC2-stored-data-in-S3

## 📌 Project Overview
This project demonstrates a Python-based application that fetches data from a public REST API, processes JSON responses using pandas, and stores the processed output in AWS cloud storage.


The application is deployed on an AWS EC2 instance and securely stores generated data files in Amazon S3.

---

## 🚀 Technologies Used
- Python
- requests
- pandas
- AWS EC2
- Amazon S3
- IAM
- Linux

---

## 🏗 Project Implementation

### 1️⃣ API Data Retrieval
- Fetched real-time data from a public REST API using Python.
- Parsed JSON responses and extracted relevant fields.

### 2️⃣ Data Processing
- Structured extracted data into a pandas DataFrame.
- Converted datetime fields and performed basic inspection.
- Generated processed output as a CSV file.

### 3️⃣ Cloud Deployment
- Deployed the Python application on an AWS EC2 instance.
- Configured IAM roles for secure access to AWS resources.
- Uploaded processed output files to Amazon S3.

---

#### 🔹 Code Example (Jupyter Notebook)
```python
import requests
import pandas as pd
import matplotlib
import json

# Step 1: Call Public API
url = "https://api.weather.gov/points/39.7456,-97.0892"
response = requests.get(url)
response.json()

# Step 2: Call hourly forecast API
url = 'https://api.weather.gov/gridpoints/TOP/32,81/forecast/hourly'
response = requests.get(url)
response.json()

# Step 3: Parse JSON response into Python dictionaries/lists
periods = response.json()["properties"]["periods"]

# Step 4: Extract temperature with timestamp
temp_dict = {}
for period in periods:
    temp_dict[period["startTime"]] = period['temperature']
temp_dict

# Step 5: Create pandas DataFrame
temp_df = (
    pd.DataFrame({
        "Datetime": temp_dict.keys(),
        "Temperature (F)": temp_dict.values()
    })
)

# Step 6: Convert Datetime strings
temp_df["Datetime"] = pd.to_datetime(temp_df["Datetime"])
temp_df.head()

# Step 7: Plot Temperature Data
temp_df.set_index("Datetime").plot()


## 🎯 Key Outcomes
- Demonstrated API integration and JSON parsing.
- Applied data processing using pandas.
- Gained hands-on experience with AWS EC2 deployment.
- Implemented secure cloud storage using S3.

---

## 📎 Repository Structure
