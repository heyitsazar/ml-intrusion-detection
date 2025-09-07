# Intrusion Detection with Machine Learning

This project is about building a machine learning model to detect intrusions (suspicious or malicious activity) using a Kaggle dataset. The dataset combines network-level features with user behavior, making it possible to train a model that can separate normal activity from attacks.

## Dataset

* Source: [Kaggle – Cybersecurity Intrusion Detection Dataset](https://www.kaggle.com/datasets/dnkumars/cybersecurity-intrusion-detection-dataset)
* **Network features:** packet size, protocol type (TCP, UDP, ICMP), encryption used.
* **User behavior features:** number of login attempts, failed logins, session duration, unusual access times, IP reputation score, browser type.
* Target variable: `attack_detected` (binary flag: 1 = attack, 0 = safe).

## Preprocessing

* Dropped irrelevant or incomplete columns (`session_id`, `encryption_used`).
* Handled missing values by removing columns with null data.
* Converted categorical features (e.g., protocol type, browser) into numerical form using one-hot encoding.
* Split dataset into training (75%) and testing (25%).

## Model

* **Random Forest Classifier** was used as the main model.
* **GridSearchCV** was applied to try different hyperparameter combinations and find the best fit.
* Best parameters found:

  * `n_estimators = 200`
  * `max_depth = 20`
  * `min_samples_split = 5`

## Results

* Cross-validation accuracy: **\~89%**
* Test set accuracy: **\~89%**

This shows that the tuned Random Forest model can effectively detect intrusions with high accuracy.

## How to Run

1. Clone this repository.
2. Open the Jupyter Notebook file (`ml-intrusion-detection.ipynb`).
3. Run the notebook step by step to:

   * Load and preprocess the dataset.
   * Train the Random Forest model with GridSearchCV.
   * Evaluate accuracy on the test set.

⚠️ Note: The dataset is not included in this repository. You can download it from Kaggle [here](https://www.kaggle.com/datasets/dnkumars/cybersecurity-intrusion-detection-dataset).

## Takeaways

* Network and user behavior features together provide strong signals for intrusion detection.
* Good preprocessing (handling missing data, encoding categorical values) is just as important as the choice of model.
* Hyperparameter tuning makes a big difference—accuracy improved significantly after optimization.
