# llm_refusal_explained

We use [uv](https://docs.astral.sh/uv/) locally, and pip for Colab usage. All the .ipynb notebooks for Phase_1_no_AI, plus the notebooks/01_data_inspection.ipynb notebook were checked in colab. It might well be that the current uv version to run it locally is not sufficient, please update if necessary.


## Task
Our task revolves around the differentiation between refusal/overrefusal for unsafe/safe prompts within the Gemma family based on the XSTest dataset (see more below).

Whilst one of our subteams (AI) confronted themselves with investigating how the input and output patterns change when varying the initial input prompt (i.e., instructing the LLM to be helpful versus overly secure), the other subteam (non-AI) compared different models within the Gemma 3 family (specifically the 1b, 4b and 12b model) and investigated how their safety behavior varies when model complexity increases.

## Model(s)
We primarily made use of and investigated the Gemma 3 model family (https://deepmind.google/models/gemma/gemma-3/). As stated above, various Gemma 3 models were employed. Their reactions on the prompts of the XSTest dataset were investigated. 
For prompt embedding and LLM as a judge output categorization (was the prompt refused or answered?) further models were used. In the case of the (no-AI) team, for prompt embedding nomic-embed-text-v1.5 (https://huggingface.co/nomic-ai/nomic-embed-text-v1.5) was used (we also tried Qwen/Qwen3-Embedding-4B but finally chose the former). The role of the LLM as a judge was completed by an OpenAI Luna model for the no-AI team.

## Dataset(s)
Our group made use of the XSTest datset (Röttger et al., 2024), CC BY 4.0 (https://creativecommons.org/licenses/by/4.0/), see: github.com/paul-rottger/xstest which includes a collection of various safe and unsafe prompts and their contentwise categorization. 

## Important note on safety
Since we only used a LLM as a judge to verify the models' outputs we, to the best of our knowledge, do not publish complete model replies in our work in order to safeguard the public from potentially harmful content. Even though these answers are interesting in their own right, only their embeddings and the respective input prompts will be published to enable the replication of most of the work.  


## Set up
### Local
```bash
git clone https://github.com/dambedn/llm_refusal_explained.git
cd llm_refusal_explained
uv sync --group local        # creates .venv from uv.lock (Python >=3.12)
#uv run nbstripout --install  # strips notebook outputs on commit
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