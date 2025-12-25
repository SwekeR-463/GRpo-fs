- fp8 doesnt run on kaggle t4/p100 :(
- setup = cold start sft on openmath mini + grpo on dapo math 17k
- first run on llama3.2-1b-instruct
<img width="1208" height="427" alt="image" src="https://github.com/user-attachments/assets/7628804f-c3ac-428b-ac99-efb69288021a" />

- switched to `<reasoning>...</reasoning>` for second run
- also added trackio for curves
- one interesting obv was spiking of gradnorm when grpo run to 1.1-1.3 while for sft it was 0.5-0.6
- more insights from gpt:-
- SFT exhibits low and stable gradient norms, consistent with supervised maximum-likelihood training on fixed targets.
- GRPO introduces higher-magnitude gradients due to relative ranking within sampled completion groups, leading to sharper but controlled updates.
- This contrast highlights how GRPO actively reshapes model behavior beyond format alignment achieved via SFT.
