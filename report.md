# Formality Detection Evaluation System - Report

## Introduction

This report documents the development and evaluation of a formality detection system. The goal is to assess different approaches for detecting formality levels in text, with a focus on evaluating their performance across different datasets and metrics.

## Methodology

### Data Collection and Preparation

I used two main datasets:

1. **Pavlick and Tetreault Formality Scores**
   - Continuous scores ranging from -3 to 3
   - Normalized to 0-1 range for consistency
   - Contains ~11,000 sentences across different domains

2. **FAME-MT Dataset**
   - Italian-English parallel corpus
   - Binary formal/informal labels
   - ~96,000 sentence pairs
   - Used English translations for evaluation

### Model Approaches

We evaluated three different approaches:

1. **Pre-trained Models**
   - mDeBERTa-base-formality-ranker
   - XLM-R formality classifier
   - Both models fine-tuned for formality detection

2. **N-gram Model**
   - Character-level n-grams (2-6)
   - Logistic Regression classifier
   - Trained on both datasets

3. **LLM-based Approach**
   - GPT-Neo 1.3B
   - Prompt-based formality scoring
   - 1-5 scale converted to 0-1 range

### Evaluation Metrics

We used both binary and continuous metrics:

#### Binary Metrics
- Accuracy
- Precision
- Recall
- F1 Score
- Confusion Matrix

#### Continuous Metrics
- Mean Absolute Error (MAE)
- Mean Squared Error (MSE)
- R² Score
- Pearson Correlation
- Spearman Correlation

## Results

### Model Performance

#### Binary Classification
- Accuracy: 0.670
- Precision: 0.605
- Recall: 0.980
- F1 Score: 0.748

The high recall but lower precision suggests the model is biased towards predicting formal text, potentially due to class imbalance in the training data.

#### Continuous Scoring
- MAE: 0.368
- MSE: 0.177
- R²: -2.071
- Pearson Correlation: 0.600
- Spearman Correlation: 0.763

The negative R² score indicates that the model performs worse than a simple mean predictor. However, the relatively high Spearman correlation suggests good ranking performance.

### Model Comparison

1. **Pre-trained Models**
   - XLM-R showed better performance on continuous scoring
   - mDeBERTa performed better on binary classification
   - Both models struggled with informal text detection

2. **N-gram Model**
   - Performed well on binary classification (93.3% accuracy)
   - Less effective for continuous scoring
   - Good generalization across domains

3. **LLM-based Approach**
   - Showed promise but required significant prompt engineering
   - High computational cost
   - Good at capturing nuanced formality levels

## Challenges and Limitations

1. **Data Quality**
   - Inconsistent labeling across datasets
   - Domain-specific biases
   - Limited coverage of informal text

2. **Model Limitations**
   - Difficulty in capturing context-dependent formality
   - Bias towards formal text
   - Computational constraints with LLM approach

3. **Evaluation Challenges**
   - Subjectivity in formality assessment
   - Lack of standardized evaluation metrics
   - Domain transfer issues

## Future Work

1. **Data Improvements**
   - Collect more diverse informal text
   - Create domain-specific evaluation sets
   - Improve annotation guidelines

2. **Model Enhancements**
   - Implement cross-validation
   - Add model calibration
   - Develop ensemble approaches

3. **Evaluation Framework**
   - Add error analysis
   - Implement domain-specific metrics
   - Create visualization tools

4. **Practical Applications**
   - Develop web interface
   - Add batch processing
   - Create API for integration

## Conclusion

The evaluation system provides a comprehensive framework for assessing formality detection models. While current results show room for improvement, the system successfully highlights the strengths and weaknesses of different approaches. Future work should focus on addressing the identified limitations and expanding the evaluation framework. 