# llm_refusal_explained

We use [uv](https://docs.astral.sh/uv/) locally, and pip for Colab usage.


## Task

## Model(s)

## Dataset(s)

## Set up
### Local
```bash
git clone https://github.com/dambedn/llm_refusal_explained.git
cd llm_refusal_explained
uv sync --group local        # creates .venv from uv.lock (Python >=3.12)
uv run nbstripout --install  # strips notebook outputs on commit
```
Run code with `uv run python script.py`, or select `.venv` as the kernel in your IDE.

### Adding a package
```bash
uv add <package>             # runtime dependency
```
Commit `pyproject.toml` and `uv.lock` together. 

### Colab
To open a notebook which is on github:
  [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/dambedn/llm_refusal_explained/blob/main/PATH/TO/notebook.ipynb)
  
Change PATH/TO/notebook.ipynb with relative path from repo root.

First cell of each notebook:
```python
!git clone https://github.com/dambedn/llm_refusal_explained.git 2>/dev/null || (cd llm_refusal_explained && git pull)
%cd llm_refusal_explained
!pip list --format=freeze | grep -v -i -E "^(transformers|accelerate|datasets)==" > /content/constraints.txt
!pip install -q -r requirements-colab.txt -c /content/constraints.txt
```
Colab's preinstalled torch is used. The Hugging Face token goes in Colab Secrets (`HF_TOKEN`), never in the repo.
## Project structure

- `notebooks/`: original shared starter notebook.
- `phase-1/no-ai/`: Phase I no-AI notebook and shareable analysis. Run the analysis notebook with `phase-1/no-ai/analysis/` as the working directory so its data files are found.
- `phase-1/ai-assisted/`: Phase I inference, judging and analysis notebooks. These use the notebook working directory for their data and outputs; the analysis expects six CSV files under `outputs/judged/`, which are not included.
- `phase-2/`: reserved for Phase II.
- `ai-interactions/`: AI interaction records.

The original notebooks retain their code and saved outputs; review their input paths and outputs before running or publishing them.
