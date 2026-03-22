# AnalystAI: AI Powered Data Analyst

> Ask questions in plain English about LA Metro Bike Share 2024 data and get SQL queries, interactive charts, and AI insights instantly.


## What is AnalystAI?

AnalystAI is an end-to-end AI powered data analyst built on top of a fine-tuned Llama 3.2 3B model. It eliminates the need for SQL knowledge — users simply ask questions in plain English and instantly receive:

- Auto-generated SQL queries
- Interactive charts (bar, line, pie)
- AI-generated data insights
- Downloadable results (CSV and Excel)

## Project Structure
```
AnalystAI/
  notebooks/
    t2s_dataset_creation.ipynb   Text2SQL training dataset creation
    t2s_training.ipynb           QLoRA fine-tuning of Llama 3.2 3B
    t2s_evaluation.ipynb         Model evaluation on Spider benchmark
    bs_data_preparation.ipynb    LA Metro Bike Share data preparation
    analyst_app.ipynb            Main Gradio application
  database/
    README.md                    Database schema documentation
```

## Tech Stack

| Component | Technology |
|-----------|------------|
| LLM | Llama 3.2 3B (fine-tuned with QLoRA) |
| Training | Unsloth + TRL + PEFT |
| Database | SQLite |
| Charts | Plotly |
| App | Gradio |
| Data | LA Metro Bike Share 2024 |

## Model

Fine-tuned Llama 3.2 3B using QLoRA on 7,300 Text-to-SQL examples combining Spider benchmark and LA Metro Bike Share domain-specific queries.


**Model on HuggingFace:** [Krupa1420/text2sql-llama3-qlora](https://huggingface.co/Krupa1420/text2sql-llama3-qlora)

## Dataset

Real LA Metro Bike Share 2024 data cleaned and published on HuggingFace.

| Table | Rows | Description |
|-------|------|-------------|
| trips | 519,235 | All bike trips in 2024 |
| stations | 226 | Active station locations |
| weather | 8,784 | Hourly LA weather data |

**Dataset on HuggingFace:** [Krupa1420/la-metro-bikeshare-2024](https://huggingface.co/datasets/Krupa1420/la-metro-bikeshare-2024)

**Text2SQL Training Dataset:** [Krupa1420/text2sqldata](https://huggingface.co/datasets/Krupa1420/text2sqldata)

## Example Queries

| Question | Type |
|----------|------|
| How many trips were taken in total? | Simple |
| How many trips were taken each month? | Line Chart |
| What are the top 10 busiest stations? | Bar Chart |
| How many electric vs standard bike trips? | Pie Chart |
| Which station had the most trips on rainy days? | Triple JOIN |
| What is the average trip duration on rainy vs sunny days? | Weather JOIN |

## How to Run

### Step 1 - Clone repo
```bash
git clone https://github.com/Krupa1420/AnalystAI.git
cd AnalystAI
```

### Step 2 - Install dependencies
```bash
pip install unsloth gradio plotly pandas openpyxl torch transformers
```

### Step 3 - Download database
```python
from huggingface_hub import hf_hub_download

db_path = hf_hub_download(
    repo_id   = "Krupa1420/la-metro-bikeshare-2024",
    filename  = "bikeshare_2024.sqlite",
    repo_type = "dataset"
)
```

### Step 4 - Run the app
Open `notebooks/analyst_app.ipynb` and run all cells.

## Architecture
```
User Question (plain English)
        |
Fine-tuned Llama 3.2 3B (Text-to-SQL)
        |
SQL Query generated
        |
SQLite Database (519K real trips)
        |
Results + Chart + AI Insight
```

## Author

**Krupa Patel**
MS Computer Science — California State University Northridge

[![HuggingFace](https://img.shields.io/badge/HuggingFace-Krupa1420-yellow)](https://huggingface.co/Krupa1420)
[![GitHub](https://img.shields.io/badge/GitHub-Krupa1420-black)](https://github.com/Krupa1420)
