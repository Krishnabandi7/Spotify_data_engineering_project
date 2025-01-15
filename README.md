# Spotify_data_engineering_project

Archetecture Diagram
![Screenshot 2025-01-15 144920](https://github.com/user-attachments/assets/b3820428-f0b2-438a-9fc7-f4fdeb8177b4)


1. Create an S3 Bucket with Subfolders (Staging and Warehouse):
Open the AWS Management Console.
Navigate to S3 and create a new bucket (e.g., spotify-data-pipeline).
Inside the bucket, create two folders:
staging: To store raw data.
warehouse: To store transformed and processed data.
2. Create an IAM Role (spotify-music) with Full Access:
Go to the IAM service.
Create a role and choose AWS service > Glue as the use case.
Attach the following policies:
AmazonS3FullAccess
AWSGlueServiceRole
AmazonAthenaFullAccess
Name the role (e.g., spotify-music-role) and save it.
3. Create an ETL Job (Visual ETL) in AWS Glue:
Navigate to the AWS Glue Studio.
Create a new visual ETL job:
![Screenshot 2025-01-15 150703](https://github.com/user-attachments/assets/7a9ebe8f-b209-454d-b8a4-de9548c42307)

Add S3 bucket (staging) as the source.
Perform transformations (e.g., joining, filtering, dropping fields).
Set the S3 bucket (warehouse) as the target.
Assign the IAM Role created earlier.
Save and run the job.
5. Create an AWS Glue Crawler:
Go to the AWS Glue Console and create a new crawler:
Data source: S3 bucket (warehouse).
IAM Role: Use the spotify-music-role.
Run the crawler to populate the schema in the Glue Data Catalog.
6. Create a Database (Spotify):
In the AWS Glue Console, create a new database named spotify.
Associate this database with the crawler during configuration.
Ensure permissions are set for the IAM Role to access the database.
7. Run the Glue Crawler:
Start the crawler to scan the data and populate the spotify database.
Verify that the tables and metadata are added to the Glue Data Catalog.
8. Set Up Amazon Athena:
Navigate to Amazon Athena.
Configure a query result location by specifying a new S3 bucket (e.g., spotify-athena-results).
Use the spotify database to run SQL queries like:
SELECT * FROM tracks LIMIT 10;
SELECT album, COUNT(*) FROM tracks GROUP BY album;
Verify that query results are saved to the specified S3 bucket.
9. Create Visualizations in QuickSight:
   ![Screenshot 2025-01-15 151433](https://github.com/user-attachments/assets/b559065a-e480-414a-97db-202d59d1fdfe)

Open Amazon QuickSight and create a new dataset.
Connect QuickSight to Athena and select the spotify database.
Import tables and build basic visualizations, such as:
Bar charts showing track counts by album.
Pie charts visualizing artist contribution.
Share insights via dashboards.

![image](https://github.com/user-attachments/assets/e57490d9-18dd-4170-91c7-770c8996cf15)


![image](https://github.com/user-attachments/assets/00f98f37-b870-48e6-b809-f575bfb7b5e0)


![image](https://github.com/user-attachments/assets/d5a0715b-b5a7-442e-a190-cf2716239bf7)

![image](https://github.com/user-attachments/assets/82aefcdf-9988-4bc8-a147-5c154373cf4d)



