- RDS stands for Relational Database Service
- Its a managed DB service for DB using SQL as a query language
- Suited for [[OLTP]]
- It allows you to create databases in the cloud that are managed by AWS
	- Postgres
	- MySQL
	- MariaDB
	- Oracle
	- Microsoft SQL Server
	- IBM DB2
	- Aurora (AWS Proprietary database)

##### Advantage of RDS over deploying DB on [[EC2]]
- RDS is a managed service:
	- Automated provisioning, OS patching
	- Continuous backups and restore to specific timestamp ([[Point in Time Restore]])
	- Monitoring Dashboards
	- [[Read Replicas]] for improved read performance
	- Multi AZ setup for Disaster Recovery
	- Maintenance windows for upgrades
	- Scaling capability (Vertical and horizontal)
	- Storage backed by [[EBS]]
	- **CANNOT** SSH into your instances

##### RDS Solution Architecture
![[Pasted image 20251228104232.png]]