ETL Pipeline Implementation
===========================

ETL Pipeline Implementation using Apache Airflow,Astronomer,PostgreSQL and Open Meteo API. This project employs these technologies to implement an Extract-transform-Load Pipeline to extract weather data using Open Meteo API,Transform the data and then Load the data into a PostgreSQL database. Then using Apache Airflow, we implement DAGs so that the data can be extracted automatically on a regular basis(hourly,daily,weekly,etc.).

Overview
========

Clone the repository using git clone function. Then Install the astro CLI using winget on windows,brew on mac or curl on linux. Then restart the IDE after successfull astro CLI installation. check if installed correctly or not by typing 'astro version'. Open docker desktop and keep it running. use the command 'astro dev start' to create the airflow. Airflow login page will open at localhost:8080/home. The default UserID and password are 'admin' and 'admin' respectively. 'weather_etl-pipeline' DAG will be shown there. click on it. click on Run button to start the DAG. Green Colour implies running successfully. The weather data will be stored in a postgreSQL database. to access it,download 'dbeaver; software. After installing it,open the software and Go to database>New database Connection>PostgreSQL and enter the details. The host will be localhost. ID and password will be both 'postgres' by default. Click on test Connection. After that click on Finish. Now to see the data from the database, Go to SQL Editor>Go to SQL Script. write the command 'select * from weather_data' and click ctrl+Enter. It will displayed all the data captured till now. Currently, the weather data is captured for 'Patna,bihar'. If you want to get the weather data for a different location,change the LATITUDE AND LONGITUDE in the etlweather.py file under dags folder.

Project Contents
================

Your Astro project contains the following files and folders:

- dags: This folder contains the Python files for your Airflow DAGs. By default, this directory includes one example DAG:
    - `example_astronauts`: This DAG shows a simple ETL pipeline example that queries the list of astronauts currently in space from the Open Notify API and prints a statement for each astronaut. The DAG uses the TaskFlow API to define tasks in Python, and dynamic task mapping to dynamically print a statement for each astronaut. For more on how this DAG works, see our [Getting started tutorial](https://www.astronomer.io/docs/learn/get-started-with-airflow).
- Dockerfile: This file contains a versioned Astro Runtime Docker image that provides a differentiated Airflow experience. If you want to execute other commands or overrides at runtime, specify them here.
- include: This folder contains any additional files that you want to include as part of your project. It is empty by default.
- packages.txt: Install OS-level packages needed for your project by adding them to this file. It is empty by default.
- requirements.txt: Install Python packages needed for your project by adding them to this file. It is empty by default.
- plugins: Add custom or community plugins for your project to this file. It is empty by default.
- airflow_settings.yaml: Use this local-only file to specify Airflow Connections, Variables, and Pools instead of entering them in the Airflow UI as you develop DAGs in this project.

Deploy Your Project Locally
===========================

1. Start Airflow on your local machine by running 'astro dev start'.

This command will spin up 4 Docker containers on your machine, each for a different Airflow component:

- Postgres: Airflow's Metadata Database
- Webserver: The Airflow component responsible for rendering the Airflow UI
- Scheduler: The Airflow component responsible for monitoring and triggering tasks
- Triggerer: The Airflow component responsible for triggering deferred tasks

2. Verify that all 4 Docker containers were created by running 'docker ps'.

Note: Running 'astro dev start' will start your project with the Airflow Webserver exposed at port 8080 and Postgres exposed at port 5432. If you already have either of those ports allocated, you can either [stop your existing Docker containers or change the port](https://www.astronomer.io/docs/astro/cli/troubleshoot-locally#ports-are-not-available-for-my-local-airflow-webserver).

3. Access the Airflow UI for your local Airflow project. To do so, go to http://localhost:8080/ and log in with 'admin' for both your Username and Password.
