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

User Guide: https://databricks-prod-cloudfront.cloud.databricks.com/public/4027ec902e239c93eaaa8714f173bcfc/3117515145466176/2105701564358663/2802065411328882/latest.html
