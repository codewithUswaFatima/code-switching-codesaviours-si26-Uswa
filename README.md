# Code Switching NLP | Code Saviours SI-26 | Uswa

## Project 2 — Roman Urdu–English Code-Switching Dataset

This repo contains a word-level labelled dataset of naturally code-switched
Roman Urdu / English sentences, the kind of mixed language 230 million
Pakistanis actually type online (Twitter/X, Reddit, YouTube comments,
WhatsApp, Facebook).

### Contents
- `SI26-Week6-Uswa.ipynb` — Colab notebook that builds and exports the dataset
- `dataset.csv` — flat, word-level labelled dataset (word, label, source sentence)
- `DATASET_CARD.md` — full dataset documentation (also mirrored on HuggingFace)

### Label scheme
| Label | Meaning |
|-------|---------|
| `URD` | Word is Roman Urdu |
| `ENG` | Word is English |
| `MIX` | Hybrid/ambiguous token — an English loanword used with Urdu grammar/inflection, or a word that reads as either language in context |

### Links
- HuggingFace Dataset: `https://huggingface.co/datasets/122Uswa/code-switching-codesaviours-si26-Uswa`
- Colab Notebook: `SI26-Week6-Uswa.ipynb` (in this repo)

### How the data was collected
Sentences were compiled to reflect real Pakistani online code-switching
patterns (Twitter/X, Reddit r/pakistan, YouTube comments, WhatsApp chat
style, Facebook), combining common Roman Urdu clauses and everyday English
clauses the way they naturally appear together in casual conversation.
Personal/identifying information was excluded from any real message sources.
