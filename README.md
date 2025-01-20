# Analytics-data-lake
This repository contains a Python script for Automating Sports Analytics(NBA) Data Lake using AWS services. The script integrates  Amazon S3, AWS Glue, and Amazon Athena for streamlining data ingestion, processing, querying and enabling faster insights from large datasets.

# Architectural Diagram
![Analyticsdatalake drawio](https://github.com/user-attachments/assets/2321cd1f-7a78-45c1-b558-96019f5c7984)


# Overview
The Fucntionality of nba_data_lake_setup.py script includes:
- Creates an Amazon S3 Bucket where raw and processed NBA data will be stored.
- Uploads NBA Data to S3 in JSON Format.
- Creates an AWS Glue database and an external table for querying the data.
- Configures Athena for quering data in the S3 Bucket.

# Prerequisites
1.  SportsDataIO Account and API Key.
- Create an account on SportsData.io.
- Navigate to Developers. Click on Introduction and Testing, Select SportsDataIO API Free Trial.
- Complete the Free Trial Form and Select NBA as the Product.
- Open the Confirmation Link Sent to your Email and Click on Launch Developer Portal.
- Navigate to NBA in the Sports panel, Scroll down to Standings section to View your API Key in the drop down box under Query String Parameters.
- Copy and keep your API KEY safe as it will be needed in the Python Script.
   
2.   IAM Permissions for User - Attach Neccessary Permissions to User or Role running the Script.
- Amazon S3 Permissions:
  - s3:CreateBucket
  - s3:PutObject
  - s3:DeleteBucket
  - s3:ListBucket
- AWS Glue Permissions:
  - glue:CreateDatabase
  - glue:CreateTable
  - glue:DeleteDatabase
  - glue:DeleteTable
- AWS Athena Permissions:
  - athena:StartQueryExecution
  - athena:GetQueryResults

 # Project Setup and Installation
 
Step 1: Open CloudShell
- Sign into your AWS Account and open CloudShell.


Step 2: Create the Script file.
- In the CloudShell, create the script file using the command and Press Enter.

      nano nba_data_lake_setup.py

- Paste the python code in the source code folder, Save and Exit.

  
Step 2: Create .env file.

- In the CloudShell, create the env file using the command and Press Enter.

      nano .env

- Paste the variables into the file, Save and Exit. #Replace your_sportsdata_api_key with your API key.

      SPORTS_DATA_API_KEY=your_sportsdata_api_key  
      NBA_ENDPOINT=https://api.sportsdata.io/v3/nba/scores/json/Players
  
- Echo the .env file into .gitignore to avoid exposing your API KEY.

       echo ".env/" >> .gitignore


Step 3: Create the Script file.



    

