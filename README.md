# CAFA-6 Protein Function Prediction (ESM2 + LR / XGBoost + GO Hierarchy)

This repository implements a protein function prediction pipeline for the CAFA-6 challenge using precomputed ESM2 embeddings, classical multi-label classifiers, and Gene Ontology (GO) hierarchy propagation.

## Overview

The pipeline consists of protein representation using precomputed ESM2 embeddings, multi-label classification with Logistic Regression and XGBoost under a One-vs-Rest strategy, post-processing with Gene Ontology hierarchy propagation to enforce the true-path rule, and generation of CAFA-compliant submission files. Two main models are provided: Logistic Regression + ESM2 + GO hierarchy and XGBoost + ESM2 + GO hierarchy.

## Environment

The code is implemented in Python and was tested using:

Python 3.13.2

The implementation is IDE-independent and can be executed in any environment that supports Jupyter notebooks, such as Jupyter Notebook or Visual Studio Code.

## Required Libraries

Install all required dependencies using:

pip install numpy pandas scipy scikit-learn tqdm xgboost

The project relies on the following Python packages: numpy, pandas, scipy, scikit-learn, xgboost, and tqdm.

## Repository Structure

The repository contains the following files:

- LR_ESM2_Go.ipynb: Logistic Regression pipeline
- XGboost_ESM2_Go.ipynb: XGBoost pipeline
- README.md: Project documentation
- go-basic.obo: Gene Ontology hierarchy file
- IA.tsv: Allowed GO term whitelist
- train_sequences.fasta: Training protein sequences
- train_terms.tsv: Training Gene Ontology annotations
- train_taxonomy.tsv: Training taxonomy information
- testsuperset.fasta: Test protein sequences
- testsuperset-taxon-list.tsv: Test taxonomy information
- sample_submission.tsv: Example CAFA submission format
The embeddings can be downloaded from the following Google Drive link: https://drive.google.com/drive/folders/1m2NWBZx6ADvTHvad2MkeDe9Up32sqzTn?usp=drive_link



All files are expected to be located in the root directory of the repository.

## Data Description

Training data consists of protein sequences and their associated Gene Ontology annotations. Protein sequences are represented using precomputed ESM2 embeddings stored in NumPy format. The Gene Ontology hierarchy is provided via the go-basic.obo file and is used during inference to propagate prediction scores according to parent–child relationships.

## Running the Code

This project is implemented using Visual Studio Code and can be executed using any compatible Python environment.

To run the experiments:
1. Ensure all required dependencies are installed.
2. Open one of the provided notebooks:
   - LR_ESM2_Go.ipynb for the Logistic Regression model
   - XGboost_ESM2_Go.ipynb for the XGBoost model
3. Run all cells sequentially to perform training, validation, inference, GO hierarchy propagation, and submission file generation.

## Output

The final output is a CAFA-compliant submission file with the following format:

EntryID    GO_ID    Confidence

An example of the required format is provided in sample_submission.tsv.

## Notes

Logistic Regression serves as a strong and stable baseline model when combined with ESM2 embeddings. XGBoost is included as a non-linear comparison model. Gene Ontology hierarchy propagation plays a critical role in improving recall and ensuring biological consistency of predictions. The use of precomputed ESM2 embeddings significantly reduces computational cost.

## Acknowledgements

This project was developed for the CAFA-6 Protein Function Prediction challenge.
