# 🚀 Enterprise Level: Architectures - Global Risk Monitoring Agent

## 🛑 Reviewer Instructions: Submission Checklist 🛑

This project is focused on **Enterprise Architectures, Large-Scale Orchestration, Governance, and Safety**. Developers **must** ensure the following requirements are met for review:

1.  **Repository Forking & Naming:** This repository **must be forked** to your personal GitHub account and **renamed** exactly to:
    `Agentic-AI-Enterprise-Capstone-Project-3-GlobalRiskMonitoring-Agent`
2.  **Language Requirement:** All code must be implemented using **Python**.
3.  **Advanced Components:** The solution must demonstrate **Multi-Agent Orchestration, Advanced Safety/Guardrails, Multi-Tool Ecosystems, and Robust Testing (Unit, Integration, RAG Metrics)**.
4.  **Complete Documentation:** All sections of this README (Requirements, Execution, Views) must be fully completed with project-specific details, code, and screenshots.

-----

## 🌟 Project Summary

This Capstone project involves building a sophisticated **Global Risk Monitoring Agent** designed to operate at an enterprise scale. The agent continuously monitors financial news, geopolitical events, and regulatory updates across multiple data sources to provide real-time, triaged risk summaries to different business units.

This project demonstrates **large-scale agent orchestration** managing a multi-tool ecosystem, advanced **governance (e.g., PII masking, source verification)**, and robust, quantifiable **evaluation and optimization**.

### Key Methodologies:

  * **Core Concept:** **Large-Scale Orchestration** (managing concurrent streams).
  * **Testing:** **Unit, Integration, RAG Metrics** (Retrieval & Grounding).
  * **Safety & Governance:** Implementing PII masking and source attribution/Guardrails.
  * **Data Handling:** **Multi-Tool Ecosystem** (concurrent RAG, external APIs, structured data lookups).

-----

## 🧠 Related Training Topics

This project covers the **Enterprise Architectures** section of the training.

| Training Topic | Relevance to This Project | Implementation Details |
| :--- | :--- | :--- |
| **Large-Scale Agent Orchestration** | Core system design. | Uses an **Orchestration Framework** (e.g., specialized ADK patterns or flow engine integration) to manage concurrent data ingestion, parallel processing by multiple agents, and final delivery.  |
| **Multi-Tool Ecosystems** | Data integration complexity. | Agents utilize a minimum of **three distinct tools concurrently**: 1. **Vector Search Tool** (RAG), 2. **External API Tool** (Market Data), and 3. **Structured DB Tool** (Client Profiles). |
| **Safety & Governance / Guardrails** | Enterprise compliance. | Implements a **Safety Agent** that applies **PII masking** and utilizes a Guardrail system to enforce **topic filtering** and prevent adversarial input/output generation. |
| **Advanced Evaluation** | Production quality assurance. | Implements a monitoring layer to track **quantitative metrics** (Latency, Cost, Accuracy) and specific **RAG Metrics** (Precision@K, Groundedness). |
| **Optimization** | Cost and performance tuning. | Demonstrates techniques like **response caching**, **model selection** based on task complexity, and **batch processing**. |

-----

## 📋 Requirements (Functional and Non-Functional)

### Functional Requirements (FR)

| ID | Requirement | Specific Description | Status |
| :--- | :--- | :--- | :--- |
| **FR01** | Concurrent Orchestration | The system must concurrently ingest data from at least two sources (e.g., News Feed, Regulatory DB) and route them to parallel processing agents. | `PENDING` |
| **FR02** | Multi-Tool Use | The Triage Agent must use at least **three distinct tools** (RAG, External API, Structured DB) within a single execution flow. | `PENDING` |
| **FR03** | Safety Filter | Implement a **Safety Agent** to redact or flag PII (Personal Identifiable Information) in input data before processing. | `PENDING` |
| **FR04** | Source Attribution | The final report must contain traceable links or identifiers for all source documents/APIs used to generate the risk summary. | `PENDING` |
| **FR05** | Role-Based Reporting | The final structured output must be tailored to different "roles" (e.g., a "Trading Desk" view vs. a "Compliance" view). | `PENDING` |

### Non-Functional Requirements (NFR)

| ID | Requirement | Category | Metric |
| :--- | :--- | :--- | :--- |
| **NFR01** | Throughput | Performance | The system must process **X** monitoring events per minute while maintaining P95 latency. |
| **NFR02** | Governance | Safety | PII masking success rate must be **99.9%** on test data containing sensitive information. |
| **NFR03** | RAG Quality | Evaluation | **Retrieval Precision@3** (P@3) on the regulatory RAG tool must be greater than **90%**. |
| **NFR04** | Cost | Optimization | Demonstrate a **15% reduction** in total token usage through the use of model selection/caching compared to a baseline single-model approach. |

-----

## 🧪 Testing and Validation (Enterprise Grade)

Enterprise-level solutions require rigorous testing across all components:

### 1\. Unit and Integration Testing

  * **Unit Tests:** Must cover all individual agents, tools, and helper functions (e.g., PII masking utility, API wrappers).
  * **Integration Tests:** Must validate the successful execution of the full multi-agent flow, ensuring the Orchestrator passes data correctly between sub-agents and tools (e.g., mocking the API/DB responses to test the full loop).
    ```bash
    # Command to run all tests
    pytest tests/
    ```

### 2\. RAG Metrics Evaluation

Testing the **quality of the RAG system** (Regulatory Data RAG) is critical:

  * **Retrieval Metrics:** Implement evaluation of **Retrieval Precision@K** (P@3 or P@5) using a small, annotated test set of questions and expected document IDs.
  * **Groundedness:** Implement an LLM-based evaluation to score the final generated risk summary on its **Groundedness** (i.e., whether the facts cited in the output are actually present in the retrieved documents).
    ```bash
    # Command to run RAG evaluation script
    python evaluation/rag_evaluator.py --metric precision@3
    ```

### 3\. Safety and Guardrails Validation

  * **PII Masking Test:** Must include dedicated test cases to verify the PII masking agent correctly redacts various forms of sensitive data (names, social security numbers, etc.).
  * **Prompt Injection Testing:** Demonstrate test cases attempting to bypass the agent's instructions (e.g., malicious prompts) and show how the **Guardrail** system successfully blocks or neutralizes the output.
    ```bash
    # Command to run safety test suite
    pytest tests/safety_tests.py
    ```

-----

## 🚀 Implementation and Execution

### 1\. Prerequisites and Setup

Requires **Python 3.9+**, Gemini API Key, and access credentials for external data sources and the cloud environment.

  * **API Key:** Your Gemini API key must be configured in your environment.
  * **External Configs:** **[Placeholder: Specific environment variables needed for third-party systems like Market Data APIs or Regulatory DBs.]**

### 2\. How to Build (Install & Initialize)

In addition to installing libraries, you must initialize the cloud infrastructure components (Vector Stores, Databases).

```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. Initialize Infrastructure (One-time setup)
# This script sets up vector databases, mock external service endpoints, and structured tables.
python setup_enterprise_infra.py --cloud_region "us-central1"
```

### 3\. How to Run (Local Testing)

Run the simulation endpoint locally to verify the orchestration logic.

```bash
uvicorn main:app --reload
```

The local monitoring controller will be available at `http://localhost:8000`.

### 4\. How to Test (Local Endpoint)

Test the orchestration with a simulated event stream using the `/monitor` endpoint.

```bash
# Example curl request submitting a new regulatory event for processing
curl -X POST http://localhost:8000/monitor \
     -H "Content-Type: application/json" \
     -d '{
         "event_id": "REG-2025-001",
         "raw_text": "New central bank capital requirements issued for all non-depository institutions...",
         "source": "FINRA"
     }'
```

### 5\. Deployment Instructions

**[Placeholder: Detailed instructions for deploying the complex multi-service architecture (e.g., using Terraform/Cloud Deployment Manager, Cloud Run services, and pub/sub queues).]**

-----

## 🖼️ Project Views

Here will be the relevant screenshots demonstrating the successful execution of the enterprise architecture.

### 1\. Large-Scale Orchestration Flow

\![Placeholder for screenshot of the orchestration engine dashboard (e.g., Airflow/Kubeflow UI) showing successful execution of concurrent tasks.]

### 2\. Advanced Evaluation Metrics

\![Placeholder for screenshot of the monitoring dashboard (e.g., Prometheus/Grafana) displaying F1 Score, End-to-End Latency, and Cost per Query.]

### 3\. Safety and Governance Output

\![Placeholder for screenshot of the final structured report clearly showing the redacted PII fields and the embedded source attribution links.]
