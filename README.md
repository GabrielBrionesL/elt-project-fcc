# ELT Project
This repository contains a custom Extract, Load, Transform (ELT) project that utilizes Docker and PostgreSQL to demonstrate a simple ELT process.

## Repository Structure
1. docker-compose.yaml: This file contains the configuration for Docker Compose, which is used to orchestrate Docker containers. It defines:
  - `source_postgres`: The source PostgreSQL database
  - `destination_postgres`: The destiantion POstgreSQL database
  - `elt_script1`: The service that runs the ELT script
2. elt_script: This folder contains the Dockerfile that sets up a Python environment and installs PostgreSQL. This folder also includes the Python script that performs the ELT process.
3. source_dbt_init: This folder contains the SQL script that initializes the source databse with sample data.

## How It Works
- Docker Compose: Using the `docker-compose.yaml` file, three Docker containers are launched:
  - A source PostgreSQL database with sample data.
  - A destination PostgreSQL database.
  - A Python environment executing the ELT script.
- ELT Process: The `elt_script.py` script waits for the source PostgreSQL database to be available, then uses `pg_dump` to export the source database to a SQL file. It then employs `psql` to load this SQL file into the destination PostgreSQL database.
- Database Initialization: The `init.sql` script initializes the source database with sample data, creating tables and populating them with sample data.
