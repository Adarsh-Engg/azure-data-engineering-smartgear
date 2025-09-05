
# Azure Data Engineering Case Study — SmartGear Retail

This repository contains my end-to-end solution for the **SmartGear Retail** case study, 
part of an Azure & Data Analytics assignment. The goal was to build the first slice 
of an Azure analytics platform for a mid-sized retailer.

## 📂 Project Structure
- **Task A**: Provisioned Azure Storage (resource group, storage account, raw container, CSV uploaded).
- **Task B**: Databricks ETL notebook to aggregate sales by region, saved as parquet.
- **Task C**: Synapse serverless SQL query to explore parquet data.
- **Task D**: Data Factory pipeline for nightly ingest (CSV → landing with date suffix).
- **Reflection**: Lessons learned documented in `reflection.md`.

## 🛠️ Tools & Services
- Azure Storage
- Azure Databricks
- Azure Synapse Analytics (serverless SQL)
- Azure Data Factory
- Azure CLI

## Resources
- Resource Group: **rg-smartgear-dev**
- Storage Account: **rgassmartgear**
- Container: **raw**
- File: **smartgear_sales.csv**

## Verification Steps
```powershell
az group show --name rg-smartgear-dev --output table
az storage account show --resource-group rg-smartgear-dev --name rgassmartgear --output table
az storage container list --account-name rgassmartgear --output table
az storage blob list --account-name rgassmartgear --container-name raw --output table


## 📊 Key Learnings
# Reflection Memo

When I started this project, Azure felt like stepping into a massive workshop filled with every tool imaginable. I knew the basics — that Azure had services for storage, analytics, and automation — but I had never experienced how the pieces connect together in one workflow. This assignment gave me exactly that: a guided journey through the entire Azure data cycle, from raw file ingestion to automation.

The biggest surprise for me was the Azure CLI. Honestly, when I first looked at the commands, they seemed intimidating. I thought I would be more comfortable clicking around in the portal. But when I finally ran a few CLI commands, I realized how powerful and efficient it was. With just one line, I could check whether my resource group was live, confirm my storage account, or list all containers. And using the `--output table` option gave me clean results that were perfect for screenshots and sharing. It felt like I had discovered a professional shortcut — something data engineers use every day to save time.

While completing the project, I walked through the full Azure setup cycle myself:
- Created a **Resource Group**: `rg-smartgear-dev`  
- Provisioned a **Storage Account**: `rgassmartgear`  
- Set up a **Container**: `raw`  
- Uploaded the **File**: `smartgear_sales.csv`  

This gave me confidence that I could create and manage resources from scratch, not just read about them. Each step felt like building a layer of the foundation for a future analytics platform.

Of course, not everything went smoothly. The toughest moment came when I tried to list blobs in my container using Azure CLI with my login. The command failed with a permissions error, saying I didn’t have the required role. At first, I was frustrated because I thought I had done everything correctly. But that roadblock turned into one of the most important lessons of the project. I discovered that in Azure, there are usually multiple doors to solve a problem. The secure, long-term door was to request the right RBAC role, like **Storage Blob Data Reader**. The quick, practical door was to use the storage account key directly. By using the key, I was able to move forward without losing momentum, while also learning how security and access control are carefully designed in the cloud. This balance between security and convenience is something I’ll carry with me into future projects.

Another key learning was the difference between Data Factory and Databricks. At first, both looked like tools for moving data, but I now see their unique strengths. Data Factory is like a delivery service — perfect for moving files on schedule, reliable and low-code. If a CSV needs to land in a container every night, Data Factory handles it. Databricks is more like a workshop — where raw parts come in and you clean, reshape, or even build advanced models with Python or SQL. My takeaway: Data Factory keeps data flowing, while Databricks turns raw data into real insights

Looking back, this assignment was more than just a set of tasks. It was a journey where I built, broke, fixed, and understood. From creating a simple storage container to thinking about how an entire analytics pipeline fits together, I learned to see Azure not as individual services but as parts of a living ecosystem. Each tool has its place, and the real skill is knowing when and how to use them together.

This experience gave me confidence that I can not only follow steps but also troubleshoot, adapt, and tell the story of what I built. And for me, that’s the biggest win of all.


---
👤 **Author:** Adarsh Singh  
📅 Completed: September 2025

