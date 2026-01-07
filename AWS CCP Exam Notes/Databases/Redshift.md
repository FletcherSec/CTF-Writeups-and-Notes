- Redshift is based on PostgreSQL, but its not used for [[OLTP]]
- Its [[OLAP]] - online analytical processing (used for analytics and data warehousing)
- Load data once every hour, not every second
- 10x better performance than other data warehouses, scales to PBs of data
- Columnar storage of data (instead of row based)
- Massively Parallel Query Execution (MPP), highly available
- Pay as you go based on the instances provisioned
- Has a SQL interface for performing the queries
- Integrated with BI tools such as AWS [[Quicksight]] or [[Tableau]]

##### Redshift Serverless
- Automatically provisions and scales data warehouse underlying capacity
- Run analytics workloads without managing data warehouse infrastructure
- Pay only for what you use (save costs) 
- Use cases: Reporting, dashboarding applications, realtime analytics