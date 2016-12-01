Intro to managed dbs in aws
---
* relational
* big data and integration
* no sql
* some fourth one
* managed db allows you to avoid time sink of maintaining dbs
* relational
  * rds
  * no infra to manage
  * application compatibility
  * instant provisioning
  * cost effective
  * lots of types (postgres, mysql, etc)
* RDS for Aurora
  * mysql compatible with 5x better performance on the same hardware
  * scalable up to 64 TB in single db, up to 15 read replicas
  * highly available, durable and fault tolerant custom SSD storage layer: 6 way replicated across 3 AZs
  * transparent encryption for data at rest using AWS KMS
  * one last bullet i didnt get
  * supports postgres now as well as mysql
* Database conversion capabilities with amazon database migration service
  * mssql -> amazon aurora, mysql, postgresSQL
* relational dbs optimized storage
* nosql optimized for compute
* dynamodb - non-relational managed nosql database service
  * no limit on how much data - 4-6ms regardless of amount of data
  * cost modeled on througput and size
  * no throughput limit
  * no storage limit
  * automatically partitions data
  * always deployed in three availability zones, it is always clustered
* elasticache
  * in memory key value store
  * high performance
  * redis and memchaced
  * fully managed; zero admin
  * highly available and reliable
  * hardened by Amazon
  * 400 microseconds response
  * limit is 3.4 TB
  * can take snapshots for recovery
* Amazon Redshift
  * relational data warehouse - a lot faster, simpler, cheaper
  * massively parallel; petabyte scale
  * fully managed
  * HDD and SSD platforms
  * real-time data ingested by amazon kinesis is analyzed in amazon redshift and they use tableau
* Amazon Elasticsearch Service
  * distrubuted seach and analytics engine
  * managed service using ES and kibana
  * fully managed; zero admin
  * highly available and reliable
  * tightly integrayed with other aws services
  * used often for logs aggregation, like cloudwatch and cloudtrail, centralized logging, might be cool for us
* Amazon EMR
  * managed platform
  * mapreduce, apache spark, presto
  * launch cluster in minutes
  * hadoop clusters
  * storage with S3, HDFS, or MapR
  * leverage elasticity of the cloud
  * baked in security
  * pay by hour and save with Spot
  * flexibility to customize

