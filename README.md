# ADF Dax Extractor

Power Query has become the de facto standard for data engineering tasks performed by power users. With Power Query, users can easily combine data from dozens of sources and quickly produce the outcomes they need. Behind the scenes, they are effectively building data pipelines.

With the rise of Power BI, this approach has accelerated. Many organizations now have Power BI models that serve as a single source of truth. Increasingly, key users will point to a published Power BI report and say, “the data you need is there.”

In environments without Microsoft Fabric, this means you need to extract data from a semantic model and feed it into the next stage of your data pipeline.

This Azure Data Factory (ADF) project leverages the Power BI executeDaxQueries API to run DAX queries on published Power BI semantic models and write the resulting JSON output to a storage account for further processing.

The connection is established using a service principal (Azure Entra App) and all secrets (such as the Power BI tenant ID, semantic model ID, app secret, etc.) are securely stored in Azure Key Vault, outside of ADF itself.

This project is reusable and ideal whenever you need to extract data from published semantic models without having to reinvent the wheel.

![image](https://github.com/user-attachments/assets/e4ca6bd7-58d0-4d50-bf28-55baa2461d3f)
