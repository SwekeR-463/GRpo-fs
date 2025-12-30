# GRpo-fs

This is implementation of GRPO that was proposed in DeepSeek Math Paper in PyTorch.

### Basic Intuition

After reading the paper, this is my basic understanding of how it works --
* For each Q, model generates several possible answers
* Each answer is scored using a reward function
* The avg score of all answers generated is calculated for that Q
* The model compares each answer's score to the avg to see how good it is -> advantage.
* The model then updates to favor answers with higher advantages

### Experiments
* `grpo-fs-smoll2360m.ipynb` - first grpo training run with base setup with [smolm2-360m](https://huggingface.co/HuggingFaceTB/SmolLM2-360M) of prompt and stuff
* `grpo-fs-3hrs.ipynb` - added time limit for x hours but in this notebook i trained for 3 hours
* `grpo-fs-better-prompt.ipynb` - changed the base prompt to the prompt used in [willcb's script](https://gist.github.com/willccbb/4676755236bb08cab5f4e54a0475d6fb#file-grpo_demo-py)
* `grpo-with-think.ipynb` - in this prompt changed the *reasoning* to *think* and actually helped in structured output out of all above runs

<img width="1643" height="236" alt="Screenshot from 2025-08-09 11-55-56" src="https://github.com/user-attachments/assets/d17144f5-ca6c-49ed-a6f0-39e52df3aceb" />

* `grpo-gemma3-270m-eossplit.ipynb` - used the latest released [gemma3-270m](https://huggingface.co/google/gemma-3-270m) and first time after running multiple runs with gemma3 i got **nan** in training loss in step1 itself
  
<img width="558" height="264" alt="Screenshot from 2025-08-15 10-23-36" src="https://github.com/user-attachments/assets/682515da-1831-4114-ae8f-dfa45ddde57f" />

* also it started reward hacking ig the format and started returning `<eos>` tokens only continuously

<img width="1112" height="472" alt="Screenshot from 2025-08-15 11-23-44" src="https://github.com/user-attachments/assets/3d2fe73d-51d8-4313-bebd-1fb328117f29" />

* `grpo-gemma3-270m-crf.ipynb` - changed the format reward function to penalize for returning more than one `<eos>` token in the output and here it started outputing `</explanation>` and `<asciimath>` in every alternate output that i printed after each 5 steps

### Learnings
* After watching the [RL Workshop](https://youtu.be/OkEGJ5G3foU?si=NFKyF8wLQEd3jQEb) got comfortable with the maths part and also understood if want to apply grpo directly use the `instruct-tuned` model and if want to use `base-model` first sft then grpo.
* More learnings to come once i start writing better reward functions or play around the grpo & lora hyperparams that are available in trl & peft respectively.
* As I have started using trackio, for rewards always have to look at rewards/mean for understanding the reward curve.
* Why sft has near stable grad norms while rlvr has quite unstable norms? SFT exhibits low and stable gradient norms, consistent with supervised maximum-likelihood training on fixed targets. GRPO introduces higher-magnitude gradients due to relative ranking within sampled completion groups, leading to sharper but controlled updates. Also policy diffs, grads are multiplied with variance increasing it and each step uses new samples from changing policies.
- In TRL, `reward` indicates the mean reward and `reward_std` indicates the std dev of rewards which gives insight into the variability of model's ouptut.
