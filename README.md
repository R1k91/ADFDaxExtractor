# ADF Dax Extractor

Power Query has become the de facto standard for data engineering tasks performed by power users. With Power Query, users can easily combine data from dozens of sources and quickly produce the outcomes they need. Behind the scenes, they are effectively building data pipelines.

With the rise of Power BI, this approach has accelerated. Many organizations now have Power BI models that serve as a single source of truth. Increasingly, key users will point to a published Power BI report and say, “the data you need is there.”

In environments without Microsoft Fabric, this means you need to extract data from a semantic model and feed it into the next stage of your data pipeline.

This Azure Data Factory (ADF) project leverages the Power BI executeQueries API to run DAX queries on published Power BI semantic models and write the resulting JSON output to a storage account for further processing.

The connection is established using a service principal (Azure Entra App) and all secrets (such as the Power BI tenant ID, semantic model ID, app secret, etc.) are securely stored in Azure Key Vault, outside of ADF itself.

This project is reusable and ideal whenever you need to extract data from published semantic models without having to reinvent the wheel.

![image](https://github.com/user-attachments/assets/3deff02d-e7c2-429f-a7b4-80eac22b1032)

## Prerequisites
In order to leverage this project you need the following resources:

- Azure Subscription
- Azure Resource Group
- Azure Key Vault
- Azure Data Factory
- Azure Storage Account
- Power BI Workspace
- Power BI Semantic Model
- Microsoft Entra App

## Azure Key Vault Secrets
No secrets are saved inside Azure Data Factory, all the sensitive information are saved inside Azure Key Vault and retrived via APIs by ADF.

| Parameter Name                          | Description                              |
|-----------------------------------------|------------------------------------------|
| spn-client-id         | SPN Client ID                                              |
| pbi-tenant-id         | Power BI Tenant ID                                         |
| spn-secret            | SPN Secret                                                 |
| workspace-id          | Workspace ID                                               |
| model-id              | Model ID                                                   |
| storage-endpoint      | Storage Endpoint                                           |
| storage-container-name| Storage Container Name                                     |

## Pipeline Parameters
This project is based on single pipeline that accepts a set of parameters to interact with Key Vault, Storage Account and Power BI.

| Parameter Name                          | Description                                                                 |
|-----------------------------------------|-----------------------------------------------------------------------------|
| pp_kv_dns                               | Key Vault DNS URL                                                          |
| pp_kv_secret_name_spn_client_id         | Secret name for SPN Client ID                                              |
| pp_kv_secret_name_pbi_tenant_id         | Secret name for Power BI Tenant ID                                         |
| pp_kv_secret_name_spn_secret            | Secret name for SPN Secret                                                 |
| pp_kv_secret_name_workspace_id          | Secret name for Workspace ID                                               |
| pp_kv_secret_name_model_id              | Secret name for Model ID                                                   |
| pp_dax_query                            | DAX query to be executed                                                   |
| pp_kv_api_version                       | API version for Key Vault                                                  |
| pp_kv_secret_name_storage_endpoint      | Secret name for Storage Endpoint                                           |
| pp_kv_secret_name_storage_container_name| Secret name for Storage Container Name                                     |****
