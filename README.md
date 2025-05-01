### Astro-Airflow
The Astro CLI is the command line interface for data orchestration. It's the easiest way to get started with Apache Airflow and can be used with all Astronomer products `https://www.astronomer.io/docs/astro/cli/overview`. The project utilizes container technology a.k.a `docker` to build the project and deploy it to kubernetes after a series of testing locally with `minio` a.k.a `AWS S3` and `Spark`
### Project Implementation Steps
The project design incorporates different steps when using the `Yahoo Finance API`
- `is_api_available` -> 
- `get_stock_prices` ->
- `store_prices` -> 
- `format_prices` ->
- `get_formatted_prices` -> 
#### Dependencies
- Install  Astro CLI for your operating system `brew install astro` and check version `astro version`
- Initialize the Astro development environment for Airflow `astro dev init`
- Docker download the necessary packages for Airflow with the start command `astro dev start`
- `NOTE:` If Port is taken -> List running processes `sudo lsof -i :PORT` then kill the process `kill -9 PID` OR `sudo kill -9 PID`
- To `stop`, `restart` and `kill` when testing -> `astro dev stop`, `astro dev restart` and `astro dev kill` respectively
- Access to the Airflow Cli command `astro dev bash` OR use this command for docker `docker exec -it CONTAINER_IMAGE /bin/bash`
### Project Environment Config
- Build the DockerFile for the Spark Master `docker build -t airflow/spark-master . `
- Build the docker image for the Spark Worker `docker build -t airflow/spark-worker .`
- Build the docker container for Spark from the notebooks/stock_transform folder `docker build -t airflow/stock-app .`
#### Test DAG
- Run to test the API call `astro dev run tasks test stock_market is_available 2025-01-01`
- Run to test DAG `astro dev run dags test stock_market 2025-01-01`
- For any updates - restart the environment `astro dev restart` 
