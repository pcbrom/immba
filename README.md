# IMMBA: Integrated Mixed Models with Bootstrap Analysis for Robust LLM Evaluation

**Di Oliveira, V., Brom, P.C., & Weigang, L. (2025). IMMBA: Integrated Mixed Models with Bootstrap Analysis — A Statistical Framework for Robust LLM Evaluation**

## Overview

IMMBA is a statistically rigorous framework engineered for the robust evaluation of Large Language Models (LLMs). It synergistically integrates Linear Mixed Models (LMMs) with bootstrap resampling techniques to decompose the variability observed in LLM outputs into fixed effects, such as model configurations, decoding parameters, and retrieval methods and random effects (including prompt phrasing). This approach facilitates a nuanced and interpretable performance analysis.

In contrast to conventional aggregate metrics like accuracy or BLEU, IMMBA explicitly models the stochasticity and variability intrinsic to LLM outputs across diverse experimental conditions. This capability is essential for high-stakes applications that demand reproducibility and trustworthiness.

---

## Key Features

- **Variance decomposition**: Disaggregates total output variability into fixed effects, random prompt effects, and residual noise.
- **Hierarchical modeling**: Conceptualizes prompts as random effects, effectively capturing linguistic variability.
- **Bootstrap resampling**: Fortifies estimator robustness and enhances confidence intervals under relaxed distributional assumptions.
- **Full factorial experimental design**: Assesses combinations of model architectures, temperature settings, top-p sampling, and retrieval methodologies.
- **Multi-metric evaluation**: Rigorously scores LLM outputs across dimensions of quality, agreement, accuracy, and hallucination.
- **Scalable pipeline**: Facilitates the evaluation of multiple models and configurations in a reproducible and systematic manner.

---

## Experimental Design

- **Models evaluated**: Six LLMs encompassing both open-source and proprietary architectures.
- **Decoding parameters**: Temperature settings (0.1, 1.0, 1.9) and top-p values (0.1, 0.5, 0.9).
- **Retrieval methods**: Comparison between baseline semantic retrieval and retrieval-augmented generation.
- **Prompts**: Curated prompts derived from Mercosur Common Nomenclature (NCM) classification tasks.
- **Replicates**: Approximately 196 replicates per experimental condition to ensure adequate statistical power.
- **Total runs**: Over 21,000 evaluated responses to enable comprehensive variance analysis.

---

## Methodology

1. **Linear Mixed Model (LMM) formulation** to model observed scores as a function of fixed experimental factors, their interactions, random prompt effects, and residual error.

2. **Bootstrap resampling** (1000 iterations) to derive robust estimates of variance components and confidence intervals.

3. **Evaluation metrics** assessed by human raters on a 0-10 scale:
   - Quality (clarity and coherence)
   - Agreement (semantic alignment with expert baseline)
   - Accuracy (factual correctness)
   - Hallucination (degree of fabrication; lower scores are preferable)

---

## Usage

The repository encompasses scripts to:

- Design and generate a comprehensive experimental plan incorporating all model, prompt, and parameter combinations.
- Automate prompt augmentation and dispatch queries to various LLM APIs (OpenAI GPT, Deepseek, Google Gemini, HuggingFace models).
- Aggregate and preprocess results for subsequent statistical modeling.
- Fit the Linear Mixed Models utilizing bootstrap resampling to extract variance components and interaction effects.
- Generate detailed reports and visualizations for interpreting model behavior under varying conditions.

---

## Results Highlights

- Fixed effects accounted for approximately 23% of output variability.
- Prompt phrasing contributed to around 7% of variability, underscoring the significance of modeling prompt randomness.
- Residual noise constituted approximately 70%, emphasizing the inherent stochasticity and subjectivity of the outputs.
- Statistically significant interaction effects were identified between retrieval methods and model architectures.
- Bootstrap-enhanced confidence intervals bolstered estimation reliability.

---

## Dependencies

- Python 3.8+
- pandas, openpyxl, tqdm
- statsmodels
- transformers, datasets
- OpenAI SDK, Deepseek SDK, Google GenAI SDK
- torch
- dotenv
