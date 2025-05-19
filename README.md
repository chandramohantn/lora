# LORA
Low-Rank Adaptation is a technique designed to efficiently fine-tune large language models. Instead of updating all the model parameters, LoRA introduces training a small subset of parameters, making the process more resource efficient.

## The Core Idea
During fine-tuning a model, the weight matrices are typically adjusted to adapt the model to specific tasks. LoRA proposes that the necessary adjustments to these weight matrices be approximated through low-rank matrices. This means instead of modifying the entire weight matrix, we can represent the changes using two smaller matrices, significantly reducing the number of parameters that need to be trained.

## How LoRA works
1. Freeze Original Weights: The pre-trained models weight remain unchanged during fine-tuning.
2. Introduce Low-Rank Matrices: 