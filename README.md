# named-entity-recognition-a4-tsutaoka-schlaerth

# Cybersecurity NER: Building a Custom Named Entity Recognition Pipeline

**Course:** BSAN 6200 – Text Mining & Social Media Analytics  
**Assignment:** Assignment 4 – Named Entity Recognition  
**Authors:** Josh Tsutaoka and Thomas Schlaerth

---

## Overview

This project builds a full **Named Entity Recognition (NER)** pipeline in the cybersecurity domain using the **CyNER 2.0** dataset. The goal was to test how well a general pretrained NER model performs on technical cybersecurity text, improve annotation quality through guideline development and inter-annotator agreement, and train custom models that better recognize cybersecurity-specific entities.

The project includes:
- a pretrained baseline model
- annotation guideline creation and revision
- multi-batch manual annotation
- inter-annotator agreement analysis
- custom model training
- fine-tuning with expanded data
- three-model comparison
- cross-domain inference on Twitter data

---

## Project Goal

Most general NER models are trained on broad text sources such as news articles, which means they are usually not designed for cybersecurity language. Cybersecurity reports contain technical and domain-specific entities such as malware names, CVE identifiers, threat actor groups, attack indicators, and system references.

This project asks:

**Can a custom cybersecurity NER pipeline outperform a general pretrained NER model on cybersecurity text?**

---

## Dataset

We used the **CyNER 2.0** dataset from Hugging Face. The dataset contains **7,751 documents** from cybersecurity threat reports and includes **5 entity types**.

### Entity Types
- **Malware** — named malicious software or tool
- **Indicator** — observable signal of malicious activity
- **System** — named platform, operating system, hardware component, or environment
- **Organization** — company, threat actor group, institution, or victim organization
- **Vulnerability** — exploit, CVE, weakness, or attack vector

---

## Full Project Pipeline

### 1. Pretrained Baseline
We first applied a general-domain pretrained model:

- `dslim/bert-base-NER`

The purpose of this step was to establish a baseline and show how poorly a general NER model transfers to cybersecurity text. The baseline produced near-zero F1 scores across most entities and frequently confused cybersecurity entities with incorrect general-domain labels.

### 2. Annotation Guidelines
We created and revised annotation guidelines to define the five cybersecurity entity types more clearly.

- **Annotation Guidelines v1.0** — initial rules before annotation
- **Annotation Guidelines v1.1** — refined rules after Batch 1 disagreement analysis

The guideline revisions were especially important for ambiguous entity types such as **Indicator, System, and Organization**.

### 3. Annotation Batches
The annotation process was completed in three stages:

- **Batch 1** — both annotators labeled the same shared documents for initial IAA
- **Batch 2** — larger annotation round with split work and overlap for consistency checks
- **Batch 3** — Model 1 pre-annotated new documents, which were then manually corrected

This design followed the assignment’s iterative annotation workflow of shared annotation, agreement review, refinement, and model-assisted correction.

### 4. Inter-Annotator Agreement
We measured annotation consistency using:
- **Cohen’s Kappa**
- **Entity-level F1**

Batch 1 revealed that **Malware** was already strong, while **Indicator, System, and Organization** had weak agreement. After revising the guidelines, Batch 2 agreement improved substantially. 

### 5. Custom Model Training
We trained two custom model stages:

- **Model 1** — trained on manually annotated Batch 1 and Batch 2 data
- **Model 2** — fine-tuned further using corrected Batch 3 data

This gave us a clear model progression:
- pretrained baseline
- custom Model 1
- refined Model 2

### 6. Model Comparison
We compared all major model stages:
- pretrained baseline
- Custom Model 1
- Custom Model 2

Evaluation included:
- precision
- recall
- F1 score
- per-entity breakdown
- qualitative error analysis

### 7. Cross-Domain Inference
To test generalization, we applied the cybersecurity-trained model to Twitter text. This showed that the final model did not transfer well to general-domain social media NER, which was expected because it learned domain-specific cybersecurity patterns rather than general named-entity behavior.

---

## Key Results

### Pretrained Baseline
The pretrained baseline performed very poorly on the cybersecurity dataset. It produced near-zero F1 scores across the five entity types and often misclassified cybersecurity entities into the wrong label categories.

### Inter-Annotator Agreement
IAA improved significantly after guideline refinement:

- **Batch 1 Cohen’s Kappa:** 0.748
- **Batch 2 Cohen’s Kappa:** 0.891

This showed that refining the annotation guidelines improved consistency and created stronger training data.

### Final Custom Model Performance
The final fine-tuned model showed large gains over the pretrained baseline.

#### Model 2 Per-Entity F1
- **Malware:** 0.829
- **Indicator:** 0.706
- **System:** 0.568
- **Organization:** 0.647
- **Vulnerability:** 0.639
- **Macro F1:** 0.681

### Cross-Domain Inference
When applied to Twitter, the model did not generalize well as a general NER system. It tended to force Twitter entities into cybersecurity-specific categories, showing that the model was strongly domain-specific. This was actually a useful finding because it suggested the model learned cybersecurity patterns rather than broad entity behavior.

---

## Main Takeaways

- General-domain NER models do not work well on cybersecurity text.
- Annotation quality has a major effect on model performance.
- Guideline refinement improved inter-annotator agreement substantially.
- Domain-specific fine-tuning greatly improved NER performance.
- The final model works much better within cybersecurity than outside it.
- The project shows that specialized NER systems need both high-quality annotation and domain-relevant training data.

---

