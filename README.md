# LLM-as-a-Judge: How Reliable Are Small Open Models as Evaluators?

Human evaluation of chatbot answers is slow and expensive, so it is now common to let a strong
LLM grade other models' outputs. This project asks two questions:

1. **Can a small open-weight model be a trustworthy judge?** Its verdicts are compared with
   expert human votes from the MT-Bench study, and probed for the known failure modes of LLM
   judges: **position bias**, **verbosity bias** and unparseable output.
2. **Can it rank models?** The judge is used to build a leaderboard of several small
   instruction-tuned models from pairwise comparisons and 1–10 grades.

## Method

**Pairwise comparison with position swap.** The judge sees a question and two answers and
must output `[[A]]`, `[[B]]` or `[[C]]` (tie), using the MT-Bench judge prompt. Every pair is
judged twice, once as (A, B) and once as (B, A). A verdict counts only if it survives the swap;
otherwise the pair is scored as a tie (the conservative scheme from Zheng et al., 2023).

**Single-answer grading.** Each answer is also scored 1–10 independently, and a pairwise
verdict is derived from the two scores. This is cheaper (O(n) instead of O(n²) for leaderboards)
but loses the direct comparison.

**Metrics** (see `src/metrics.py`):

| Metric | Meaning |
|---|---|
| `agreement_without_ties` | Accuracy against the human majority, excluding pairs where either side says tie (MT-Bench's headline number) |
| `agreement_with_ties` / `cohen_kappa` | 3-way agreement and chance-corrected agreement |
| `agreement_with_ties_no_swap` | Same, but using only the first ordering, to show what swapping buys |
| `position_consistency` | Share of pairs where the verdict is unchanged after swapping the answers |
| `inconsistent_prefers_first_slot` | Among order-dependent verdicts, how often the judge simply picked the answer shown first |
| `judge_picks_longer_answer` vs `human_picks_longer_answer` | Verbosity bias relative to humans |
| `single_grading_agreement_*` | Agreement when verdicts are derived from 1–10 scores |
| `parse_error_rate` | Output that didn't follow the required format |

## How to run

Everything (code, explanations, results and charts) is in a single notebook: **[`llm_as_a_judge.ipynb`](llm_as_a_judge.ipynb)**.

1. Open it in Jupyter, VS Code or Google Colab (*Runtime → Change runtime type → GPU*).
2. Run the first cell to install dependencies.
3. Adjust the configuration cell if needed, then *Run all*.

Outputs (tables, JSON, charts) are written to `results/`.

## Results

Outputs go to `results/judge_eval/summary.md` and `results/model_comparison/leaderboard.md`.
Per-pair raw judge outputs are saved as JSONL for error analysis.

| Judge | Agreement w/o ties | Kappa | Position consistency | Picks longer (judge / human) |
|---|---:|---:|---:|---:|
| Qwen2.5-0.5B-Instruct | | | | |
| Qwen2.5-1.5B-Instruct | | | | |
| Qwen2.5-3B-Instruct | | | | |

For reference, MT-Bench reports ~66% agreement without ties between GPT-4 and humans, about the
same as human–human agreement.

### Questions to explore

- How does agreement scale with judge size?
- How much of the agreement comes from swap-debiasing (`agreement_with_ties` vs `_no_swap`)?
- Is the judge more verbosity-biased than the human experts?
- Does pairwise judging beat single-answer grading for small judges?

## References

- Zheng et al., *Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena*, NeurIPS 2023. [arXiv:2306.05685](https://arxiv.org/abs/2306.05685)
- Dataset: [`lmsys/mt_bench_human_judgments`](https://huggingface.co/datasets/lmsys/mt_bench_human_judgments)

---
*Developed as part of the Large Language Models course, University of Tehran (Spring 2026).*
