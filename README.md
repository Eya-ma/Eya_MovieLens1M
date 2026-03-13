# MovieLens 1M Recommendation Analysis using LLMs and Conformal Evaluation

## Project Overview

This project investigates the use of Large Language Models (LLMs) for rating prediction and recommendation analysis using the MovieLens-1M dataset.

Unlike other datasets that rely heavily on textual content such as reviews, MovieLens-1M is primarily composed of **structured interaction data** between users and movies. Despite the absence of textual reviews, the dataset contains rich contextual information including user demographics and movie metadata.

The goal of this project is to explore how LLM-based approaches can be applied to structured recommendation data while maintaining reliable evaluation through statistical and semantic validation techniques.

The experimental pipeline includes data preprocessing, prompt construction, model fine-tuning, classical evaluation metrics, conformal prediction for statistical reliability, and hallucination detection.

---

# Dataset

The experiments are conducted on the **MovieLens-1M dataset**, one of the most widely used benchmark datasets in recommender systems research.

The dataset contains:

* 1 million ratings
* 6,040 users
* 3,952 movies

Each interaction includes:

* User ID
* Movie ID
* Rating value
* Timestamp

Additionally, the dataset provides contextual information such as:

* User demographic data (age, gender, occupation)
* Movie metadata (title, genres)

Because of its clean structure and balanced scale, MovieLens-1M is commonly used for evaluating recommendation algorithms and conducting controlled experimental studies.

Dataset source:
https://grouplens.org/datasets/movielens/1m/

---

# Data Preprocessing

The preprocessing stage prepares the dataset for training and evaluation.

Key preprocessing steps include:

* Loading and merging the rating, user, and movie tables
* Cleaning and formatting the data
* Handling missing or inconsistent values
* Encoding categorical attributes
* Preparing contextual inputs for the model
* Constructing user interaction histories

Since the dataset does not contain textual reviews, the contextual information is derived from **structured metadata and interaction patterns**.

---

# Prompt Construction

To adapt the structured dataset for LLM training, the data is converted into an **instruction-style prompt format**.

Each training instance includes contextual information such as:

Input:

* User demographic attributes
* Movie metadata (title, genre)
* User interaction history (optional)

Output:

* Predicted rating

Two experimental settings are considered:

* With user history
* Without user history

This setup allows analyzing the effect of historical interaction information on rating prediction.

---

# Model Fine-Tuning

The base model used in this project is **Mistral-7B**, which is fine-tuned using the structured MovieLens dataset.

Training configuration:

* Instruction-style prompt format
* Parameter-efficient fine-tuning
* Two training epochs
* Hyperparameter tuning

The objective is to enable the model to learn relationships between contextual information and user rating behavior.

---

# Model Evaluation

Model performance is evaluated using classical regression metrics.

Evaluation metrics include:

* RMSE (Root Mean Squared Error)
* MAE (Mean Absolute Error)
* AUC (Area Under the Curve)

These metrics measure the accuracy and reliability of predicted ratings.

---

# Conformal Prediction

To evaluate the **statistical reliability of predictions**, conformal prediction techniques are applied.

Conformal prediction provides:

* Calibrated prediction intervals
* Uncertainty quantification
* Statistical guarantees on prediction coverage

This approach improves the trustworthiness of model outputs.

Experiments are conducted in both settings:

* With user history
* Without user history

---

# Hallucination Detection

Although the dataset is structured, LLM predictions may still produce inconsistent outputs. Therefore, hallucination detection mechanisms are applied.

Two types of hallucinations are analyzed:

### Syntactic hallucinations

These correspond to structural inconsistencies in the generated output.

### Uncertainty-based hallucinations

These indicate predictions with high uncertainty or unreliable behavior.

---

# Semantic Verification using LLM as a Judge

To further validate prediction quality, an additional LLM is used as an evaluator.

The judge model evaluates whether the predicted rating is coherent with the contextual information provided to the model.

The evaluation produces:

* Coherence score
* Verdict
* Explanation

This process provides an additional semantic validation layer for the predicted ratings.

---

# Visualization and Analysis

Several visualizations are generated to analyze experimental results, including:

* Prediction error distributions
* Model performance comparisons
* Hallucination statistics
* Semantic coherence evaluation

These analyses help better understand the strengths and limitations of the proposed approach.

---

# Research Objective

The main objective of this project is to explore how Large Language Models can be applied to **structured recommendation datasets** and to study their behavior in comparison with text-rich datasets.

The study focuses on:

* Leveraging contextual metadata in recommendation tasks
* Evaluating prediction reliabi
