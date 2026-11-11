# Comparative Genomic Analysis and Phylogenetic Relationships of Dengue Virus Serotypes Using R

## 1. Introduction

Dengue is a mosquito-borne viral disease caused by the dengue virus (DENV). The virus belongs to the Flavivirus genus and has four major serotypes: DENV-1, DENV-2, DENV-3, and DENV-4. Although these serotypes cause similar clinical diseases, they have genetic differences that can be investigated through genomic analysis.

Bioinformatics provides computational methods to study biological sequences, identify genetic similarities and differences, and investigate evolutionary relationships. DNA and RNA sequence analysis can help researchers understand the genetic characteristics of viruses and compare different viral strains.

This project applies bioinformatics techniques using the R programming language to compare eight dengue virus nucleotide sequences representing the four dengue virus serotypes. The analysis includes nucleotide composition, GC-content calculation, genome-length comparison, multiple sequence alignment, genetic distance calculation, and phylogenetic tree construction.

The sequences were retrieved from the National Center for Biotechnology Information (NCBI) GenBank database using their accession numbers. The analysis was performed using R packages including rentrez, Biostrings, DECIPHER, ggplot2, dplyr, and ape.

## 2. Problem Statement

Dengue virus consists of four genetically distinct serotypes. Understanding the similarities and differences between these serotypes is important for studying viral diversity and evolutionary relationships.

However, comparing several biological sequences manually is difficult and time-consuming. Computational bioinformatics methods are required to organize, compare, and visualize genomic information.

Therefore, this project investigates the nucleotide composition and genetic relationships among selected dengue virus sequences using R-based bioinformatics techniques.

## 3. Research Question

How do the nucleotide composition and genetic distances of selected dengue virus sequences differ among the four dengue virus serotypes, and what relationships can be identified through phylogenetic analysis?

## 4. Objectives

### Main Objective

To perform comparative genomic analysis of four dengue virus serotypes using bioinformatics tools in R.

### Specific Objectives

- Retrieve dengue virus nucleotide sequences from the NCBI database.
- Calculate nucleotide frequencies of adenine, thymine, guanine, and cytosine.
- Calculate and compare GC content among the selected sequences.
- Compare the genome lengths of the selected sequences.
- Perform multiple sequence alignment.
- Calculate pairwise genetic distances.
- Construct a phylogenetic tree using the Neighbor-Joining method.
- Interpret the similarities and differences among the selected dengue virus sequences.

## 5. Dataset Description

The dataset contains eight nucleotide sequences obtained from the NCBI GenBank database. Two sequences were selected for each dengue virus serotype.

| Serotype | Accession numbers |
|---|---|
| DENV-1 | KM204119, EU848545 |
| DENV-2 | KM204118, AF038403 |
| DENV-3 | KU050695, M93130 |
| DENV-4 | KR011349, AY947539 |

The four primary reference genome accessions are KM204119, KM204118, KU050695, and KR011349. A published study reports these sequences as complete genomes representing DENV-1 to DENV-4. The study also identifies EU848545, AF038403, M93130, and AY947539 as previously published reference sequences for the respective serotypes.

**Data source:** NCBI GenBank (https://www.ncbi.nlm.nih.gov/nuccore/)

The sequences were downloaded in FASTA format using the rentrez package in R. All eight sequences were stored in a single FASTA file for further analysis.

## 6. Tools and Technologies

The project was implemented using the following tools and packages.

| Tool or package | Purpose |
|---|---|
| R | Main programming language |
| RStudio | Development environment |
| rentrez | Retrieve nucleotide sequences from NCBI |
| Biostrings | Import and process biological sequences |
| DECIPHER | Perform multiple sequence alignment |
| ggplot2 | Create data visualizations |
| dplyr | Data manipulation |
| ape | Calculate genetic distances and construct phylogenetic trees |
| NCBI GenBank | Biological sequence database |

## 7. Methodology

The project followed a sequence of bioinformatics analysis steps.

### 7.1 Data Collection

Eight dengue virus nucleotide sequences were retrieved from NCBI using their accession numbers. The rentrez package was used to access the NCBI nucleotide database and download the sequences in FASTA format.

The downloaded sequences were combined into a single FASTA file. Each sequence header was labelled with its accession number and corresponding serotype.

### 7.2 Data Import and Preparation

The Biostrings package was used to import the FASTA file into R as a DNAStringSet object.

The number of sequences, sequence names, and sequence lengths were examined to verify that the data had been imported successfully.

Eight sequences were successfully loaded. Their lengths ranged from 10,643 to 10,736 nucleotides.

### 7.3 Nucleotide Frequency Analysis

The nucleotide frequencies of each sequence were calculated using the letterFrequency() function from Biostrings.

The analysis counted the occurrences of four nucleotides:

- Adenine (A)
- Thymine (T)
- Guanine (G)
- Cytosine (C)

The results were organized into a data frame containing the accession number, genome length, and nucleotide counts.

### 7.4 GC Content Analysis

GC content represents the percentage of guanine and cytosine nucleotides in a DNA sequence.

The following formula was used:

GC Content (%) = ((G + C) / (A + T + G + C)) × 100

The GC content was calculated separately for all eight sequences and added to the nucleotide analysis table.

### 7.5 Data Visualization

The ggplot2 package was used to create graphical representations of the sequence characteristics.

Two bar charts were generated:

1. Genome Length Comparison: compares the nucleotide lengths of the eight dengue virus sequences.
2. GC Content Comparison: compares the GC-content percentages of the eight sequences.

These visualizations help identify differences in genome length and nucleotide composition.

### 7.6 Multiple Sequence Alignment

Multiple sequence alignment was performed using the AlignSeqs() function from the DECIPHER package.

The purpose of alignment was to arrange corresponding nucleotide positions across the eight sequences. Gaps may be introduced to improve positional alignment.

The aligned sequences were saved in FASTA format for further analysis.

### 7.7 Genetic Distance Calculation

The ape package was used to calculate pairwise genetic distances between the aligned sequences.

The dist.dna() function was applied using the raw distance model. This calculates the proportion of compared nucleotide positions that differ between two sequences. Positions containing gaps or ambiguous nucleotides were excluded pairwise.

The resulting genetic distances were converted into an eight-by-eight distance matrix and saved as a CSV file.

A heatmap was created to visualize the genetic distances. Lower values indicate greater sequence similarity, while higher values indicate greater sequence difference.

### 7.8 Phylogenetic Tree Construction

A phylogenetic tree was constructed using the Neighbor-Joining method.

The nj() function from the ape package used the genetic distance matrix to estimate the tree. The resulting tree was plotted and saved as a PNG image. It was also exported in Newick format for reuse in other phylogenetic software.

## 8. Results and Findings

### 8.1 Sequence Length Results

The eight sequences had lengths ranging from 10,643 to 10,736 nucleotides.

The four primary reference sequences had the following lengths:

| Serotype | Primary accession | Sequence length |
|---|---|---:|
| DENV-1 | KM204119 | 10,736 |
| DENV-2 | KM204118 | 10,723 |
| DENV-3 | KU050695 | 10,696 |
| DENV-4 | KR011349 | 10,664 |

The results show that the selected dengue virus sequences have slightly different genome lengths.

### 8.2 GC Content Results

The calculated GC content values were:

| Serotype | First sequence | Second sequence | Average GC content |
|---|---:|---:|---:|
| DENV-1 | 46.74% | 46.80% | 46.77% |
| DENV-2 | 46.06% | 46.04% | 46.05% |
| DENV-3 | 46.69% | 46.64% | 46.67% |
| DENV-4 | 47.17% | 47.25% | 47.21% |

DENV-4 showed the highest average GC content, approximately 47.21%, while DENV-2 showed the lowest average GC content, approximately 46.05%.

DENV-1 and DENV-3 had relatively similar GC-content values.

### 8.3 Genetic Distance Results

The pairwise genetic distance analysis produced the following distances between the two selected sequences within each serotype:

| Serotype | Sequence pair | Genetic distance |
|---|---|---:|
| DENV-1 | KM204119 and EU848545 | 0.004195 |
| DENV-2 | KM204118 and AF038403 | 0.000933 |
| DENV-3 | KU050695 and M93130 | 0.002618 |
| DENV-4 | KR011349 and AY947539 | 0.000940 |

The DENV-2 pair had the lowest within-serotype genetic distance, followed closely by DENV-4. The DENV-1 pair had the highest within-serotype distance among the four pairs.

The distance matrix also showed larger distances between sequences belonging to different serotypes than between the two sequences within the same serotype.

### 8.4 Phylogenetic Tree Results

The Neighbor-Joining phylogenetic tree displayed eight sequence labels.

The two selected sequences belonging to each serotype formed a pair in the resulting tree:

- DENV-1: KM204119 and EU848545.
- DENV-2: KM204118 and AF038403.
- DENV-3: KU050695 and M93130.
- DENV-4: KR011349 and AY947539.

The tree topology was consistent with the low within-serotype genetic distances observed in the distance matrix. The DENV-1 and DENV-3 pairs were grouped together at a closer internal branching point in this particular tree.

These observations describe the selected dataset and should not be interpreted as a universal evolutionary classification of the four serotypes.

## 9. Discussion

The analysis demonstrated that R can be used to perform several important bioinformatics tasks, from sequence retrieval to phylogenetic tree construction.

The nucleotide frequency analysis showed that the selected dengue sequences differ in their nucleotide composition. GC-content comparison revealed that DENV-4 had the highest average GC content, while DENV-2 had the lowest.

The genetic distance analysis provided additional information about sequence similarity. The two sequences within each serotype had relatively low genetic distances compared with sequences from different serotypes. This indicates that the selected sequences within each serotype were more similar to one another than to the selected sequences from other serotypes.

The phylogenetic tree supported these observations by grouping the two sequences belonging to each serotype together. Therefore, the distance matrix and phylogenetic tree provided complementary views of the genetic relationships among the selected sequences.

However, the findings are limited to the eight sequences included in this study. The analysis does not represent the complete genetic diversity of all dengue virus strains worldwide.

## 10. Limitations

This project has several limitations:

1. Only eight dengue virus sequences were included in the analysis.
2. Only two sequences represented each serotype, which is insufficient to describe the full genetic diversity of each serotype.
3. The selected records have slightly different sequence lengths and may differ in their genomic coverage.
4. The raw genetic distance model does not correct for multiple substitutions occurring at the same nucleotide position.
5. The phylogenetic analysis used the Neighbor-Joining method without bootstrap support analysis.
6. The analysis was based on nucleotide sequences and did not include protein-level analysis or clinical information.

Future work could include a larger collection of dengue virus sequences, more detailed sequence quality checks, model-based evolutionary analysis, and statistical support for phylogenetic branches.

## 11. Conclusion

This project successfully demonstrated a comparative genomic analysis of four dengue virus serotypes using R.

Eight nucleotide sequences were collected from NCBI and analyzed through nucleotide frequency calculation, GC-content analysis, genome-length comparison, multiple sequence alignment, genetic distance calculation, and phylogenetic tree construction.

The results showed differences in nucleotide composition and genetic distances among the selected sequences. The Neighbor-Joining tree grouped the two selected sequences belonging to each serotype together, consistent with their low within-serotype genetic distances.

Overall, the project demonstrates how bioinformatics tools and R programming can be applied to biological sequence analysis and the investigation of genetic relationships among viral sequences.

## 12. Project Structure

```text
ICA3_Dengue_Bioinformatics/
│
├── code/
│   └── 01_dengue_analysis.R
│
├── data/
│   ├── dengue_reference_sequences.fasta
│   └── README.md
│
├── results/
│   ├── nucleotide_analysis.csv
│   ├── genome_length_comparison.png
│   ├── gc_content_comparison.png
│   ├── aligned_dengue_sequences.fasta
│   ├── genetic_distance_matrix.csv
│   ├── genetic_distance_heatmap.png
│   ├── phylogenetic_tree.png
│   └── phylogenetic_tree.nwk
│
├── README.md
├── report.Rmd
└── ICA3_Dengue_Bioinformatics.Rproj
```

## 13. References

1. Añez, G., Heisey, D. A., Volkova, E., and Rios, M. (2016). Complete Genome Sequences of Dengue Virus Type 1 to 4 Strains Used for the Development of CBER/FDA RNA Reference Reagents and WHO International Standard Candidates for Nucleic Acid Testing. *Genome Announcements*, 4(1), e01583-15. https://doi.org/10.1128/genomeA.01583-15

2. National Center for Biotechnology Information (NCBI). GenBank Nucleotide Database. https://www.ncbi.nlm.nih.gov/nuccore/

3. Paradis, E., and Schliep, K. (2019). ape 5.0: An environment for modern phylogenetics and evolutionary analyses in R. *Bioinformatics*, 35(3), 526–528. https://doi.org/10.1093/bioinformatics/bty633

4. Lawrence, M., Huber, W., Pagès, H., et al. (2013). Software for computing and annotating genomic ranges. *PLoS Computational Biology*, 9(8), e1003118. https://doi.org/10.1371/journal.pcbi.1003118

5. Wickham, H. (2016). *ggplot2: Elegant Graphics for Data Analysis*. Springer.

6. R Core Team. R: A Language and Environment for Statistical Computing. https://www.r-project.org/

---



Registration Number:2021/ICT/91

