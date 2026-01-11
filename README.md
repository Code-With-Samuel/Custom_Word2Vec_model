
# Train Custom Word2Vec Model (Game of Thrones sample)

This repository contains a small project and notebook for training a custom Word2Vec model on text files (sample Game of Thrones text slices) located in the `data/` folder.

**Contents**
- **`game_of_thrones_word2vec.ipynb`**: Jupyter notebook that demonstrates preprocessing, training a Word2Vec model, and evaluating word vectors.
- **`hello.py`**: Minimal script included for quick sanity checks or examples.
- **`data/`**: Plain-text input files used for training (e.g. `001ssb.txt`, `002ssb.txt`, ...).
- **`requirements.txt` / `pyproject.toml`**: Python dependencies.

## Summary

Train a custom Word2Vec embedding on your own corpus (here: sample GOT text files). The notebook shows how to:

- Load and clean text files from `data/`
- Tokenize and optionally filter stopwords
- Train a Word2Vec model with Gensim
- Save and explore resulting embeddings (nearest neighbors, vector arithmetic)

## Prerequisites

- Python 3.8+ recommended
- Git (optional)

Install dependencies:

```powershell
pip install -r requirements.txt
```

If you prefer a virtual environment on Windows (PowerShell):

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

## Data

Place plain text files in the `data/` directory. This repository already includes small example files:

- `data/001ssb.txt` ... `data/005ssb.txt`

Each file should contain one or more paragraphs of raw text. The notebook concatenates and preprocesses them before training.

## Usage

1. Open and run the notebook to interactively train and evaluate a Word2Vec model:

```powershell
jupyter notebook game_of_thrones_word2vec.ipynb
```

2. Or run small script examples (if provided) for quick checks:

```powershell
python hello.py
```

The notebook contains commented cells showing how to configure model hyperparameters (embedding size, window, min count, epochs) and how to save/load the trained model.

## Example (quick commands)

Train from the notebook and then run a quick Python snippet to print nearest neighbors:

```python
from gensim.models import Word2Vec
model = Word2Vec.load('word2vec.model')  # path used in the notebook example
print(model.wv.most_similar('king', topn=10))
```

Adjust the model path and target word to your trained artifacts.

## Notes and Recommendations

- If your corpus is small, lower `min_count` or increase `epochs` to improve learning.
- Consider lemmatization or preserving case depending on your downstream use.
- For larger corpora, train with more workers and use faster I/O.

## Files of interest

- [game_of_thrones_word2vec.ipynb](game_of_thrones_word2vec.ipynb) — Notebook to run and modify
- [hello.py](hello.py) — Example script
- [requirements.txt](requirements.txt) — Python dependencies

## Contributing

Contributions are welcome — submit issues or PRs with improvements (cleaning, model exporting, evaluation scripts).
