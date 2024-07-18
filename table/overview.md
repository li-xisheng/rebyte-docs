## What is a Table?

> Handle structured data for your assistant.

Table is a virtual database that represents a read-only view to your original data source. The original data source can be a csv, Excel, postgres, mysql, parquet, JSON, sqlite, snowflake, s3, bigquery etc.

**Table** has the following characteristics:
* **Read-only**: Table is a read-only view to your original data source, which means rebyte never writes to your original data source.
* **Partial View**: you can select a subset of columns and rows from your original data source to create a table. For example, you can hide sensitive columns, or filter out rows that are not relevant to your assistant. **This means you never need to alter your original data source**.
* **Transient**: Table is transient, which means it's not persisted in rebyte's database, it's only available during the execution of the tool. This is to ensure that your data is secure and private.

## Table Lifecycle
1. **Build Table**: two things need to be specified when building a table:
    * **Data Source**: the original data source, such as a csv file, a database table, etc.
    * **View**: how to map the original data source to the table, such as selecting columns, filtering rows, etc.
2. You can build a **tool** to enable a natural language query to table. Here are three steps:
    * **Load table action**: Load the table data into memory, and output a complete table schema. 
    * **LLM action**: combine the table schema with the natural language query to generate an SQL query. You can use any LLM. In the future, we will provide a specialized model for just outputting SQL queries. 
    * **Query table action**: search the table with the generated SQL query, and output the result.

## Important Notes
* **Data Security**: Table is transient, which means it's not persisted in rebyte's database, it's only available during the execution of the tool. But tool run logs may contain the table data, tool run logs are stored in rebyte's database, so be careful when using sensitive data in the table. 
* **Table Size**: Currently we don't have a limit on the table size, from our experience, a table with 1M rows and 10 columns can be processed in a few seconds.
* **Maximum Rows Per Query**: Only the first 1024 rows are returned in the query table action, this is to prevent the assistant from returning too much data. If you see error, try to use a more specific query, or set a LIMIT in the SQL query. 