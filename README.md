# Custom ELT Pipeline with Airflow

This project demonstrates a containerized Extract, Load, Transform (ELT) pipeline using **Docker**, **PostgreSQL**, **Python**, and **Apache Airflow**. It automates the process of moving and transforming data between databases while providing workflow orchestration.

## Technologies Used

- **Docker & Docker Compose** – Containerized services for reproducible environments  
- **PostgreSQL** – Source and destination databases  
- **Python** – ELT script for extraction, transformation, and loading  
- **Apache Airflow** – Workflow orchestration and scheduling  

## How It Works

1. **Docker Compose** spins up the following containers:
   - `source_postgres` – Source PostgreSQL database with sample data  
   - `destination_postgres` – Destination PostgreSQL database for transformed data  
   - `elt_script` – Runs the Python ELT script  
   - `airflow_webserver` & `airflow_scheduler` – Airflow services for orchestration

2. **Database Initialization**:
   - `init.sql` creates tables for users, films, film categories, actors, and film actors  
   - Populates the tables with sample data

3. **ELT Process**:
   - Waits for the source database to be ready  
   - Extracts data from the source database using `pg_dump`  
   - Loads data into the destination database using `psql`  
   - Applies transformations as needed

4. **Airflow Orchestration**:
   - DAGs define task dependencies and schedule automated runs of the ELT process  
   - Logs and task monitoring are available via the Airflow Web UI

Source PostgreSQL: localhost:5433

Destination PostgreSQL: localhost:5434

Airflow Web UI: localhost:8080

Run the ELT process:

ELT starts automatically via Airflow DAGs

Logs can be monitored in Airflow Web UI

Highlights
Containerized workflow automation with Docker

Integrated Airflow DAGs for scheduling and orchestration

Automated ELT process with Python and PostgreSQL

Easy to extend with additional data sources, transformations, or destinations
