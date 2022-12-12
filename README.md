# jb-test-method-name-prediction

## Notes

1. Metrics are not sensitive to the order of tokens. It's easy to hack metrics by adding all of the permutations of tokens to the train dataset. But in practice such model will be useless.
2. I have lost one instance while I was working on this task. That's why I have only wandb logs for first 2 experiments (see screenshots).

## Results

| Model  | Precision | Recall  | F1 |
| ------------- | ------------- | ------------- | ------------- |
| Baseline  | 0.4238  | 0.3068  | 0.3436  |
| 30 epochs  | 0.4599  | 0.4351  | 0.4356  |
| 30 epochs + cosine LR scheduler  | 0.4680  | 0.4474  | 0.4462  |
| 30 epochs + cosine LR scheduler + mlm backbone  | 0.4685  | 0.4465  | 0.4453  |
| 30 epochs + cosine LR scheduler + mlm backbone + beam search  | **0.4765**  | 0.4428  | 0.4470  |
| 30 epochs + cosine LR scheduler + mlm backbone + SWA  | 0.4693  | **0.4550**  | **0.4501**  |

## What I tried and what didn't work

- increase/decrease batch size
- increase/decrease learning rate
- increase/decrease standard deviation in decoder initialization
- different LR schedulers (with warmup, with restarts, etc.)
- AdamW optimizer
- different backbones ('CAUKiel/JavaBERT', 'CAUKiel/JavaBERT-uncased')
- fewer decoder layers
- word dropout
- freeze encoder with fine-tuning
- top-k sampling/nucleus sampling

## Possible next steps

- more decoder layers
- [beam search normalization](https://opennmt.net/OpenNMT/translation/beam_search/)
- [beam search optimization](https://arxiv.org/abs/1606.02960)
- [direct F1 optimization](https://towardsdatascience.com/the-unknown-benefits-of-using-a-soft-f1-loss-in-classification-systems-753902c0105d)
- different learning rates for layers in encoder and decoder
