[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/rahmantj93/llm-summarisation-xsum/blob/main/AI_Assignment.ipynb)

# LLM Summarisation: Zero-shot, Few-shot and Prompt Engineering

## Overview
This project compares four different prompting approaches for text summarisation 
using the [XSum dataset](https://huggingface.co/datasets/EdinburghNLP/xsum) and 
the `facebook/bart-large-cnn` model.

## Approaches Compared
- Zero-shot prompting
- Few-shot prompting
- Prompt engineering (zero-shot)
- Prompt engineering (few-shot)

## Results
| Approach      | ROUGE-1 | ROUGE-2 | ROUGE-L |
|---------------|---------|---------|---------|
| Zero-shot     | 0.2042  | 0.0343  | 0.1415  |
| Few-shot      | 0.2042  | 0.0343  | 0.1415  |
| PE Zero-shot  | 0.2015  | 0.0298  | 0.1365  |
| PE Few-shot   | 0.1061  | 0.0077  | 0.0818  |

## Key Findings
- **Zero-shot and Few-shot produce identical results** because BART's 
  encoder-decoder architecture does not benefit from in-context examples 
  the way instruction-tuned decoder-only LLMs do
- **PE Zero-shot scored slightly lower** than baseline, as the instruction 
  prefix altered BART's summarisation behaviour without meaningfully 
  improving it
- **PE Few-shot scored substantially lower** — embedding a demonstration 
  example inside the prompt consumed valuable input-token budget (1024 
  limit) and caused the target article to be truncated, degrading quality
- BART was fine-tuned on CNN/DailyMail's multi-sentence summaries, explaining 
  the performance gap on XSum's concise single-sentence format

## Technologies Used
- Python
- HuggingFace Transformers
- BART (facebook/bart-large-cnn)
- Google Colab (T4 GPU)
- ROUGE evaluation metric

## How to Run
1. Open the notebook in Google Colab
2. Enable T4 GPU (Runtime → Change runtime type)
3. Add your HuggingFace token to Colab Secrets as `HF_TOKEN`
4. Run all cells in order (takes ~15 minutes on T4 GPU)

## Dataset
[EdinburghNLP/xsum](https://huggingface.co/datasets/EdinburghNLP/xsum) — 
BBC news articles with single-sentence abstractive summaries.

## References
- Lewis, M. et al. (2020) *BART: Denoising Sequence-to-Sequence Pre-training 
  for Natural Language Generation*. arXiv:1910.13461
- Narayan, S., Cohen, S.B. and Lapata, M. (2018) *Don't Give Me the Details, 
  Just the Summary!* arXiv:1808.08745
- Wolf, T. et al. (2020) *HuggingFace's Transformers: State-of-the-art Natural 
  Language Processing*. arXiv:1910.03771
