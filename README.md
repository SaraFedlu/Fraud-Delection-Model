# **Fraud Detection Project**

## **Overview**
This project focuses on building robust fraud detection models for e-commerce and banking transactions. The goal is to accurately identify fraudulent activities using advanced machine learning techniques and geolocation analysis. The project involves:
- Exploratory Data Analysis (EDA) to understand transaction patterns.
- Feature engineering to create meaningful features for model training.
- Training and evaluating machine learning and deep learning models.
- Using SHAP and LIME for model explainability.
- Deploying the best-performing model for real-time fraud detection.



## **Datasets**
The project uses the following datasets:
1. **Fraud_Data.csv**:
   - Contains e-commerce transaction data.
   - Columns: `user_id`, `signup_time`, `purchase_time`, `purchase_value`, `device_id`, `source`, `browser`, `sex`, `age`, `ip_address`, `class`.
2. **IpAddress_to_Country.csv**:
   - Maps IP address ranges to countries.
   - Columns: `lower_bound_ip_address`, `upper_bound_ip_address`, `country`.
3. **creditcard.csv**:
   - Contains anonymized credit card transaction data.
   - Columns: `Time`, `V1` to `V28` (PCA-transformed features), `Amount`, `Class`.



## **Project Structure**
```
fraud-detection-project/
├── data/
│   ├── Fraud_Data.csv
│   ├── IpAddress_to_Country.csv
│   └── creditcard.csv
├── notebooks/
│   ├── eda.ipynb
│   └── modeling.ipynb
├── models/
│   └── random_forest_fraud (MLflow model)
├── README.md
└── requirements.txt
```



## **Dependencies**
To run the code, ensure you have the following Python libraries installed:
- pandas
- numpy
- scikit-learn
- tensorflow
- keras
- imbalanced-learn (for SMOTE)
- shap
- lime
- mlflow

You can install the dependencies using:
```bash
pip install -r requirements.txt
```



## **How to Run the Code**
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/SaraFedlu/Fraud-Detection-Model.git
   cd Fraud-Detection-Model
   ```

2. **Run the EDA Notebook**:
   - Open `notebooks/eda.ipynb` in Jupyter Notebook or Google Colab.
   - Execute the cells to perform exploratory data analysis and preprocessing.

3. **Run the Modeling Notebook**:
   - Open `notebooks/modeling.ipynb` in Jupyter Notebook or Google Colab.
   - Execute the cells to train and evaluate machine learning and deep learning models.

4. **Track Experiments with MLflow**:
   - Start the MLflow server:
     ```bash
     mlflow ui
     ```
   - Access the MLflow dashboard at `http://localhost:5000` to view logged experiments and models.



## **Key Findings**
1. **Best Performing Model**:
   - **Random Forest** achieved the highest accuracy and precision for both e-commerce and credit card datasets.
2. **Class Imbalance**:
   - Addressing class imbalance with SMOTE significantly improved model performance on the credit card dataset.
3. **Model Explainability**:
   - SHAP and LIME provided valuable insights into how individual features influenced predictions.



## **Results**
### **E-commerce Dataset**
| Model               | Accuracy | Precision | Recall | F1-Score |
|---------------------|----------|-----------|--------|----------|
| Logistic Regression | 0.9057   | 0.0       | 0.0    | 0.0      |
| Decision Tree       | 0.8981   | 0.4671    | 0.5712 | 0.5140   |
| Random Forest       | 0.9563   | 0.9961    | 0.5382 | 0.6989   |
| Gradient Boosting   | 0.9057   | 1.0       | 0.0004 | 0.0007   |

### **Credit Card Dataset (After SMOTE)**
| Model                       | Accuracy | Precision | Recall | F1-Score |
|-----------------------------|----------|-----------|--------|----------|
| Random Forest (Credit Data) | 0.9999   | 0.9997    | 1.0    | 0.9999   |



## **Model Explainability**
### **SHAP**
- **Interaction Plot**: Visualized interaction effects between features like `V1` and `Time`.
- **Force Plot**: Explained individual predictions, highlighting key features like `V1` and `V11`.

### **LIME**
- **Feature Importance**: Identified features like `V3` and `V7` as strong contributors to non-fraud predictions.



## **Deployment**
The best-performing model (**Random Forest**) was logged using MLflow and can be deployed for real-time fraud detection. To deploy the model:
1. Load the model from the MLflow artifact store.
2. Set up a real-time prediction API using Flask or FastAPI.
3. Monitor model performance and retrain periodically.



## **Contributing**
Contributions to this project are welcome! If you find any issues or have suggestions for improvement, please open an issue or submit a pull request.



## **License**
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.



## **Contact**
For questions or feedback, please contact:
- **Sara Fedlu**
- **GitHub**: [SaraFedlu](https://github.com/SaraFedlu)
