✈️ Flight Delay Prediction for Hartsfield–Jackson Atlanta International Airport

📌 Overview

This project features a serverless machine learning pipeline designed to predict flight delays at Hartsfield-Jackson Atlanta International Airport (ATL). Predictions are based on historical flight delay records and meteorological data.

📂 Repository Contents

✅ Flight Information & Weather Data (2024) - Includes flight and atmospheric conditions at ATL.

✅ Interactive Graphical User Interface (GUI) built using Gradio.

🔗 Live Interface: Explore the Model on Hugging Face

🏗️ System Architecture

The serverless architecture ensures scalability and flexibility. The pipeline runs as scheduled tasks, eliminating the need for manual intervention. The workflow includes:

1️⃣ Data Acquisition & Processing
2️⃣ Feature Engineering
3️⃣ Model Training & Hyperparameter Optimization
4️⃣ Prediction Generation & Deployment

📊 Models Implemented

XGBoost 🌳

Multi-Layer Perceptron (MLP) 🧠

Ridge Regressor 📈

🔧 Hyperparameter Optimization: Optuna was used for fine-tuning model performance.

🔄 Pipeline Breakdown

🗂️ 1. Historical Data Acquisition & Processing

This phase gathers and preprocesses data from multiple sources:

📌 Weather Data from OpenMeteo 🌦️
📌 Flight Data from the Bureau of Transportation Statistics (BTS) ✈️

📊 Processed datasets are stored as Feature Groups within Hopsworks.

🛠️ 2. Feature Engineering & Model Training

Following initial data preparation, additional feature engineering is performed:

✔️ Removing redundant variables 🗑️
✔️ Encoding the "carrier" feature (one-hot & label encoding) ✈️
✔️ Standardizing numerical values using StandardScaler 📏
✔️ Lagging delay values by one month to capture temporal patterns ⏳
✔️ Transforming "month" variable into sine & cosine components 🔄
✔️ Feature selection tests:

Coefficient of Variation Analysis 📉 (removing low-variance features)

Correlation Matrix Examination 🔗 (reducing multicollinearity)

Feature Importance Tests ⭐ (eliminating low-impact features)

📌 Final Model Training:

XGBoost, MLP, and Ridge Regressor were trained.

Optuna was used for hyperparameter tuning.

Models were stored in Hopsworks Model Registry.

🎯 3. Fine-Tuning & Additional Training

Further fine-tuning was explored with the MLP model, trained on alternative datasets:

📌 Enhanced Training Dataset: Includes extra time-series features (two- and three-month lagged values).
📌 Zylalabs Historical Flight Data: Integrated with OpenMeteo weather data.

🛑 Final Model Choice:
✅ MLP trained on the Enhanced Dataset (Best performance, deployed) 🚀
❌ MLP trained on Zylalabs Data (Inferior results, excluded) ❌

🖥️ Graphical User Interface (GUI)

👨‍💻 Built using Gradio, allowing users to interact with the model:

🎚️ Adjust input values using sliders
📌 Select an airline carrier from a dropdown menu
🎨 Color-coded delay score:

🔵 Minimal Delays (-1)

🔴 Severe Delays (5)
⚡ 3D Interactive Sphere displaying predictions

📊 Model Performance

🔍 Evaluation Metrics: Mean Squared Error (MSE) & R² Score

🔹 Pre-Tuning Results:

XGBoost: MSE: 0.49, R²: 0.70

MLP: MSE: 0.19, R²: 0.73

Ridge Regressor: MSE: 0.16, R²: 0.76

🔹 Post-Tuning Results:

XGBoost: MSE: 0.46, R²: 0.72

MLP: MSE: 0.20, R²: 0.71

Ridge Regressor: MSE: 0.15, R²: 0.79

🔹 Alternative Dataset Results (Post-Tuning):

MLP (Enhanced Dataset - BTS & OpenMeteo): MSE: 0.07, R²: 0.90 ✅

MLP (Zylalabs & OpenMeteo): MSE: 0.90, R²: 0.08 ❌

📌 Final Selection: MLP trained on the Enhanced Training Dataset 🚀

🛠️ Software & Tools Used

🖥️ Google Colab - Development Environment
🚀 Hugging Face - GUI Hosting Platform
🖼️ Gradio - GUI Framework
📦 Hopsworks - Feature Store & Model Registry
📊 Bureau of Transportation Statistics (BTS) - Flight Data Source
🌦️ OpenMeteo - Weather Data API
📄 Pandas - Data Manipulation
🔍 Optuna - Hyperparameter Tuning
📈 Plotly - Data Visualization

🔧 Running the Code

📌 To view the UI, simply follow the Hugging Face Space link.
https://huggingface.co/Feranmii/airport_delay

⚙️ Setup Requirements

✅ Access to Hopsworks (Feature Store & Model Registry)
✅ Zylalabs Historical Flights API (API key required)

💡 API Keys Setup: Save your credentials as text files:

hopsworks-api-key.txt (Hopsworks API Key)

zyla_key.txt (Zylalabs API Key)

🏃 Execution Order

1️⃣ historical_backfill_data (2).ipynb
2️⃣ feature_and_training_pipeline.ipynb
3️⃣ fine_tuning_pipeline_USE_THIS_ONE (1).ipynb
4️⃣ ui.ipynb

📌 Other notebooks in the repository are supplementary and not required for core execution.