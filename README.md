Code Switching NLP

Identifies whether each word in a mixed-language sentence is Roman Urdu, English, or a hybrid/ambiguous token.

Why this matters

Roman Urdu–English code-switching — mixing the two languages mid-sentence — is how millions of Pakistanis actually write online: on Twitter/X, Reddit, YouTube comments, and WhatsApp. Most NLP models are trained on clean, monolingual text, so they break down on this kind of naturally mixed input. Reliable word-level language identification is a building block for anything downstream that needs to actually understand this text — sentiment analysis, chatbots, content moderation, or search — for a huge, largely underserved user base.

Live Demo

https://huggingface.co/spaces/122Uswa/code-switching-language-id-uswa

Type a mixed Roman Urdu / English sentence and the app labels each word as URD, ENG, or MIX.

How it works

A pretrained multilingual model (xlm-roberta-base) was fine-tuned as a token classifier: it reads a sentence word by word and labels each one as Roman Urdu (URD), English (ENG), or a hybrid/ambiguous loanword (MIX) — e.g. an English word like "presentation" used inside an otherwise Urdu sentence. Training used a custom dataset of 191 naturally code-switched sentences (~2,000 labelled words), built from realistic Roman Urdu–English patterns plus a small set of real, redacted WhatsApp messages.

Results
Label	F1 Score
URD (Roman Urdu)	0.9953
ENG (English)	0.9898
MIX (hybrid/loanword)	0.7500

Overall F1: 0.9904 · Overall Accuracy: 0.9904

The model is very strong on clearly Urdu or clearly English words. The MIX class is the hardest — as expected, since ambiguous loanwords are genuinely harder to label even for humans — and is the clearest area for improvement with more MIX-labelled training examples.

How to run locally
bash
pip install transformers torch
python
from transformers import AutoTokenizer, AutoModelForTokenClassification
import torch

tokenizer = AutoTokenizer.from_pretrained("122Uswa/code-switching-codesaviours-si26-uswa")
model = AutoModelForTokenClassification.from_pretrained("122Uswa/code-switching-codesaviours-si26-uswa")

words = ["Aaj", "mera", "presentation", "hai", "bhai"]
inputs = tokenizer(words, is_split_into_words=True, return_tensors="pt")
with torch.no_grad():
    logits = model(**inputs).logits
preds = torch.argmax(logits, dim=2)[0].tolist()
print(preds)  # map back to URD/ENG/MIX using model.config.id2label
Demo Video

Loom walkthrough

Built by: Uswa Fatima | Code Saviours SI-26 | 2026
