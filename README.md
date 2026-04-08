<div align="center">

<img src="https://img.shields.io/badge/Gemma_4_31B-April_2026-4285F4?style=for-the-badge&logo=google&logoColor=white"/>
<img src="https://img.shields.io/badge/HumanEval-164_Problems-FF6B35?style=for-the-badge"/>
<img src="https://img.shields.io/badge/pass@1-95.1%25-22C55E?style=for-the-badge"/>
<img src="https://img.shields.io/badge/Status-Complete-22C55E?style=for-the-badge"/>

<br/><br/>

# humaneval-gemma4-benchmark

### Independent benchmark of Google's Gemma 4 31B on the HumanEval coding benchmark (Chen et al., 2021)

<br/>

> **"Can a model released in 2026 solve coding problems designed to challenge AI in 2021?"**
>
> **Short answer: 95.1% of the time.**

<br/>

![HumanEval Results Chart](https://raw.githubusercontent.com/hypernab/humaneval-gemma4-benchmark/main/charts/humaneval_chart.png)

<br/>

</div>

---

## 📌 What Is This?

In 2021, OpenAI published **"Evaluating Large Language Models Trained on Code"** — introducing the **HumanEval benchmark**: 164 hand-crafted Python programming problems to measure how well AI can write correct code from a docstring alone.

Their best model at the time, **Codex**, scored **28.8% pass@1**.

This project asks: *how far have we come since then?*

Idenpendently ran the same 164 problems on **Gemma 4 31B** Google DeepMind's flagship open model released just 7 days before this project. Only zero shot evaluation.

---

## 🏆 Results

<div align="center">

| Model | Organization | Year | pass@1 | Source |
|:------|:------------|:----:|:------:|:------:|
| Codex (code-davinci) | OpenAI | 2021 | 28.8% | Original Paper |
| GPT-3.5 | OpenAI | 2022 | 48.1% | Published |
| GPT-4 | OpenAI | 2023 | 67.0% | Published |
| **Gemma 4 31B** | **Google** | **2026** | **95.1%** | **This Repo** |

</div>

<br/>

**156 out of 164 problems solved correctly on the first attempt.**

- **+66.3%** over the original Codex baseline (2021)
- **+28.1%** over GPT-4 (2023)
- One of the first independent HumanEval evaluations of Gemma 4 31B(hopefully..)

---

## 🔬 Methodology

### Dataset
**HumanEval** (Chen et al., 2021) — 164 hand-written Python problems, each with a function signature, docstring, and hidden unit tests. Loaded directly from `openai/openai_humaneval`

### Model
**Gemma 4 31B Instruct** (`models/gemma-4-31b-it`) via Google AI Studio API
- Released: April 2, 2026
- License: Apache 2.0 (fully open)
- Architecture: 30.7B dense transformer, multimodal
- Context window: 256K tokens

### Evaluation Setup
| Parameter | Value |
|---|---|
| Metric | pass@1 |
| Temperature | 0.2 |
| Max output tokens | 512 |
| Prompt strategy | Zero-shot |
| Evaluator | Official OpenAI human-eval harness |

### Prompt 
Zero-shot. 

```
System: You are a Python coding assistant.
        Complete the function body ONLY.
        Return ONLY raw Python code, no markdown, no backticks.

User:   Complete this Python function:

        def has_close_elements(numbers: List[float], threshold: float) -> bool:
            """ Check if in given list of numbers, are any two numbers
            closer to each other than given threshold.
            ...
            """
```

---

## How To Reproduce

### Prerequisites
- Google Account
- Free API key from [aistudio.google.com/apikey](https://aistudio.google.com/apikey) — no credit card needed
- Google Colab (free)

### Steps

**1. Clone this repo**
```bash
git clone https://github.com/hypernab/humaneval-gemma4-benchmark
```

**2. Open `humaneval_benchmark_clean.ipynb` in Google Colab**
```
File → Upload notebook → select the .ipynb file
```

**3. Paste your Google AI Studio API key in Cell 1**
```python
API_KEY = "YOUR_GOOGLE_AI_STUDIO_KEY_HERE"
```

**4. Run all cells in order**

Results save automatically to Google Drive after every single problem — safe against disconnections.

---

## 📚 References

```bibtex
@article{chen2021codex,
  title   = {Evaluating Large Language Models Trained on Code},
  author  = {Chen, Mark and others},
  journal = {arXiv preprint arXiv:2107.03374},
  year    = {2021}
}

@misc{gemma4_2026,
  title  = {Gemma 4: Frontier Multimodal Intelligence on Device},
  author = {Google DeepMind},
  year   = {2026},
  url    = {https://blog.google/technology/developers/gemma-4/}
}
```

---

## 🛠️ Tools Used

`Python` · `Google Colab` · `Google AI Studio` · `google-genai` · `HuggingFace Datasets` · `human-eval` · `Matplotlib`

---

<div align="center">

*Built as a project in AI benchmarking — extending a landmark 2021 paper with the newest available open models.*

<br/>

<img src="https://img.shields.io/badge/Made_with-Google_Colab-F9AB00?style=flat-square&logo=googlecolab&logoColor=white"/>
<img src="https://img.shields.io/badge/Model-Gemma_4_31B-4285F4?style=flat-square&logo=google&logoColor=white"/>
<img src="https://img.shields.io/badge/Benchmark-HumanEval-FF6B35?style=flat-square"/>
<img src="https://img.shields.io/badge/License-Apache_2.0-blue?style=flat-square"/>

<br/><br/>

:)

</div>
