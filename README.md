# Analytics Data Lake
This repository contains a Python script for Automating Sports Analytics(NBA) Data Lake using AWS services. The script integrates  Amazon S3, AWS Glue, and Amazon Athena for streamlining data ingestion, processing, querying and enabling faster insights from large datasets.

# Architectural Diagram
![Analyticsdatalake drawio](https://github.com/user-attachments/assets/2321cd1f-7a78-45c1-b558-96019f5c7984)


# Overview
The Fucntionality of nba_data_lake_setup.py script includes:
- Creates an Amazon S3 Bucket where raw and processed NBA data will be stored.
- Uploads NBA Data to S3 in JSON Format.
- Creates an AWS Glue database and an external table for querying the data.
- Configures Athena for querying data in the S3 Bucket.

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

- Copy the python code in the source code folder and Paste in the Text Editor, Save and Exit the text editor.

  
Step 2: Create .env file.

- Create the env file using the command and Press Enter.

      nano .env

- Paste the variables into the file, Save and Exit. #Replace your_sportsdata_api_key with your API key.

      SPORTS_DATA_API_KEY=your_sportsdata_api_key  
      NBA_ENDPOINT=https://api.sportsdata.io/v3/nba/scores/json/Players
  
- Echo the .env file to .gitignore to avoid exposing your API KEY.

       echo ".env/" >> .gitignore


Step 3: Create a Requirement file to specify the dependencies. (library and Packages needed - boto3, requests and python-dotenv)

-Create requirements.txt file and Press Enter.

      nano requirements.txt

- Paste the dependencies needed to run the project, Save and Exit the text editor.

      boto3==1.26.137
      requests==2.28.2
      python-dotenv==1.0.0
  
Step 4: Create a Virtual environment for the Python project.

- Run the commmand to create an isolated environment for the Python project:

      python -m venv venv
  
- Activate the Virtual environamnet by running the command: 

      source venv/bin/activate

- Echo the Virtual environament to .gitignore to ensure that the virtual environment directory is not tracked by Git.

        echo "venv" >> .gitignore

Step 5: Install the Dependencies.

- Run the commmand to Install the required Packages: 

      pip install -r requirements.txt
  
Step 6: Run the Python Script.

- In the CLI, type the command to Run the Python Script:

        python3 nba_data_lake_setup.py

Step 7:  Verify the Resources created.

- Verify Amazon S3 Bucket Creation:
  - In the AWS Management Console search bar, Type S3 and click on it.
  - Confirm if the Bucket with the preferred unique name has been created and Click on the bucket.
    
- Inspect the Objects in the Amazon S3 Bucket:
  - Click on the Bucket and Verify the Objects stored in the Bucket (There should be 2 Objects named Athena Results and Raw Data).
  - Click on the Raw Data Object and verify the file with the JSON Format.
  - Click on the File in the JSON Format and Open the file.
  - Choose an Application to View the file (i.e Visual Studio Code). You'll see a long string of NBA Data.
      
- Launch Amazon Athena to Query Data stored in S3:
  -  In the AWS Management Console search bar, Type Athena and click on it.
  -  Navigate to Launch Query Editor.
  -  In the Query Editor, Paste a Sample Query Below (The provided SQL query retrieves a list of players from the nba_players table who play the position of point guard 'PG').

            SELECT FirstName, LastName, Position, Team
            FROM nba_players
            WHERE Position = 'PG';
     
  - Click Run to execute the Query
  - Scroll down to View the Query Result.

## Bonus Step: If you are interested in cleaning up and preventing incurring unneccesary cloud costs:
- In the CloudShell, create the script file using the command and Press Enter.

      nano delete_aws_resources.py

- Copy the code in the delete aws resources folder and Paste in the text editor, Save and Exit the text editor.
- Run the code. This will delete all resources.

      python3 delete_aws_resources.py


  





    

