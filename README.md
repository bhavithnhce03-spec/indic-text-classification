# Hindi Sentiment Classification

A baseline sentiment classifier for Hindi product reviews, built with TF-IDF and Logistic Regression.

## Dataset
IndicSentiment (AI4Bharat), Hindi subset: 1,154 reviews labeled Positive or Negative
(581 positive, 573 negative). Text column: `INDIC REVIEW`.

## Method
1. Cleaned the data (dropped 2 rows with missing values).
2. Stratified 80/20 train/test split (`random_state=42`).
3. TF-IDF features with unigrams and bigrams (`min_df=2`), fitted on training data only.
4. Hindi-aware tokenizer (`token_pattern`), because the default one splits Devanagari
   words at vowel signs.
5. Logistic Regression classifier.

## Results (231 held-out reviews)
| Class | Precision | Recall | F1 |
|---|---|---|---|
| Negative | 0.88 | 0.90 | 0.89 |
| Positive | 0.89 | 0.88 | 0.89 |

Accuracy 0.89, macro-F1 0.89. Confusion matrix: [[103, 12], [14, 102]].

## Error analysis
Mistakes came mainly from:
- Negation (e.g. "मोनोटोनिक नहीं है" read as negative)
- Mixed sentiment in one review
- Figurative or long text with no explicit sentiment words
- Very short reviews, and English words spelled in different ways in Devanagari

## Next steps
Fine-tune MuRIL (a transformer pretrained on Indian languages) and compare with this baseline.

## Run
Open the notebook in Google Colab and run all cells.
