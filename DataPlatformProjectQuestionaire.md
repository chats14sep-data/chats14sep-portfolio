# Gathering Data Projects Requirements

In the last 3-5 years, the variety of data and ways to onboard, process, and visualize data using various tools and technologies have grown exponentially. Before 2015, if you worked on Microsoft platform data projects, you had limited tools like SQL Server for storage and transformation, SSIS for integration, SSAS for modeling, and SSRS for reporting. Now, for each step during that data evolution journey, there are multiple technologies and options available at our disposal. Hence, it is very important to choose them wisely. It’s paramount to ask the right set of questions upfront to gather low-level requirements to select the right toolset and architecture. Polyglot persistence is a new way to design data platform architecture.

---

## Functional Requirements Questions to Ask:

### 1. What are we trying to create?
- On-prem data platform (SQL Server, SSIS, SSRS, Power BI Report Server)?
- Cloud-based data platform?
- Hybrid data platform?

### 2. If Cloud, what kind of data system are we trying to develop?
- Warehouse system (MPP architecture, e.g., Synapse, Databricks, Azure HD Insight)?
- Operational System (Replicated data store, e.g., SQL replication, Replicated Secondary Database for reporting system)?
- Lakehouse – combination of data lake and warehouse (new data management and processing paradigm)?

### 3. What kind of data project are we trying to execute?
- Migration project (Leverage Migration Assistant for online/offline migration)?
- Modernization project (Decommission legacy platform and redevelop ingestion and integration platform on cutting-edge technology)?

### 4. What kind of data processing do we need?
- **Batch processing** (data is loaded in batch mode incrementally from source system)?
- **Streaming processing** (data is continuously loaded from IoT devices or events)?

### 5. Things to consider in ingestion and integration patterns:
- Deciding on the right Orchestration Tool
- Metadata Framework or configuration table (to easily onboard new objects during the ingestion process)
- Incremental load/Full load
- Data frequency and scheduling options
- Load processing:
  - Insert-Insert, Upsert, Not Matched Delete on Target, Autoloader, etc.
- Layers of data processing:
  - Raw → Staging → Transform (Dim and facts)
  - Landing → Bronze → Silver → Gold
- Number of data sources
- Connectors to the data sources
- Internal or external sources and connectivity options

---

## Non-Functional Requirements Questions to Ask:

### Performance:
- How fast should the data be accessible from the Source to the Serving layer?
- Latency for data to be accessed by the end user via the reporting platform or API layer?
- Time taken by the reporting layer to load the report (involves processing and buffer speed at the server side)?
- Processing performance factors:
  - Time taken for the user to access the data
  - Time taken to load the data into the database

### Security:
- **Security Infrastructure (Azure):**
  - Do we need private endpoints or service endpoints to secure PaaS services holding data?
  - Do we need advanced threat protection or Azure Defender?
  - How keys/passwords/tokens/connection strings managed or stored? (Key Vault)?
  - Inbound and outbound rules to access data?

- **Data Security:**
  - How is data secured at rest?
  - How is data secured in motion (transit)?
  - Are we handling PII data? How is it managed and maintained?
  - Is data masking required?
  - Row-level security, column-level security, and role-based security?
  - Data sovereignty rules?

### Scalability:
- How easily can the solution handle unpredicted workloads, and how can it scale down during non-peak hours?

### Cost:
- Use PaaS services wherever possible.
- Separate compute and storage; pause compute when not in use for cost savings.

---

## Governance:
- Is there a centralized Data Catalog system?
- Is Data Dictionary available?
- Is metadata layer information available for the business to consume?
- Is data lineage implementation done?
