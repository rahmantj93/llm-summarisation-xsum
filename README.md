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
| Zero-shot     | 0.2045  | 0.0344  | 0.1415  |
| Few-shot      | 0.2045  | 0.0344  | 0.1415  |
| PE Zero-shot  | 0.2007  | 0.0301  | 0.1364  |
| PE Few-shot   | 0.1945  | 0.0271  | 0.1355  |

## Key Findings
- BART's encoder-decoder architecture does not benefit from in-context 
  examples, causing zero-shot and few-shot to produce identical results
- Prompt engineering with strict length constraints reduced ROUGE scores 
  slightly due to summaries being cut off
- BART was fine-tuned on CNN/DailyMail, explaining the performance gap 
  on XSum's more abstractive single-sentence summaries

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
4. Run all cells in order

## Dataset
BBC news articles with single-sentence summaries
[EdinburghNLP/xsum](https://huggingface.co/datasets/EdinburghNLP/xsum)

