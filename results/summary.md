## Agreement

|                       |   agreement_without_ties_vs_human |   agreement_with_ties_vs_human |   cohen_kappa_vs_human |   agreement_without_ties_vs_gpt4 |   agreement_with_ties_vs_gpt4 |   cohen_kappa_vs_gpt4 |   agreement_with_ties_no_swap_vs_human |   single_agreement_without_ties_vs_human |
|:----------------------|----------------------------------:|-------------------------------:|-----------------------:|---------------------------------:|------------------------------:|----------------------:|---------------------------------------:|-----------------------------------------:|
| Qwen2.5-0.5B-Instruct |                             0     |                          0.243 |                 -0.006 |                            0     |                         0.13  |                -0.006 |                                  0.297 |                                    0.58  |
| Qwen2.5-1.5B-Instruct |                             0.737 |                          0.283 |                  0.018 |                            0.787 |                         0.23  |                 0.051 |                                  0.38  |                                    0.681 |
| Qwen2.5-3B-Instruct   |                             0.828 |                          0.54  |                  0.311 |                            0.893 |                         0.593 |                 0.39  |                                  0.543 |                                    0.639 |
| GPT-4 (reference)     |                             0.827 |                          0.647 |                  0.449 |                          nan     |                       nan     |               nan     |                                nan     |                                  nan     |

## Bias and reliability

|                       |   position_consistency |   inconsistent_prefers_first_slot |   inconsistent_prefers_second_slot |   tie_rate |   judge_picks_longer |   human_picks_longer |   gpt4_picks_longer |   parse_error_rate |   single_rating_parse_rate |
|:----------------------|-----------------------:|----------------------------------:|-----------------------------------:|-----------:|---------------------:|---------------------:|--------------------:|-------------------:|---------------------------:|
| Qwen2.5-0.5B-Instruct |                  0.047 |                             0     |                              0.761 |      0.993 |                1     |                0.704 |               0.769 |              0.717 |                      0.63  |
| Qwen2.5-1.5B-Instruct |                  0.183 |                             0.024 |                              0.971 |      0.817 |                0.873 |                0.704 |               0.769 |              0     |                      0.693 |
| Qwen2.5-3B-Instruct   |                  0.67  |                             0.474 |                              0.412 |      0.337 |                0.759 |                0.704 |               0.769 |              0.007 |                      0.537 |
