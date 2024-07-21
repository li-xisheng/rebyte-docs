## Create a Fraud Analysis Assistant

Background: You are a data scientist in a financial company, and you are responsible for building a fraud analysis assistant to help your team identify potential fraud cases. The assistant should be able to analyze transaction data and identify suspicious patterns.

What you will have:
* A csv file containing 100k transaction records. For your convenience, we have prepared a sample file for you. You can download it [here](https://storage.googleapis.com/cui-runtime/fraud1.csv), or [google spreadsheet link](https://docs.google.com/spreadsheets/d/1mY57k8zYkhCZo51XEydnplWRSu75KiOAhvolTE4IUpw/edit?gid=1496520613#gid=1496520613). Or you can import to google spreadsheet, Google will automatically convert it to csv format.
One benefit of using google spreadsheet is that you can edit the data directly, rebyte will automatically sync the data.

### Step 1: Create A Table in ReByte

This step involves creating a table in ReByte, you should choose the "csv" format, and upload the csv file, or paste your Google spreadsheet link.

You can explore the data by clicking the "Explore," and use any SQL query to filter the data.

let's say you finally have a table named "transaction" in ReByte.

### Step 2: Create A Fraud Analysis Tool
Create a new tool in ReByte, and name it "Fraud Analysis."
ReByte has prebuilt template for data analysis,
you can choose the "Data Analysis" template, and then you can modify it to fit your need.
**Remember** to change the table to the "transaction" table you created in step 1 in both the "load table" and "query table" actions.


**IMPORTANT**:
You should change the tool to point to load schema from the "transaction" table, also run SQL on the same table.
You probably want to change input dataset to reflect what you want to analyze.


### Step 3: Add 'Fraud Analysis' Tool to Your Assistant
Now you can add the "Fraud Analysis" tool to your team's assistant. 

Another way you can do is create a new assistant, specifically for fraud analysis, and add the "Fraud Analysis" tool to this assistant.


Party time! You have successfully built a fraud analysis assistant.

Now it's ready to use by your team members. 

Try querying the assistant with questions like:

* **Show me the top 10 transactions with the highest amount**

* **How many transactions are there in total? How many are fraudulent?**