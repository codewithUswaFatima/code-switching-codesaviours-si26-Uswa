---
license: cc-by-4.0
language:
- ur
- en
tags:
- code-switching
- roman-urdu
- pakistani-english
- sequence-labeling
task_categories:
- token-classification
pretty_name: Code Switching Codesaviours SI26
---

# Code-Switching Dataset: Roman Urdu ↔ English (Pakistan)

## Dataset Description

This dataset contains **180 naturally code-switched sentences** (well above
the 150 minimum) blending **Roman Urdu** and **English**, the way Pakistani
speakers actually write online. Every word in every sentence is labelled at
the token level, making this a word-level **sequence labelling / language
identification** dataset for code-switched text.

Roman Urdu–English mixing is extremely common in Pakistani digital
communication (Twitter/X, Reddit, YouTube comments, WhatsApp, Facebook) but
is poorly handled by most existing NLP models, which are trained on
monolingual corpora. This dataset is a small step toward closing that gap.

## How it was collected

The dataset combines two sources:

1. **180 constructed sentences** built from common Roman Urdu clauses
   ("Aaj mera mood nahi hai", "Bhai kal mera presentation hai") combined
   with everyday English clauses ("still not prepared at all", "I was
   literally waiting for you") in natural conjunction patterns, plus
   additional hand-written naturalistic examples.
2. **11 real sentences** collected from the author's own WhatsApp chats
   (covering casual, academic/FYP-related, and tech-support conversation),
   manually redacted of names and identifying details before inclusion.

No personally identifying information is included in either source.

## Dataset Structure

Flat CSV, one row per **word**:

| column     | description                                   |
|------------|------------------------------------------------|
| `sentence` | the full original mixed-language sentence      |
| `word`     | a single token from that sentence               |
| `label`    | `URD`, `ENG`, or `MIX` — see below               |

## Label Meanings

- **URD** — the word is Roman Urdu (e.g. `bohot`, `nahi`, `hai`, `karna`)
- **ENG** — the word is English (e.g. `meeting`, `honestly`, `deadline`)
- **MIX** — a hybrid/ambiguous token: typically an English loanword used
  inside an Urdu grammatical frame (e.g. `presentation`, `mood`, `scene`
  appearing mid-Urdu-clause), or a word whose language identity is genuinely
  ambiguous without broader context

## Stats

- **191** unique sentences (180 constructed + 11 collected from real WhatsApp chats)
- **2,025** word-level labelled entries
- Roughly balanced ENG/URD split (~1,000 each), with a smaller set of MIX
  tokens capturing loanword code-mixing specifically

## Intended Use

- Training/evaluating token-level language identification models for
  code-switched Roman Urdu–English text
- Pretraining data augmentation for Pakistani-English NLP tools
- Linguistic research on code-switching patterns

## Limitations

- Sentences are representative/naturalistic constructions rather than a raw
  scrape of live social media, so they may not capture every dialectal
  variation, spelling inconsistency, or platform-specific slang found in the
  wild. Users building production systems should supplement with real,
  consented social-media data.
- Roman Urdu has no standardized spelling — this dataset uses common
  transliteration conventions but variants exist.

## Author

Uswa — Code Saviours SI-26, Project 2
