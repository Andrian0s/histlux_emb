# Benchmarking library and reproduction code for [PARAPHRASUS: A Comprehensive Benchmark for Evaluating Paraphrase Detection Models]

This repository contains the code, datasets, and scripts to reproduce the results and extend from the paper "PARAPHRASUS: A Comprehensive Benchmark for Evaluating Paraphrase Detection Models" presented at COLING2025.

Any set of prediction methods can be used to run a benchmark on any of the specified datasets.

For example, to run all datasets using some example prediction methods, predict_method1 and predict_method2:
```python
from benchmarking import bench

def predict_method1(pairs):
    return [False for _ in pairs]

def predict_method2(pairs):
    return [False for _ in pairs]
methods = {
        "m1": predict_method1,
        "m2": predict_method2
    }

bench(methods, bench_id="mybench")
```
Then, to calculate the average error rate for each method, for each predicted dataset:
```bash
python3 extract_results.py mybench
```
which will save the error rates at: benches/mybench/results.json

## Table of Contents
- [Overview](#overview)
- [Directory Structure](#directory-structure)
- [Reproducing the Experiments](#reproducing-the-experiments)
- [Further Experimentation](#further-experimentation)
- [BibTeX Reference](#bibtex-reference)
- [Datasets and License](#datasets-and-license)
- [Further Support](#further-support)

## Overview

This repository allows replication of the experiments from the research titled "PARAPHRASUS: A Comprehensive Benchmark for Evaluating Paraphrase Detection Models" and is extendable to allow further experimentation, qualitative analysis. It includes:

- Original predictions generated using the models described in the paper, useful for further qualitative or quantitative analysis.
- Scripts and configuration files to reproduce the results.
- Utility scripts to reproduce statistics plots and so on.

## Directory Structure

The repository is organized as follows:

```
├── original_reproduction_code
│   └── The initial version of the repository.
├── datasets_no_results
│   └── Contains the datasets used in the experiments, in a JSON format. Copied for every new benchmark
├── models
│   └── Empty models file used in the experiments.
├── benchmarking.py
│   └── Main benchmarking code, for running predictions on the datasets using specified methods.
├── extract_results.py
│   └── Script for extracting result of a benchmark.
├── sample_llm.py
│   └── Sample script to run benchmarks using LM Studio, with the three prompt templates used in the paper.
├── logger.py
│   └── Utility for managing logging: all events are logged both to stdout and to a local logs.log file.
```

## Reproducing the Experiments

Predictions using the LLMs in the paper can be run locally (provided LM Studio is running and serving the model meta-llama-3-8b-instruct (Meta-Llama-3-8B-Instruct-Q4_K_M.gguf)) like so:
```bash
python3 sample_llm.py reproduce
```
Then, to extract the results (average error rates):
```bash
python3 extract_results.py reproduce
```
Note: You can replace '*reproduce*' with any name

The predictions of the methods mentioned in the paper are given as a benchmark with the identifier 'paper'.
That means, the results (error rates) can be extracted like so:
```bash
python3 extract_results.py paper
```
At benches/paper the file results.json is generated:
```json
{
    "CLF": {
        "PAWSX": {
            "XLM-RoBERTa-EN-ORIG": "15.23%",
            "LLama3 zero-shot P1": "44.67%",
            "LLama3 zero-shot P2": "40.73%",
            "LLama3 zero-shot P3": "38.06%",
            "LLama3 ICL_4 P1": "38.95%",
            "LLama3 ICL_4 P2": "34.12%",
            "LLama3 ICL_4 P3": "33.21%"
        },
        "STS-H": {
            "XLM-RoBERTa-EN-ORIG": "54.07%",
            "LLama3 zero-shot P1": "56.21%",
            "LLama3 zero-shot P2": "37.57%",
            "LLama3 zero-shot P3": "41.72%",
            "LLama3 ICL_4 P1": "44.67%",
            "LLama3 ICL_4 P2": "41.72%",
            "LLama3 ICL_4 P3": "39.05%"
        },
        "MRPC": {
            "XLM-RoBERTa-EN-ORIG": "33.41%",
            "LLama3 zero-shot P1": "23.59%",
            "LLama3 zero-shot P2": "45.86%",
            "LLama3 zero-shot P3": "37.51%",
            "LLama3 ICL_4 P1": "33.22%",
            "LLama3 ICL_4 P2": "45.16%",
            "LLama3 ICL_4 P3": "46.72%"
        }
    },
    "MIN": {
        "SNLI": {
            "XLM-RoBERTa-EN-ORIG": "32.39%",
            "LLama3 zero-shot P1": "7.29%",
            "LLama3 zero-shot P2": "1.00%",
            "LLama3 zero-shot P3": "1.25%",
            "LLama3 ICL_4 P1": "1.95%",
            "LLama3 ICL_4 P2": "0.84%",
            "LLama3 ICL_4 P3": "0.50%"
        },
        "ANLI": {
            "XLM-RoBERTa-EN-ORIG": "7.24%",
            "LLama3 zero-shot P1": "13.03%",
            "LLama3 zero-shot P2": "1.19%",
            "LLama3 zero-shot P3": "1.69%",
            "LLama3 ICL_4 P1": "2.01%",
            "LLama3 ICL_4 P2": "0.75%",
            "LLama3 ICL_4 P3": "0.75%"
        },
        "XNLI": {
            "XLM-RoBERTa-EN-ORIG": "26.69%",
            "LLama3 zero-shot P1": "12.33%",
            "LLama3 zero-shot P2": "1.36%",
            "LLama3 zero-shot P3": "1.32%",
            "LLama3 ICL_4 P1": "2.79%",
            "LLama3 ICL_4 P2": "0.30%",
            "LLama3 ICL_4 P3": "0.25%"
        },
        "STS": {
            "XLM-RoBERTa-EN-ORIG": "46.57%",
            "LLama3 zero-shot P1": "12.89%",
            "LLama3 zero-shot P2": "2.41%",
            "LLama3 zero-shot P3": "3.54%",
            "LLama3 ICL_4 P1": "3.54%",
            "LLama3 ICL_4 P2": "3.12%",
            "LLama3 ICL_4 P3": "2.41%"
        },
        "SICK": {
            "XLM-RoBERTa-EN-ORIG": "37.01%",
            "LLama3 zero-shot P1": "0.87%",
            "LLama3 zero-shot P2": "0.13%",
            "LLama3 zero-shot P3": "0.04%",
            "LLama3 ICL_4 P1": "0.26%",
            "LLama3 ICL_4 P2": "0.00%",
            "LLama3 ICL_4 P3": "0.00%"
        }
    },
    "MAX": {
        "TRUE": {
            "XLM-RoBERTa-EN-ORIG": "31.36%",
            "LLama3 zero-shot P1": "8.98%",
            "LLama3 zero-shot P2": "34.73%",
            "LLama3 zero-shot P3": "35.33%",
            "LLama3 ICL_4 P1": "29.94%",
            "LLama3 ICL_4 P2": "40.12%",
            "LLama3 ICL_4 P3": "50.90%"
        },
        "SIMP": {
            "XLM-RoBERTa-EN-ORIG": "5.27%",
            "LLama3 zero-shot P1": "14.67%",
            "LLama3 zero-shot P2": "47.33%",
            "LLama3 zero-shot P3": "37.50%",
            "LLama3 ICL_4 P1": "33.33%",
            "LLama3 ICL_4 P2": "42.33%",
            "LLama3 ICL_4 P3": "45.50%"
        }
    }
}
```

## Further Experimentation

You can run your own experiments using any prediction methods of your choosing

## BibTeX Reference

If you use this repository or the reproduced results in your work, please cite the original paper:

\`\`\`bibtex
@misc{michail2024paraphrasuscomprehensivebenchmark,
      title={PARAPHRASUS : A Comprehensive Benchmark for Evaluating Paraphrase Detection Models}, 
      author={Andrianos Michail and Simon Clematide and Juri Opitz},
      year={2024},
      eprint={2409.12060},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2409.12060}, 
}
\`\`\`

## Datasets and License

This repository inherits its license from the original release, and all datasets used are publicly available from the following links (among many others):

1. **PAWS-X**  
   Link: [PAWS-X Dataset](https://github.com/google-research-datasets/paws/tree/master/pawsx)

2. **SICK-R**  
   Link: [SICK-R Dataset](https://zenodo.org/records/2787612)

3. **MSRPC**  
   Link: [Microsoft Research Paraphrase Corpus](https://www.microsoft.com/en-us/download/details.aspx?id=52398)

4. **XNLI**  
   Link: [XNLI Dataset](https://cims.nyu.edu/~sbowman/xnli/)

5. **ANLI**  
   Link: [Adversarial NLI (ANLI)](https://github.com/facebookresearch/anli) 

6. **Stanford NLI (SNLI)**  
   Link: [SNLI Dataset](https://nlp.stanford.edu/projects/snli/)

7. **STS Benchmark**  
   Link: [STS Benchmark](https://ixa2.si.ehu.eus/stswiki/index.php/STSbenchmark)

8. **OneStopEnglish Corpus**  
   Link: [OneStopEnglish Corpus](https://github.com/nishkalavallabhi/OneStopEnglish)


Within this work, we introduce a dataset (and an annotation on an existing one) which are also available within our repository under the same license as the source dataset

1. **AMR True Paraphrases** Source: (https://github.com/amrisi/amr-guidelines) Dataset: [AMR-True-Paraphrases](https://huggingface.co/datasets/impresso-project/amr_true_paraphrases)

2. **STS Benchmark (Scores 4-5) (STS-H) with Paraphrase Label** 
   Link: [STS Hard](https://huggingface.co/datasets/impresso-project/sts-h-paraphrase-detection)


## Further Support

In the future, we will work towards adding more datasets (also multilingual) and to make the benchmark more compute efficient. If you are interested in contributing or need support reproducing/recreating/extending the results, please reach out to andrianos.michail@uzh.ch
