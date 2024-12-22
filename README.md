Machine Learning Pipeline Automation This project will automate a complete machine learning workflow based on configurations provided in a JSON file. The pipeline is generic and reusable, adapting dynamically to various configurations for feature handling, feature reduction, and model training.

Features JSON-Based Configuration:

Reads a JSON file (algoparams_from_ui.json) to extract the necessary settings for the pipeline of ML, including:
Target variable and prediction type (Regression/Classification).
Feature handling methods, eg imputation strategies.
Features reduction techniques, eg. PCA, Tree-based, Correlation-based, etc.
Model selection and the hyperparameter tuning settings. Data Preprocessing from CSV :
Reads a CSV file (iris.csv) based on the feature handling. Supports imputation of missing value by mean, custom value, etc. Feature Reduction:

Multiple dimensionality reduction methods implemented including: PCA for reducing dimensionality. Tree-based feature importance. Correlation with the target variable. Allow disabling reduction and using all features. Dynamic Model Selection:

Dynamically select models based on prediction_type either Regression or Classification, depending upon what has been marked as active in JSON with the is_selected flag. The above supports various sklearn models including RandomForest, LinearRegression, GradientBoosting, etc. Hyperparameter Tuning:

It uses GridSearchCV to perform hyperparameter optimization for each of the selected models. Metrics Evaluation:

Evaluates models using the appropriate metrics: Regression: R² Score, RMSE. Classification (if extended): Accuracy, F1 Score, etc. Logs the best parameters and performance for each model. Pipeline Structure:

Combines feature handling, reduction, and model training into a unified sklearn pipeline for modularity and reusability. File Structure algoparams_from_ui.json: Configuration file defining target, features, models, and hyperparameters. iris.csv: Sample dataset used for testing the pipeline. ml_pipeline.py: Main Python script implementing the pipeline. requirements.txt: Dependencies required to run the project. Usage Clone the repository: git clone cd Install dependencies: pip install -r requirements.txt Run the script:

bash python ml_pipeline.py Update the algoparams_from_ui.json file to run different configurations:
Turn on/off algorithms. Switch between feature handling and reduction techniques. Vary hyperparameter ranges. Sample Configuration Example JSON snippet for regression task:

json { "target": { "prediction_type": "Regression", "target": "petal_width" }, "feature_handling": { "sepal_length": { "is_selected": true, "feature_variable_type": "numerical", "feature_details": { "missing_values": "Impute", "impute_with": "Average of values" } } }, "algorithms": { "RandomForestRegressor": { "is_selected": true, "min_trees": 10, "max_trees": 20 } } } Key Dependencies pandas: Data loading and manipulation. numpy: Numerical operations. sklearn: Machine learning models and utilities. logging: For progress and error logging. Future Improvements Extend support for classification tasks. Add advanced feature engineering options. Integrate cross-validation for metrics evaluation. Contribution Feel free to open issues or submit pull requests if you have suggestions or improvements. Ensure your contributions adhere to the project's coding style and standards.
