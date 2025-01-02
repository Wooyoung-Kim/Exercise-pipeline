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
   - 
