# Task 03 — Text Generation with Markov Chains


A simple statistical text-generation algorithm using Markov chains: a model that predicts the probability
of the next character or word based on the previous *n* character(s)/word(s), then chains predictions
together to generate new text.

## Overview

This project implements Markov chain text generation two ways:

1. **From scratch** — character-level and word-level n-gram tables built with plain Python
   (`collections.defaultdict` + `random.choice`), to show the underlying statistics directly.
2. **With `markovify`** — a widely used Python library that adds sentence-awareness on top of the same
   core idea, for more practical/readable output.

The corpus used is **"The Wonderful Wizard of Oz"** by L. Frank Baum (public domain, via Project
Gutenberg) — any plain text file can be substituted.

## Pipeline

1. **Load the corpus** — download and clean a public-domain text file.
2. **Character-level Markov chain** — build an n-gram → next-character table; generate text by chaining
   random weighted choices. Compare orders 2, 4, and 8.
3. **Word-level Markov chain** — same idea, one level up (n-gram of words → next word). Compare orders 1, 2, and 3.
4. **`markovify`** — sentence-aware generation with `state_size` (the library's term for order) 1, 2, and 3.
5. **Custom generation** — adjustable parameters to generate from your own text or settings.
6. **Save outputs** — write generated samples to `generated_text/samples.json`.

## Files

| File | Description |
|---|---|
| `Markov_Chain_Text_Generation.ipynb` | Main notebook — runs on CPU, no GPU needed |
| `requirements.txt` | Python dependencies |

## How to run

1. Open `Markov_Chain_Text_Generation.ipynb` in [Google Colab](https://colab.research.google.com/) (or
   run locally — no GPU required).
2. Run all cells top to bottom.

To use your own text, replace the corpus-download cell with:
```python
with open("your_text.txt", encoding="utf-8") as f:
    text = f.read()
```

## Key concepts demonstrated

- **N-gram order / state size** — how many previous characters or words the model looks at before
  predicting the next one. Low order → more novel but less coherent output; high order → safer grammar
  but closer to copying the source verbatim.
- **Character-level vs. word-level** — character-level chains can invent new "words" (sometimes
  nonsense); word-level chains always use real whole words but can produce odd sentence structure.
- **Weighted random choice** — the "chain" in Markov chain: at each step, the next token is chosen at
  random from all tokens that followed the current n-gram in the training text, weighted by frequency.


## Requirements

```
markovify
```

Install with:
```bash
pip install -r requirements.txt
```


