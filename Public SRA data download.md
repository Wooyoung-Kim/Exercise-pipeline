
# SRA Data Download Guide

This repository provides a comprehensive guide for downloading public SRA (Sequence Read Archive) data using SRA Toolkit and alternative methods. Follow the steps below to download and manage your data efficiently.

---

## Step 1: Install Anaconda

- Download and install the Anaconda from the [Anaconda](https://www.anaconda.com/download).
- Follow the installation instructions for your operating system (Linux, macOS, Windows).

## Step 2: Set Up Environment

Run the following command to set up your environment:
```bash
conda create -n sra_env python=3.9 -y 
```

## Step 3: Install SRA Toolkit

Activate the environment and install SRA Toolkit using:
```bash
conda activate sra_env
conda install -c bioconda -c conda-forge sra-tools
```

## Step 4: Download SRA Data

### Option 1: Manual Download
1. Activate your environment:
    ```bash
    conda activate sra_env
    ```
2. Download the SRA data using prefetch:
    ```bash
    prefetch --progress SRR15702754
    ```
3. Convert the SRA data to FASTQ format:
    ```bash
    fastq-dump --split-files --gzip SRR15702754/SRR15702754.sra
    ```

### Option 2: Automatic Download Using Python Script

Ensure you have an accession list file ready (e.g., `SRR_Acc_List.txt`). Use the script below:

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

## Common Issues and Tips

1. **Slow Download Speeds**
   - Use a faster internet connection or try downloading at off-peak hours.

2. **Environment Variable Issues**
   - Ensure your `PATH` is correctly set to include the SRA Toolkit binaries.

3. **File Not Found Errors**
   - Double-check the file paths and ensure all required files exist.

---

Happy Data Analysis!
