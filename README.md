# Formality Detection Evaluation System

This project implements an evaluation system for formality detection models, comparing different approaches and providing comprehensive metrics for assessment.

## Project Structure

```
.
├── README.md
├── evaluation_system.ipynb
├── requirements.txt
└── data/
    ├── it-en.formal.tsv
    └── it-en.informal.tsv
```

## Setup

1. Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

## Datasets

The system uses two main datasets:

1. **Pavlick and Tetreault Formality Scores**
   - Source: Hugging Face Datasets
   - Format: Continuous scores (-3 to 3, normalized to 0-1)
   - Size: ~11,000 sentences

2. **FAME-MT Dataset**
   - Source: Italian-English parallel corpus
   - Format: Binary formal/informal labels
   - Size: ~96,000 sentence pairs

## Models

The system evaluates three types of models:

1. **Pre-trained Models**
   - mDeBERTa-base-formality-ranker
   - XLM-R formality classifier

2. **N-gram Model**
   - Character-level n-grams (2-6)
   - Logistic Regression classifier

3. **LLM-based Approach**
   - GPT-Neo 1.3B
   - Prompt-based formality scoring

## Evaluation Metrics

The system provides both binary and continuous evaluation metrics:

### Binary Metrics
- Accuracy
- Precision
- Recall
- F1 Score
- Confusion Matrix

### Continuous Metrics
- Mean Absolute Error (MAE)
- Mean Squared Error (MSE)
- R² Score
- Pearson Correlation
- Spearman Correlation

## Usage

1. Open the Jupyter notebook:
```bash
jupyter notebook evaluation_system.ipynb
```

2. Run the cells in sequence to:
   - Load and preprocess data
   - Train/evaluate models
   - Generate evaluation metrics

## Results

Current model performance:

### Binary Classification
- Accuracy: 0.670
- Precision: 0.605
- Recall: 0.980
- F1 Score: 0.748

### Continuous Scoring
- MAE: 0.368
- MSE: 0.177
- R²: -2.071
- Pearson Correlation: 0.600
- Spearman Correlation: 0.763

## Future Improvements

1. Add cross-validation
2. Implement error analysis
3. Add model interpretability
4. Create web interface
5. Support batch processing
6. Add model calibration analysis

## License

MIT License 