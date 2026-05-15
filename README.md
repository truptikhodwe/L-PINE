# L-PINE: Legal Page-Indexed Navigation Engine

L-PINE is a high-precision, reasoning-first Retrieval-Augmented Generation (RAG) pipeline specifically designed for the complexities of patent law and legal research. Unlike traditional RAG systems that rely on arbitrary text chunking, L-PINE utilizes a hierarchical **3-tier PageIndex architecture** to maintain structural fidelity and absolute traceability to the source material.

## The L-PINE Architecture

The system operates through a specialized multi-agent flow that mimics human legal research:

* **Tier 1: Global Router (The Librarian)** – Identifies the relevant primary source document using a global `catalog.json`.
* **Tier 2: Navigation Layer (The Navigator)** – Pinpoints the exact page(s) within the document using specialized page-level summaries (`*_index.json`).
* **Tier 3: Content Repository (The Reasoner)** – Fetches verbatim text and multimodal AI analysis of diagrams and tables from page-specific Markdown files to synthesize a grounded response.

## Dataset Access

To view the dataset that has been created for this project, please **[click here](https://drive.google.com/drive/folders/1SIQI_bxqzuqy3o4-VOs8rCcK3iZScEQR?usp=sharing)**.

## Important Files

* `catalog.json` (Tier 1): Maps legal anchors and technical keywords to document IDs for global routing. (In the dataset)
* `*_index.json` (Tier 2): Stores concise legal summaries for every page to facilitate targeted navigation. (In the dataset)
* `/tier_3_data/` (Tier 3): Contains the core knowledge base—Markdown files storing verbatim text and layout-aware analysis (diagrams, tables, etc.). (In the dataset)
* `CORE_PIPELINE.py`: The core coordination logic for the Librarian, Navigator, and Reasoner agents.
* `L-PINE_evaluation/`: Testing of the L-PINE Pipeline. 

## Experimental Results

L-PINE was evaluated against a standard Milvus-based RAG pipeline using a 100-question stress test focused on Indian patent rules and regulations.

| Metric | L-PINE Performance |
| :--- | :--- |
| **Average Fidelity Score** | 93.16 / 100 |
| **Median Fidelity** | 100.00 |
| **Routing Accuracy (n ± 1)** | 85% |
| **High Fidelity Band (80-100)** | 90% |

*The **85% routing accuracy** confirms the effectiveness of the "Neighbor-Aware" retrieval logic in navigating dense, multi-page legal documents.*
