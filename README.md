# Interplay of Molecular Mechanisms Between IBD and Colon Cancer

A bioinformatics research project investigating the molecular and mechanistic interplay between **Inflammatory Bowel Disease (IBD)** and **colon cancer** through systematic literature review, multi-omics data collection, and differential gene expression analysis using publicly available datasets.

This work was conducted as part of a voluntary research internship at the **University of Birmingham** (May – October 2025).

---

## Project Overview

Chronic intestinal inflammation in IBD is a well-established risk factor for colorectal cancer, yet the shared molecular mechanisms remain incompletely understood. This project takes a computational approach — systematically mining public omics repositories and applying differential expression analysis — to identify candidate genes that may underlie this interplay.

---

## Workflow

### 1. Literature Review

Reviewed five peer-reviewed publications on the IBD–colorectal cancer relationship, covering:
- Epidemiology, etiology, and surveillance of IBD-associated colorectal cancer
- The role of gut microbiota and inflammatory biomarkers in colorectal cancer risk
- Pathophysiology of inflammation-driven oncogenesis
- Pharmacological prevention strategies

Key sources included publications from PubMed covering immunological, microbiological, and molecular perspectives on chronic inflammation and cancer development.

---

### 2. Data Collection

**GEO (Gene Expression Omnibus) — Transcriptomics**

Searched NCBI GEO using the query `ibd and colon cancer`, returning 59 results. Screened all results and identified **25 datasets** with usable sample data. For each dataset, the following information was recorded:

- Paper name and PMID number
- GSE accession number
- Model organism (human or mouse)
- Number of samples and sample descriptions

**OmicsDI — Proteomics & Metabolomics**

Supplementary data was also collected from the OmicsDI platform across two additional repositories:

- **PRIDE (Proteomics)** — 4 results; all from *Mus musculus*, colon tissue, colon cancer disease context
- **MetaboLights (Metabolomics)** — 5 results; recorded project numbers, instruments, repositories, and sample counts

All collected metadata was organised into a structured Excel file with separate sheets for each repository.

---

### 3. GEO2R Differential Expression Analysis

Applied GEO2R (limma-based linear modelling) to compare gene expression between clinical conditions. Identified GEO datasets within the 59 results that supported two-group GEO2R analysis. Three datasets were selected for analysis:

| GSE Accession | Description | Comparison |
|---|---|---|
| GSE83687 | MSH IBD Population Specimen Collection | Control vs Ulcerative Colitis |
| GSE164871 | RNA-seq of Crohn's Disease and Control Samples | Control vs Crohn's Disease |
| GSE158952 | Transcriptome Profiling of Rectal and Ileal Tissues in IBD | Ulcerative Colitis vs Crohn's Disease |

GSE164871 was identified via the [IBDExplore](https://abbviegrc1.shinyapps.io/ibdexplore/) platform.

---

### 4. Top Gene Identification with Python

GEO2R results were exported as `.tsv` files and processed using Python to identify the most statistically significant genes. The analysis pipeline:

- Loaded `.tsv` output files using **pandas**
- Sorted genes by adjusted p-value (FDR-corrected)
- Extracted the **top 15 most significant genes** per dataset
- Visualised results using **matplotlib** — bar plots and volcano plots

---

## Tools & Technologies

| Category | Tools Used |
|---|---|
| Literature search | PubMed |
| Dataset discovery | NCBI GEO, OmicsDI, IBDExplore |
| Differential expression | GEO2R (limma-based) |
| Data processing | Python, pandas |
| Visualisation | matplotlib |
| Data organisation | Microsoft Excel |
| Environment | Jupyter Notebook |

---

## Key Outputs

- Curated metadata spreadsheet of 25 GEO datasets and 9 proteomics/metabolomics datasets relevant to IBD and colorectal cancer
- Differential expression results for three GEO datasets across Crohn's disease, ulcerative colitis, and control comparisons
- Top 15 candidate genes identified per dataset, ranked by statistical significance
- Bar plots and volcano plots visualising gene expression patterns

---

## Repository Structure

```
├── data/
│   ├── geo_dataset_summary.xlsx       # Curated GEO and OmicsDI metadata
│   └── tsv/                           # GEO2R output files per dataset
├── notebooks/
│   └── top_genes_analysis.ipynb       # Python analysis pipeline
├── figures/                           # Bar plots and volcano plots
└── README.md
```

---

## How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/nagarnamit-gif/GEO2R.git
   cd GEO2R
   ```

2. Install dependencies:
   ```bash
   pip install pandas matplotlib jupyter
   ```

3. Launch the notebook:
   ```bash
   jupyter notebook notebooks/top_genes_analysis.ipynb
   ```

---

## Data Sources

All gene expression data is publicly available via:
- [NCBI Gene Expression Omnibus (GEO)](https://www.ncbi.nlm.nih.gov/geo/)
- [OmicsDI](https://www.omicsdi.org/)
- [IBDExplore](https://abbviegrc1.shinyapps.io/ibdexplore/)

---

## Author

**Namit Nagar**  
MSc Bioinformatics, Queen Mary University of London  
[LinkedIn](https://linkedin.com/in/namit-nagarb89b85300) · [GitHub](https://github.com/nagarnamit-gif)
