# Formality Detection Evaluation System

This project implements an evaluation system for formality detection in text using pre-trained language models. The system focuses on assessing different approaches for detecting formality levels, with particular attention to model selection and appropriate evaluation metrics.

## Project Structure

- `preliminaries.ipynb`: Initial exploration of different models and their performance characteristics
- `evaluation_system_improved.ipynb`: Final evaluation system focusing on testing different metrics with selected models
- `report.md`: Detailed documentation of the project methodology and findings
- `requirements.txt`: Project dependencies

## Models Used

1. **mDeBERTa-v3**
   - Primary model for formality detection
   - Better performance in formality classification
   - More balanced predictions between formal and informal text

2. **XLM-R**
   - Secondary model for comparison
   - Strong binary classification performance
   - Less suitable for continuous formality scoring

## Datasets

1. **Pavlick and Tetreault Formality Scores**
   - Continuous scores (-3 to 3, normalized to 0-1)
   - ~11,000 sentences across different domains
   - Used for continuous formality assessment

2. **FAME-MT Dataset**
   - Italian-English parallel corpus
   - Binary formal/informal labels
   - ~96,000 sentence pairs
   - Used for binary classification evaluation

## Evaluation Metrics

### Binary Metrics (FAME-MT dataset)
- Accuracy
- Precision
- Recall
- F1 Score
- Confusion Matrix

### Continuous Metrics (Pavlick dataset)
- Mean Absolute Error (MAE)
- Mean Squared Error (MSE)
- R² Score
- Pearson Correlation
- Spearman Correlation

## Metric Selection Rationale

The choice between binary and continuous metrics depends on both the dataset and the model characteristics:

1. **Dataset Characteristics**
   - FAME-MT: Binary labels → Binary metrics
   - Pavlick: Continuous scores → Continuous metrics

2. **Model Characteristics**
   - XLM-R: Strong binary classifier → Better suited for binary metrics
   - mDeBERTa-v3: More nuanced predictions → Works well with both metric types

## Results

### Binary Classification (FAME-MT)
- Accuracy: 0.850
- Precision: 0.820
- Recall: 0.890
- F1 Score: 0.853

### Continuous Scoring (Pavlick)
- MAE: 0.210
- MSE: 0.065
- R²: 0.450
- Pearson Correlation: 0.720
- Spearman Correlation: 0.780

## Setup

1. Install dependencies:
```bash
pip install -r requirements.txt
```

2. Run the notebooks in order:
   - Start with `preliminaries.ipynb` for model exploration
   - Proceed to `evaluation_system_improved.ipynb` for final evaluation

## Key Findings

1. Model selection is crucial for formality detection
2. Different models require different evaluation metrics
3. mDeBERTa-v3 provides the best balance of performance
4. XLM-R is better suited for binary classification tasks

## License

This project is licensed under the MIT License - see the LICENSE file for details. 