# 18-Ingest-realtime-data-with-Azure-Stream-Analytics-and-Azure-Synapse-Analytics
In this exercise, you'll use Azure Stream Analytics to process a stream of sales order data, such as might be generated from an online retail application. The order data will be sent to Azure Event Hubs, from where your Azure Stream Analytics jobs will read the data and ingest it into Azure Synapse Analytics.

In this lab, you'll implement a real-time data pipeline using **Azure Event Hubs**, **Azure Stream Analytics**, and **Azure Synapse Analytics**. This architecture simulates ingesting streaming sales order data from an online retail application into Synapse Analytics for real-time analytics and reporting.

## 📌 Objectives

- Set up **Azure Event Hubs** to simulate a real-time data stream.
- Process and transform data using **Azure Stream Analytics**.
- Ingest data into **Azure Synapse Analytics** using a dedicated SQL pool.
- Query and validate the ingested data in **Synapse Studio**.
---
## 🛠️ Steps

### 1. Create an Azure Event Hub

- Create an **Event Hubs Namespace**.
- Add an **Event Hub** named `salesorders` (or similar).
- Note down the **connection string** for the Event Hub.

### 2. Simulate Streaming Data

- Use a provided **Python script** or **test data generator** to send sales order data.
- Authenticate using SAS token or connection string.

### 3. Create Azure Synapse Analytics Resources

- Create a **Synapse Analytics workspace** with a **dedicated SQL pool**.
### 🔄  4: Create Azure Stream Analytics Job

  1. Go to the **Azure portal** and create a new **Stream Analytics job**.
  2. Set the job name, region (same as Event Hub), and resource group.
  3. After creation, open the job and configure the **Inputs**:
   - Type: **Event Hub**
   - Select your existing Event Hub
   - Set **consumer group** (or use `$Default`)
   - Choose **JSON** as the data format (if applicable)

  4. Configure the **Outputs**:
   - Type: **Azure Synapse Analytics**
   - Provide:
     - Server name
     - Database name (your Synapse SQL pool)
     - Table name (`SalesOrders`)
     - Authentication type (SQL authentication recommended for simplicity)
   - Ensure the Synapse firewall allows access from the Stream Analytics job.

  5. In the **Query** section, define a transformation SQL query
---
###  5 Start the Stream Analytics Job
Make sure your Event Hub is receiving data from your generator (e.g., a Python script).
In the Stream Analytics job, click Start, and choose Now or a specific time.
Monitor the job for:
Input Events
Output Events
Errors (use Diagnostics or Logs if needed)
Let it run for several minutes while data is being sent continuously.

### 6 Query Ingested Data in Synapse Studio
Open the Azure Synapse Analytics workspace.
Go to Synapse Studio.
In the Data tab, find the SalesOrders table in your Synapse SQL pool.
Open a New SQL Script and run a query to validate data ingestion
''sql
SELECT TOP 10 *
FROM dbo.SalesOrders
ORDER BY OrderDate DESC;

### ✅ Outcome
By completing this lab, you will have successfully created a real-time data ingestion pipeline, where sales order data is streamed from an Event Hub, processed through Azure Stream Analytics, and ingested into Azure Synapse Analytics. You can then query the data in real time for further analysis.

## Screenshots
![lab181dbo](https://github.com/user-attachments/assets/19c4d177-b0a6-49c9-889a-810984fe961c)
![lab182sajop](https://github.com/user-attachments/assets/bd50a4a6-8f93-4b57-b37d-46c918f1313d)
![lab183eventhub](https://github.com/user-attachments/assets/1b0cfdfd-aee6-4cb3-818b-48aabbeebe37)
![lab183input](https://github.com/user-attachments/assets/0febe95b-af50-4ad4-8925-85c5427bdc73)
![lab184](https://github.com/user-attachments/assets/304d428d-9706-438d-b244-feb915815459)
![lab184output](https://github.com/user-attachments/assets/2e17383e-9053-4786-a110-b377af9bd996)
![lab184query](https://github.com/user-attachments/assets/54f74a3d-5130-4203-90c1-7f801723901d)
![lab184query2](https://github.com/user-attachments/assets/cf53a764-94ff-4538-908c-081d5717d7b8)
![lab185](https://github.com/user-attachments/assets/caab70d2-6a01-43d5-823b-313ce522c846)
![lab186datas](https://github.com/user-attachments/assets/ae29ab0c-9645-46c0-a2df-13376d4c4d42)
![lab186sql](https://github.com/user-attachments/assets/fe128f5a-181f-4361-b4c5-48dfb37bf91e)
![lab187sajop2](https://github.com/user-attachments/assets/e25fb5f9-f35d-4bf0-953c-a08e6a81df8e)
![lab187input](https://github.com/user-attachments/assets/86868378-3a5f-423b-ba6e-97a3b1701a6e)
![lab187output](https://github.com/user-attachments/assets/eb3661c8-9121-4c13-8f49-4ef48c8a6deb)
![lab187query](https://github.com/user-attachments/assets/2529b9f5-3c53-4a0f-a825-8002c8f71c2e)
![lab187query2](https://github.com/user-attachments/assets/5bd0963d-2c36-4318-b54d-c3dcbac78dac)
![lab188startjop](https://github.com/user-attachments/assets/3d7249f9-cb1d-4a2e-a339-f1a5523ae88a)
![lab188files](https://github.com/user-attachments/assets/6ba0dee8-6a6e-4f11-8f3c-0ed7c4181f8b)
![lab188codes](https://github.com/user-attachments/assets/e9074b18-e7b9-4c26-829d-5354fe8e4331)
![lab188codes2](https://github.com/user-attachments/assets/d4d5d2af-dec0-440a-a3ab-9c9d9db7eb23)
![lab189](https://github.com/user-attachments/assets/7b06f295-52bf-480c-ad76-811499e86c0a)
![lab189delete](https://github.com/user-attachments/assets/44e6b7ed-167a-4de6-a59e-656f2e7cab84)
