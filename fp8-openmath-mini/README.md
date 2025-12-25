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
<img width="3020" height="1448" alt="loss_sft_llama1b_openmathmini" src="https://github.com/user-attachments/assets/b8a24d30-8e5b-4605-8fe7-6e226e939c32" />


<img width="882" height="600" alt="llama1b-v1-1-reward" src="https://github.com/user-attachments/assets/5dbcea96-4cec-448d-8c2e-e16f473cd372" />


<img width="882" height="600" alt="llama1b-v1-1-loss" src="https://github.com/user-attachments/assets/b6a14f76-7608-4a29-b32f-9ce2fa3d8755" />


<img width="882" height="600" alt="llama1b-v1-1-kl" src="https://github.com/user-attachments/assets/782dd5ea-6890-477b-9140-3c6c093c27a7" />
