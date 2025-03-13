# Reproduction code, supplementary materials for [Adapting Multilingual Embedding Models to Historical Luxembourgish](https://www.arxiv.org/abs/2502.07938)
![License: AGPLV3+](https://img.shields.io/badge/License-AGPLV3+-brightgreen.svg)

## Overview

This repository allows replication of the experiments from the research titled "Adapting Multilingual Embedding Models to Historical Luxembourgish". This repository includes:

- Scripts and notebooks to replicate the training and evaluation of the examined models.
- The training and test data created through articles in Historical Luxembourgish.
- Our reccomended adapted models to be used for semantic search to and from Historical Luxembourgish.

## Repository Organization:

The repository is organized as follows:

```
├── RAW_test_set_sentences
│   └── The test set sentences that constitute the bitext mining task, in a jsonl raw unprocessed format.
├── prepared_training_sentences
│   └── The prepared sentences pairs used within the training set. (Also available in HuggingFace datasets format)
├── raw_translations_json
│   └── The original post-corrected translations files before training and test split.
├── HistLuxEmb_Prepare_Data_and_Evaluation.ipynb
│   └── Jupyter notebook to follow through to prepare the data (including utilities) and evaluate existing models.
├── HistLuxEmb_Contrastive_Training.ipynb
│   └── Jupyter notebook to follow through to perform the contrastive training that was appleid to LaBSE, LuxEmbedder and M-GTE.
├── HistLuxEmb_M-Mpnet_Knowledge_Dist.py
│   └── Python script to extend the Multilingual-MPNet model to support Historical and Modern Luxembourgish.
```

## Released Datasets:

Training Set:

[HistLuxAlign](https://huggingface.co/datasets/impresso-project/HistLuxAlign)

Bitext Mining Test Set (already prepared for convinience):

[GoogleDriveLink](https://drive.google.com/file/d/1B_na_iXXa5nNcfh8L7sNIln9hNkji0ad/view?usp=share_link)

## Released Models:

Reccomended: [histlux-gte-multilingual-base](https://huggingface.co/impresso-project/histlux-gte-multilingual-base)

Alternative: [histlux-paraphrase-multilingual-mpnet-base-v2](https://huggingface.co/impresso-project/histlux-paraphrase-multilingual-mpnet-base-v2)

## Further Support
If you are interested in contributing or need further support reproducing/recreating/extending the results, please reach out to andrianos.michail@cl.uzh.ch.

## BibTeX Reference

If you would like to cite this project, or the associated paper, here's a bibtex:

```bibtex
@misc{michail2025adaptingmultilingualembeddingmodels,
      title={Adapting Multilingual Embedding Models to Historical Luxembourgish}, 
      author={Andrianos Michail and Corina Julia Raclé and Juri Opitz and Simon Clematide},
      year={2025},
      eprint={2502.07938},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2502.07938}, 
}
```

## About Impresso

### Impresso project

[Impresso - Media Monitoring of the Past](https://impresso-project.ch) is an interdisciplinary research project that aims to develop and consolidate tools for processing and exploring large collections of media archives across modalities, time, languages and national borders. The first project (2017-2021) was funded by the Swiss National Science Foundation under grant No. [CRSII5_173719](http://p3.snf.ch/project-173719) and the second project (2023-2027) by the SNSF under grant No. [CRSII5_213585](https://data.snf.ch/grants/grant/213585) and the Luxembourg National Research Fund under grant No. 17498891.

### Copyright

Copyright (C) 2025 The Impresso team.

### License

This program is provided as open source under the [GNU Affero General Public License](https://github.com/impresso/impresso-pyindexation/blob/master/LICENSE) v3 or later.
