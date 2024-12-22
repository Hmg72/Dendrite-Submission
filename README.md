Machine Learning Pipeline Automation
This project automates a complete machine learning workflow based on configurations specified in a JSON file. The pipeline is designed to be generic and reusable, adapting dynamically to various configurations for feature handling, feature reduction, and model training.

Features
JSON-Based Configuration:

Parses a JSON file (algoparams_from_ui.json) to extract all necessary settings for the ML pipeline, including:
Target variable and prediction type (Regression/Classification).
Feature handling methods (e.g., imputation strategies).
Feature reduction techniques (PCA, Tree-based, Correlation-based, etc.).
Model selection and hyperparameter tuning settings.
CSV Data Preprocessing:

Loads a CSV file (iris.csv) and preprocesses it according to the feature handling configuration.
Supports missing value imputation using mean, custom values, or other strategies.
Feature Reduction:

Implements multiple methods for feature reduction, including:
PCA for dimensionality reduction.
Tree-based feature importance.
Correlation with the target variable.
Option to disable reduction and use all features.
Dynamic Model Selection:

Dynamically selects models based on prediction_type (Regression or Classification) and the algorithms marked as active (is_selected) in the JSON.
Supports various sklearn models like RandomForest, LinearRegression, GradientBoosting, etc.
Hyperparameter Tuning:

Uses GridSearchCV to perform hyperparameter optimization for each selected model.
Metrics Evaluation:

Evaluates models using appropriate metrics:
Regression: R² Score, RMSE.
Classification (if extended): Accuracy, F1 Score, etc.
Logs the best parameters and performance for each model.
Pipeline Structure:

Combines feature handling, reduction, and model training into a unified sklearn pipeline for modularity and reusability.
File Structure
algoparams_from_ui.json: Configuration file defining target, features, models, and hyperparameters.
iris.csv: Sample dataset used for testing the pipeline.
ml_pipeline.py: Main Python script implementing the pipeline.
requirements.txt: Dependencies required to run the project.
Usage

Clone the repository:

git clone <repository-url>
cd <repository-name>
Install dependencies:


pip install -r requirements.txt

Run the script:

bash
python ml_pipeline.py
Modify the algoparams_from_ui.json file to test various configurations:

Enable or disable algorithms.
Change feature handling and reduction methods.
Adjust hyperparameter ranges.
Example Configuration
Sample JSON snippet for regression tasks:

json
{
    "target": {
        "prediction_type": "Regression",
        "target": "petal_width"
    },
    "feature_handling": {
        "sepal_length": {
            "is_selected": true,
            "feature_variable_type": "numerical",
            "feature_details": {
                "missing_values": "Impute",
                "impute_with": "Average of values"
            }
        }
    },
    "algorithms": {
        "RandomForestRegressor": {
            "is_selected": true,
            "min_trees": 10,
            "max_trees": 20
        }
    }
}
Key Dependencies
pandas: Data loading and manipulation.
numpy: Numerical operations.
sklearn: Machine learning models and utilities.
logging: For progress and error logging.
Future Improvements
Extend support for classification tasks.
Add advanced feature engineering options.
Integrate cross-validation for metrics evaluation.
Contribution
Feel free to open issues or submit pull requests if you have suggestions or improvements. Ensure your contributions adhere to the project's coding style and standards.
