# 🔍 Nuclear Regulatory Term Alignment (CNSC ↔ USNRC)

This project aims to identify, validate, and align overlapping technical terminology between the Canadian Nuclear Safety Commission (CNSC) and the U.S. Nuclear Regulatory Commission (USNRC). The goal is to support regulatory harmonization, reduce ambiguity in safety documentation, and enable machine-readable crosswalks between agency vocabularies.

## 🔬 Methodology

### 1. Exact Term Matching
- Terms from both glossaries are normalized (lowercased + trimmed)
- Matches are flagged if term strings are identical

### 2. Semantic Similarity Verification
- Exact matches are compared using `all-MiniLM-L6-v2` from Sentence-BERT
- Definitions are embedded and cosine similarity is computed
- Matches with similarity < threshold (0.27) are dropped
- Output: `verified_exact_matches.json`

### 3. Future Steps
- Abbreviation disambiguation (e.g., “AOO” ↔ “Anticipated Operational Occurrence”)
- Knowledge graph generation (Neo4j)
- UI-based review tool for regulators and engineers

# Nuclear Glossary Term Matcher

1. **Create and activate the virtual environment with Python 3.12 or more:**
   ```bash
   python3 -m venv term_env
   source term_env/bin/activate
   ```

2. **Launch Jupyter:**
   ```bash
   jupyter notebook
   ```

3. **Open `matcher.ipynb` and run all cells sequentially**

## Required Files
- `cnsc_full_glossary_final.json`
- `usnrc_glossary_final.json`

## Output Files
- `all_matches.json` - All term matches with similarity scores
- `verified_exact_matches.json` - Verified matches only (similarity >= 0.27)
