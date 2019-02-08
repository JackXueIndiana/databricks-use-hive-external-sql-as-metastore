# databricks-use-hive-external-sql-as-metastore
This article is to show you how to connect Azure Databricks cluster to a HD Insight hive table which has its metadata stored in an Azure SQL Database.

The Azure Databricks cluster is the version of 5.0 (includes Apache Spark 2.4.0, Scala 2.11)

The Azure HD Insight Hadoop cluster is the version of Hadoop 2.7 (HDI 3.6)

We mainly followed these two documents:
1. Official guide: https://docs.azuredatabricks.net/user-guide/advanced/external-hive-metastore.html
2. Github resource: https://github.com/AdamPaternostro/Azure-Databricks-External-Hive-and-ADLS

Here is our steps:
1. Make sure that the HDI has Azure SQL DB as metastore and ADLS gen 1 as data repo
2. Mount the ADLS to the Databricks cluster
3. Edit the Databricks cluster's Spark Config (advanced) with the attached file.
4. Run the notebook and you should see the commends for %fs, %sql working as expected.

Be advised that currently there is a limitation: 
- All authentication info in the settings are NOT encrypted. 
- The SQL user needs to have read/write access to the db.
- Since the setting is for cluster, thus the passthrough in NOT in scope.
