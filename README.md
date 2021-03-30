---
language:
- en
thumbnail: https://www.eleuther.ai/images/eai_logo.png
tags:
- text generation
- pytorch
- the Pile
- causal-lm
license: apache-2.0
datasets:
- the Pile
---

# GPT Neo 2.7B

It was released on EleutherAI's [GitHub page](https://github.com/EleutherAI/gpt-neo) the 21st of March 2021.

## Model Description

GPT Neo is a transformers model pretrained on a very large corpus of English data in a self-supervised fashion. This means it was pretrained on the raw texts only, with no humans labeling them in any way (which is why it can use lots of publicly available data) with an automatic process to generate inputs and labels from those texts. More precisely, inputs are sequences of continuous text of a certain length and the targets are the same sequence, shifted one token (word or piece of word) to the right. The model uses internally a mask-mechanism to make sure the predictions for the token i only uses the inputs from 1 to i but not the future tokens.

It obtains a 5.646 perplexity on The Pile, and a 11.39 perplexity on Wikitext

It uses a mix of global and local attention across its layers. It was trained for 400000 steps.

## Intended Use and Limitations

This way, the model learns an inner representation of the English language that can then be used to extract features useful for downstream tasks. The model is best at what it was pretrained for however, which is generating texts from a prompt.

### How to use

You can use this model directly with a pipeline for text generation. This example generates a different sequence each time it's run:

```py
>>> from transformers import pipeline
>>> generator = pipeline('text-generation', model='EleutherAI/gpt-neo-2.7B')
>>> generator("EleutherAI has", do_sample=True, min_length=50)

[{'generated_text': 'EleutherAI has made a commitment to create new software packages for each of its major clients and has'}]
```

### Limitations and Biases

## Training data

## Training procedure

## Eval results

### BibTeX entry and citation info

```bibtex
@inproceedings{...,
  year={2020}
}
```
