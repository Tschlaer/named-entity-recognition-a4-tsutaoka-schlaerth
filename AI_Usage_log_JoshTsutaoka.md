# AI Usage Log — Assignment 4: Named Entity Recognition
BSAN 6200 Text Mining & Social Media Analytics | Student A: Josh Tsutaoka

**AI Tool Used**
Claude (Anthropic) — claude.ai chat interface

---

## AI-Assisted Tasks (Permitted)

### Data Loading & Environment Setup
- Debugged HuggingFace Hub ReadTimeout error when loading CyNER2.0 dataset in Google Colab — identified that pd.read_parquet over hf:// was timing out; resolved by switching to load_dataset() with HF_HUB_DOWNLOAD_TIMEOUT=120
- Assisted with HF_TOKEN setup in Google Colab Secrets panel; confirmed CyNER2.0 is a public dataset requiring no token
- Resolved ModuleNotFoundError for transformers and datasets — identified that a runtime restart was required after pip install before imports would work

### Pretrained Model Application — dslim/bert-base-NER
- Generated full pipeline code for running dslim/bert-base-NER on the complete CyNER2.0 dataset (7,751 documents), including BERT_TO_CYNER label remapping (ORG→Organization, PER→Organization, LOC→System, MISC→Malware) and char-offset to token-level BIO alignment
- Generated spaCy en_core_web_sm pipeline code with SPACY_TO_CYNER mapping as a second pretrained baseline
- Generated FP/FN/wrong-label error analysis code comparing predictions against gold BIO labels; output revealed Indicator→Organization (1,156 cases) and System→Malware (793 cases) as top confusion pairs
- Generated per-entity results table (TP, FP, FN, Precision, Recall, F1) across all 5 CyNER entity types

### Dataset Export for Annotation
- Generated 10-document random sample (random_state=42) from CyNER2.0 training set and CSV export (batch1_10docs.csv) for Label Studio Batch 1 annotation setup
- Generated batch export code saving tokens, gold bio_labels, and hf_pred columns so both annotators could load the same documents and compare predictions against ground truth
