# Fine-tuning Gemma 3 to Use Tools
Example code for fine-tuning gemma-3-1b-it for function calling.

Resources:
- [YouTube Video](https://youtu.be/fAFJYbtTsC0)
- [Blog Post](https://medium.com/@shawhin/fine-tuning-llms-for-tool-use-5f1db03d7c55)
- [Training Data](https://huggingface.co/datasets/shawhin/tool-use-finetuning)
- [Fine-tuned Model](https://huggingface.co/shawhin/gemma-3-1b-tool-use) | [Original Model](https://huggingface.co/google/gemma-3-1b-it)

## Project Content
```bash
llm-tool-use-ft/
├── 1-gen_queries.ipynb
├── 2-gen_traces.ipynb
├── 3-data_prep.ipynb
├── 4-finetune_model.ipynb
├── 5-eval_model.ipynb
├── data/
│ ├── eval_results.csv
│ ├── eval_summary_by_type.csv
│ ├── eval_summary.csv
│ ├── modified_traces_.csv
│ ├── queries.csv
│ └── traces.csv
├── prompts/
│ ├── system_cot.md
│ └── system.md
├── utils/
│ ├── data_prep.py
│ ├── gen_data.py
│ ├── tool_calling.py
│ ├── tools.py
│ └── tools.yaml
├── data_viewer.py
├── pyproject.toml
├── requirements.txt
└── uv.lock
```

## How to Run

### Prerequisites
- Python 3.12 or higher
- [uv](https://docs.astral.sh/uv/) package manager

### Setup Instructions

1. **Install uv** (if not already installed):
   ```bash
   # On macOS/Linux
   curl -LsSf https://astral.sh/uv/install.sh | sh
   
   # On Windows
   powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
   ```

2. **Clone the repository**:
   ```bash
   git clone https://github.com/ShawhinT/llm-tool-use-ft.git
   cd llm-tool-use-ft
   ```

3. **Create and activate the environment**:
   ```bash
   uv venv
   source .venv/bin/activate
   uv sync
   ```

4. **Set up environment variables**:
   Create a `.env` file in the project root:
   ```bash
   echo "OPENAI_API_KEY=your_openai_api_key_here" > .env
   echo "HF_TOKEN=your_hf_api_key_here" > .env
   echo "TOGETHER_API_KEY=your_tai_api_key_here" > .env
   ```

5. **Launch JupyterLab**:
   ```bash
   uv run jupyter lab
   ```

### Running the Pipeline

Execute the notebooks in the following order:

1. **`1-gen_queries.ipynb`** - Generate training queries
2. **`2-gen_traces.ipynb`** - Generate tool use traces  
3. **`3-data_prep.ipynb`** - Prepare training data
4. **`4-finetune_model.ipynb`** - Fine-tune the model
5. **`5-eval_model.ipynb`** - Evaluate the fine-tuned model

### Optional: Data Viewer

To explore the generated data interactively:
```bash
uv run streamlit run data_viewer.py
```

### Alternative: Using requirements.txt

If you prefer using pip:
```bash
pip install -r requirements.txt
```
