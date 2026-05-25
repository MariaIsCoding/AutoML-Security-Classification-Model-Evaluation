# Week 5: AutoML Security Classification & Model Evaluation

## Overview

This project explored no-code machine learning model development, classification evaluation, and comparative model analysis in a cybersecurity context.

The objective was to train a custom phishing detection classifier, evaluate its performance using standard machine learning metrics, and compare generic versus fine-tuned transformer models to assess suitability for cybersecurity alert classification.

As part of the broader AI Quiz Generator capstone, this lab provided practical experience in model selection, performance interpretation, and understanding how AI models behave under different classification tasks.

---

## Objectives

- Train a custom classification model without writing code
- Evaluate performance using confusion matrix analysis
- Measure classification quality using accuracy, precision, recall, and F1 score
- Compare generic vs fine-tuned transformer models
- Assess model suitability for cybersecurity-related classification workflows
- Analyze tradeoffs between confidence, specialization, and practical deployment

---

## Part A: Custom AutoML Model Training

### Task
Binary classification:

- **Phishing**
- **Legitimate**

### Platform
Google Teachable Machine

### Training Setup

| Configuration | Value |
|-------------|-------|
| Training Images per Class | 20 |
| Test Images per Class | 5 |
| Total Test Samples | 10 |
| Training Time | ~30 seconds |

This exercise demonstrated the complete no-code ML lifecycle:

- dataset preparation
- supervised model training
- held-out evaluation
- confusion matrix analysis
- performance interpretation

---

## Model Performance

### Test Results

| Metric | Score |
|-------|-------|
| Accuracy | 80% |
| Precision | 80% |
| Recall | 80% |
| F1 Score | 80% |

---

## Confusion Matrix

|                  | Predicted Phishing | Predicted Legitimate |
|------------------|-------------------|---------------------|
| Actual Phishing  | TP = 4            | FN = 1              |
| Actual Legitimate| FP = 1            | TN = 4              |

---

## Key Findings

The classifier demonstrated balanced performance across precision and recall, correctly identifying the majority of phishing and legitimate samples.

However, false negatives remain the highest-risk failure case in a cybersecurity setting, since undetected phishing attempts can lead to:

- credential theft
- unauthorized access
- financial loss
- system compromise

This reinforced an important practical lesson:

> Accuracy alone is not enough in security-focused machine learning. Error type matters.

---

## Part B: Transformer Model Comparison

Three pretrained Hugging Face models were evaluated across cybersecurity-themed classification inputs.

### Models Tested

#### Generic Model
- `distilbert-base-uncased-finetuned-sst-2-english`

General-purpose sentiment classification model.

---

#### Fine-Tuned Model A
- `mrm8488/bert-tiny-finetuned-sms-spam-detection`

Specialized spam classification model with closer relevance to phishing and malicious communication detection.

---

#### Fine-Tuned Model B
- `cardiffnlp/twitter-roberta-base-sentiment-latest`

Social media sentiment analysis model.

---

## Evaluation Goal

The comparison focused on understanding:

- how domain specialization affects classification behavior
- whether high confidence correlates with correctness
- how generic models differ from task-adapted models
- which model characteristics better support security automation workflows

---

## Comparative Findings

### Generic Model Strengths
- Extremely high confidence scores (~99%)
- Strong detection of clearly malicious cybersecurity language
- Fast, consistent classification behavior

### Generic Model Weaknesses
- Overclassified nearly everything as negative
- Poor nuance for benign or neutral events
- High confidence did not always mean accurate reasoning

---

### Fine-Tuned Model Strengths
- More nuanced classification behavior
- Better separation between categories
- More specialized pattern recognition
- Better suitability for task-specific workflows

---

## Biggest Insight

One of the most important findings was that confidence alone is not a reliable indicator of model quality.

The generic model frequently produced extremely confident outputs while lacking contextual nuance, while fine-tuned models often showed lower confidence but better task alignment.

This highlighted a key machine learning engineering principle:

> A highly confident generic model can still be less useful than a lower-confidence specialized model.

---

## Recommended Model

### Selected Model
`mrm8488/bert-tiny-finetuned-sms-spam-detection`

### Why
This model offered the strongest balance of specialization and practical classification relevance for cybersecurity-oriented text filtering.

Because it was trained for spam detection, its learned patterns aligned more closely with identifying suspicious communication behavior than general sentiment models.

---

## Deployment Considerations

### Confidence Threshold
**85%**

Low-confidence predictions should be flagged for review instead of automatically accepted.

---

### Priority Metric
**Recall**

In cybersecurity, false negatives are more dangerous than false positives.

Missing a malicious event is significantly riskier than investigating an extra benign alert.

---

## Tech Stack

- Google Teachable Machine
- Hugging Face Transformers
- AutoML / No-Code ML
- Binary Classification
- Confusion Matrix Analysis
- Precision / Recall / F1 Evaluation
- Cybersecurity Classification Testing

---

## Improvements / Future Enhancements

Several improvements would strengthen this prototype:

- expand the training dataset significantly
- improve dataset diversity with edge cases
- test larger held-out evaluation sets
- fine-tune a custom cybersecurity-specific classifier
- compare against security-domain transformer models
- test ensemble classification approaches
- explore anomaly detection models for suspicious activity identification

---

## Key Takeaways

This project provided hands-on experience with the practical machine learning evaluation lifecycle, from training and testing to comparative model assessment and deployment reasoning.

Rather than treating AI outputs as black boxes, the project emphasized measurable evaluation, model behavior analysis, and security-focused decision-making.
