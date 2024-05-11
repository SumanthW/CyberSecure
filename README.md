# CyberSecure
# # Cyber Security Company Data Pipeline

# # Overview
This repository contains a simulation of a cyber security company's data analysis pipeline. The company receives JSON files from clients (websites) and analyzes them in the cloud based on threshold definitions provided by the clients. The primary goal is to detect and mitigate Distributed Denial of Service (DDoS) attacks by analyzing event-level data and security specifications.

# # Problem Definition
Online services are susceptible to DDoS attacks, which can disrupt their functionality by overwhelming their systems with excessive traffic. To ensure the availability and integrity of online services, it's crucial to analyze and mitigate these attacks effectively. This project aims to provide a comprehensive system for analyzing DDoS attacks using a combination of security specifications and event-level data.

# # Dataset
The dataset consists of JSON files containing event-level information such as IP address, website, location, session start, session end, and number of clicks. Additionally, a CSV file contains security definitions provided by clients, including thresholds for maximum requests per hour, minimum clicks, and validity dates.

# # Analysis Dimensions
The analysis is conducted based on three dimensions: time, location, and website. Events are tagged as DDoS attacks or not based on the security definitions provided by clients across these dimensions.

# # Strategy
The data pipeline utilizes Kafka or any messaging queue system to simulate a producer-consumer scenario for data streaming. Batch processing is performed at an hourly level to classify events as DDoS attacks. The pipeline architecture involves multiple stages, including data ingestion, preprocessing, transformation, and visualization.

# # Data Pipeline Architecture
The data pipeline consists of the following stages:

Source: JSON data is generated from multiple sources (client websites) using a Kafka producer concept. Producers broadcast JSON data as messages to a Kafka topic.
Ingestion: Data broadcasted by producers is received and persisted by Kafka brokers. Messages are buffered until they reach a threshold size, then written to JSON files and pushed to an Amazon S3 bucket.
Raw Data: The JSON files and CSV containing security definitions are stored in an S3 bucket. AWS Glue is used to define tables for the data.
ETL (Extract, Transform, Load): Data undergoes preprocessing and transformation stages using AWS Glue. Joins and aggregations are performed to identify potential DDoS attacks.
Visualization: The processed data is visualized using various analytics tools, allowing for analysis based on location, date, and client (website). Key performance indicators (KPIs) related to DDoS attacks are presented through static and interactive visualizations.

# # KPI Metrics
Key performance indicators include the count of DDoS attacks over time, trends in the number of attacks, popular attack locations, average attack length, and average number of clicks per attack.

Repository Structure
src/: Contains source code for data generation, ingestion, preprocessing, and visualization.
data/: Placeholder for sample data files.
docs/: Documentation files, including this README.
scripts/: Additional scripts or utilities used in the pipeline.
tests/: Unit tests for pipeline components.

# # Usage
Clone the repository.
Install required dependencies.
Configure Kafka and AWS credentials.
Run the data pipeline scripts in the appropriate order.
