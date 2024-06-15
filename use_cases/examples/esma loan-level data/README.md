# Example use case: ESMA loan-level data

This folder contains an example of our Regulatory Reporting solution, built around the reporting requirements
for Corporate loans, as published by ESMA on 3 September 2020, as part of the disclousre requirements under article 7 of Regulation (EU) 2017/2402. 
[RTS] https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:32020R1224
[ITS] https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:32020R1225

ESMA sets out disclosure requirements for all types of securitisations including details of the structure of the securitisation transaction, of the underlying exposures and of the performance of the transaction. 

This example contains the following folders: 
* `data_generator`: contains a simple containerised application that generates sample data
* `dbt`: contains a DBT project which specifies the source to report transformation
* `deploy`: an Airflow DAG that uploads the sample data and transforms it using DBT

# Pre-requisites
Make sure that you have followed the instructions in the [tutorial](../../../docs/TUTORIAL.md) to create the 
GCP infrastructure via Terraform.

# How to execute the demo
You can use the convenience script `run_demo.sh` to execute the demo.
```
./run_demo.sh
```
The script will do the following:
* Inialise the environment variables
* Create a containerised data generator application
* Create a containerised data transformation application
* Submit the DAG to Composer

## How to tailor the code to your need
If you wish to use this solution in a real implementation, you may want to start by tailoring the following files to 
your needs:
* `dbt/models/schema/yml`: moodify the sources to align to your data
* `dbt/models/src`: moodify the files in this folder to implement a mapping logic from your data into these structures
