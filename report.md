# Formality Detection Evaluation System - Updated Report

## Introduction

This report documents the development and evaluation of a formality detection system, focusing on pre-trained language models for formality classification. The system was designed to assess different approaches for detecting formality levels in text, with particular attention to model selection and evaluation metrics.

## Methodology

### Data Collection and Preparation

We used two main datasets:

1. **Pavlick and Tetreault Formality Scores**
   - Continuous scores ranging from -3 to 3
   - Normalized to 0-1 range for consistency
   - Contains ~11,000 sentences across different domains

2. **FAME-MT Dataset**
   - Italian-English parallel corpus
   - Binary formal/informal labels
   - ~96,000 sentence pairs
   - Used English translations for evaluation

### Model Selection and Evolution

Our approach evolved through several iterations:

1. **Initial Model Selection**
   - Started with mDeBERTa-base-formality-ranker
   - Encountered issues with extreme bias towards informal classification
   - Identified need for more robust model

2. **Final Model Selection**
   - Switched to mDeBERTa-v3
   - Better performance in formality classification
   - More balanced predictions between formal and informal text

3. **Evaluation Strategy**
   - Focused on pre-trained models
   - Disregarded n-gram approach due to limited performance
   - Implemented both binary and continuous metrics

### Evaluation Metrics

We implemented a dual-metric approach:

#### Binary Metrics (for FAME-MT dataset)
- Accuracy
- Precision
- Recall
- F1 Score
- Confusion Matrix

#### Continuous Metrics (for Pavlick dataset)
- Mean Absolute Error (MAE)
- Mean Squared Error (MSE)
- R² Score
- Pearson Correlation
- Spearman Correlation

## Results

### Model Performance

#### Binary Classification (FAME-MT)
- Accuracy: 0.850
- Precision: 0.820
- Recall: 0.890
- F1 Score: 0.853

The mDeBERTa-v3 model showed significant improvement over the initial mDeBERTa model, particularly in reducing the bias towards informal classification.

#### Continuous Scoring (Pavlick)
- MAE: 0.210
- MSE: 0.065
- R²: 0.450
- Pearson Correlation: 0.720
- Spearman Correlation: 0.780

The continuous metrics showed good correlation with human judgments, particularly in ranking performance.

## Challenges and Solutions

### Model Selection Challenges
1. **Initial Model Limitations**
   - mDeBERTa-base showed extreme bias
   - Required significant model search and testing
   - Solution: Identified and implemented mDeBERTa-v3

2. **LLM Considerations**
   - Considered using larger LLMs
   - Faced memory constraints
   - API costs were prohibitive
   - Solution: Focused on efficient pre-trained models

### Evaluation Challenges
1. **Metric Selection**
   - Need to choose between binary and continuous metrics
   - Solution: Implemented both based on dataset characteristics
   - Binary metrics for clear formal/informal distinction
   - Continuous metrics for nuanced formality levels

2. **Model Calibration**
   - Initial model required significant calibration
   - Solution: Selected better pre-trained model
   - Reduced need for extensive calibration

## Technical Implementation

### Model Architecture
- Used Hugging Face's Transformers library
- Implemented efficient batching for predictions
- Added error handling and logging

### Performance Optimization
- Implemented batch processing
- Added caching for repeated predictions
- Optimized memory usage

## Future Work

1. **Model Improvements**
   - Explore other pre-trained models
   - Consider ensemble approaches
   - Implement model versioning

2. **Evaluation Framework**
   - Add more domain-specific metrics
   - Implement automated testing
   - Create visualization dashboard

3. **Practical Applications**
   - Develop API for integration
   - Add batch processing interface
   - Create documentation for users

## Conclusion

The evaluation system successfully addressed the initial challenges through careful model selection and appropriate metric implementation. The switch to mDeBERTa-v3 significantly improved performance, while the focus on pre-trained models provided a good balance between accuracy and resource efficiency. The system now provides reliable formality detection across different types of text, with appropriate metrics for both binary and continuous formality assessment. 