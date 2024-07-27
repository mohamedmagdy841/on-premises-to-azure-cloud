# Cloud Transformation: Migrating Data from On-Premises to Azure

## Project Description

This project demonstrates an end-to-end data engineering workflow using various Azure services. By ingesting tables from an on-premise SQL Server database using Azure Data Factory and storing the data in Azure Data Lake. The storage container contains three layers: bronze, silver, and gold. Azure Databricks is used to transform the raw data (bronze) to cleaned data (silver) to the cleanest form of data (gold). Azure Synapse Analytics is then used to load the cleaned data, and finally, Microsoft Power BI is used to integrate with Azure Synapse Analytics to build an interactive dashboard. Microsoft Entra ID and Azure Key Vault are used for monitoring and governance purposes.

## Architecture

<p align="center">
  <img width="900" src="https://github.com/user-attachments/assets/cab51914-57c7-411d-b601-0cd8a3d6efa7">
</p>

## Data Sources

The primary data source for this project is the AdventureWorksLT2017 sample dataset from Microsoft, a lightweight version of the AdventureWorks database. It simulates a retail business scenario with various tables capturing customer information, product details, and sales orders.

Key tables include:
- **Customer**: Customer profiles and demographics.
- **SalesOrderHeader**: Summary of sales orders.
- **SalesOrderDetail**: Details of individual sales order items.
- **Product**: Product details and inventory status.
- **ProductCategory**: Product categorization.

Data is ingested from the on-premise [AdventureWorksLT2017](https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver16&tabs=ssms) SQL Server database.

<p align="center">
  <img width="900" src="https://github.com/user-attachments/assets/ccb668d2-30bf-4a59-ac02-b6d928f5850f">
</p>

## Technologies Used

- **Azure Data Factory**: For data ingestion from on-premise SQL Server.
- **Azure Data Lake Storage Gen2**: For storing data in bronze, silver, and gold layers.
- **Azure Databricks**: For data transformation.
- **Azure Synapse Analytics**: For data loading and further processing.
- **Microsoft Power BI**: For data visualization and creating interactive dashboards.
- **Azure Key Vault**: For securing sensitive information.
- **Microsoft Entra ID**: For identity and access management.

## Setup and Configuration

To set up and configure the necessary components:

1. **Create a Resource Group**: Organize all Azure services within a single resource group.
2. **Azure Data Factory**: Create an instance and configure a self-hosted integration runtime for secure data movement.
3. **Azure Data Lake Storage Gen2**: Set up an account and create containers for bronze, silver, and gold data layers.
4. **Azure Databricks**: Deploy a workspace, configure clusters, and create notebooks for data transformation.
5. **Azure Synapse Analytics**: Create a workspace and set up dedicated SQL pools.
6. **Azure Key Vault**: Store and manage secrets securely.
7. **Microsoft Entra ID**: Configure identity and access management.
8. **Microsoft Power BI**: Connect to Azure Synapse Analytics and build interactive dashboards.

<p align="center">
  <img width="900" src="https://github.com/user-attachments/assets/c06ab6d0-c597-4ce3-87a5-c68dafb33c5f">
</p>

## Data Ingestion

The data ingestion process involves connecting the on-premise SQL Server database to Azure Data Factory and copying all the data to Azure Data Lake Storage Gen2. The steps are as follows:

1. **Set Up Integration Runtime**: Install a self-hosted integration runtime to enable secure data movement.
2. **Create Linked Services**: Connect to both the on-premise SQL Server and Azure Data Lake Storage Gen2.
3. **Define Data Sets**: Represent the structure and location of the source and destination data.
4. **Build Data Pipelines**: Orchestrate data movement with copy activities and schedule triggers.
5. **Monitor and Manage**: Track progress, performance, and handle issues using Azure Data Factory's monitoring features.

<p align="center">
  <img width="900" src="https://github.com/user-attachments/assets/b531c931-1db3-4e8c-ad45-bd50d1be50ab">
</p>

## Data Storage

Data is stored in Azure Data Lake Storage Gen2, organized into three layers:

1. **Bronze Layer**: Raw, unprocessed data copied from the on-premise SQL Server. This layer acts as a landing zone for initial data storage.
2. **Silver Layer**: Data transformed and cleaned from the bronze layer. This stage includes basic processing to make the data more usable.
3. **Gold Layer**: The final, most refined data. This layer contains data that has been thoroughly cleaned and optimized for analysis and reporting.

<p align="center">
  <img width="900" src="https://github.com/user-attachments/assets/7ef8303c-30b3-4f03-ba92-84cf61471b4e">
</p>

## Data Processing

Data processing involves transforming raw data into a refined format:

1. **Bronze to Silver**:
   - **Transformation**: Convert columns such as `OrderDate`, `DueDate`, `ShipDate`, and `ModifiedDate` from string to date type to enhance data consistency and usability.

2. **Silver to Gold**:
   - **Transformation**: Rename certain columns by adding underscores to improve naming conventions and ensure clarity.

## Data Pipeline

<p align="center">
  <img width="900" src="https://github.com/user-attachments/assets/3c4d7f3e-205b-46dd-b419-8bfea7a94735">
</p>

## Data Visualization

In data visualization, the following charts were created:

1. **Bar Column Chart**: Displays total sales by product category, providing insights into sales performance across different product groups.
2. **Pie Chart**: Shows gender classification by job title, illustrating the distribution of genders within various roles.

<p align="center">
  <img width="900" src="https://github.com/user-attachments/assets/c78fb9e6-c6da-487d-8ebd-745aee6fa791">
</p>
