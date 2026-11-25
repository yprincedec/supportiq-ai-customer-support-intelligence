# SupportIQ — AI-Powered Customer Support & Intelligence Platform

SupportIQ is an end-to-end portfolio and research prototype exploring customer-support analytics, ticket intelligence, machine learning, NLP, retrieval-augmented generation (RAG), and support-assistance workflows.

> **Project status:** Phase 1 — Dataset Audit
> **Workflow:** Google Colab for experimentation; GitHub for version control and documentation.
> **Scope:** This is a prototype, not a production customer-support system.

## 1. Problem Statement

Customer-support teams handle large volumes of tickets and need ways to understand recurring issues, prioritize work, identify trends, and provide consistent assistance. SupportIQ will explore a modular workflow for ticket data auditing, operational analysis, suitable ML experiments, semantic retrieval, and response-assistance prototypes.

Model capabilities and evaluation claims will be added only after experiments are completed and verified.

## 2. Dataset Sources & Intended Use

We use two datasets for different purposes. They are not interchangeable.

### A. Primary operational dataset — Support Ticket Dataset (humans_only)

- **Publisher / dataset ID:** [s2pidape/support-ticket-dataset](https://huggingface.co/datasets/s2pidape/support-ticket-dataset)
- **Configuration:** `humans_only`
- **Role:** Primary source for ticket-level audit, exploratory analysis, operational metrics, and ML experiments supported by its actual fields.
- **Loading:** Hugging Face `datasets` library in Google Colab.
- **Due diligence:** Provenance, collection/generation method, schema, licence, and limitations must be checked against the dataset card and inspected records before making claims about realism or suitability.
- **Redistribution:** Raw data will not be committed here unless the applicable licence and dataset terms explicitly permit it.

### B. NLP and response experiment dataset — Bitext Customer Support

- **Publisher:** Bitext.
- **Canonical dataset:** [Bitext Customer Support LLM Chatbot Training Dataset](https://huggingface.co/datasets/bitext/Bitext-customer-support-llm-chatbot-training-dataset)
- **Original publisher repository:** [bitext/customer-support-llm-chatbot-training-dataset](https://github.com/bitext/customer-support-llm-chatbot-training-dataset)
- **Role:** Separate experiments for intent classification, instruction/response analysis, NLP preprocessing, and response-assistance prototypes.
- **Publisher-described size:** 26,872 question/answer pairs, 27 intents, and 10 categories.
- **Licence shown on Hugging Face:** CDLA-Sharing-1.0. Review its terms before redistributing data or derivatives.

### Dataset separation

The primary ticket dataset is the operational-analysis source. Bitext is a separately published hybrid synthetic customer-service instruction/response dataset. Bitext responses are examples, not verified answers to tickets in the primary dataset. We will not use Bitext examples as ground-truth operational outcomes.

## 3. Planned Technology Stack

| Area | Tools |
|---|---|
| Programming and analysis | Python, Pandas, NumPy |
| Classical machine learning | Scikit-learn |
| NLP | Scikit-learn text tools, Sentence Transformers |
| Semantic retrieval | FAISS |
| GenAI / RAG | Open-source models and retrieval components, selected after feasibility checks |
| API | FastAPI |
| User interface | Streamlit |
| Persistence | SQLite |
| Experiment environment | Google Colab |
| Version control | Git and GitHub |

The stack is a project plan. A component will be marked implemented only after its code and results are committed and verified.

## 4. Planned Architecture

```text
Support Ticket Dataset (humans_only) --> Audit --> Cleaning / EDA
                                               |
                                               +--> Supported ML experiments

Bitext Customer Support --> NLP / intent / response experiments
                                               |
                           Sentence Transformers --> FAISS
                                               |
                                          RAG / assistant
                                               |
                                        FastAPI service
                                               |
                                       Streamlit interface
                                               |
                                          SQLite storage
```

The two dataset streams remain distinct. Any future retrieval corpus, model training data, and evaluation set will be documented separately.

## 5. Development Roadmap

- [ ] Phase 1 — Audit the primary support-ticket dataset.
- [ ] Phase 1B — Audit the Bitext dataset and document its licence and schema.
- [ ] Phase 2 — Data cleaning, exploratory analysis, and data-quality report.
- [ ] Phase 3 — Baseline ML experiments and leakage-safe evaluation.
- [ ] Phase 4 — NLP and intent-classification experiments with Bitext.
- [ ] Phase 5 — Embeddings, FAISS indexing, and retrieval evaluation.
- [ ] Phase 6 — RAG / response-assistance prototype with appropriate safeguards.
- [ ] Phase 7 — FastAPI backend and SQLite persistence.
- [ ] Phase 8 — Streamlit interface, tests, documentation, and final evaluation.

Roadmap items remain unchecked until completed and verified.

## 6. Data Quality, Leakage & Evaluation Principles

- Inspect dataset provenance, schema, licence, and limitations before modelling.
- Keep raw data separate from cleaned and derived data.
- Split data before fitting learned preprocessing steps such as vectorizers and encoders.
- Check exact and near-duplicate records before splitting; prevent duplicates from leaking across evaluation partitions.
- Exclude identifiers from features unless a justified, leakage-safe use is demonstrated.
- Inspect timestamps, labels, and text for target leakage or post-outcome information.
- Fit preprocessing only on training data and apply it to validation/test data.
- Keep a held-out test set untouched until final evaluation.
- Report suitable metrics, including per-class results where class imbalance matters.
- Do not present synthetic-data performance as proof of real-world customer-support performance.

## 7. Repository Structure

```text
supportiq-ai-customer-support-intelligence/
├── data/
│   └── README.md
├── notebooks/
│   ├── 01_dataset_audit.ipynb
│   └── 02_bitext_nlp_audit.ipynb
├── reports/
│   └── dataset_audit/
├── src/
├── models/
├── app/
├── tests/
├── requirements.txt
├── .gitignore
└── README.md
```

Large raw datasets, credentials, API keys, and private information must not be committed. The data/README.md file will document download instructions and expected local paths.

## 8. Reproducibility & GitHub Workflow

Each milestone should include a saved and reproducible notebook or source-code change, verified outputs, a concise findings summary, updated documentation, and a descriptive Git commit.

No result, deployment, upload, or model performance will be described as complete until verified.

## 9. Current Progress

**Current milestone:** Repository initialized; primary dataset configuration has been loaded in the Colab session. Dataset metadata and audit findings are still pending verification.

## Acknowledgements

- Support Ticket Dataset publisher: [s2pidape on Hugging Face](https://huggingface.co/datasets/s2pidape/support-ticket-dataset).
- Bitext: [Hugging Face dataset](https://huggingface.co/datasets/bitext/Bitext-customer-support-llm-chatbot-training-dataset) and [original GitHub repository](https://github.com/bitext/customer-support-llm-chatbot-training-dataset).

Consult the original dataset cards, publisher documentation, and licences for authoritative terms and attribution requirements.