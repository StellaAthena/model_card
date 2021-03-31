---
language:
- en
thumbnail:
- https://www.eleuther.ai/images/eai_logo.png
tags:
- text generation
- pytorch
- the Pile
- causal-lm
license: apache-2.0
datasets:
- the Pile
---

# GPT-Neo 2.7B

## Model Description

GPT-Neo 2.7B is a transformer model designed using EleutherAI's replication of the GPT-3 architecture. GPT-Neo refers to the class of models, while 2.7B represents the number of parameters of this particular pre-trained model. It is the same size as OpenAI's "Ada" model.

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

GPT-Neo was trained as an autoregressive language model. This means that its core functionality is taking a string of text and predicting the next token. While language models are widely used for tasks other than this, there are a lot of unknowns with this work.

GPT-Neo was trained on the Pile, a dataset known to contain profanity, lewd, and otherwise abrasive language. Depending on your usecase GPT-Neo may produce socially unacceptable text. See Sections 5 and 6 of the Pile paper for a more detailed analysis of the biases in the Pile.

As with all language models, it is hard to predict in advance how GPT-Neo will respond to particular prompts and offensive content may occur without warning. We recommend having a human curate or filter the outputs before releasing them, both to censor undesirable content and to improve the quality of results.

## Training data

GPT-Neo 2.7B was trained on the Pile, a large scale curated dataset created by EleutherAI for the purpose of training this model.

## Training procedure

This model was trained for 400,000 steps on the Pile.

## Eval results

### Language Modeling Baselines

EleutherAI is currently in the process of carrying out further evaluations of GPT-Neo. The following table should be considered a work-in-progress. If you would like to contribute evaluations you have done, please reach out on our Discord.

| Model and Size   | Pile BPB      | Pile PPL      | Wikitext PPL.  |
| ---------------- | ------------- | ------------- | -------------- |
| GPT-Neo 1.3B     |  0.7527       | 6.159         | 13.10          |
| GPT-3 1.3B       |  ------       | -----         | -----          |
| GPT-2 1.5B       |  1.0468       | -----         | 17.48          |
| **GPT-Neo 2.7B** |  **0.7165**   | **5.646**     | **11.39**      |
| GPT-3 Ada 2.7B   |  0.9631       | -----         | -----          |
| GPT-3 175B       |  0.7177       | -----         | -----          |

All GPT-2 and GPT-3 scores are from their respective papers, except for the Pile test results which are from the Pile paper.

### Down-Stream Applications

### BibTeX entry and citation info

```bibtex
@article{gao2020pile,
  title={The Pile: An 800GB Dataset of Diverse Text for Language Modeling},
  author={Gao, Leo and Biderman, Stella and Black, Sid and Golding, Laurence and Hoppe, Travis and Foster, Charles and Phang, Jason and He, Horace and Thite, Anish and Nabeshima, Noa and others},
  journal={arXiv preprint arXiv:2101.00027},
  year={2020}
}
```
