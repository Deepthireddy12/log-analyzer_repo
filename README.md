# Log Analyzer LLM

This repository contains everything needed to fine-tune Mistral-7B on JSONL application logs using LoRA, merge the adapters, convert to GGUF for Ollama, and run inference.

-------------------------------------

## Repository Structure
log-analyzer_repo/
├── README.md
├── .gitignore
├── input_data/
│ └── order_logs.jsonl # sample log entries
├── scripts/
│ ├── LLM_finetune.ipynb # fine-tune, merge, convert end-to-end, download
│ ├── LLM_finetune.py
│ ├── Videos
    └── execution # execution on prompt

------------------------------------

## Prerequisites

- **Python 3.8+**  
- **CUDA-enabled GPU** (≥16 GB VRAM recommended for FP16 training)  
- **Docker** (for OpenWebUI)  
- **Ollama** installed and running on your machine  
- **Git** for version control  

------------------------------------

## Installation

1. **Clone the repo**  
   ```bash
   git clone <your-repo-url>
   cd log-analyzer-repo

-------------------------------------

## Input data

The folder has the input data that I used to fine tune purpose. Upload the jsonl while running your code.(to your collab environment if using collab)

--------------------------------------

## Running inference

Run quick sanity checks in pure Python:

python scripts/inference.py data/order_logs_sample.jsonl

-----------------------------------------

## Ollama Deployment and running

-Open command prompt and run the following commands to see the output

mkdir -p ~/.ollama/models/log-analyzer 
mv log-analyzer.gguf ~/.ollama/models/log-analyzer/log-analyzer.gguf

ollama create log-analyzer -f Modelfile
ollama run  log-analyzer

## I already have modelfile for the .gguf model placed in the "log-analyzer_" folder. Download the .gguf model from code execution

------------------------------------------

## Input format in command prompt

### Instruction:
Analyze the following application logs to identify number of errors, order flow, and trace IDs for failures.

### Input:

### Response:
 
Give some chunk of data from our jsonl file provided after ###Input:

---------------------------------------------
