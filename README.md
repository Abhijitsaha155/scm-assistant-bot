# AI-Powered Supply Chain Governance Assistant

## Objective

This project implements a Retrieval-Augmented Generation (RAG) chatbot using Flowise and Google Gemini. The chatbot answers supplier governance and supply chain questions using uploaded CSV and PDF files.

---

## Public Chatbot URL

[Launch Chatbot](https://cloud.flowiseai.com/chatbot/b01e3eaa-6eb9-40af-9fa0-40facc212631)

---

## Technologies Used

- Flowise Cloud
- Google Gemini
- Gemini Embeddings
- In-Memory Vector Store
- Retrieval-Augmented Generation (RAG)
- CSV + PDF Processing

---

## LLM Used

`gemini-2.5-flash`

---

## Embedding Model

`gemini-embedding-001`

---

## Architecture

```text
Document Store
        ↓
Gemini Embeddings
        ↓
In-Memory Vector Store
        ↓
Google Gemini
        ↓
Conversational Retrieval QA Chain
```

---

## Chunk Configurations Tried

### Configuration 1 — CSV Record Chunking

- Flowise automatically chunked the CSV dataset into approximately 600–650 character chunks.
- Each chunk primarily contained one supplier purchase-order record.

#### Observation

Smaller record-level chunks improved supplier-specific retrieval accuracy, disruption analysis, and supplier filtering queries.

---

### Configuration 2 — PDF Policy Chunking

- The governance policy PDF was chunked into 8 larger contextual chunks ranging from approximately 1000–2400 characters.

#### Observation

Larger policy chunks improved governance reasoning, escalation policy retrieval, and contextual understanding for compliance-related queries.

---

## Retrieval Configuration Adjustment

- Vector Store Top-K retrieval was increased from `5` to `15`.

### Observation

Increasing Top-K improved retrieval coverage for analytical and governance-policy queries by returning more relevant supplier records and policy context simultaneously.

---

# Sample Queries and Outputs

## Q1

### Question

> Which Tier-3 suppliers have an active disruption flag, and what response level applies per policy?

### Answer

Based on the provided documents, here are the Tier-3 suppliers with active disruption flags and the applicable response levels:

- **Sahyadri Alloy Tech (SUP-017)**
  - Active Disruption: Political instability flag
  - Response Level: High

- **Archipelago PCB Corp (SUP-041)**
  - Active Disruption: Export license risk
  - Response Level: High

---

## Q2

### Question

> Which suppliers qualify for the annual Volume Rebate Program and how many are there?

### Answer

The provided documents do not contain information about an **Annual Volume Rebate Program** or its qualification criteria. Therefore, the system could not determine:

- Which suppliers qualify
- Total number of qualifying suppliers

---

## Q3

### Question

> Which region has the highest total PO value, and does it breach the concentration limit?

### Answer

The region with the highest total PO value is **EMEA** with a total of **$2,622,811.31**.

#### Breakdown by Region

- **EMEA:** $2,622,811.31
- **APAC:** $1,016,963.03
- **LATAM:** $205,266.53

No governance policy regarding a **concentration limit** was found in the retrieved context, so the system could not determine whether a breach occurred.

---

## Q4

### Question

> Which suppliers are on Supplier Watch List (SWL) status and what does it restrict?

### Answer

The provided documents do not contain any explicit reference to:

- Supplier Watch List (SWL)
- SWL restrictions
- Associated governance rules

The retrieved data mainly includes supplier attributes such as:

- Risk level
- Compliance score
- Defect rate
- Active disruptions

---

## Q5

### Question

> Which product category has the highest average defect rate and does it exceed the Tier-2 limit?

### Answer

The product category with the highest average defect rate is:

- **Industrial Textiles:** `2.194%`

However, the retrieved governance documents did not define any Tier-2 defect-rate threshold, so the system could not determine whether this exceeds the allowed limit.

---

# Future Improvements

- Integrate SQL/DataFrame agents for precise numerical aggregation
- Use hybrid retrieval combining vector search and structured querying
- Improve governance-policy extraction accuracy
- Add supplier analytics dashboards and visualizations
- Implement memory and multi-agent workflows
- Enhance chunking strategies for better retrieval precision
- Add real-time supplier monitoring and alert systems
- Improve handling of complex analytical and policy-based queries
