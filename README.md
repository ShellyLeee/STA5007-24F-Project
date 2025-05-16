# STA5007-24F-Project: Fine-tuning Gemma2 on GPT-4 Chinese QA Dataset
> Project code guide for STA5007 Advanced Natural Language Processing in 2024 Fall, Department of Statistics and Data Science, SUSTech

This project focuses on fine-tuning the Google Gemma2 model, a transformer-based large language model, for Chinese question-answering tasks. The primary goal is to enhance the model's ability to generate accurate, contextually relevant, and high-quality answers to a diverse range of questions. The fine-tuning process leverages FreedomIntelligence/Evol-Instruct-Chinese-GPT4, a dataset of 70,000 high-quality Chinese question-answer pairs, specifically designed for instruction-tuned models (link: https://huggingface.co/datasets/FreedomIntelligence/Evol-Instruct-Chinese-GPT4). Due to computational constraints, a subset of 1,000 samples was selected for training.

The project mainly includes four parts:
- Dataset Creation: dataset loading and preprocessing
- Initial Model Evaluation: initial Gemma2 model loading, inference, and evaluation
- Fine-tuning Gemma2 on Given Dataset:
  - Use RAG, Perfix tuning and LoRA
  - Set up the pipeline and parameters for training
- Fine-tuned Model Evaluation: model inference and evaluation
- Rebustness Analysis of Fine-tuned Gemma2 Model: test the model in different language

Specifically on the fine-tuning techniques, we employ RAG to supply background knowledge for queries containing specialized terms, thereby improving the fine-tuning performance of the model. The fine-tuning strategy employs LoRA (Low-Rank Adaptation), a parameter-efficient method that injects trainable low-rank matrices into the attention layers, significantly reducing memory and computation requirements. We also explored Prefixed Tuning Strategy. Additionally, the AdamW optimizer was utilized for effective weight decay and adaptive learning rates. Training was structured around a predefined instruction-output format to align the model's capabilities with the dataset structure.

To assess the model's performance, we conducted evaluations before and after fine-tuning. The initial model was tested for its ability to answer questions, serving as a baseline for comparison. Post-fine-tuning, the model underwent inference testing and evaluation using a suite of metrics, including BLEU, ROUGE, METEOR, and BERTScore, which collectively measure linguistic fluency, semantic accuracy, and relevance. The fine-tuned model demonstrated significant improvements, particularly in handling complex instructions and generating contextually appropriate responses.
