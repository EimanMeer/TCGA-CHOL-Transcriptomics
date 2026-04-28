# TCGA-CHOL: Unbiased Transcriptomic Discovery & Regulatory Axis Mapping

## 🧬 Project Overview
This project presents an end-to-end bioinformatics pipeline for the discovery of dysregulated gene networks in **Cholangiocarcinoma (CHOL)**. Using raw sequencing data from 44 TCGA libraries, the analysis identifies high-significance Differentially Expressed Genes (DEGs) and maps the **lncRNA-mRNA Regulatory Axis** through co-expression modeling.

## 🔬 Key Research Phases

### 1. Data Integration & Matrix Construction
- **Automated Merging:** Programmatically merged 44 individual GDC RNA-Seq `.tsv` files into a master count matrix.
- **Handling Metadata:** Developed a logic to distinguish between **Tumor** and **Normal** samples based on TCGA barcode nomenclature (e.g., `-01` vs `-11`).

### 2. Differential Gene Expression (DGE)
- **Statistical Framework:** Implemented `DESeq2` using the Negative Binomial Generalized Linear Model.
- **Filtering:** Applied a strict threshold of $P_{adj} < 0.01$ and $|log2FC| > 2$ to identify robust biomarker candidates.
- **Biotype Annotation:** Integrated Ensembl identifiers with `org.Hs.eg.db` to categorize results into mRNAs, lncRNAs, and miRNAs.

### 3. Regulatory Axis Modeling
- **VST Transformation:** Applied Variance Stabilizing Transformation to normalize counts for downstream correlation.
- **Correlation Matrix:** Calculated **Spearman Rank Correlation** between top-tier lncRNAs and protein-coding mRNAs to identify potential cis/trans-regulatory interactions.

## 🛠 Tech Stack and Tools
- **Language:** R
- **Core Packages:** - `DESeq2`: Differential expression analysis.
  - `EnhancedVolcano`: High-resolution genomic visualization.
  - `pheatmap`: Co-expression and correlation clustering.
  - `tidyverse`: Data wrangling and transformation.

## 📊 Visual Results
The pipeline generates two primary scientific visualizations:
1. **Volcano Plot:** Illustrating the global transcriptomic shift between Tumor and Normal tissue.
2. **Correlation Heatmap:** Displaying the strength of the regulatory relationship within the identified lncRNA-mRNA axis.
