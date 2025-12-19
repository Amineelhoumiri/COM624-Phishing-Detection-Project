# Privacy-Aware Phishing Detection System
**COM624 Machine Learning Coursework**

This project implements a privacy-preserving machine learning system for detecting phishing emails. It utilizes a hybrid approach combining traditional Machine Learning (Random Forest) and Deep Learning (LSTM) with a federated learning simulation to demonstrate privacy compliance.

## Project Structure

*   **`data/`**: Contains the raw and processed datasets.
*   **`plots/`**: Stores generated plots (Confusion Matrices, ROC Curves, EDA).
*   **`dashboard.py`**: The main Streamlit application for the interactive demo.
*   **`main.py`**: Principal script for data loading, cleaning, and anonymization.
*   **`feature_engineering.py`**: Extracts features and generates EDA visualizations.
*   **`LSTM_Model.py`**: Trains the Deep Learning model used by the dashboard.
*   **`BERT_Model.py`**: Trains the BERT-based transformer model (optional high-performance model).
*   **`Random_Forest_Modeling.py`**: Trains the baseline Random Forest model.
*   **`clustering_modeling.py`**: Performs unsupervised clustering analysis (K-Means, DBSCAN).
*   **`federated_learning_simulation.py`**: Simulates the privacy-preserving distributed training.

## How to Run the Project

Follow these steps to reproduce the entire pipeline and launch the dashboard.

### 1. Prerequisites
Ensure you have **Python 3.9+** installed.
Install the required dependencies:

```bash
pip install -r requirements.txt
```

*(Note: If `pip` is not recognized, attempt `python -m pip install -r requirements.txt`)*

### 2. Execution Pipeline
Run the scripts in this specific order to process data and train the models.

**Step 1: Data Preprocessing & Cleaning**
Loads datasets, cleans text, and anonymizes email addresses to ensure GDPR compliance.
```bash
python main.py
```

**Step 2: Feature Engineering**
Generates metadata features (link counts, keyword flags) and Exploratory Data Analysis (EDA) plots.
```bash
python feature_engineering.py
```

**Step 3: Train the LSTM Model**
Trains the deep learning model and saves the necessary artifacts (`lstm_phishing_model.keras`, `tokenizer.pickle`) for the dashboard.
```bash
python LSTM_Model.py
```

**Step 4: Other Models & Analysis (Optional)**
You may run these scripts to compare performance metrics and explore clusters:
```bash
python Random_Forest_Modeling.py
python BERT_Model.py
python clustering_modeling.py
python federated_learning_simulation.py
```

### 3. Launching the Dashboard
To start the interactive GUI, execute the following command:

```bash
streamlit run dashboard.py
```

*   This will launch a local web server (typically accessible at **http://localhost:8501**).
*   **Interactive Detection Tab**: Input custom email content to observe real-time prediction scores.
*   **Alert Simulation Tab**: View the simulated privacy-aware Security Operations Center (SOC) alert feed.

## Troubleshooting
*   **Model not found**: Ensure `python LSTM_Model.py` has been executed successfully before starting the dashboard.
*   **TensorFlow OneDNN warnings**: These are standard optimization messages and can be disregarded.
