
- model = ministral 3b
- plain grpo runs using `loss_type="grpo"`
- sudoku env made from scratch
- model gives out `.py` funcs to fill the boxes in sudoku and accordingly rewards are given back -- one for valid and executable `.py` code, one for using no external python library and one for successful valid moves even if strategy eventually fails.
- one thing i noticed is reward hacking where the model(ministral) mostly generated executable `.py` code and used no external python library leading to reward being around ~7-8.
