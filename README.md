# End-To-End-Data-Engineering-Project  (Azure Data Factory, Azure SQL Database, Azure Databricks(Scala,Spark,SQL), Azure Synapse, Power BI, ADLS Gen 2)
Workspace_publish and adf_publish branches contains data from Data Factory, Databricks and Synapse

End-to-End Azure Data Engineering Project Summary
1. Environment Setup

    Resource Group: Created a centralized resource group medallion-spark-dbt-rg in the Sweden Central region.
    Azure Services Deployed:
        Azure Data Lake Gen2 (medallionsto) for storage.
        Azure Data Factory (medallionadf) for orchestration.
        Azure Databricks (medallionsparkdtbrcks) for data processing and transformation.
        Azure Key Vault (medallionsparkkey) for secure management of secrets and credentials.
        Azure SQL Database (medalliondb) and Azure SQL Server (medallion-srvr) for structured data storage.
        Azure Synapse Workspace (medallion-syn) for analytics.
        Power Bi for report building
   

2. Data Ingestion

    Data ingested from Azure SQL Database (AdventureWorksLT2017) into the Bronze Layer of the Azure Data Lake Gen2 in raw format.
    Azure Data Factory Pipelines:
        Configured pipelines to extract, load, and store raw data into the /bronze layer of the Data Lake.
        Automated scheduling and monitoring for consistent data ingestion.

3. Data Transformation

    Medallion Architecture:
        Data transformation in Databricks:
            Processed data from the Bronze Layer and stored clean, validated data in the Silver Layer at /mnt/silver/2024-12-03/.
            Applied necessary transformations (e.g., filtering, deduplication) to align with the predefined schemas for tables like SalesLT.Customer and SalesLT.Product.
        Stored transformed data in Parquet format for optimized querying and analytics.
    Integration: Databricks integrated with Azure Key Vault for secure credential handling.

4. Data Loading

    Loaded refined data from the Silver Layer into:
        The Gold Layer in the Data Lake for aggregated and analytics-ready data.
        Azure Synapse for further structured reporting and analysis.

5. Data Reporting

    Created interactive dashboards using Power BI:
        Connected to the Azure SQL Database and Gold Layer for visualization.
        Dashboards covered key business insights like customer demographics, product performance, and sales trends.

6. End-to-End Pipeline Testing

    Performed comprehensive testing for pipeline integrity:
        Validated data ingestion, transformation, and loading processes.
        Ensured data consistency across Bronze, Silver, and Gold layers.
        Tested the Power BI dashboards for accuracy and responsiveness.
    Automated and monitored the pipeline using Azure Data Factory triggers and logs.
