## 🧠 Introduction

Psychiatric clinical notes contain some of the most sensitive personal information in healthcare, including references to names, dates, locations, and detailed personal histories. Ensuring patient privacy while preserving the clinical value of such records is a critical challenge in the age of AI-powered health systems.
![Project Flow](./project%20flow.PNG)

Large Language Models (LLMs) offer powerful capabilities for understanding and generating natural language, including potential applications in de-identification and clinical documentation. However, traditional anonymization tools often fail to handle the nuance and contextual complexity of psychiatric texts—either over-sanitizing (removing useful content) or missing sensitive identifiers.

**MindShield** is a benchmark and anonymization framework designed to tackle this problem. It leverages the power of LLMs to anonymize mental health records in a way that is both privacy-preserving and clinically meaningful. Specifically, MindShield combines:

- A synthetic dataset of annotated psychiatric notes  
- A tag-based anonymization pipeline using LLM prompts  
- A QA-based evaluation protocol to assess how well anonymized records preserve clinical meaning  
- Metrics that quantify the trade-off between privacy protection and information retention

By simulating real-world mental health documentation, **MindShield** pushes LLMs beyond simple string substitution and toward **context-aware anonymization**.

🧩 **Project Goal**  
The goal of MindShield is to develop and evaluate a robust anonymization pipeline for psychiatric records using LLMs — one that protects sensitive personal health information while preserving the clinical insights needed for downstream medical reasoning and AI tasks.


## 🧾 Project Data

### 🔹 Overview

The MindShield dataset was synthetically generated to simulate realistic psychiatric records containing both **personal identifiers** and **clinical information**. It consists of structured prompts, annotated samples, anonymization outputs, and evaluation metadata.

---

### 🔹 Data Sources

#### 🧠 Clinical Questions (DSM-5 Guided)

A curated set of clinical questions was developed based on **DSM-5 diagnostic criteria**, covering major psychiatric disorders. Each disorder (e.g., Major Depressive Disorder, Generalized Anxiety Disorder, PTSD) is associated with a set of clinically meaningful yes/no questions such as:

- *"Does the patient describe a persistent depressed mood?"*
- *"Has the patient lost interest or pleasure in usual activities?"*
- *"Does the patient report insomnia or hypersomnia?"*

These questions were used to simulate clinician-style assessments and to validate the clinical content retention after anonymization.

#### 🔐 Personal Questions (EPII Framework)

To simulate sensitive personal health information (PHI), a structured set of prompts was designed based on **EPII (Epidemic-Pandemic Impact Inventory)** and similar frameworks. Categories include:

- Patient's Name  
- Date of Birth  
- Address / City  
- Occupation  
- Education / Family Status  
- Substance Use / Trauma History

Example prompts include:

- *"Full residential address:"*  
- *"Highest educational level completed:"*  
- *"Details of any past trauma or abuse:"*

---

### 🔹 Record Construction

Each synthetic psychiatric note was built by:

1. **Sampling personal questions** to generate realistic PHI-filled sections.
2. **Sampling clinical questions per diagnosis**, then simulating patient answers (e.g., "The patient reports...", "She denies...", etc.).
3. **Combining personal and clinical content** into a full-text paragraph that mimics real mental health documentation.

Each record is stored with the following fields:

| Field              | Description                                         |
|-------------------|-----------------------------------------------------|
| `text_original`    | Full synthetic note with PHI and clinical content  |
| `tags_gold`        | Ground-truth tags for PHI and clinical spans       |
| `text_anonymized`  | Output of the LLM anonymizer                       |
| `tags_detected`    | Re-extracted tags from the anonymized version      |
| `QA_score`         | Score from clinical question-answering evaluation  |

---

### 🔹 Dual Annotation Strategy

Two tagging schemes are used:

- **PII tags**: for identifying names, dates, places, etc.  
- **Clinical tags**: for preserving medically relevant statements (e.g., symptoms, diagnoses)

This dual tagging enables both:

✅ **Privacy validation**: measuring how well sensitive data was removed  
✅ **Clinical fidelity evaluation**: testing whether key psychiatric information was preserved

---

The result is a rich benchmark for evaluating anonymization techniques under both privacy and utility constraints — tailored to the subtlety of psychiatric records.


## 🗂️ Project Structure

The **MindShield** repository is organized into two main directories: `data/` and `notebooks/`. These components together form the basis for generating, anonymizing, and evaluating psychiatric records using LLMs.

```bash
MindShield/
├── data/                                 # Source materials for record generation
│   ├── clinical_questions_dsm5.csv       # DSM-5-based clinical question set
│   ├── personal_questions_epii.csv       # Personal identifier question prompts
│   └── clinical_answers_gpt.csv          # Simulated answers generated by GPT-3.5 Turbo
│
├── notebooks/                            # Core notebook-based pipelines
│   ├── DATA_LLM_Victoria_Uriel.ipynb     # Data construction: building full synthetic records
│   ├── Anonymization_LLM_Victoria_Uriel.ipynb  # Anonymization using LLM prompts
│   └── EDA_LLM_Victoria_Uriel.ipynb      # Evaluation: Tag matching, QA scoring, visualization
│
├── requirements.txt                      # Environment dependencies
└── README.md                             # Project overview and documentation

```
## 🚀 Quick Start

Follow these steps to set up and run the **MindShield** anonymization pipeline locally.

### Clone the repository

```bash
git clone https://github.com/your-org/MindShield.git
cd MindShield
2. Install dependencies
It’s recommended to use a virtual environment. Then install the required packages:

bash
Copy
Edit
pip install -r requirements.txt



If you're using the OpenAI API (for anonymization or text generation), set your API key:

Option A – In your shell (recommended):

bash
Copy
Edit
export OPENAI_API_KEY="your-api-key"

Then open and run the notebooks in the following order:

notebooks/DATA_LLM_Victoria_Uriel.ipynb
➤ Generates synthetic psychiatric records from structured clinical and personal prompts.

notebooks/Anonymization_LLM_Victoria_Uriel.ipynb
➤ Applies LLM-based anonymization pipeline.

notebooks/EDA_LLM_Victoria_Uriel.ipynb
```



---

## 👥 Developers

**MindShield** was developed as part of an academic project exploring LLM-based anonymization in mental health records.  

Built with care and curiosity by:

- **Victoria Chuykina**  
- **Uriel Atzmon**

Year: 2025

---

*For feedback, questions, or collaborations — feel free to reach out!*

