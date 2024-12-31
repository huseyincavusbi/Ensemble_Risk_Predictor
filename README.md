# Ensemble_Risk_Predictor

<a href="https://colab.research.google.com/github/huseyincavusbi/Ensemble_Risk_Predictor/blob/main/Ensemble_Risk_Predictor.ipynb" target="_blank"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/huseyincavusbi/Ensemble_Risk_Predictor/blob/main/Ensemble_Risk_Predictor.ipynb)

This project provides an ensemble machine learning model to predict the risk of heart disease based on various health indicators. It utilizes a combination of feature selection techniques, resampling methods, and ensemble learning to achieve robust and accurate predictions.

## Table of Contents

*   [Project Overview](#project-overview)
*   [Dataset](#dataset)
*   [Methodology](#methodology)
    *   [Feature Selection](#feature-selection)
    *   [Data Resampling](#data-resampling)
    *   [Model Training](#model-training)
    *   [Cross-Validation](#cross-validation)
*   [Usage](#usage)
    *   [Prerequisites](#prerequisites)
    *   [Running the Project](#running-the-project)
    *   [Inputting Data Directly](#inputting-data-directly)
    *   [Using a CSV File](#using-a-csv-file)
    *   [Combining and Analyzing Multiple CSV Files](#combining-and-analyzing-multiple-csv-files)
*   [Health Advice Generation](#health-advice-generation)
*   [Contributing](#contributing)
*   [License](#license)

## Project Overview

The Ensemble Risk Predictor is designed to assist healthcare professionals and individuals in assessing the risk of heart disease. It utilizes a publicly available dataset from Kaggle, and employs a combination of feature selection (RFE), a resampling (SMOTETomek) technique to handle class imbalance, and an ensemble model (EasyEnsembleClassifier with RandomForestClassifier base estimators) to make predictions.

This project also includes the ability to analyze data from CSV files and provide tailored health advice using the Google Gemini API.

## Dataset

The model is trained and evaluated on the [Heart Disease Health Indicators Dataset](https://www.kaggle.com/datasets/alexteboul/heart-disease-health-indicators-dataset) from Kaggle. This dataset contains a variety of health-related features collected from individuals, and includes a binary indicator for whether a person has experienced a heart attack.

## Methodology

The following steps were taken in building the Ensemble Risk Predictor:

### Feature Selection

Recursive Feature Elimination (RFE) was used with a Decision Tree classifier to select the most relevant features for predicting heart disease risk.

### Data Resampling

Because the dataset contains an imbalanced target class, a combination of SMOTE (Synthetic Minority Over-sampling Technique) and Tomek links were used to address the imbalance issue, leading to more robust model training.

### Model Training

An Easy Ensemble Classifier was trained with multiple Random Forest Classifier base estimators.

### Cross-Validation

The model was evaluated using Stratified K-Fold cross-validation to get robust performance metrics.

## Usage

### Prerequisites

Before using the project, ensure that you have the following:

*   **Python 3.6+**
*   The required Python packages:
    ```bash
    kagglehub==0.3.5
    pandas==2.2.2
    numpy==1.26.4
    matplotlib==3.8.0
    seaborn==0.13.2
    scikit-learn==1.5.2
    plotly==5.24.1
    imbalanced-learn==0.12.4
    joblib==1.4.2
    google-generativeai==0.8.3
    ```
    You can install these using pip:
    ```bash
    pip install kagglehub==0.3.5 pandas==2.2.2 numpy==1.26.4 matplotlib==3.8.0 seaborn==0.13.2 scikit-learn==1.5.2 plotly==5.24.1 imbalanced-learn==0.12.4 joblib==1.4.2 google-generativeai==0.8.3
    ```
*   A Gemini API key from Google AI Studio or Google Cloud Console. See instructions in the source code or below.

### Running the Project

This project is designed to run in Google Colab, using the provided notebook ([Ensemble_Risk_Predictor.ipynb](https://colab.research.google.com/github/huseyincavusbi/Ensemble_Risk_Predictor/blob/main/Ensemble_Risk_Predictor.ipynb)). To use it:

1.  Open the notebook in Google Colab.
2.  Run each cell in order. This will:
    *   Clone the GitHub repository
    *   Download the dataset
    *   Install necessary libraries
    *   Train the model using the provided notebook.
    *  Allow you to interact with the model.

### Inputting Data Directly

Once the notebook has been executed, you'll be prompted to input data or use a csv file, then you can input patient data directly via the console. You will be asked to provide the name of a patient and all the features as defined above. The model will then generate a prediction on the risk score.

### Using a CSV File

Alternatively, you can also use a CSV file that includes all required features, with an additional "PatientName" column. The model will iterate over each row, generate risk scores, and add a new column `RiskScore` to the CSV.

### Combining and Analyzing Multiple CSV Files

The project also supports a functionality to combine and analyze data from multiple CSV files. It will prompt you for the CSV files and saves the results into one output file.

## Health Advice Generation

The project uses the Google Gemini API to generate a basic advice based on the risk score.

**Important Security Warning: Never hardcode your API key directly into any notebook.**

To use health advice generation, you need to securely add your Gemini API key as a secret:

1.  **Get your API Key:** Follow these instructions on how to get one:
        *   **Google AI Studio (Recommended for easy setup):**
            Go to [Google AI Studio](https://aistudio.google.com/app/apikey). Create a new API key and copy it.
        *   **Google Cloud Console (Vertex AI):**
            If you want a more comprehensive project, create a new project, enable the "Vertex AI API", and then create and copy the API key.
2.  **Store your API key in Colab Secrets:**
    *   In your Google Colab notebook, go to the left sidebar and click on the **key icon** (Secrets).
    *   Click **"+ Add Secret"**
    *   For the **"Name"** field, use `GEMINI_API_KEY`
    *   Paste your Gemini API key in the **"Value"** field.
    *  Click **"Add Secret"**
    *  This will store your API key securely, without exposing it in the notebook code.

## Contributing

Contributions to this project are welcome! Feel free to fork the repository, make changes, and submit a pull request. You can contribute by:

*   Improving the accuracy of the model.
*   Adding more sophisticated risk analysis tools.
*   Enhancing the user interface and experience.
*   Adding support for other datasets
*   Adding different model architectures
*  Improve the documentation

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
