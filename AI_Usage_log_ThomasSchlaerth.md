# AI Usage Log — Assignment 4: Named Entity Recognition
BSAN 6200 Text Mining & Social Media Analytics | Student B: Thomas Schlaerth

**AI Tool Used**
Claude (Anthropic) — claude.ai chat interface

---

## AI-Assisted Tasks (Permitted)

- Debugged HuggingFace error when loading Broad_Twitter_Corpus in Google Colab 
- Debugged error with not being able to connect to CyNER2.0
- Debugged code not showing up on GitHub
- Generated full pipeline code for running dslim/bert-base-NER on the complete CyNER2.0 dataset (7,751 documents), including BERT_TO_CYNER label remapping (ORG→Organization, PER→Organization, LOC→System, MISC→Malware) and char-offset to token-level BIO alignment
- Generated spaCy en_core_web_sm pipeline code with SPACY_TO_CYNER mapping as a second pretrained baseline
- Generated FP/FN/wrong-label error analysis code comparing predictions against gold BIO labels; output revealed Indicator→Organization (1,156 cases) and System→Malware (793 cases) as top confusion pairs
- Generated per-entity results table (TP, FP, FN, Precision, Recall, F1) across all 5 CyNER entity types
- Generated 100-document random sample (random_state=42) from CyNER2.0 training set and CSV export (batch1_100docs.csv) for Label Studio Batch 2 annotation setup
- Generated 90-document random sample (random_state=42) from CyNER2.0 training set and CSV export (batch1_90docs.csv) for Label Studio Batch 3 annotation setup
- Generated batch export code saving tokens, gold bio_labels, and hf_pred columns so both annotators could load the same documents and compare predictions against ground truth
- Trained Model 1 and Model 2
- Compared all three model performances with IAA and F1 scores
