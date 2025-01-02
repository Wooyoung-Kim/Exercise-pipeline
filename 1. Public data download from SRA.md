# SRA Data Download Guide

This repository provides a comprehensive guide for downloading public SRA (Sequence Read Archive) data using SRA Toolkit and alternative methods. Follow the steps below to download and manage your data efficiently.

---

## Prerequisites

1. **Install Anaconda**
   - Download and install the Anaconda from the [Anaconda](https://www.anaconda.com/download).
   - Follow the installation instructions for your operating system (Linux, macOS, Windows).

2. **Setting Environment**
   - Run the following command to set up your environment:
     ```bash
     conda create -n sra_env python=3.9 -y 
     ```
3. **SRA toolkit download**

   ```bash
   # Example for MacOS terminal
   conda activate sra_env
   conda install -c bioconda -c conda-forge sra-tools
   ```
## Basic Usage

1. **Download public SRA data**
   ```bash
   conda activate sra_env
   #prefetch --progress [SRA accesion number]
   prefetch --progress SRR15702754
   ```
   ```bash
   fastq-dump --split-files --gzip SRR15702754/SRR15702754.sra
   ```
2. **Automatic download**
   - Using python script
   - download accession list file from the [SRA] (https://www.ncbi.nlm.nih.gov/Traces/study/?acc=SRP335420&o=acc_s%3Aa)
   ```python
   import os
   import sys, glob

   # samples
   sra_list = []  # 빈 리스트를 생성하여 줄을 저장할 준비
   Acc = "/Users/wy/Exercise_scRNAseq/SRR_Acc_List.txt"
   with open(Acc, 'r') as file:
       for line in file:
           sra_list.append(line.strip())  # 각 줄의 개행 문자(\n)를 제거하고 리스트에 추가
           
   for i in sra_list:
       os.system("prefetch --progress "+i) #download
       os.system("fastq-dump --split-files --gzip " + i+"/"+i+".sra")
       os.system("rm -r " + i + "/")
   ```
