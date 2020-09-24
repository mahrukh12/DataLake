Project
Apache Spark & Data Lake
In this project build ETL pipeline that will be able to extract songs and log data from an S3 bucket. It willprocess the data using Spark and load the data back into s3 as a set of dimensional tables in spark parquet files. The prupose of this project is to helps analysts to continue finding insights on what their users are listening to.
ETL Pipeline

The data gets that gets extracted will need to be transformed to to fit the data model in the target destination tables. For instance the source data for timestamp is in unix format and that will need to be converted to timestamp from which the year, month, day, hour values etc can be extracted which will fit in the relevant target time and songplays table columns. The script will also need to cater for duplicates, ensuring that they aren't part of the final data that is loaded in the tables.

About Datasets

The datasets used are retrieved from the s3 bucket and are in the JSON format. There are two datasets namely log_data and song_data. The song_data dataset is a subset of the the Million Song Dataset while the log_data contains generated log files based on the songs in song_data.

Summary
    Preamble
    Spark Process
    Project Structure
        etl.py
        dl.cfg
   Prerequisites
   Terminal commands
   Built With
   Author
   
    
Preamble

Data source is provided by one public S3 buckets. This bucket contains info about songs, artists and actions done by users (which song are listening, etc..). The objects contained in the bucket are JSON files. The entire elaboration is done with Apache Spark

Spark process

The ETL job processes the song files then the log files. The song files are listed and iterated over entering relevant information in the artists and the song folders in parquet. The log files are filtered by the NextSong action. The subsequent dataset is then processed to extract the date , time , year etc. fields and records are then appropriately entered into the time, users and songplays folders in parquet for analysis.

Project structure

This is the project structure, if the bullet contains /
means that the resource is a folder:
    
    

    /data - A folder that cointains two zip files, helpful for data exploration
    etl.py - The ETL engine done with Spark, data normalization and parquet file writing.
    dl.cfg - Configuration file that contains info about AWS credentials
etl.py

This script once executed retrieves the song and log data in the s3 bucket, transforms the data into fact and dimensional tables then loads the table data back into s3 as parquet files.
dl.cfg

This file Will contain your AWS keys.

Lets Get Started

In order to have a copy of the project up and running locally, heres few things:
Prerequisites

    Python 2.7 or greater.

    AWS Account.

    Set your AWS access and secret key in the config file.

    [AWS]
    AWS_ACCESS_KEY_ID = <your aws key>
    AWS_SECRET_ACCESS_KEY = <your aws secret>

Terminal commands

    Execute the ETL pipeline script by running:

    $ python etl.py

Built With

    Python and pySpark
Author

    Mahrukh Malik