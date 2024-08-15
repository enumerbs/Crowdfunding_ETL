Data Analytics Boot Camp - Project 2 - Group 4

# Crowdfunding ETL

## Results

This project's source code and results are structured as follows:
- ***README.md*** (this file) provides an overview of the project folder structure, together with implementation notes and other details.
- ***ETL_Mini_Project_GPresneill.ipynb*** has the source code for the 'Crowdfunding ETL' data processing. This Jupyter Notebook was run to process the input data and analysis.
- ***crowdfunding_db_schema.sql*** contains the PostgreSQL SQL script for creating the various database tables and their relationships. (Refer to the implementation notes below for more details.)
- ***crowdfunding_db_schema.png*** provides a Entity-Relationship Diagram corresponding to the above schema.
- ***Resources*** subfolder contains the:
    - supplied input data files (Excel spreadsheets) for this analysis, and
    - the CSV files generated from the analysis, that were then used to populate the corresponding PostgreSQL database tables.
- ***select.queries*** subfolder contains:
    - ***crowdfunding_db.sql*** file contains PostgreSQL query statements for selecting the data from each table
    - corresponding screenshots of the final SQL queries run in pgAdmin4 to verify the database creation/table contents, namely:
        - Campaign.jpg
        - Contact.jpg
        - Category.jpg
        - Subcategory.jpg

## Implementation notes

Jupyter Notebook - section 'Create the Contacts DataFrame'
- We found we needed to use `header=3` parameter in order to read the data file correctly. (The starter code comment suggested `header=2` but the actual Excel file had 3 rows above the data table.)


Create the Crowdfunding Database - QuickDBD
- We inspected the 4 CSV files (output from the Jupyter Notebook analysis) and created an Entity-Relationship Diagram (ERD) using QuickDBD.
- The ERD included definition of Postgres-compatible data types, and table relationships including primary and foreign key constraints.
- QuickDBD was then used to export the design as:
    - a Postgres-compatible SQL script (***crowdfunding_db_schema.sql***)
    - a corresponding ERD diagram image (***crowdfunding_db_schema.png***)

Create the Crowdfunding Database - Postgres
- pgAdmin4 was used to create the ***crowdfunding_db*** Postgres database.
- The 'Query Tool' was then used to run the table creation script (that is, the contents of our ***crowdfunding_db_schema.sql*** file).
- We then right-clicked on each table name and ran the 'Import/Export Data' option to select each individual CSV file from our ***Resources*** folder, taking care to load the files in an appropriate order according to the table relationships. For example, one possible load order is:
    1. Subcategory.csv
    1. Category.csv
    1. Contact.csv
    1. Campaign.csv
