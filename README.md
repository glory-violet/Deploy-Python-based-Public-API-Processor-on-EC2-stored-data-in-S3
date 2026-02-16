# Deploy-Python-based-Public-API-Processor-on-EC2-stored-data-in-S3

## 📌 Project Overview
This project demonstrates a Python-based application that fetches data from a public REST API, processes JSON responses using pandas, and stores the processed output in AWS cloud storage S3.

---

## 🚀 Technologies Used
- **Python** – Primary language for fetching API data, processing JSON, and managing data workflows.  
- **requests** – Python library to make HTTP calls to public APIs. Fetches real-time data in a simple and structured way.  
- **pandas** – Used to organize, process, and analyze data. Converts JSON responses into DataFrames, handles datetime conversion, and prepares data for plotting or storage.  
- **AWS EC2** – Virtual server to deploy the Python application. Enables running scripts continuously or on-demand in the cloud.  
- **Amazon S3** – Cloud storage for securely storing processed CSV/output files. Ensures persistent storage and easy access.  
- **IAM** – AWS Identity and Access Management ensures secure access to EC2 and S3. Defines roles and permissions so Python script can safely upload files.  
- **Linux** – Operating system for the EC2 instance. Provides a stable environment to run Python scripts, manage files, and deploy applications.

---

## 🏗 Project Implementation

### 1️⃣ API Data Retrieval
- Fetched real-time data from a public REST API using Python.
- Parsed JSON responses and extracted relevant fields.

### 2️⃣ Data Processing
- Structured extracted data into a pandas DataFrame.
- Converted datetime fields and performed basic inspection.
- Generated processed output as a CSV file.

#### 🔹 Python Code Example (Jupyter Notebook)
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

### 3️⃣ Cloud Deployment
- Deployed the Python application on an AWS EC2 instance.
- Configured IAM roles for secure access to AWS resources.
- Uploaded processed output files to Amazon S3.

#### 🔹 Cloud Code Example (Python script running on EC2)
# Step 1: Save DataFrame to CSV locally on EC2
csv_file = "temperature_data.csv"
temp_df.to_csv(csv_file, index=False)

# Step 2: Upload CSV to S3
s3 = boto3.client('s3')
bucket_name = 'your-s3-bucket-name'

s3.upload_file(csv_file, bucket_name, csv_file)
print(f"{csv_file} uploaded to S3 bucket {bucket_name} successfully!")
```
---

## 🙏 Conclusion
This project demonstrates a complete workflow from public API data retrieval to cloud deployment using AWS EC2 and S3. It highlights hands-on skills in Python scripting, data processing with pandas, API integration, and secure cloud storage.  

**Thank you for visiting this project!**
