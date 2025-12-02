    
# PeptideFlow: Protein Digestion and Amino Acid Analysis Pipeline

**PeptideFlow** is a Nextflow pipeline designed to automate the processing of protein sequences. It takes FASTA files as input, performs in-silico digestion, counts amino acid frequencies in both full proteins and digested peptides, visualizes the data, and generates a comprehensive summary report.

## 🚀 Pipeline Workflow

This pipeline consists of the following modular steps:

1.  **Protein Digestion** (`digestProtein`): Reads input FASTA files and performs in-silico digestion to generate a list of peptides.
2.  **Amino Acid Counting** (`countAA`): Counts amino acid occurrences in the original protein sequence vs. the generated peptides.
3.  **Visualization** (`plotCount`): Generates plots visualizing the amino acid counts for each protein.
4.  **Reporting** (`generateReport`): Aggregates data from all samples to create a summary TSV report.
5.  **Archival** (`archiveResults`): Collects all plots and the report into a single compressed tarball (`results.tgz`).

## 🛠️ Prerequisites

To run this pipeline, you will need:

*   **Nextflow** (version 20.04.0 or later)
*   **Java** (version 8 or later, required by Nextflow)
*   **Python 3** (with necessary libraries for the scripts, e.g., `matplotlib`, `pandas`, `biopython`)

## 📂 Project Structure

Ensure your directory is organized as follows so Nextflow can find the scripts and inputs automatically:

```text
.
├── main.nf                 # Main Nextflow pipeline script
├── nextflow.config         # (Optional) Configuration settings
├── fasta/                  # Directory containing input .fasta files
│   ├── protein_A.fasta
│   └── protein_B.fasta
├── bin/                    # Python scripts called by the pipeline
│   ├── 01_digest_protein.py
│   ├── 02_count_amino_acids.py
│   ├── 03a_plot_count.py
│   └── 03b_get_report.py
└── README.md
```
  

🏃 Usage
1. Clone the repository

```    
git clone https://github.com/your-username/PeptideFlow.git
cd PeptideFlow
```
2. Prepare Input Data

Place your protein FASTA files into the fasta/ directory.
3. Run the Pipeline

Execute the pipeline using Nextflow:
```   
nextflow run main.nf
```

📊 Outputs

After a successful run, the pipeline will generate a results.tgz file in your working directory. You can extract it to view:

    Plots (*.png): Visualizations of amino acid counts for each protein.

    Report (protein_report.tsv): A summary table of the analysis.

Note: Intermediate files (peptides, individual counts) are stored in the work/ directory created by Nextflow.
📝 Customization

You can modify the python scripts in the bin/ folder to change how digestion is performed (e.g., changing enzymes) or how the plots are styled. Nextflow automatically adds files in bin/ to the system PATH inside the pipeline processes.
