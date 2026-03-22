# AnalystAI — AI-Powered Data Analyst

Ask questions in plain English about LA Metro Bike Share 2024 data and get SQL queries, interactive charts, and AI insights instantly.


## What it does
- Converts plain English questions to SQL automatically
- Executes queries on real LA Metro Bike Share 2024 data
- Generates interactive charts (bar, line, pie)
- Provides AI-generated insights using fine-tuned Llama 3.2 3B
- Download results as CSV or Excel

## Tech Stack
- **LLM** : Llama 3.2 3B fine-tuned with QLoRA
- **Data** : LA Metro Bike Share 2024 (519K trips, 226 stations)
- **Charts** : Plotly
- **App** : Gradio
- **DB** : SQLite

## Project Structure
```
AnalystAI/
  notebooks/
    t2s_dataset_creation.ipynb  - Text2SQL dataset creation
    t2s_training.ipynb          - QLoRA fine-tuning
    t2s_evaluation.ipynb        - Model evaluation
    bs_data_preparation.ipynb   - Bike Share data preparation
    analyst_app.ipynb           - Main Gradio app
  database/
    README.md                   - Database documentation
```

## HuggingFace
- Model : [Krupa1420/text2sql-llama3-qlora](https://huggingface.co/Krupa1420/text2sql-llama3-qlora)
- Dataset : [Krupa1420/la-metro-bikeshare-2024](https://huggingface.co/datasets/Krupa1420/la-metro-bikeshare-2024)

## How to Run
```bash
git clone https://github.com/Krupa1420/AnalystAI.git
cd AnalystAI
pip install unsloth gradio plotly sqlite3 pandas openpyxl
```

Open `notebooks/analyst_app.ipynb` and run all cells.

## Author
Krupa Patel | MS Computer Science — Cal State Northridge
