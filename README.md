# jbjb-test-method-name-prediction


| Model  | Precision | Recall  | F1 |
| ------------- | ------------- | ------------- | ------------- |
| Baseline  | 0.4238  | 0.3068  | 0.3436  |
| 30 epochs  | 0.4599  | 0.4351  | 0.4356  |
| 30 epochs + cosine LR scheduler  | 0.4680  | 0.4474  | 0.4462  |
| 30 epochs + cosine LR scheduler + mlm backbone  | 0.4685  | 0.4465  | 0.4453  |
| 30 epochs + cosine LR scheduler + mlm backbone + beam search  | **0.4765**  | 0.4428  | 0.4470  |
| 30 epochs + cosine LR scheduler + mlm backbone + SWA  | 0.4693  | **0.4550**  | **0.4501**  |
