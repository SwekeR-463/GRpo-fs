- fp8 doesnt run on kaggle t4/p100 :(
- setup = cold start sft on openmath mini + grpo on dapo math 17k
---
- first run on llama3.2-1b-instruct
<img width="1208" height="427" alt="image" src="https://github.com/user-attachments/assets/7628804f-c3ac-428b-ac99-efb69288021a" />

---
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

---

- third run using qwen3-0.6b
- nice format following
<img width="1124" height="224" alt="image" src="https://github.com/user-attachments/assets/433ce6bd-be95-4ce9-a918-71395ffa7b9b" />


- sft metrics for qwen3 0.6b


<img width="1306" height="600" alt="loss_sft_qwen3" src="https://github.com/user-attachments/assets/b3c91f3d-c1c8-43ba-a339-d293e4be7323" />

<img width="1306" height="600" alt="grad_norm_sft_qwen3" src="https://github.com/user-attachments/assets/2f8ecce1-0656-46a4-93aa-0ab187d84e94" />





- weird that most of the reward is coming to be -7.5

- grpo metrics for qwen3 0.6b

<img width="882" height="600" alt="reward_qwen3" src="https://github.com/user-attachments/assets/853bf4ae-57f6-43aa-a410-4919be985e93" />


<img width="882" height="600" alt="grad_norm_qwen3" src="https://github.com/user-attachments/assets/43b66c54-2138-4372-9edc-c70dd0615936" />






<img width="882" height="600" alt="kl_qwen3" src="https://github.com/user-attachments/assets/9b1e2d86-2be4-4831-9ab4-5d35f38e51ec" />






<img width="882" height="600" alt="loss_qwen3" src="https://github.com/user-attachments/assets/9a30afce-8836-4748-9600-9a8dbbafddc5" />

---


- fourth run with qwen3-1.7b using dapo(which is the default `loss_type` in hf trl)

- sft runs


<img width="882" height="600" alt="qwen3-17b-sft-loss" src="https://github.com/user-attachments/assets/059e02ea-48e5-4591-a1c9-680c32609f23" />



<img width="1364" height="600" alt="qwe3-17b-sft-gradnorm" src="https://github.com/user-attachments/assets/2420132d-8453-464f-9dd6-53a6caaa8c63" />

- dapo runs after cold start


<img width="882" height="600" alt="qwen3-17b-dapo-rewards" src="https://github.com/user-attachments/assets/de2ff23f-3089-469f-816e-3492d1706450" />


<img width="882" height="600" alt="qwen3-17b-dapo-gradnorm" src="https://github.com/user-attachments/assets/b2370962-67f0-4fc5-b046-3b78b455fd58" />


<img width="882" height="600" alt="qwen3-17b-dapo-kl" src="https://github.com/user-attachments/assets/e09be35b-31e1-4cdd-ad13-6769434a1ccf" />



<img width="882" height="600" alt="qwen3-17b-dapo-loss" src="https://github.com/user-attachments/assets/e3aa55f0-bbbc-4d39-bcda-12103a2c361c" />

---


