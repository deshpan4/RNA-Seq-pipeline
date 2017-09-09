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
## Prerequisites
Following tools should be installed before executing this pipeline on the host system:
* samtools
* cufflinks version 2.2.1
* Tophat2 version 2.2.1
* FastQC
* cutadapt
* HTSeq
* Bowtie2
* R version 3.3 or higher
## Download
Use git clone:
```
git clone https://github.com/deshpan4/RNA-Seq-pipeline
```
## Download
