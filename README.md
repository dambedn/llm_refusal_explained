# llm_refusal_explained

We use [uv](https://docs.astral.sh/uv/), instead of pip/conda/mamba, to manage Python and dependencies.

### Local
```bash
git clone https://github.com/dambedn/llm_refusal_explained.git
cd llm_refusal_explained
uv sync --group local        # creates .venv from uv.lock (Python 3.12)
uv run nbstripout --install  # strips notebook outputs on commit
```
Run code with `uv run python script.py`, or select `.venv` as the kernel in your IDE.

### Adding a package
```bash
uv add <package>             # runtime dependency
```
Commit `pyproject.toml` and `uv.lock` together. Then refresh the Colab file:
```bash
uv export --no-hashes --no-dev --no-emit-project -o requirements-colab.txt
```

### Colab
First cell of each notebook:
```python
!git clone https://github.com/dambedn/llm_refusal_explained.git 2>/dev/null || (cd llm_refusal_explained && git pull)
%cd llm_refusal_explained
!pip install -q -r requirements-colab.txt
```
Colab's preinstalled torch is used. The Hugging Face token goes in Colab Secrets (`HF_TOKEN`), never in the repo.