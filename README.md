# GRpo-fs

This is implementation of GRPO that was proposed in DeepSeek Math Paper in PyTorch.

### Basic Intuition

After reading the paper, this is my basic understanding of how it works --
* For each Q, model generates several possible answers
* Each answer is scored using a reward function
* The avg score of all answers generated is calculated for that Q
* The model compares each answer's score to the avg to see how good it is -> advantage.
* The model then updates to favor answers with higher advantages
