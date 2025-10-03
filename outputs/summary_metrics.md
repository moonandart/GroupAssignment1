# Sentiment Analysis – Summary Metrics
_Generated: 2025-10-03 15:22:13_

## Best Model
- **Best:** NaiveBayes
- Validation Accuracy (NB): 0.5882352941176471
- Validation Accuracy (LR): 0.5698529411764706

## Validation Metrics (Best Model)
- Accuracy: 0.5882
- Macro F1: 0.5873
- Weighted F1: 0.5868

## Test Metrics (Final Model)
- Accuracy: 0.6337
- Macro F1: 0.6322
- Weighted F1: 0.6320

## Artifacts
- Vectorizer (local): `./artifacts/tfidf_vectorizer_NaiveBayes_20251003_150729.joblib`
- Model (local): `./artifacts/model_NaiveBayes_20251003_150729.joblib`
- Vectorizer (Drive): `/content/drive/My Drive/Proyek/OutputSentimentNew/artifacts/tfidf_vectorizer_NaiveBayes_20251003_150729.joblib`
- Model (Drive): `/content/drive/My Drive/Proyek/OutputSentimentNew/artifacts/model_NaiveBayes_20251003_150729.joblib`

## Confusion Matrices
- Naive Bayes: `./outputs/confusion_matrix_nb.png`
- Logistic Regression: `./outputs/confusion_matrix_lr.png`

## Validation Classification Report (Full JSON)
```json
{
  "0": {
    "precision": 0.5754716981132075,
    "recall": 0.6853932584269663,
    "f1-score": 0.6256410256410256,
    "support": 89.0
  },
  "1": {
    "precision": 0.65,
    "recall": 0.5714285714285714,
    "f1-score": 0.6081871345029239,
    "support": 91.0
  },
  "2": {
    "precision": 0.5465116279069767,
    "recall": 0.5108695652173914,
    "f1-score": 0.5280898876404494,
    "support": 92.0
  },
  "accuracy": 0.5882352941176471,
  "macro avg": {
    "precision": 0.5906611086733947,
    "recall": 0.5892304650243096,
    "f1-score": 0.587306015928133,
    "support": 272.0
  },
  "weighted avg": {
    "precision": 0.5906104812482255,
    "recall": 0.5882352941176471,
    "f1-score": 0.5868064345027159,
    "support": 272.0
  }
}
```

## Test Classification Report (Full JSON)
```json
{
  "0": {
    "precision": 0.5929203539823009,
    "recall": 0.7444444444444445,
    "f1-score": 0.6600985221674877,
    "support": 90.0
  },
  "1": {
    "precision": 0.7142857142857143,
    "recall": 0.5494505494505495,
    "f1-score": 0.6211180124223602,
    "support": 91.0
  },
  "2": {
    "precision": 0.6222222222222222,
    "recall": 0.6086956521739131,
    "f1-score": 0.6153846153846154,
    "support": 92.0
  },
  "accuracy": 0.6336996336996337,
  "macro avg": {
    "precision": 0.6431427634967458,
    "recall": 0.634196882022969,
    "f1-score": 0.6322003833248211,
    "support": 273.0
  },
  "weighted avg": {
    "precision": 0.6432500963474415,
    "recall": 0.6336996336996337,
    "f1-score": 0.6320365961204882,
    "support": 273.0
  }
}
```