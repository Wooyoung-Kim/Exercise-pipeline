# Cellranger Guide
## Quick start guide

Here is a quick start guide to installing Cell Ranger. For detailed instructions, please refer to the tutorial section below.

- Step 1 – Download and unpack the cellranger-x.y.z.tar.gz tar file in any location. In this example, we unpack it in a directory called /program
- ```bash
  mkdir program
  ```
  ```bash
  cd /program
  ```
  ```bash
  wget -O cellranger-9.0.0.tar.gz "https://cf.10xgenomics.com/releases/cell-exp/cellranger-9.0.0.tar.gz?Expires=1735839161&Key-Pair-Id=APKAI7S6A5RYOXBWRPDA&Signature=ezyaDFSgX-9FDmPDzKPm9iRqIXy0WcBLhz61QmHv9STXq09ZVgpKjC~pAWZAaEIeDg9oEvSHavlXRyqzMweVetwtesTAgW477SfYLAsoHbXaQVlzb0FhyEYqI1nOrbK8MVKjuklhelQyTchKudprvxxK~xJYerkwWLMWgTgCiwJxiHm-MX6YeoW3yLRsHEPqwF7Z3DhEgORF4En4fneBFXQa1N0DOXRK09wfya6izikowsa3woBEqU6qrIsd7YOYcldKPlSx~gKH04DkxbyqBaSKuzUR5WlFYIRA2s9csa2X~toui8KJqsqZoNe1Y9VLLPnOhEu8nR~8ODbVXo3jpA__"
  ```
  ```bash
  tar -xzvf cellranger-x.y.z.tar.gz
  ```
- Step 2 - unpack the reference annotation files in project folder
- ```bash
  cd ..
  ```
- ```bash
  mkdir scWAT
  ```
  ```bash
  cd /scWAT
  ```
  - Human reference
  ```bash
  wget "https://cf.10xgenomics.com/supp/cell-exp/refdata-gex-GRCh38-2024-A.tar.gz"
  ```
  ```bash
  tar -xzvf refdata-gex-GRCh38-2024-A.tar.gz
  ```
  -mouse reference
  ```bash
  wget "https://cf.10xgenomics.com/supp/cell-exp/refdata-gex-GRCm39-2024-A.tar.gz"
  ```
  ```bash
  tar -xzvf refdata-gex-GRCm39-2024-A.tar.gz
  ```
- Step 3 - cellranger count
- ```python
  import os
  import sys, glob
  sra_list = []  # 빈 리스트를 생성하여 줄을 저장할 준비
  with open("/data1/kwy/scWAT/scWAT_list.txt", 'r') as file:
     for line in file:
        sra_list.append(line.strip())  # 각 줄의 개행 문자(\n)를 제거하고 리스트에 추가
  for i in sra_list:
     os.system("~/data1/kwy/program/cellranger-9.0.0/cellranger count --id="+i+" --fastqs=/data1/kwy/scWAT --sample="+i + " --transcriptome=/data1/kwy/scWAT/refdata-gex-GRCm39-2024-A --create-bam=false --r1-length=26") #"--r1-length=26" that is optional
   ```
- --id : output folder name
- --fastqs : fastq file path
- --sample : *_S1_R1_001.fastq.gz file * name
- --transcriptome : reference annotation file path
