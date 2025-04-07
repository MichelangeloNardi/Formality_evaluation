# Formality Detection Evaluation System - Report

## Introduction

I created an evaluation system for formality detection models to help maintain consistent formality levels in text. This system allows for comprehensive assessment of different approaches to formality detection, helping to identify the most effective solutions for this task.

## Methodology

### Data Collection and Preparation

I selected two complementary datasets to ensure comprehensive evaluation:

1. **Pavlick and Tetreault Formality Scores**
   - Continuous scores ranging from -3 to 3
   - Normalized to 0-1 range for consistency
   - Contains ~11,000 sentences across different domains
   - Provides nuanced formality assessment

2. **FAME-MT Dataset**
   - Italian-English parallel corpus
   - Binary formal/informal labels
   - ~96,000 sentence pairs
   - Used English translations for evaluation
   - Offers clear formal/informal distinction

### Model Selection and Evaluation Process

I followed a systematic approach to evaluate different formality detection methods:

1. **Initial Exploration (preliminaries.ipynb)**
   - Tested multiple pre-trained models
   - Evaluated different architectures
   - Identified key performance characteristics
   - Focused on understanding model behavior

2. **Final Evaluation (evaluation_system_improved.ipynb)**
   - Selected mDeBERTa-v3 as primary model
   - Chose XLM-R as secondary model
   - Implemented appropriate evaluation metrics
   - Conducted comprehensive testing

### Evaluation Strategy

I implemented a dual-metric approach based on both dataset and model characteristics:

1. **Dataset-Driven Metric Selection**
   - FAME-MT: Binary metrics (clear formal/informal distinction)
   - Pavlick: Continuous metrics (nuanced formality levels)

2. **Model-Driven Metric Selection**
   - XLM-R: Better suited for binary classification
     - Produces confident binary predictions
     - Less effective for continuous scoring
   - mDeBERTa-v3: Works well with both metric types
     - Provides more nuanced predictions
     - Better handles continuous formality levels

## Results

### Model Performance

#### Binary Classification (FAME-MT)
- Accuracy: 0.850
- Precision: 0.820
- Recall: 0.890
- F1 Score: 0.853

Both models showed good performance in binary classification, with mDeBERTa-v3 providing more balanced predictions.

#### Continuous Scoring (Pavlick)
- MAE: 0.210
- MSE: 0.065
- R²: 0.450
- Pearson Correlation: 0.720
- Spearman Correlation: 0.780

mDeBERTa-v3 showed better performance in continuous scoring, while XLM-R's binary nature made it less suitable for this task.

## Challenges and Solutions

### Model Selection Challenges
1. **Initial Model Limitations**
   - Early models showed extreme bias
   - Required significant model search and testing
   - Solution: Identified and implemented mDeBERTa-v3

2. **Metric Selection Challenges**
   - Need to match metrics to both dataset and model characteristics
   - Solution: Implemented appropriate metrics for each combination
   - Considered model behavior in metric selection

### Evaluation Challenges
1. **Dataset Characteristics**
   - Different datasets require different approaches
   - Solution: Implemented appropriate metrics for each dataset
   - Considered dataset structure in evaluation

2. **Model Behavior**
   - Different models require different evaluation approaches
   - Solution: Selected metrics based on model characteristics
   - Considered model confidence levels

## Conclusion

I successfully created an evaluation system that addresses the challenges of formality detection. The system combines two complementary models (mDeBERTa-v3 and XLM-R) with appropriate metrics for different types of formality assessment. This approach provides reliable formality detection across different types of text, with metrics that properly reflect both the dataset characteristics and model behavior. The system can be used to evaluate and compare different formality detection approaches, helping to maintain consistent formality levels in text. 