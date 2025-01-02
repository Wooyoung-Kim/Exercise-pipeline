# Cellranger Guide

This repository provides a comprehensive guide for downloading public SRA (Sequence Read Archive) data using SRA Toolkit and alternative methods. Follow the steps below to download and manage your data efficiently.

---

## Prerequisites

1. **Install cellranger**
   - Download and install the cellranger from the [10X genomics]
```bash
#install cellranger
wget -O cellranger-9.0.0.tar.gz "https://cf.10xgenomics.com/releases/cell-exp/cellranger-9.0.0.tar.gz?Expires=1735839161&Key-Pair-Id=APKAI7S6A5RYOXBWRPDA&Signature=ezyaDFSgX-9FDmPDzKPm9iRqIXy0WcBLhz61QmHv9STXq09ZVgpKjC~pAWZAaEIeDg9oEvSHavlXRyqzMweVetwtesTAgW477SfYLAsoHbXaQVlzb0FhyEYqI1nOrbK8MVKjuklhelQyTchKudprvxxK~xJYerkwWLMWgTgCiwJxiHm-MX6YeoW3yLRsHEPqwF7Z3DhEgORF4En4fneBFXQa1N0DOXRK09wfya6izikowsa3woBEqU6qrIsd7YOYcldKPlSx~gKH04DkxbyqBaSKuzUR5WlFYIRA2s9csa2X~toui8KJqsqZoNe1Y9VLLPnOhEu8nR~8ODbVXo3jpA__"
```
#install reference annotation file
```bash
#Human
wget "https://cf.10xgenomics.com/supp/cell-exp/refdata-gex-GRCh38-2024-A.tar.gz"
```
```bash
#mouse
wget "https://cf.10xgenomics.com/supp/cell-exp/refdata-gex-GRCm39-2024-A.tar.gz"
```
   - Follow the installation instructions for ubuntu server
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
  mkdir project
  cd /project
- 
