# End-to-End-Zillow-Data-Engineering-Pipeline-with-AWS-and-Airflow

In this project, I developed a comprehensive data engineering pipeline that automates the extraction, transformation, and loading (ETL) of real estate data from Zillow. Leveraging AWS services like IAM, S3, EC2, Lambda, and Redshift along with Apache Airflow, I created a workflow that efficiently processes and stores the data for analysis. Additionally, I used Amazon QuickSight to create interactive dashboards and visualizations, turning raw data into actionable insights.


Architecture Overview:
The architecture for this project integrates several key components:

1. Data Extraction (Airflow + RapidAPI):
   - I started by setting up a Python script within Airflow that extracts real estate data from Zillow via the RapidAPI interface. The data is saved to the raw data bucket in S3 for further processing.

2. Data Storage (AWS S3):
   - The raw JSON data is first stored in a raw data bucket in S3. Then, I configured a Lambda function 'copyRawJsonFile-lambdaFunction' to automatically copy this data to another S3 bucket, ensuring a backup and preparing it for the next stage.

3. Data Transformation (AWS Lambda + Pandas):
   - Another Lambda function 'transformation-convert-to-csv-lambdaFunction' was created to process the raw JSON data. Using Pandas, I transformed the data into a structured CSV format, which was then saved in a transformed data bucket in S3.

4. Data Loading (Airflow + Redshift):
   - I used Airflow’s S3KeySensor to monitor the transformed data bucket in S3 for the transformed CSV files. Once detected, the data was loaded into an Amazon Redshift table using the S3ToRedshiftOperator, where I had already created a Zillow data table.

5. Data Visualization (Amazon QuickSight):
   - Finally, I connected Amazon QuickSight to the Redshift database to create interactive dashboards and visualizations. These visuals provided insights into various real estate trends.



Learning Outcomes:
- Cloud Service Integration: This project taught me how to integrate AWS services like IAM, S3, EC2, Lambda, Redshift, and QuickSight with Airflow, enabling the creation of a scalable and automated data pipeline.
- Data Transformation and ETL: I gained hands-on experience in handling raw JSON data, performing data transformations with Pandas, and converting it into a format suitable for analysis.
- Orchestration with Airflow: Through the use of Apache Airflow, I learned to orchestrate various tasks, manage dependencies, and ensure a smooth data flow.
- Data Visualization: Using Amazon QuickSight, I was able to create insightful and interactive visualizations, effectively turning raw data into meaningful insights.
- Error Handling and Robustness: I implemented mechanisms like S3KeySensor and Lambda functions, which ensured the robustness of the pipeline and allowed for reliable data processing and error handling.



Conclusion:
This project represents a full-scale implementation of an automated data engineering pipeline, from data extraction to visualization. By integrating multiple AWS services and leveraging modern data engineering practices, I was able to create a robust and scalable solution. The skills and knowledge I gained through this project, particularly in ETL processes, cloud computing, data visualization, and workflow automation, are invaluable and have equipped me to tackle complex data challenges in real-world scenarios. The addition of Amazon QuickSight to create visuals further enhanced the project by providing clear and actionable insights from the data.
