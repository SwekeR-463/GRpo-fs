
- model = ministral 3b
- plain grpo runs using `loss_type="grpo"`
- sudoku env made from scratch
- model gives out `.py` funcs to fill the boxes in sudoku and accordingly rewards are given back -- one for valid and executable `.py` code, one for using no external python library and one for successful valid moves even if strategy eventually fails.
- one thing i noticed is reward hacking where the model(ministral) mostly generated executable `.py` code and used no external python library leading to reward being around ~7-8.
<img width="882" height="600" alt="ministral-sudoku-reward" src="https://github.com/user-attachments/assets/234052ef-c6d5-4619-b23e-52ca8406f940" />
<img width="882" height="600" alt="ministral-sudoku-frac-reward-zero-std" src="https://github.com/user-attachments/assets/9b11729a-2af9-4ebb-969d-621ffe5bb0f4" />
<img width="882" height="600" alt="ministral-sudoku-grad-norm" src="https://github.com/user-attachments/assets/12e0968c-1168-470d-aa17-7d1bf9f17517" />
<img width="882" height="600" alt="ministral-sudoku-kl" src="https://github.com/user-attachments/assets/2bcd5e38-5297-4691-a2ec-271443481ad0" />
<img width="882" height="600" alt="ministral-sudoku-loss" src="https://github.com/user-attachments/assets/e47f29cd-bddd-4d82-a4cb-8adb6bcb2a0f" />
<img width="1364" height="600" alt="ministral-sudoku-reward-std" src="https://github.com/user-attachments/assets/1d21bab6-8b49-4895-a53f-55fbb0dca9ea" />
