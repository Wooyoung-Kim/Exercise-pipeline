
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
# SRA 데이터 다운로드 및 처리 자동화 스크립트

import os

# SRA ID 목록 파일 경로 설정
accession_file = "/Users/wy/Exercise_scRNAseq/SRR_Acc_List.txt"

try:
    # 파일 읽기 및 SRA ID 저장
    with open(accession_file, 'r') as file:
        sra_list = [line.strip() for line in file]
    
    # SRA 데이터 다운로드 및 변환
    for sra_id in sra_list:
        print(f"Processing {sra_id}...")
        os.system(f"prefetch --progress {sra_id}")
        os.system(f"fastq-dump --split-files --gzip {sra_id}/{sra_id}.sra")
        os.system(f"rm -r {sra_id}/")
    print("All processes completed successfully.")
except FileNotFoundError:
    print(f"Error: File not found - {accession_file}")
except Exception as e:
    print(f"An unexpected error occurred: {e}")
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
