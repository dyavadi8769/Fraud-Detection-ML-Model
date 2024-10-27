# Fraud-Detection-ML-Model
## Dataset Overview:
- Source: This dataset is related to card transactions and taken from a publicly available platform Kaggle.
- Shape: The dataset contains 1,000,000 samples and 8 features.
- Purpose: This dataset is designed for fraud detection in card transactions, where the objective might be to classify transactions as fraudulent or legitimate based on various features.

## Features:
1. distance_from_home: This represents the distance between the transaction location and the cardholder's home. It could indicate abnormal activity if unusually high.
2. distance_from_last_transaction: The distance between this transaction and the previous one. Significant differences could be a red flag for fraudulent transactions.
3. ratio_to_median_purchase_price: This ratio compares the transaction amount to a median purchase price, which may indicate unusual spending behavior.
4. repeat_retailer: A binary feature (0 or 1), indicating whether the retailer is frequently used by the cardholder.
5. used_chip: A binary indicator of whether the transaction used a chip, which is generally more secure than a magnetic stripe.
6. used_pin_number: A binary feature that shows if a PIN was used during the transaction, adding a layer of security.
7. online_order: A binary variable denoting whether the transaction was conducted online, which may carry different fraud risks compared to in-person transactions.

## Target:
1. fraud: The target variable (0 or 1), where 1 represents a fraudulent transaction and 0 indicates a legitimate one.

## Challenges and Limitations:
1. Imbalanced Classes: Fraudulent transactions are generally rare, which may make the dataset imbalanced. Imbalance can affect model performance and may require specialized techniques, such as resampling or using balanced metrics.
2. Feature Correlation: Some features, like distance_from_home and distance_from_last_transaction, may be correlated, impacting model interpretability and requiring feature selection or engineering.
3. Binary Nature of Some Features: Many features are binary, limiting the range of information they provide and potentially affecting the model’s ability to detect nuanced patterns.
4. Potential Noise: Real-world transaction data may include noise due to measurement errors or outliers, which can challenge model generalization.

This dataset is suitable for exploring supervised classification techniques, particularly in fraud detection tasks where models need to accurately identify rare events.

## Task Overview: 
The task is to build a predictive model for detecting fraudulent transactions in a credit card transaction dataset. The goal is to classify each transaction as either legitimate or fraudulent based on various features associated with the transaction. Fraud detection is crucial for financial institutions and customers alike, as it helps reduce financial losses and protects cardholders from unauthorized usage.

## Target Variable
- Target: fraud
- Values: This binary variable is labeled as 1 for fraudulent transactions and 0 for legitimate transactions. The goal is to predict the likelihood of a transaction being fraudulent based on the given features.

## Rationale: 
- Detecting fraud in real time is vital in the financial industry due to the high cost and potential damage of fraudulent activities. Financial institutions and card issuers can save millions in losses annually by implementing accurate fraud detection algorithms. For customers, fraud detection ensures the security of their accounts and minimizes unauthorized usage, promoting trust and security in digital transactions.

- This problem is relevant because fraudsters often use advanced methods to bypass detection, and a robust fraud detection model can help mitigate these risks. The task is also challenging and interesting due to the data imbalance, which reflects real-world conditions where fraudulent transactions are relatively rare.

## Relevant Features
1. distance_from_home: Measures how far a transaction is from the cardholder’s home location. Unusually high values could suggest fraudulent activity, especially if the cardholder typically transacts within a limited range.
2. distance_from_last_transaction: The distance between this transaction and the previous one, potentially indicating fraud if the distance is anomalously high in a short period.
3. ratio_to_median_purchase_price: Compares the transaction amount to the cardholder’s median purchase price, with extreme values potentially suggesting unusual behavior.
4. repeat_retailer: Indicates if the retailer is a common merchant for the cardholder. Fraudulent transactions may often occur at uncommon locations.
5. used_chip: Transactions with chip use are generally more secure. Absence of chip use might indicate higher fraud risk.
6. used_pin_number: Indicates if a PIN was used, which enhances transaction security.
7. online_order: Online transactions may be more susceptible to fraud than in-person transactions, as physical verification is absent.

## Challenges:
1. Class Imbalance: Fraud is rare, causing the model to favor legitimate transactions. Requires resampling techniques or specialized metrics to handle.

2. Noisy Data & Label Errors: Errors and outliers in data can confuse the model, necessitating data cleaning and careful preprocessing.

3. Feature Overlap: High correlation among features, such as distances, can reduce model interpretability and may require feature selection.

4. Binary Features: Limited information in binary features may restrict model complexity, potentially impacting performance.

5. Evolving Fraud Tactics: Fraud methods change, so models may need frequent retraining or updating to stay effective.

6. False Positives: Flagging legitimate transactions as fraud can harm customer trust, requiring a balance between sensitivity and specificity.

6. Real-Time Requirements: Detecting fraud in real time demands efficient models with minimal latency, often challenging for complex architectures.

7. Interpretability: Models need to be explainable for compliance and trust, especially in regulated industries, often necessitating interpretable techniques.

## Comparison of Memorization and Generalization Performance
The table presents the results of different models based on three metrics: classification accuracy, F1 score, and AUC. The goal is to assess how well each model balances memorization (performance on training data) and generalization (performance on test data).

1. Logistic Regression
- Train vs. Test Accuracy: Close (0.9585 vs. 0.9591), indicating good generalization with minimal overfitting.
- F1 Score: Lower than other models but consistent between train and test, which shows balanced handling of classes, given the task's imbalanced nature.
- AUC: High AUC scores on both train (0.9766) and test (0.9753) suggest it’s reliable for distinguishing between classes.
- Reliability: Logistic Regression demonstrates the best generalization, suggesting it’s a reliable choice, especially given its resistance to overfitting.

2. Decision Tree
- Train vs. Test Accuracy: Large difference (0.9990 vs. 0.9915) suggests some overfitting.
- F1 Score: High on training data (0.9929) but lower on test (0.9355), indicating a tendency to memorize the training data.
- AUC: Near perfect on training (0.9999) but lower on test (0.9681), reinforcing that the model might overfit the training data.
- Reliability: Due to its tendency to memorize, Decision Tree is less reliable here for generalization.

3. Support Vector Machine (SVM)
- Accuracy: High on both train (0.9950) and test (0.9938), suggesting robust generalization.
- F1 Score: Also high and balanced (0.9652 on train and 0.9531 on test), supporting good generalization.
- AUC: Not available due to limitations with SVM in calculating probability scores.
- Reliability: SVM is highly reliable for this task due to its consistent high performance across train and test sets, indicating good generalization with limited overfitting.

4. K-Nearest Neighbors (KNN)
- Accuracy: Perfect on train (1.0000) but slightly lower on test (0.9900), suggesting overfitting.
- F1 Score: Shows perfect memorization on training data but drops on the test data (0.9255), indicating overfitting.
- AUC: High on both train and test, but overfitting is still a concern due to its proximity to 1.0000 on training data.
- Reliability: KNN tends to overfit, making it less reliable for generalization in this context.

5. Random Forest
- Accuracy: Near-perfect on both train (0.9991) and test (0.9942), indicating very strong generalization.
- F1 Score: Consistent between train (0.9937) and test (0.9564), suggesting balanced class handling and generalization.
- AUC: Almost perfect on both train and test, indicating excellent discrimination capability.
- Reliability: Random Forest demonstrates the most reliable generalization in this task due to its high consistency across metrics and balanced performance on both train and test sets.

## Conclusion and Recommended Techniques
- Most Reliable Techniques: Logistic Regression, SVM, and Random Forest show the best generalization and balanced performance.
- Reasoning:
> - Logistic Regression performs well across all metrics, demonstrating strong generalization with minimal overfitting, making it suitable for imbalanced data.
> - SVM shows robust performance in both accuracy and F1 scores without overfitting, making it highly reliable for generalization.
> - Random Forest combines high accuracy and F1 scores, with excellent AUC, indicating that it captures complex patterns while still generalizing effectively.

In this context, Logistic Regression, SVM, and Random Forest are reliable for fraud detection due to their ability to handle imbalanced data while maintaining consistent performance across all metrics on both training and test sets.

## Summary of the findings based on the plots:

1. Impact of Feature Addition:

- Adding new features such as distance_ratio, log_last_transaction_distance, price_to_distance_ratio generally improved the model's test accuracy and F1 score, indicating that these features provided meaningful information that enhanced the model's predictive ability.
- However, some features (like log_purchase_price_ratio) showed a dip in both train and test performance metrics, suggesting they might not contribute significant discriminatory power or could introduce noise.

2. Effect of Feature Removal:

- Removing certain features, especially those derived from transformations (e.g., log_last_transaction_distance and log_price_to_distance_ratio), led to fluctuations in test performance, especially in AUC and F1 score, showing that these engineered features contributed to the model's ability to generalize.
- In particular, removing core features like total_distance caused a significant drop in test F1 and AUC, indicating its high relevance in identifying patterns of fraudulent transactions.

3. General Observations:

- The model performs best when combining key engineered features without excessive transformations or binary flags that don't contribute as much.
- The consistency in metrics such as Test AUC and Test F1 across many of the engineered features suggests that certain features improve the model's robustness in detecting true positives, essential for fraud detection.
  
In conclusion, carefully engineered features like ratios and logarithmic transformations of transactional metrics improved model generalization, whereas overly simplistic or redundant binary features added limited value. The best classifier maintained a high generalization performance when selecting key engineered features, optimizing the balance between complexity and interpretability.
