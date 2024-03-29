# D2S - Databricks DataShift Shuttle
### What is D2S?
D2S stands for Databricks DataShift Shuttle. It's a versatile data transfer solution built on Databricks enabling seamless data movement between different systems and environments. Whether it's an adhoc transfer across internal teams or scheduled data pipelines moving data to and fro between internal systems and external data stakeholders, it gets your data lift, shift and load operations done in a simple & compliant way. Also, it brings your team a good level of Data Governance perspective for all - __"Could you quickly pull this data for me"__ kind of requests from your allied teams!

#### Move your data easily to and fro across platforms
* Between AWS S3 Bucket and Relational Databases - MySQL or PostgreSQL
* Between different Relational Databases - MySQL or PostgreSQL
* Between an SFTP Server and AWS S3 Bucket
* Between different AWS S3 accounts
  
#### Features
* File selection based on file naming pattern containing dates and timestamps
  * Selects latest file evaluated based on timestamp present in file name
  * Writes file with user provided name pattern included with timestamp or date pattern
* Copying multiple files between different S3 Buckets in a single go
* Many to one conversion of files between SFTP server to S3 bucket
* Load data into table in either append or overwrite mode
* Write data from database table to different file formats: csv, txt and parquet
* Keeps track of file details, number of records present, source-destination details etc.
* Receive an email notification with comprehensive details and status of process run once it's finished

#### In a nutshell, D2S brings in a robust Data Governance perspective to your data team providing you a complete view of a Dataset journey details including:
* Which Dataset?  : Track identity of Dataset & number of records present in it
* What Time?      : Track timestamps at which data got processed
* Where to Where? : Track source and destination of dataset
* Who?: Track who is sending out & receiving in data

## User Guide
#### S3 - Relational Databases
Notebook / Service name:  S3-DB
Functionality: Reads files from AWS S3 and loads into Relational Database table

##### Notebook Widgets Input guide:
* Source_S3_Access : Valid S3 access name defined in configs notebook.
* Source_S3_File_Path : File path at S3 location which needs to be processed.
* Allowed input patterns for Source_S3_File_Path:
  * Exact S3 file path can be provided : s3://bucket-name/prefix/filename
  * Name Pattern with date : s3://bucket-name/prefix/filename_yyyymmdd.format [File with latest date will be selected]
  * Name pattern with datetime: s3://bucket-name/prefix/filename_yyyymmddHHMMSS.format [File with latest timestamp will be selected]
  * Just path to directory: S3://bucket-name/prefix/   [Note: All files present in directory will be processed in this case]
* Header Row: True by default, can be changed to False using dropdown option
* Load Type: Append mode by default, can be changed to Overwrite using dropdown option
* Target DB: Target database type, can be selected from dropdown
* Target DB Access: Valid DB access name defined in configs notebook
* Target DB Table: Target table name with pattern: schema.table_name
* Notification Recipeints: Multiple email ids separated with ',' are allowed.

#### Relational Databases - S3
Notebook / Service name:  DB-S3
Functionality: Reads data from Relational Database table and writes file to AWS S3 bucket

##### Notebook Widgets Input guide
* Source DB: Source database type, can be selected from dropdown.
* Source DB Access: Valid DB access name defined in configs notebook.
* Source DB Table: Target table name with pattern: schema.table_name
* DML : SQL query can be input to get required data. If left blank, SELECT * FROM Source DB Table will be used
* Target_S3_Access : Valid S3 access name defined in configs notebook.
* Target_S3_File_Path : File path at destination S3 bucket.
* Allowed input patterns for Target_S3_File_Path:
  * Exact S3 file path can be provided : s3://bucket-name/prefix/filename
  * Name Pattern with date : s3://bucket-name/prefix/filename_yyyymmdd.format [File with latest date will be selected]
  * Name pattern with datetime: s3://bucket-name/prefix/filename_yyyymmddHHMMSS.format [File with latest timestamp will be selected]
  * Just path to directory: S3://bucket-name/prefix/ [In this case, table_name_yyyymmddhhmmss.csv will be used as final file name]
* Target Delimiter: ',' will be used as default in final file
* Notification Recipeints: Multiple email ids separated with ',' are allowed.

#### SFTP - S3
Notebook / Service name:  SFTP-S3
Functionality: Transfers files from SFTP Server to AWS S3 bucket

##### Notebook Widgets Input guide
* Source SFTP Access: Valid SFTP access name defined in configs notebook.
* Source_SFTP_File_Path : File path in SFTP Server.
* Allowed input patterns for Source_SFTP_File_Path:
  * Exact SFTP file path can be provided : /Home/Dir-1/Dir-2/filename
  * Name Pattern with date : /Home/Dir-1/Dir-2/filename_yyyymmdd.format [File with latest date will be selected]
  * Name pattern with datetime: /Home/Dir-1/Dir-2/filename_yyyymmddHHMMSS.format [File with latest timestamp will be selected]
  * Just path to directory: /Home/Dir-1/Dir-2/ [Note: All files present in directory will be processed to a single file in this case]
* Target_S3_Access : Valid S3 access name defined in configs notebook.
* Target_S3_File_Path : File path at destination S3 bucket.
* Allowed input patterns for Target_S3_File_Path:
  * Exact S3 file path can be provided : s3://bucket-name/prefix/filename
  * Name Pattern with date : s3://bucket-name/prefix/filename_yyyymmdd.format
  * Name pattern with datetime: s3://bucket-name/prefix/filename_yyyymmddHHMMSS.format
* Notification Recipeints: Multiple email ids separated with ',' are allowed.

#### S3 - S3
Notebook / Service name:  S3-S3
Functionality: Transfers files between S3 Buckets

##### Notebook Widgets Input guide
* Source_S3_Access : Valid S3 access name defined in configs notebook.
* Source_S3_File_Path : File path at S3 location which needs to be processed.
* Allowed input patterns for Source_S3_File_Path:
  * Exact S3 file path can be provided : s3://bucket-name/prefix/filename
  * Name Pattern with date : s3://bucket-name/prefix/filename_yyyymmdd.format [File with latest date will be selected]
  * Name pattern with datetime: s3://bucket-name/prefix/filename_yyyymmddHHMMSS.format [File with latest timestamp will be selected]
  * Just path to directory: S3://bucket-name/prefix/   [Note: All files present in directory will be processed in this case]
* Target_S3_Access : Valid S3 access name defined in configs notebook.
* Target_S3_File_Path : File path at destination S3 bucket.
* Allowed input patterns for Target_S3_File_Path:
  * Exact S3 file path can be provided : s3://bucket-name/prefix/filename
  * Name Pattern with date : s3://bucket-name/prefix/filename_yyyymmdd.format [File with latest date will be selected]
  * Name pattern with datetime: s3://bucket-name/prefix/filename_yyyymmddHHMMSS.format [File with latest timestamp will be selected]
  * Just path to directory: S3://bucket-name/prefix/ 
* Notification Recipeints: Multiple email ids separated with ',' are allowed.

DB - DB
Notebook / Service name: DB-DB
Functionality: Transfers data between database tables. Can be within same database or different database

Notebook Widgets Input guide
Source DB: Source database type, can be selected from dropdown.
Source DB Access: Valid DB access name defined in configs notebook.
Source DB Table: Target table name with pattern: schema.table_name
DML : SQL query can be input to get required data. If left blank, SELECT * FROM Source DB Table will be used
Target DB: Target database type, can be selected from dropdown
Target DB Access: Valid DB access name defined in configs notebook
Target DB Table: Target table name with pattern: schema.table_name
Load Type: Append mode by default, can be changed to Overwrite using dropdown option
Notification Recipeints: Multiple email ids separated with ',' are allowed.

User Guide: https://databricks-prod-cloudfront.cloud.databricks.com/public/4027ec902e239c93eaaa8714f173bcfc/3117515145466176/2105701564358663/2802065411328882/latest.html
