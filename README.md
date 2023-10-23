# AZURE-END-TO-END-DATA-PIPELINE
## DATA INGESTION
So the initial stage of this project, my data was stored on Postgres on my local desktop, so that was my data source, and to bring the data into Azure cloud, I made use of Azure Data Factory for data ingestion, this step started the flow for our build up in the end to end data pipeline.
## DATA SOURCE
My data source was a local Postgres database hosted on my local computer, this database contained critical data sets necessary for our analytics and reporting objectives. Also to connect an on premise database to Azure cloud, you would need to have Microsoft Integrated Runtime installed on your PC.
## Azure Data Factory
Azure Data Factory is a cloud-based data integration service, was selected as the tool for this task, it is efficient to connect to various data sources, orchestrate data movement, and also facilitate data transformation.
## DATA INGESTION PROCESS
Connection Setup - I established a secure connection between Azure Data Factory and my local Postgres database with the help of Microsoft Integrated Services.
![Screenshot (14)](https://github.com/MijanScripts/AZURE-END-TO-END-DATA-PIPELINE/assets/69738470/0f85d942-8b4e-4be2-a47d-412a9133ab0e)
Data Extraction - I identified the specific database, tables  and data elements to be ingested
Data Movement - Azure Data Factory was used to transfer data from the Postgres database into Azure, ensuring data integrity and security.
Data Storage -  Data that was ingested into Azure was stored in a Azure Data Lake Gen 2, in a bronze container. We would go on to create silver and gold container.
 ![Screenshot (16)](https://github.com/MijanScripts/AZURE-END-TO-END-DATA-PIPELINE/assets/69738470/bc7bd24e-5f0f-4e3d-a2f4-c73c93023aa0)

## DATA PROCESSING WITH AZURE DATABRICKS
In the next step of my  data pipeline, I used Azure DataBricks to transform, refine and enrich the data that was originally ingested into the Azure Data Lake Gen2 bronze container. And we would go on to create the silver and gold containers, with distinct roles in the data processing.
## BRONZE LAYER:Storing Raw Data
The raw data from the local Postgres database was initially stored in the bronze container within Azure Data Lake Gen2. The Bronze layer serves as a repository for the raw, unprocessed and unaltered data source.
 ![Screenshot (13)](https://github.com/MijanScripts/AZURE-END-TO-END-DATA-PIPELINE/assets/69738470/5f9938d7-6bf8-4c6d-ab64-a31e0a6e26aa)
## SILVER LAYER: Data Transformations
Azure DataBricks was used in creating the silver container, Data from the bronze container was processed in the silver layer, and this phase involved data cleaning, removing and replacing null values, removing redundant data elements and transformations. 
All of these data manipulation was done in DataBricks using Pyspark, the processed data in the silver layer represents an intermediate state where data is refined for further analysis.
![Screenshot (18)](https://github.com/MijanScripts/AZURE-END-TO-END-DATA-PIPELINE/assets/69738470/19538d5e-6f12-4201-aa24-754c35ef72fa)
## GOLD LAYER: Clean and Final Data for Reporting
I created the Gold container to store the clean and final data that is intended for reporting and visualization. And reporting and visualization is done with Azure synapse and Power BI
![Screenshot (19)](https://github.com/MijanScripts/AZURE-END-TO-END-DATA-PIPELINE/assets/69738470/7ab92d13-4473-499c-880a-1b48aa126356)

## DATA REPORTING AND VISUALIZATION
## Azure Synapse Azure 
Synapse offers a comprehensive environment for data explorationand ad-hoc querying, and it is the analytics and data warehouse used to interact with the gold layer. 
And with the help of azure I moved data into azure synapse data warehouse and created views that I needed for reporting and to create my visualizations. 
![Screenshot (23)](https://github.com/MijanScripts/AZURE-END-TO-END-DATA-PIPELINE/assets/69738470/544c7022-d130-470e-8154-fe4aeb8aa816)
## Power BI
Microsoft Power BI, the desktop version was the choice tool for my visualization and it has Azure Synapse as one of its data sources to extract data for visualization.
## AUTOMATION
Now one of the important skills of a Data Engineer is the ability to automate processes, and reducing human input and increasing work efficiency. So after creating our end to end pipeline, we had to automate it so that when new data is added, it would be ingested, the data would be processed and moved through all layers, and then would also be visualized.
And we used Data Factory for scheduling our pipeline to run midnight everyday, you could schedule as much as you want and for it to run as frequently as you like too.
![Screenshot (34)](https://github.com/MijanScripts/AZURE-END-TO-END-DATA-PIPELINE/assets/69738470/ba94ce22-cf8a-4ec8-83e0-734727412fde)

## DATA GOVERNANCE AND SECURITY
Azure Active Directory and Key Vaults were used for data security and governance, I made use of Secrets in Key Vault to hide important information like database passwords and tokens. Used Azure Active Directory to grant User roles to groups. 






