# Cybersecurity NER: Building a Custom Named Entity Recognition Pipeline

**Course:** BSAN 6200 – Text Mining & Social Media Analytics  
**Assignment:** Assignment 4 – Named Entity Recognition  
**Authors:** Josh Tsutaoka and Thomas Schlaerth

---

## Project Summary

### 1. Introduction
This project focused on building a full **Named Entity Recognition (NER)** pipeline for cybersecurity text using the **CyNER 2.0** dataset. The main goal was to test whether a custom domain-specific NER model could outperform a general pretrained NER model on technical cybersecurity reports. The dataset contains **7,751 documents** and includes **five entity types**: **Malware, Indicator, System, Organization, and Vulnerability**. These entities are much more specialized than the people, places, and organizations usually seen in general NER datasets, which makes cybersecurity a difficult domain for standard models.

### 2. Methods
We began by applying the pretrained **dslim/bert-base-NER** model as a baseline on the cybersecurity dataset. This gave us a starting point for comparison and helped show how poorly a general NER model transfers to cybersecurity language. After that, we created **Annotation Guidelines v1.0**, manually annotated shared documents, measured inter-annotator agreement, refined the guidelines into **v1.1**, and continued annotation across later batches. We then trained **Model 1** on the manually annotated Batch 1 and Batch 2 data. Finally, we used Model 1 to pre-annotate Batch 3, manually corrected those outputs, and fine-tuned **Model 2** on the expanded dataset.

### 3. Results
The pretrained baseline performed very poorly, with near-zero F1 scores across most cybersecurity entity types. This confirmed that a general-domain NER model was not effective for cybersecurity text. 

Our annotation quality improved after revising the guidelines. In **Batch 1**, the overall **Cohen’s Kappa was 0.748** and entity-level F1 was **0.795**. After refining the rules and applying **v1.1**, **Batch 2** agreement improved to **0.891 Cohen’s Kappa** and **0.912 entity-level F1**. The biggest improvement came from the previously weak categories, especially **Indicator, System, and Organization**. 

The final custom model also showed major improvements over the baseline. **Model 2** reached a **macro F1 of 0.681**. By entity type, performance was strongest for **Malware (0.829 F1)**, followed by **Indicator (0.706)**, **Organization (0.647)**, **Vulnerability (0.639)**, and **System (0.568)**. This showed that domain-specific annotation and fine-tuning made the largest difference for entities that the pretrained baseline could barely identify.

### 4. Conclusion
Overall, this project showed that a general pretrained NER model does not transfer well to cybersecurity text, but a custom pipeline built with refined annotation guidelines and domain-specific training data can perform much better. The improvements in inter-annotator agreement also showed that clearer rules led to stronger and more reliable labeled data. In the end, the project demonstrated that success in domain-specific NER depends not only on model choice, but also on annotation quality, guideline refinement, and iterative training. 

---

## Dataset
- **Dataset:** CyNER 2.0
- **Documents:** 7,751
- **Domain:** Cybersecurity threat intelligence reports
- **Entity Types:** Malware, Indicator, System, Organization, Vulnerability 

---

## Models Used
- **Pretrained Baseline:** `dslim/bert-base-NER`
- **Model 1:** Custom fine-tuned model trained on Batch 1 and Batch 2 annotations
- **Model 2:** Refined model further fine-tuned using corrected Batch 3 annotations 

---

## Key Results
- **Batch 1 Cohen’s Kappa:** 0.748
- **Batch 2 Cohen’s Kappa:** 0.891
- **Model 2 Macro F1:** 0.681
- **Best-performing entity:** Malware (0.829 F1)

---

## Files Included
- `Assignment 4 checkpoint 1.ipynb`
- `Assignment_4_Final.ipynb`
- `Annotation Guidelines v1.0.pdf`
- `Annotation_Guidelines_v1.1.pdf`
- Final presentation slides
- Work division document
- AI usage log
- IAA analysis
- Annotated data / CoNLL exports
- Trained models or download links

---

## Work Division

### Student A — Josh Tsutaoka
- Project setup
- Annotation setup
- Initial annotation guideline creation
- Pretrained NER baseline model
- Baseline error analysis
- Preprocessing and annotation support files
- Batch 1 shared annotation
- Assigned Batch 2 annotation
- Batch 3 shared annotation
- IAA calculation
- Cohen’s Kappa and entity-level F1 analysis
- Annotation guideline refinement
- Notebook and output organization
- Presentation visuals and results interpretation

### Student B — Thomas Schlaerth
- Initial annotation guideline creation
- Batch 1 shared annotation
- Assigned Batch 2 annotation
- Batch 3 shared annotation
- Annotation consistency review
- Disagreement review participation
- Custom NER model training
- Model refinement and fine-tuning
- Final evaluation support
- Presentation preparation

### Shared Responsibilities
- Dataset selection
- Entity schema decisions
- Annotation discussions
- Guideline revision discussions
- Final presentation preparation
- Final submission review

---

## Main Takeaway
This project showed that general-domain NER models do not work well on cybersecurity text, but custom models trained on strong domain-specific annotations can perform much better. It also showed that better annotation guidelines and stronger inter-annotator agreement were a major part of building a useful final model.
