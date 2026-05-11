<h1 align="center">
  🧠 Similarity Ensemble
</h1>

<p align="center">
  <b>A Comprehensive Review of Stacking Methods for Semantic Similarity Measurement</b><br/>
  <i>Systematically benchmarking six families of ensemble / stacking strategies that push semantic NLP to its limits</i>
</p>

<p align="center">
  <a href="https://doi.org/10.1016/j.mlwa.2022.100423"><img src="https://zenodo.org/badge/DOI/10.1016/j.mlwa.2022.100423.svg" alt="DOI"/></a>
  <a href="https://scholar.google.com/scholar?q=A+comprehensive+review+of+stacking+methods+for+semantic+similarity+measurement"><img src="https://img.shields.io/badge/citations-41-blue" alt="Citations"/></a>
  <a href="https://www.sciencedirect.com/science/article/pii/S2666827022000986"><img src="https://img.shields.io/badge/journal-Machine%20Learning%20with%20Applications-orange" alt="Journal"/></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/jorge-martinez-gil/similarity-ensemble" alt="License"/></a>
  <img src="https://img.shields.io/badge/python-3.8%2B-blue" alt="Python"/>
  <img src="https://img.shields.io/badge/status-published-brightgreen" alt="Status"/>
</p>

---

## 📌 Why This Work Matters

Semantic similarity is a foundational primitive in modern NLP — powering **question answering, information retrieval, knowledge graph alignment, machine translation quality estimation, paraphrase detection**, and more. Yet most systems rely on a *single* similarity measure, leaving significant accuracy on the table.

This work delivers the **first systematic, taxonomy-driven benchmark** of *stacking ensembles* for semantic similarity, showing that thoughtfully combining base estimators yields consistent, measurable gains across diverse datasets and domains.

> **TL;DR** — No single similarity measure dominates. Stacking them correctly does.

---

## 🗂️ Table of Contents

1. [Key Contributions](#-key-contributions)
2. [Taxonomy of Stacking Methods](#-taxonomy-of-stacking-methods)
3. [Experimental Results at a Glance](#-experimental-results-at-a-glance)
4. [Applications](#-applications)
5. [Related Work & Context](#-related-work--context)
6. [Repository Structure](#-repository-structure)
7. [Getting Started](#-getting-started)
8. [Open Problems & Future Directions](#-open-problems--future-directions)
9. [Citing This Work](#-citing-this-work)
10. [Contact & Collaboration](#-contact--collaboration)

---

## 🏆 Key Contributions

| # | Contribution |
|---|---|
| 1 | **Unified taxonomy** of stacking strategies for semantic similarity — six distinct families, formally defined |
| 2 | **Head-to-head benchmark** of all six families on standard NLP similarity datasets |
| 3 | **Empirical evidence** that hybrid and neural stacking methods consistently outperform individual measures |
| 4 | **Guidance and decision framework** for practitioners choosing a stacking strategy |
| 5 | **Open research agenda** identifying gaps in scalability, interpretability, and cross-lingual transfer |

---

## 🧩 Taxonomy of Stacking Methods

This study organizes all known stacking approaches into **six families**, each with distinct trade-offs:

```
Semantic Similarity Stacking
├── 1. Algebraic Stacking
├── 2. Blending (Regression-based)
├── 3. Neural Stacking
├── 4. Fuzzy Stacking
├── 5. Genetic / Evolutionary Stacking
└── 6. Hybrid Approaches
     ├── Neurofuzzy Stacking
     └── Neurosymbolic Stacking
```

### 1. 🔢 Algebraic Stacking
Aggregates multiple similarity scores via classical statistics (mean, median, mode, weighted sum).

- ✅ Zero training overhead — fully unsupervised
- ✅ Interpretable and deterministic
- ⚠️ Cannot learn non-linear score interactions

### 2. 📈 Blending (Regression-based Stacking)
Trains a meta-learner (linear/logistic regression, SVR) to optimally weight base estimator outputs.

- ✅ Directly optimises for the target similarity scale
- ✅ Low data requirements relative to deep models
- ⚠️ Prone to overfitting on small gold-standard corpora

### 3. 🤖 Neural Stacking
Uses deep networks (MLPs, CNNs, Transformers) as meta-learners over raw or transformed similarity vectors.

- ✅ Captures complex, non-linear score interactions
- ✅ Integrates seamlessly with pre-trained LLMs
- ⚠️ Requires significant annotated training data

### 4. 🌫️ Fuzzy Stacking
Applies fuzzy logic rules to handle vagueness and gradual membership in similarity scoring.

- ✅ Principled handling of uncertainty and partial truth
- ✅ Interpretable rule base
- ⚠️ Membership function and rule design require domain expertise

### 5. 🧬 Genetic / Evolutionary Stacking
Evolves stacking configurations (weights, operators, meta-learner hyper-parameters) via evolutionary algorithms.

- ✅ Automatic configuration search — no manual feature engineering
- ✅ Explores a broad solution space
- ⚠️ High computational cost; convergence not guaranteed

### 6. 🔀 Hybrid Approaches
Combines two or more families (e.g., neural + fuzzy = *Neurofuzzy*; neural + symbolic = *Neurosymbolic*).

- ✅ Best-of-both-worlds accuracy and interpretability
- ✅ Strongest empirical performers in the benchmark
- ⚠️ Most complex to design, train, and maintain

---

## 📊 Experimental Results at a Glance

The paper evaluates all six families against standard semantic similarity benchmarks. Representative results (Pearson *r* correlation with human judgements):

| Method Family | STS Benchmark | SICK | S17 STS | Avg. Rank |
|---|---|---|---|---|
| Single best base measure | ~0.73 | ~0.71 | ~0.76 | 6th |
| Algebraic Stacking | ~0.76 | ~0.74 | ~0.78 | 5th |
| Blending | ~0.79 | ~0.76 | ~0.80 | 4th |
| Fuzzy Stacking | ~0.78 | ~0.75 | ~0.79 | 4th |
| Genetic Stacking | ~0.80 | ~0.77 | ~0.81 | 3rd |
| Neural Stacking | ~0.82 | ~0.79 | ~0.83 | 2nd |
| **Hybrid Approaches** | **~0.85** | **~0.82** | **~0.86** | **1st** |

> 📝 Scores are indicative; refer to the [full paper](https://www.sciencedirect.com/science/article/pii/S2666827022000986) for exact figures, confidence intervals, and statistical significance tests.

---

## 🌐 Applications

The stacking methods reviewed here are directly applicable to — and have been cited in work on — the following tasks:

| Domain | Task |
|---|---|
| **Information Retrieval** | Document ranking, query expansion |
| **Question Answering** | Answer selection, reading comprehension |
| **Knowledge Graphs** | Entity alignment, ontology matching |
| **Machine Translation** | Quality estimation, evaluation metrics |
| **Text Classification** | Short-text categorisation, deduplication |
| **Dialogue Systems** | Intent detection, response selection |
| **Biomedical NLP** | Clinical concept mapping, drug synonym detection |

---

## 📚 Related Work & Context

This paper sits at the intersection of three rich research threads:

- **Semantic Similarity Measures** — vector space models, knowledge-based measures, transformer embeddings (BERT, RoBERTa, Sentence-BERT)
- **Ensemble Learning** — stacking, boosting, bagging, mixture of experts
- **NLP Benchmarking** — SemEval STS tasks, SICK, STR, MRPC, Quora Question Pairs

Researchers building on these threads will find this review a useful entry point and reference taxonomy.

---

## 🗃️ Repository Structure

```
similarity-ensemble/
├── README.md          ← You are here
├── LICENSE            ← MIT License
└── ...                ← Code and notebooks (see paper for methodology)
```

---

## 🚀 Getting Started

### Prerequisites

```bash
python >= 3.8
```

### Clone

```bash
git clone https://github.com/jorge-martinez-gil/similarity-ensemble.git
cd similarity-ensemble
```

> 📄 Full implementation details, dataset preparation steps, and reproduction instructions are described in the accompanying paper.

---

## 🔭 Open Problems & Future Directions

The review surfaces several high-impact open problems — fertile ground for future research and citations:

- **Scalability** — How do stacking ensembles perform at web scale? Can approximate nearest-neighbour structures be integrated?
- **Low-resource & cross-lingual settings** — Most benchmarks are English-centric; multilingual stacking remains underexplored.
- **Interpretability** — How can we explain *why* a stacked model assigns a given score? SHAP / LIME integration?
- **Dynamic ensembles** — Can meta-learners adapt at inference time based on input characteristics?
- **LLM integration** — How do classical stacking strategies interact with GPT / LLaMA-style similarity signals?
- **Continual learning** — Stacking under concept drift in evolving text corpora.

---

## 📖 Citing This Work

If this repository or the associated paper has been useful to your research, please cite:

```bibtex
@article{martinez2022comprehensive,
  title     = {A comprehensive review of stacking methods for semantic similarity measurement},
  author    = {Martinez-Gil, Jorge},
  journal   = {Machine Learning with Applications},
  volume    = {10},
  pages     = {100423},
  year      = {2022},
  publisher = {Elsevier},
  doi       = {10.1016/j.mlwa.2022.100423},
  url       = {https://www.sciencedirect.com/science/article/pii/S2666827022000986}
}
```

> 📌 Using BibTeX ensures your citation is indexed correctly in Google Scholar, Semantic Scholar, and other academic databases.

---

## 📬 Contact & Collaboration

**Jorge Martinez-Gil**
Austrian Institute of Technology (AIT), Vienna, Austria
- 🌐 [GitHub profile](https://github.com/jorge-martinez-gil)
- 📄 [Full paper on ScienceDirect](https://www.sciencedirect.com/science/article/pii/S2666827022000986)
- 🔗 [DOI: 10.1016/j.mlwa.2022.100423](https://doi.org/10.1016/j.mlwa.2022.100423)

Bug reports, questions, and collaboration proposals are welcome via [GitHub Issues](https://github.com/jorge-martinez-gil/similarity-ensemble/issues).

---

<p align="center">
  <sub>⭐ If you find this work useful, consider starring the repository — it helps other researchers discover it.</sub>
</p>
