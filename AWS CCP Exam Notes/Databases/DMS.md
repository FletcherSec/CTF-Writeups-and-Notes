- Stands for Database Migration Service
- Quickly and securely migrate databases to AWS, resilient and self healing
- The source database remains available during the migration

Source DB -> [[EC2]] running [[DMS]] -> Target DB

- Supports:
	- Homogeneous migrations: example: Oracle to Oracle
	- Heterogeneous migrations: example: Microsoft SQL Server to [[Aurora]]