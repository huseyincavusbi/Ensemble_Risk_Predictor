# Ensemble Risk Predictor
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
*   [Disclaimer](#Disclaimer)
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
    *   Train the model using the provided notebook. / Use already trained model to make predictions.
    *  Allow you to interact with the model.

### Inputting Data Directly

Once the notebook has been executed, you'll be prompted to input data or use a csv file, then you can input patient data directly via the console. You will be asked to provide the name of a patient and values for the features. The model will then generate a prediction on the risk score.

### Using a CSV File

Alternatively, you can also use a CSV file that includes all required features, with an additional "PatientName" column. The model will iterate over each row, generate risk scores, and add a new column `RiskScore` to the CSV.

### Combining and Analyzing Multiple CSV Files

The project also supports a functionality to combine and analyze data from multiple CSV files. It will prompt you for the CSV files and saves the results into one output file.

## Health Advice Generation

The project uses the Google Gemini API to generate a basic advice based on the risk score.

**Important Security Warning: Never hardcode your API key directly into any notebook.**

### 1. Obtain Your Gemini API Key

You can acquire your API key using one of the following methods:

####  *  **Google AI Studio (Recommended for Easy Setup)**

   *   **Navigate:** Visit the [Google AI Studio](https://aistudio.google.com/app/apikey).
   *   **Create API Key:** Follow the on-screen instructions to create a new API key.
   *   **Copy Key:** Once created, copy the API key. **Keep this key secure and do not share it publicly.**

####  *  **Google Cloud Console (Vertex AI)**

   *  **Create Project:** Begin by creating a new project in the [Google Cloud Console](https://console.cloud.google.com/).
   *  **Enable API:** Enable the "Vertex AI API" for your project.
   *  **Create API Key:**  Create a new API key following the instructions within the console.
   *  **Copy Key:** Copy the generated API key. **Treat this key as confidential.**

### 2. Store Your API Key in Colab Secrets

To ensure the security of your API key, we will use Google Colab's built-in Secrets feature:

   *  **Access Secrets:** In your Google Colab notebook, locate the **left sidebar** and click on the **key icon** (labeled "Secrets").

   *  **Add Secret:** Click on the button labeled **"+ Add Secret"**.

   *  **Name the Secret:** In the "Name" field, enter the following (exactly as shown): `GEMINI_API_KEY`.

   *  **Paste API Key:** In the "Value" field, carefully paste the **Gemini API key** you copied in the previous step.

   *  **Add:** Finally, click the **"Add Secret"** button.

   *  **Key Storage:** This process will securely store your API key within Colab's secret management system. Your key will not be directly visible within your notebook's code.
     
## Contributing

Contributions to this project are welcome! Feel free to fork the repository, make changes, and submit a pull request. You can contribute by:

*   Improving the performance of the model.
*   Adding more sophisticated risk analysis tools.
*   Enhancing the user interface and experience.
*   Adding support for other datasets
*   Adding different model architectures
*  Improve the documentation

## Disclaimer

This Ensemble Risk Predictor is intended for research purposes only and should not be used as a substitute for professional medical advice. The predictions provided by this model are based on an analysis of data and should not be considered a diagnosis or a guarantee of health outcomes. Always consult with a qualified healthcare professional for any health concerns or before making any decisions related to your health or treatment.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
