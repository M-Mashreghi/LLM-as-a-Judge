## Win rates

|                 |   human |   GPT-4 |   Qwen2.5-0.5B-Instruct (pairwise) |   Qwen2.5-0.5B-Instruct (single) |   Qwen2.5-1.5B-Instruct (pairwise) |   Qwen2.5-1.5B-Instruct (single) |   Qwen2.5-3B-Instruct (pairwise) |   Qwen2.5-3B-Instruct (single) |
|:----------------|--------:|--------:|-----------------------------------:|---------------------------------:|-----------------------------------:|---------------------------------:|---------------------------------:|-------------------------------:|
| gpt-4           |   0.683 |   0.789 |                              0.494 |                            0.453 |                              0.539 |                            0.56  |                            0.739 |                          0.512 |
| gpt-3.5-turbo   |   0.648 |   0.636 |                              0.5   |                            0.567 |                              0.508 |                            0.608 |                            0.636 |                          0.552 |
| claude-v1       |   0.641 |   0.693 |                              0.495 |                            0.48  |                              0.547 |                            0.616 |                            0.573 |                          0.627 |
| vicuna-13b-v1.2 |   0.51  |   0.561 |                              0.505 |                            0.509 |                              0.526 |                            0.491 |                            0.592 |                          0.637 |
| alpaca-13b      |   0.305 |   0.24  |                              0.5   |                            0.5   |                              0.425 |                            0.371 |                            0.29  |                          0.395 |
| llama-13b       |   0.204 |   0.087 |                              0.505 |                            0.453 |                              0.459 |                            0.234 |                            0.168 |                          0.244 |

## Rank correlation with humans

|                                  |   spearman_vs_human |   kendall_vs_human | top_model       |
|:---------------------------------|--------------------:|-------------------:|:----------------|
| GPT-4                            |               0.943 |              0.867 | gpt-4           |
| Qwen2.5-0.5B-Instruct (pairwise) |              -0.765 |             -0.645 | vicuna-13b-v1.2 |
| Qwen2.5-0.5B-Instruct (single)   |               0.116 |              0.138 | gpt-3.5-turbo   |
| Qwen2.5-1.5B-Instruct (pairwise) |               0.657 |              0.467 | claude-v1       |
| Qwen2.5-1.5B-Instruct (single)   |               0.771 |              0.6   | claude-v1       |
| Qwen2.5-3B-Instruct (pairwise)   |               0.943 |              0.867 | gpt-4           |
| Qwen2.5-3B-Instruct (single)     |               0.429 |              0.2   | vicuna-13b-v1.2 |
