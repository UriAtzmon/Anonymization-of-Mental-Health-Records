## 🧠 Introduction

Psychiatric clinical notes contain some of the most sensitive personal information in healthcare, including references to names, dates, locations, and detailed personal histories. Ensuring patient privacy while preserving the clinical value of such records is a critical challenge in the age of AI-powered health systems.

Large Language Models (LLMs) offer powerful capabilities for understanding and generating natural language, including potential applications in de-identification and clinical documentation. However, traditional anonymization tools often fail to handle the nuance and contextual complexity of psychiatric texts—either over-sanitizing (removing useful content) or missing sensitive identifiers.

**MindShield** addresses this gap by introducing a benchmark and framework for anonymizing mental health records using LLMs. It combines:

- A synthetic dataset of annotated psychiatric notes  
- A tag-based anonymization pipeline using LLM prompts  
- A QA-based evaluation protocol to assess how well anonymized records preserve clinical meaning  
- Metrics that quantify the trade-off between privacy protection and information retention

By simulating real-world mental health documentation, MindShield pushes LLMs beyond simple string substitution and toward **context-aware anonymization**.
