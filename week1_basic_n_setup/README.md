# 1st Week
> This link for the 1st week > https://github.com/DataTalksClub/data-engineering-zoomcamp/tree/main/week_1_basics_n_setup

1. Docker and Load data
    1. Learn about the Docker
        - run Ubuntu on Docker
        - run Python on Docker
    2. How to run PostgreSQL on the Docker & Load Data to PostgreSQL
        - run PostgreSQL on Docker
            ```
            docker run -it -e POSTGRES_USER="root" -e POSTGRES_PASSWORD="root" -e POSTGRES_DB="ny_taxi" -v {PATH-OF-FILE}\ny_taxi_postgres_data:/var/lib/postgresql/data -p 5432:5432 postgres:13
            ```
        - use pgcli for connect to PostgreSQL
            ```
            pip install pgcli
            ```

            ```
            pgcli -h localhost -p 5432 -u root -d ny_taxi
            ```
        - Load the data to PostgreSQL
            - About Data ny_taxi > https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page

    3. How to use the pgAdmin via Docker for connect to the PostgreSQL
        ```
        docker network create pg-network
        ```
        We need create the network on docker for create the connection between dockers
        ```
        docker run -it -e PGADMIN_DEFAULT_EMAIL="admin@admin.com" -e PGADMIN_DEFAULT_PASSWORD="root" -p 8080:80 --network=pg-network --name pgadmin dpage/pgadmin4
        ```
        > Remark: Should rerun the PostgreSQL docker script with the --network flag and after we used the network, we can reference the service name from --name flag. 

    4. Final script on 1st week
        - ingest_data script run on Docker
            > This script for convert jupyter notebook to python script
            ```
            jupyter nbconvert --to=script upload-data.ipynb
            ```
            ```
            docker build -t taxi_ingest:v001 .
            ```
            
        - Use the docker compose for run PostgreSQL & pgAdmin
            ```
            docker-compose up -d
            ```
        - Load yellow_taxi_data and zone to PostgreSQL
            Check your docker network first
            ```
            docker network ls
            ```
            ```
            docker run -it --network={network} taxi_ingest:v001 --user=root --password=root --host=pgdatabase --port=5432 --db=ny_taxi --table_name=zone --url=https://s3.amazonaws.com/nyc-tlc/misc/taxi+_zone_lookup.csv
            ```
            ```
            docker run -it --network={network} taxi_ingest:v001 --user=root --password=root --host=pgdatabase --port=5432 --db=ny_taxi --table_name=yellow_taxi_trips --url=https://s3.amazonaws.com/nyc-tlc/trip+data/yellow_tripdata_2021-01.csv
            ```
    5. SQL refresher

2. GCP & Terraform