# Instruction-Tuning Dataset and LoRA Adapter for the Climatology-specific Large Language Model

This repository provides the **instruction-tuning dataset** and **LoRA adapter** used in our study, 
aiming to ensure transparency and reproducibility in fine-tuning large language models (LLMs) on **recent academic papers and assessment reports concerning climate change**.

---

## Project Overview

This project aims to develop an AI-based framework that enables local governments to conduct scientifically sound climate risk assessments and design adaptation strategies, even in the absence of specialized expertise or significant resources, based on recent academic papers and assessment reports.

---

## Contents

| Item | Filename | Description |
|------|----------|-------------|
| **Dataset** | v2.zip | Question-Answer pairs in JSONL format (English and Japanese) |
| **LoRA Adapter** | checkpoint-19000.zip | LoRA adapter for Llama-3.3-Swallow-70B-Instruct-v0.4<br>(Compatible with Hugging Face) |

---

## Dataset Overview

The dataset used in this study consists of question–answer pairs based on given contexts. 
Each sample requires the model to either **generate an open-ended textual answer** or **select one of four multiple-choice options**. 
The data are organized by **language** (English or Japanese) and **answer format** (textual or multiple-choice), resulting in four subsets:

- `en_default`: English, open-ended textual answers  
- `en_multichoice`: English, multiple-choice questions  
- `jp_default`: Japanese, open-ended textual answers  
- `jp_multichoice`: Japanese, multiple-choice questions  

Each subset is divided into training, validation, and test sets in an 8:1:1 ratio. 
The number of samples in each split is shown below. 
In total, the dataset contains approximately 190,000 samples, ensuring sufficient coverage across both languages and answer types. 
This design allows models to learn variations in linguistic structures and response formats, enabling effective cross-lingual and cross-format generalization.

| Dataset | <div align="center">Train<br>(train.json)</div> | <div align="center">Validation<br>(val.json)</div> | <div align="center">Test<br>(test.json)</div> | <div align="center">Total<br>(dataset.json)</div> |
|----------|-------:|------------:|------:|--------:|
| en_default | 38,745 | 4,843 | 4,844 | 48,432 |
| en_multichoice | 37,903 | 4,738 | 4,738 | 47,379 |
| jp_default | 38,336 | 4,792 | 4,792 | 47,920 |
| jp_multichoice | 37,111 | 4,639 | 4,639 | 46,389 |
| all data | 152,095 | 19,012 | 19,013 | 190,120 |

---

## Sources of Instruction-Tuning Data

The dataset was constructed from research papers and assessment reports relevant to climate change.

### 1. Ministry of Education, Culture, Sports, Science and Technology (MEXT) 
&nbsp;&nbsp;&nbsp;&nbsp;[Advanced Studies of Climate Change Projection (SENTAN Program)](https://www.jamstec.go.jp/sentan/eng/index.html)
<!--
- Period: 2022–2024  
- Number of papers: 78  

| Year | Papers |
|------|--------:|
| 2022 | 30 |
| 2023 | 28 |
| 2024 | 19 |
---
-->

### 2. National Institute for Environmental Studies (NIES)  
&nbsp;&nbsp;&nbsp;&nbsp;[Climate Change Adaptation Information Platform (A-PLAT)](https://adaptation-platform.nies.go.jp/en/)
<!--
- Period: 2016–2019  
- Number of papers: 261  

| Year | Papers |
|------|--------:|
| 2016–2017 | 199 |
| 2018–2019 | 62 |
---
-->

### 3. Intergovernmental Panel on Climate Change (IPCC)  
&nbsp;&nbsp;&nbsp;&nbsp;[AR6 Synthesis Report: Climate Change 2023](https://www.ipcc.ch/report/sixth-assessment-report-cycle/)
<!--
- Target: Climate Change 2023 Synthesis Report (excluding glossary and index)  
-->
---

## Dataset Construction and Fine-Tuning Environment

| Component | Tool / Model | Version / Source |
|------------|---------------|------------------|
| PDF text extraction | [Docling](https://github.com/docling-project/docling) | 2.26.0 |
| Instruction generation model | [OpenGVLab/InternVL2_5-78B-MPO](https://huggingface.co/OpenGVLab/InternVL2_5-78B-MPO) | 78B MPO model |
| Fine-tuning framework | [ms-swift](https://github.com/modelscope/ms-swift) | 3.3.0 |
| Base model for fine-tuning |[tokyotech-llm/Llama-3.3-Swallow-70B-Instruct-v0.4](https://huggingface.co/tokyotech-llm/Llama-3.3-Swallow-70B-Instruct-v0.4) | f99e99588303e8a52b88076d3a5f24db19f757a6 |

---

## Intended Use

This dataset and LoRA adapter are released **for research and educational purposes** only.  
Recommended use cases include:

- Summarization and explanation of scientific and assessment reports on climate change  
- Knowledge extraction and question answering in climate science and policy domains  
- Development of AI assistants for science communication and knowledge dissemination

---

## Notes

- The dataset contains texts derived from research papers and assessment reports published by the above institutions.  
  Copyright remains with the original authors and organizations.  
- This repository is provided **to promote transparency and reproducibility in academic research**;  
  **commercial use is strictly prohibited**.  
- Users should verify and evaluate model outputs before citation or publication.

---

## License Information

Please note that the dataset and the LoRA adapter provided in this repository are distributed under different licenses. By downloading or using these resources, you agree to abide by their respective terms.

# Dataset:
The climate change QA dataset is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0).
[View CC BY-NC-SA 4.0 License details](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.en)

# LoRA Adapter:
The LoRA adapter was fine-tuned on the Llama 3.3 Swallow 70B Instruct base model. Therefore, the use of these model weights is subject to the Llama 3.3 Community License Agreement, as well as the Gemma Terms of Use.
[View Llama 3.3 Community License](https://www.llama.com/llama3_3/license/)
[View Gemma Terms of Use](https://ai.google.dev/gemma/terms)

<!--
## Citation

If you use this dataset or adapter in your research, please cite as follows:

- D. Matsuoka, S. Kawahara, K. Murakami, R. Matsumoto, R. Ito, S. Sugimoto, D. Sugiyama, M. Hara, M. Hayashida, K. Nguyen, A. Peng, T. Abe, I. Sugiyama, *Climatology-specific Large Language Model using Ensemble Projection Data toward Regional Climate Services*, Earth’s Future (2025) (submitted)
- GitHub Repository, https://github.com/kawaharas/Climate-Research-Instruction-Tuning-Dataset-and-LoRA-Adapter
-->
---

## Related Links

- [SENTAN Program](https://www.jamstec.go.jp/sentan/eng/)
- [A-PLAT](https://adaptation-platform.nies.go.jp/en/)
- [IPCC AR6 Reports](https://www.ipcc.ch/report/sixth-assessment-report-cycle/)
- [Docling Project](https://github.com/docling-project/docling)
- [OpenGVLab/InternVL2_5-78B-MPO](https://huggingface.co/OpenGVLab/InternVL2_5-78B-MPO)
- [ms-swift Framework](https://github.com/modelscope/ms-swift)
- [tokyotech-llm/Llama-3.3-Swallow-70B-Instruct-v0.4](https://huggingface.co/tokyotech-llm/Llama-3.3-Swallow-70B-Instruct-v0.4)

---
