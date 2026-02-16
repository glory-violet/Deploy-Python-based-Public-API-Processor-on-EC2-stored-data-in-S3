# Deploy-Python-based-Public-API-Processor-on-EC2-stored-data-in-S3
This project demonstrates a Python-based application that fetches data from a public REST API, processes JSON responses using pandas, and stores the processed output in AWS cloud storage.

# Public API Data Processor (AWS Deployment)

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

## 🎯 Key Outcomes
- Demonstrated API integration and JSON parsing.
- Applied data processing using pandas.
- Gained hands-on experience with AWS EC2 deployment.
- Implemented secure cloud storage using S3.

---

## 📎 Repository Structure
