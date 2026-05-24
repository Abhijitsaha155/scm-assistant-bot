###### **AI-Powered Supply Chain Governance Assistant**



**Objective**
This project implements a Retrieval-Augmented Generation (RAG) chatbot using Flowise and Google Gemini. The chatbot answers supplier governance and supply chain questions using uploaded CSV and PDF files.



**Public Chatbot URL**
[https://cloud.flowiseai.com/chatbot/b01e3eaa-6eb9-40af-9fa0-40facc212631](https://cloud.flowiseai.com/chatbot/b01e3eaa-6eb9-40af-9fa0-40facc212631)



**Technologies Used**

* Flowise Cloud
* Google Gemini
* Gemini Embeddings
* In-Memory Vector Store
* Retrieval-Augmented Generation (RAG)
* CSV + PDF Processing

&#x20;

**LLM Used**

gemini-2.5-flash



**Embedding Model**

gemini-embedding-001



**Architecture**

**Document Store → Gemini Embeddings → In-Memory Vector Store → Google Gemini → Conversational Retrieval QA Chain**



**## Chunk Configurations Tried**



**### Configuration 1 — CSV Record Chunking**



**\* Flowise automatically chunked the CSV dataset into approximately 600–650 character chunks.**

**\* Each chunk primarily contained one supplier purchase-order record.**



**Observation:**

**Smaller record-level chunks improved supplier-specific retrieval accuracy, disruption analysis, and supplier filtering queries.**



**### Configuration 2 — PDF Policy Chunking**



**\* The governance policy PDF was chunked into 8 larger contextual chunks ranging from approximately 1000–2400 characters.**



**Observation:**

**Larger policy chunks improved governance reasoning, escalation policy retrieval, and contextual understanding for compliance-related queries.**



**### Retrieval Configuration Adjustment**



**\* Vector Store Top K retrieval was increased from 5 to 15.**



**Observation:**

**Increasing Top K improved retrieval coverage for analytical and governance-policy queries by returning more relevant supplier records and policy context simultaneously.**





**### Q1**



**Which Tier-3 suppliers have an active disruption flag, and what response level applies per policy?**



**Answer:**



**Based on the provided documents, here are the Tier-3 suppliers with active disruption flags and the applicable response levels:**



**\* Sahyadri Alloy Tech (SUP-017)**



&#x20; **\* Active Disruptions: Political instability flag**

&#x20; **\* Response Level: High**



**\* Archipelago PCB Corp (SUP-041)**



&#x20; **\* Active Disruptions: Export license risk**

&#x20; **\* Response Level: High**



**---**



**### Q2**



**Which suppliers qualify for the annual Volume Rebate Program and how many are there?**



**Answer:**



**The provided documents do not contain information about an "annual Volume Rebate Program" or its qualification criteria. Therefore, I cannot determine which suppliers qualify or how many there are.**



**---**



**### Q3**



**Which region has the highest total PO value, and does it breach the concentration limit?**



**Answer:**



**The region with the highest total PO value is EMEA with a total of $2,622,811.31.**



**Breakdown by region:**



**\* EMEA: $2,622,811.31**

**\* APAC: $1,016,963.03**

**\* LATAM: $205,266.53**



**There are no governance policy rules regarding a "concentration limit" provided in the context, so it is not possible to determine if this breaches any such limit.**



**---**



**### Q4**



**Which suppliers are on Supplier Watch List (SWL) status and what does it restrict?**



**Answer:**



**Based on the provided documents, there is no explicit mention of a "Supplier Watch List (SWL)" status or any associated restrictions. The documents detail supplier attributes such as risk level, compliance scores, defect rates, and active disruptions, but they do not define or reference an SWL.**



**---**



**### Q5**



**Which product category has the highest average defect rate and does it exceed the Tier-2 limit?**



**Answer:**



**The product category with the highest average defect rate is Industrial Textiles with an average defect rate of 2.194%.**



**The provided context does not contain any governance policy rules or specific limits for defect rates based on contract tiers, so it is not possible to determine if this exceeds the Tier-2 limit.**



**Future improvements may include:**



**\* Integrating SQL/DataFrame agents for exact numerical aggregation over CSV data.**

**\* Using hybrid retrieval combining vector search and structured querying.**

**\* Improving policy extraction and governance reasoning accuracy.**

**\* Adding supplier analytics dashboards and visualizations.**

**\* Implementing memory and multi-agent workflows.**

**\* Enhancing chunking strategies for better retrieval precision.**

**\* Adding real-time supplier monitoring and alert systems.**

**\* Improving handling of complex analytical and policy-based queries.**









