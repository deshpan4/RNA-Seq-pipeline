# RNA-Seq-pipeline
An RNA-Seq pipeline for analysis of *Arabidopsis Thaliana* time-series datasets
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
* Obtaining differentially expressed common genes between Cuffdiff, DESeq and edgeR in individual sample pairs
* Obtaining differentially expressed common genes between Cuffdiff, DESeq and edgeR expressed in more than one sample pairs
## Download
Use git clone:
```
git clone https://github.com/deshpan4/RNA-Seq-pipeline
```
## Installation
Download the folder using 'git clone' command. Make sure all the dependencies are installed before running the pipeline.
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
Follow the steps mentioned in Pipeline.pdf file. This file contains detailed instructions and example commands for running the pipeline as well as post analysis scripts.
