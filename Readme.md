Sparkify Data Lake Project with Apache Spark
- The purpose of this project is to build an ETL pipeline that will be able to extract song and log data from an S3 bucket, process the data using Spark and load the data back 
  into s3 as a set of dimensional tables in spark parquet files and this helps analysts to continue finding insights on what their users are listening to.

Database Schema Design
- The tables created include one fact table, songplays and four dimensional tables namely users, songs, artists and time. This follows the star schema principle which will contain 
  clean data that is suitable for OLAP(Online Analytical Processing) operations which will be what the analysts will need to conduct to find the insights they are looking for.

ETL Pipeline
- The data gets that gets extracted will need to be transformed to to fit the data model in the target destination tables. For instance the source data for timestamp is in unix 
  format and that will need to be converted to timestamp from which the year, month, day, hour values etc can be extracted which will fit in the relevant target time and songplays 
  table columns. 
- The script will also need to cater for duplicates, ensuring that they aren't part of the final data that is loaded in the tables.

Datasets used
- The datasets used are retrieved from the s3 bucket and are in the JSON format and there are two datasets namely log_data and song_data. 
- The song_data dataset is a subset of the the Million Song Dataset while the log_data contains generated log files based on the songs in song_data.

Project Files
- etl.py : This script once executed retrieves the song and log data in the s3 bucket, transforms the data into fact and dimensional tables then loads the table data back into s3 
  as parquet files.
- dl.cfg : This script contains the AWS keys.
 
Please follow the below 2 steps in the same order to perform the entire ETL. 
- Run the below command to load the data from the JSON files into the dimension/fact tables. 
- Command : python3 etl.py
