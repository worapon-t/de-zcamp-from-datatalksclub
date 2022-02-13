## WEEK 3
> This week, we learn about data warehouse and What is Google BigQuery?.
> Link on week3 > https://github.com/DataTalksClub/data-engineering-zoomcamp/tree/main/week_3_data_warehouse

1. What is BigQuery?  
    -  Google BigQuery is a data warehouse service on Google Cloud Platform, it is the SaaS (Software as a service), we don't need to take care the service and server.
2. Partitioning & Clustering
    - Partitioning - the partition help to reduce the cost when we process the data on BigQuery and improve the performance when query. 
        - Partition by date
        - Partition by timestamp
        - Partition by integer
    - Clustering - the cluster help to reduce cost and improve the performance same the partition but the cluster build on top of Partition.
        - Cluster on fields
3. Internal in BigQuery - https://www.youtube.com/watch?v=eduHi1inM4s&feature=youtu.be
4. BQML
    - BigQuery Machine Learning - you can run the create the model on BigQuery service.
    - How to deploy the model - https://www.youtube.com/watch?v=BjARzEWaznU&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb&index=31
5. Workshop create the partition table via Airflow
        