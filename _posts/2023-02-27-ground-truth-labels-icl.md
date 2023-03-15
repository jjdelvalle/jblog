---
layout: post
title:  "Ground Truth Labels and In-context Learning"
date:   2023-02-27 14:03
categories: nlp icl few-shot
hasmath:   "true"
toc: true
hidden: true
---

With the introduction of pre-trained models and their adaption to downstream tasks {% cite howard2018universal devlin-etal-2019-bert inter-alia %}, the natural language processing (NLP) field has had its imagenet-moment. Moreover, in-context learning (ICL) {% cite NEURIPS2020_1457c0d6 %} has proven to be another great game-changer on top of pre-trained languages. However, not a lot of work has gone into exploring why ICL works and what elements are crucial to its performance. In this blog post, I go over some literature exploring why, how and when ICL works {% cite min-etal-2022-rethinking yoo-etal-2022-ground wei2023larger %}.

## Background

A few years ago, taking advantage of pre-trained languages became the way to approach a new task; by either adapting knowledge or fine-tuning the pre-trained model {% cite howard2018universal peters-etal-2018-deep inter-alia %} you could achieve state of the art performance. The battles of pre-trained languages, with their growing sizes began.

In 2020, {% cite NEURIPS2020_1457c0d6 %} introduced what they call in-context learning (ICL) as a concept for sufficiently large models. The authors propose GPT-3, a model trained on a causal language modeling task on massive amounts of data. The resulting model shows the ability of ICL. ICL consists on models getting a prompt with instructions for the task to be carried out. Additionally, examples of the task done successfully can also included. The performance of ICL is suprisingly good and best of all: no parameter updating happens.

## The Premise

We will first look at in-context learning as presented originally {% cite NEURIPS2020_1457c0d6 %}. Figure 1 shows a sample input illustrating how in-context learning is usually done. Generally a task description is included, examples can be included, and finally a prompt with the input for which a prediction is desired.

<figure>
  <a href="{{site.url}}/assets/icl_gpt3paper.png"><img src="{{site.url}}/assets/icl_gpt3paper.webp" alt="ICL input example"/></a>
  <figcaption>Fig. 1: In-context learning as presented originally.</figcaption>
</figure>

The original paper calls this specific input an example of few-shot in-context learning. From this example we can infer that we can study at least the following aspects of ICL:

1. Input-label mapping
1. Distribution of inputs
1. Label space
1. Format of input

This blog post will discuss all of them, but will focus on the first one the most.

### How does it work?

The overall mechanism of ICL is not well understood and many questions regarding why and how it works remain to be answered.

That said, recent studies {% cite von2022transformers dai2022can %} have shown that internally, the model mimics a gradient descent approach via its attention mechanism to learn from the input prompt. This conditions the model to "learn" from the input and thus generate the right output.

However, understanding how exactly the input influences the ICL mechanism and what truly matters is something that will be explored further in this blogpost.

## What Matters: The Claim and the Semi-Refutal

It has been historically assumed that a good set of examples is important for good ICL performance {% cite liu-etal-2022-makes lester-etal-2021-power %}. However, what makes a good example remained to be explored. A recent study {% cite min-etal-2022-rethinking %} proposed what is important in a prompt.

### The Claim

In their paper {% cite min-etal-2022-rethinking %} the authors explored 6 large language models (LLMs), ranging from 774 million parameters (GPT-2) to 175 billio parameters (GPT-3, see Table 1 for a full list of models evaluated). Two inference methods were tried: direct and channel. 6 different tasks were evaluated: sentiment analysis, paraphrase detection, sentence completion, NLI, hate speech detection, question answering. These tasks were evaluated on 26 datasets total.

|Model|# Params|Public|Meta-trained|
|-----|--------|------|------------|
|GPT-2 Large|774M|✔️|✘|
|MetaICL|774M|✔️|✔️|
|GPT-J|6B|✔️|✘|
|fairseq 6.7B|6.7B|✔️|✘|
|fairseq 13B|13B|✔️|✘|
|GPT-3|175B|✘|✘|

_Table 1: Models analyzed {% cite min-etal-2022-rethinking %}_

The authors ran experiments in a $k$-shot setting, where they set $k=16$ and ran each experiment on five different seeds. They used $F_1$ and accuracy as their reported metrics. Their finding were as follows:

**Input-label Mapping**: the main result of the paper shows that assigning random labels (as opposed to the ground-truth labels) in the examples of the input has no significant impact to the ICL performance.


<figure>
  <a href="{{site.url}}/assets/icl_inputlabel.png"><img src="{{site.url}}/assets/icl_inputlabel.webp" alt="ICL input-label mapping experiment results."/></a>
  <figcaption>Fig. 2: ICL performance not overly hurt when random labels are used..</figcaption>
</figure>

**Number of [correct] labels**: The effect described above seems to be consistent, regardless of what $k$ is picked. See Figure 3. Experiments also show that after a certain $k$ performance does not improve greatly.

<figure>
  <a href="{{site.url}}/assets/icl_knumber.png"><img src="{{site.url}}/assets/icl_knumber.webp" alt="Experiment results on varying k."/></a>
  <figcaption>Fig. 3: Ablations on varying numbers of examples in the demonstrations.</figcaption>
</figure>

### The Semi-Refutal



## Own Contribution

As an additional experiment, I have decided to try 

## Recent Discoveries

Very recently, (TODO ICL changes with scale)

## Conclusion




## References
{% bibliography --cited %}
