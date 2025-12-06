# Investigating the Molecular Phylogenetics and Congruence of COI and CytB Genes in the Accipitridae Family

This project reconstructs and compares phylogenetic trees for two mitochondrial genes, COI (cytochrome oxidase I) and CytB (cytochrome b), across species in the bird family *Accipitridae* (hawks, eagles, and other raptors). Using maximum likelihood methods, model testing, congruence visualization, and cophenetic distance comparisons, the study evaluates whether COI and CytB provide consistent evolutionary signals. The project investigates topological agreement, gene-specific differences, and potential evolutionary drivers of incongruence.

## Table of Contents
- [Introduction](#introduction)
- [Project Structure](#project-structure)
- [Data Sources](#data-sources)
- [Requirements](#requirements)
- [Usage](#usage)
- [Analysis Workflow](#analysis-workflow)
- [References](#references)

## Introduction
Mitochondrial genes are widely used in molecular phylogenetics because they tend to evolve rapidly, lack recombination, and are maternally inherited. In this project, COI and CytB gene sequences from *Accipitridae* were obtained from NCBI using automated queries. After quality filtering, alignment, consensus sequence generation, and model selection, phylogenetic trees were constructed using maximum likelihood (ML) methods.

Congruence between the two resulting trees was assessed using:
- **cophylogenetic visualization** (phytools)
- **cophenetic distance heatmaps**
- **topological comparison of species placements**

This project tests whether two commonly used mitochondrial markers produce consistent phylogenetic hypotheses and evaluates the reliability of mtDNA for phylogenetic inference in raptors.

## Project Structure
- `data/`:  
  Raw and cleaned FASTA files for COI and CytB sequences retrieved from NCBI.

- `scripts/`:  
  R Markdown file (`.Rmd`) containing the full analysis, including data acquisition, filtering, model testing, tree building, and visualization.

- `figures/`:  
  Exported phylogenetic trees, cophylo plots, sequence length histograms, and base composition plots.

- `README.md`:  
  Project overview and instructions.

## Data Sources
1. **NCBI Nucleotide Database (GenBank)**  
   COI and CytB mitochondrial gene sequences for members of the *Accipitridae* family, queried via the `rentrez` R package (retrieved December 4, 2024).  
   Search filters included:
   - Taxon: *Accipitridae*
   - Gene: COI / CO1 / COX1 or CytB
   - Sequence length: 600–1000 bp  
   - Maximum 300 records per gene

## Requirements
- **R (version 4.0 or higher)**

### Required R Packages  
`tidyverse`, `rentrez`, `Biostrings`, `DECIPHER`, `muscle`, `phytools`, `ape`, `phangorn`, `pheatmap`, `patchwork`, `ggtree`, `stringr`


## Usage
1. **Data Retrieval**: Query NCBI using `rentrez` to download COI and CytB mitochondrial sequences for *Accipitridae*.
2. **Quality Control**: Clean sequences by removing unveriﬁed entries, trimming ambiguous bases, and filtering low-quality sequences.
3. **Sequence Alignment**: Align COI and CytB sequences with MUSCLE and generate consensus sequences for shared species.
4. **Model Selection**: Identify best-fit nucleotide substitution models for each gene using AIC-based model testing.
5. **Phylogenetic Reconstruction**: Build and optimize maximum likelihood phylogenetic trees under the selected models.
6. **Tree Comparison**: Assess congruence using cophylogenetic visualization and comparison of tree topologies.
7. **Distance-Based Analysis**: Compute and visualize cophenetic distance differences to quantify phylogenetic discrepancies.


## Analysis Workflow
1. **Data Acquisition**
   - Query NCBI for COI and CytB sequences.
   - Extract species names and metadata.
   - Export FASTA files.

2. **Exploration and Quality Control**
   - Inspect sequence lengths.
   - Check base composition.
   - Remove low-quality or ambiguous sequences.
   - Identify shared species (n = 14).

3. **Alignment & Consensus Generation**
   - Align sequences using MUSCLE.
   - Generate consensus sequences for each species and gene.

4. **Model Testing**
   - Evaluate nucleotide substitution models.  
   - COI best model: **TIM2+G(4)**  
   - CytB best model: **GTR+G(4)**

5. **Maximum Likelihood Phylogenetic Inference**
   - Build initial NJ trees.  
   - Optimize ML trees under best-fit models.  
   - Visualize ML trees with `ggtree`.

6. **Topological Comparison**
   - Use phytools’ `cophylo()` to align trees side by side.  
   - Highlight mismatched relationships.

7. **Cophenetic Distance Analysis**
   - Compute pairwise evolutionary distances.  
   - Create a heatmap of absolute differences to quantify incongruence.

## References
- [NCBI GenBank](https://www.ncbi.nlm.nih.gov/genbank/)  

