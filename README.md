# LORA
Low-Rank Adaptation is a technique designed to efficiently fine-tune large language models. Instead of updating all the model parameters, LoRA introduces training a small subset of parameters, making the process more resource efficient.

## The Core Idea
During fine-tuning a model, the weight matrices are typically adjusted to adapt the model to specific tasks. LoRA proposes that the necessary adjustments to these weight matrices be approximated through low-rank matrices. This means instead of modifying the entire weight matrix, we can represent the changes using two smaller matrices, significantly reducing the number of parameters that need to be trained.

## How LoRA works
1. Freeze Original Weights: The pre-trained models weight remain unchanged during fine-tuning.
2. Introduce Low-Rank Matrices: For each weight matrix W in the model, LoRA adds two trainable matrices
- A with dimensions r x k
- B with dimensions d x r
- Here, r is a chosen rank (much smaller than d or k), determining the size of the adaptation.
3. Compute Adjusted Weights: The modified weight matrix becomes
- W` = W + B x A
- This adjustment allows the model to adapt to new tasks by training only the A and B matrices, leaving the original weights W untouched.

## Benefits of LoRA
- Parameter Efficiency: By training only the low rank matrices, LoRA drastically reduces the number of trainable parameters. 
- Reduced Memory Usage: Since fewer parameters are updated during training, the memory footprint during training is significantly lower.
- Faster Training: With fewer parameters to train, the fine-tuning process becomes quicker, enabling rapid adaptation to new tasks.
- Modularity: Different LoRA modules can be trained for various tasks and swapped in and out of the base model as needed, without retraining the entire model.