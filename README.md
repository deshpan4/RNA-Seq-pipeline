# RNA-Seq-pipeline
An RNA-Seq pipeline for analysis of Arabidopsis Thaliana datasets
## Getting Started
These instructions will help you to run the RNA-Seq pipeline from linux environment
The RNA-Seq pipeline performs the following tasks:
* File conversion from SRA to FastQ
* Perform quality metric using FastQC
* Adapter and Quality Trimming
* Read Alignment using Tophat2
* Read counting using HTSeq
* Differential Gene Expression using Cufflinks
* Differential Gene Expression using DESeq
* Differential Gene Expression using edgeR
* Alternative splicing analysis using spliceR
## Download
Use git clone:
```
git clone https://github.com/deshpan4/RNA-Seq-pipeline
```
## Installation
Download the RNA-Seq pipeline scripts using 'git clone' command. Make sure all the dependencies are installed before running the pipeline.
## Prerequisites
Following tools should be installed before executing this pipeline on the host system:
* samtools
* cufflinks version 2.2.1
* Tophat2 version 2.2.1
* FastQC
* cutadapt
* HTSeq
* Bowtie2
* [Index and annotation for A.thaliana](ftp://igenome:G3nom3s4u@ussd-ftp.illumina.com/Arabidopsis_thaliana/Ensembl/TAIR10/Arabidopsis_thaliana_Ensembl_TAIR10.tar.gz)
* [Blat](https://users.soe.ucsc.edu/~kent/src/blatSrc35.zip)
* R version 3.3 or higher
### R packages
* DESeq
* edgeR
* spliceR
* BSgenome
## Usage
Step-1: Run Data Processing pipeline
```
bash pipeline_Data_Processing.sh
```
Step-2: Transcript assembly
```
bash runCufflinks.sh
```
Step-3: Construct assembly file
For merging cufflinks assemblies, an assembly text file is required. For example, for samples [SRX765602](https://www.ncbi.nlm.nih.gov/sra/SRX765602[accn]) and [SRX765948](https://www.ncbi.nlm.nih.gov/sra/SRX765948[accn]), no replicates are available. Therefore, write the following information to text file using notepad or text editor.
```
/sample_SRR1659921_SRR1659922/3-Cufflinks/file-1-2-cufflinks/transcripts.gtf
/sample_SRR1660397_SRR1660398/3-Cufflinks/file-1-2-cufflinks/transcripts.gtf
```
For example, for [SRX765602](https://www.ncbi.nlm.nih.gov/sra/SRX765602[accn]), [SRX1068195](https://www.ncbi.nlm.nih.gov/sra/SRX1068195[accn]) and [SRX767119](https://www.ncbi.nlm.nih.gov/sra/SRX767119[accn]), where there are replicates available. Therefore, write the following information to text file using notepad or text editor.
```
/home/sample_SRR1659921_SRR1659922/3-Cufflinks/file-1-2-cufflinks/transcripts.gtf
/home/sample_SRR2073174_SRR2073176/3-Cufflinks/file-1-2-cufflinks/transcripts.gtf
/home/sample_SRR1661473_SRR1661474/3-Cufflinks/file-1-2-cufflinks/transcripts.gtf
```
Step-4: Compute Differential Gene Expression using Cuffdiff
```
bash computeDGEusingCuffdiff.sh
```
Step-5: Generate read counts using HTSeq
```
bash generateReadCounts.sh
```
Step-6: If the samples have biological replicates, then run the following script
```
bash computeDGEusing_DESeq_edgeR_withReplicates.sh
```
If the samples do not have biological replicates, then run the following script
```
bash computeDGEusing_DESeq_edgeR_noReplicates.sh
```
Step-7: Construct BSgenome package for A.thaliana TAIR10 data
However, there is already BSgenome package availabe in CRAN 'BSgenome.Athaliana.TAIR.TAIR9', but we recommend users to construct TAIR10 version of BSgenome which can be constructed using following steps.

Convert genome FASTA to 2bit
```
faToTwoBit genome.fa athalianaTAIR10.2bit
```

Set the 'seqs_srcdir:' in 'BSgenome.Athaliana.TAIR.TAIR10-seed' file (which is available in Genome folder) by adding the path to wherever the athalianaTAIR10.2bit file is located.

In R run the following command:

```
setwd("/path/to/seed/file")
library(BSgenome)
forgeBSgenomeDataPkg(BSgenome.Athaliana.TAIR.TAIR10-seed)
```


Step-8: Alternative splicing analysis using spliceR
```
bash computeDGEusing_DESeq_edgeR_noReplicates.sh
```
